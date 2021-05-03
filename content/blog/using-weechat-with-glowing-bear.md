---
title: "Using Weechat with Glowing Bear for IRC"
date: 2019-07-02T00:28:48+05:30
tags: ["programming", "tools"]
---

Last month, I had a new addition to my toolbox - [Glowing
Bear][gb], which has been a really nice improvement, allowing me to access
Weechat (hosted on a server) through my browser. Here's how I set it up.

But, before we begin - the curious folks might ask, "What had you been using
all this time?"

Previously, I could directly ssh[^1] into my server, and attach to a
[`screen`][screen] session which ran weechat, using the command:

[^1]: Using mosh - 'mobile shell', which supports intermittent connectivity,
which is to say that it allows me to retain the session if the network breaks in
between.

```sh
mosh USERNAME@SERVER_IP -- screen -D -RR weechat
```

This is pretty neat, why would you want to change it?

"Latency"  -  It was not pleasant, so much so, that I started running two
instances of weechat - one locally for chatting, and the one on the server for
listening to messages when AFK. It was getting pretty unmanageable, so I decided
to look for alternatives. Luckily, one of my friends, [Armageddon][armageddon],
pointed me towards [Glowing Bear][gb] - which provides a nice web frontend to
weechat.

## Setting Up Glowing Bear

Glowing Bear has pretty decent documentation available at
[https://www.glowing-bear.org/#!/][gb].

The basic architecture is somewhat similar to the [ pub-sub architecure
][pubsub] - weechat 'relays' (publishes) all messages at a particular port on
a machine where glowing bear can then 'listen' for the messages (subscribe).

Can other people listen to my messages?

If you're running glowing bear with a local instance of weechat, you shouldn't
worry too much. However, if connecting to a remote instance, you must encrypt
all communications between your browser and WeeChat.

Since [Glowing Bear][gb] uses TLS for encryption, it means that we need to put
up a signed certificate. They recommend using [Let's Encrypt][letsencrypt] for
getting a certificate, which is really easy. Just install [certbot][certbot] and
run:

```
certbot certonly --standalone -d DOMAIN_NAME
```

Once the certificates are generated, the only thing was to make them
visible to weechat:

```bash
$ mkdir -p ~username/.weechat/ssl
$ cat /etc/letsencrypt/live/DOMAIN_NAME/{fullchain,privkey}.pem > ~username/.weechat/ssl/relay.pem
$ chown -R username:username ~username/.weechat/ssl/
```

Now, the only issue with me was that I did not have superuser access to the box
I was running weechat into, and therefore could not access cert files. But,
After talking to my wonderful host at [insomnia247.nl][insomnia]:
[coolFire][cF], I came to know that certificates I'm using for my Apache VHost
should be enough to encrypt my communication (through port 443) and I need not
start an encrypted relay from weechat. coolFire was also gracious enough to
throw in some voodoo {% sidenote 'voodoo-id' "of course, by which I mean that I didn't
understand it" %} and give me a custom URL for running my weechat instance.

Now, let's start a WeeChat relay:

```
/set relay.network.password y0ur_StRonG-pa$sw0rd:of*choice
/relay add weechat 9001 # Note that this is NOT encrypted.
```

For connecting to Glowing Bear, I use port 443 - which allows me to encrypt my
connection. Note that this isn't entirely safe, because the fellow users on my
host can still monitor port 9001, which is unecrypted and only protected by a
password. But, I can manage this level of risk! :-)

## Icing over cake

I run glowing bear on qutebrowser, through which I can access the whole interface
without ever having to leave the comfort of my keyboard. \o/

## Further TODO's

Glowing Bear's notification system is a little weird - it just stops notifying
me out of the blue. Remember my friend, [Armagaeddon][armageddon] - he actually
has a weechat plugin for channeling remote notifications to local systems, but
it turned out that the script will take some additional work to work with macOS.

Another thing that I want to do is employ a chat logger - I've had some pretty
interesting conversation with people, and they just wash away as soon as I
restart weechat. This should be pretty easy to do, but I've had too much on my
plate to care right now.

[armageddon]: https://blog.lazkani.io/about_me/
[gb]:  https://www.glowing-bear.org/#!/
[insomnia]: https://wwww.insomnia247.nl
[letsencrypt]: https://letsencrypt.org/
[certbot]: https://certbot.eff.org/
[cF]: https://git.insomnia247.nl/coolfire
[screen]: https://www.gnu.org/software/screen/
[pubsub]: https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern
