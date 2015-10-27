# CS:GO Server Dockerfile

This repository contains **Dockerfile** of [CS:GO Server](http://gameservermanagers.com/lgsm/csgoserver/) for [Docker](https://www.docker.com/) published to the public [Docker Hub Registry](https://registry.hub.docker.com/).

### Base Docker Image

* [ubuntu:14.04](https://hub.docker.com/_/ubuntu/)


### Installation

1. Install [Docker](https://www.docker.com/).

2. Download [automated build](https://registry.hub.docker.com/u/johnjelinek/csgoserver/) from public [Docker Hub Registry](https://registry.hub.docker.com/): `docker pull johnjelinek/csgoserver`

   (alternatively, you can build an image from Dockerfile: `docker build -t="johnjelinek/csgoserver" github.com/johnjelinek/csgoserver-docker`)


### Usage

    docker run -dt --name csgo -v /var/docker/csgoserver:/home/csgoserver \
    -p 27015:27015/tcp -p 27015:27015/udp --entrypoint /home/csgoserver/serverfiles/srcds_run \
    johnjelinek/csgoserver -game csgo -usercon -strictportbind -ip 0.0.0.0 -port 27015 \
    +clientport 27005 +tv_port 27020 -tickrate 64 +map de_dust2 +servercfgfile csgo-server.cfg \
    -maxplayers_override 16 +mapgroup random_classic +game_mode 0 +game_type 0 \
    +host_workshop_collection  +workshop_start_map  -authkey

#### Preparation (Downloading the files onto your volume)

  1. Copy `/csgoserver` to `~/csgoserver`

  2. `./csgoserver install`

  3. Answer some questions

  4. You can test everything went well with `./csgoserver start` followed by `./csgoserver details`.

  5. If everything looks good, run with the command listed under `Usage`.

Open CS:GO and Browse Community Servers. Open `yourServerIP` to see the result.
