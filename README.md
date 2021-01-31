# Bedrock Server Config

Docker compose file containing my Minecraft Bedrock server config.

It starts two servers:

- [`minecraft-bedrock-server`](https://hub.docker.com/r/itzg/minecraft-bedrock-server)
- [`bind9`](https://hub.docker.com/_/bind9)

The Bedrock server config is just a collection of environment variables for configuring the world.

The BIND9 server is a simple recursive DNS proxy with one exception: `play.galaxite.net.` resolves as a `CNAME` to `home.attilaolah.eu.`, where I run the server.

The reason for this is that the Nintendo Switch doesn't allow 3rd party online servers, instead it comes with a pre-selected list of six servers, one of which is the Galaxite server. Overriding the DNS response allows connecting to any server instead of Galaxite.
