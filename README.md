# Bedrock Server Config

Docker compose file containing my Minecraft Bedrock server config.

It starts the following server:

- [`minecraft-bedrock-server`](https://hub.docker.com/r/itzg/minecraft-bedrock-server)

The Bedrock server config is just a collection of environment variables for configuring the world.

For Nintendo Switch players, the following should be added to `/etc/hosts`:

```
192.168.?.? geo.hivebedrock.network
192.168.?.? hivebedrock.network
192.168.?.? mco.mineplex.com
192.168.?.? play.inpvp.net
192.168.?.? mco.lbsg.net
192.168.?.? mco.cubecraft.net
192.168.?.? play.galaxite.net
192.168.?.? play.pixelparadise.gg
```

The IP is the local address of the Bedrock server. This should then be picked
up by `syntemd-resolved`, which should contain the folrlowing additional
config:

```
[Resolve]
DNS=8.8.8.8
DNSSEC=true
DNSOverTLS=yes
DNSStubListenerExtra=192.168.?.?
```

DNSSEC and DNSOverTLS are not so relevant here; the idea is to forward DNS
queries to `8.8.8.8`, but also use `/etc/hosts` to override the common servers
(again with the correct local address specified instead of `192.168.?.?`). This
works because `ReadEtcHosts` is set to `yes` by default.

The reason for this is that the Nintendo Switch doesn't allow 3rd party online
servers, instead it comes with a pre-selected list of six servers, one of which
is the Galaxite server. Overriding the DNS response allows connecting to any
server instead of Galaxite.
