---
name: Installation
order: 0
---

# Installation

Get started quickly with the Madoc Platform with Docker and a prebuilt database, with our modules configured.

To get started, pull down the madoc-example-config repository

```
$ git clone https://github.com/digirati-co-uk/madoc-example-config.git
```

Move into the repository, and run

```
$ docker-compose up -d
```

You should now be able to access the site at [http://localhost:8898](http://localhost:8898) and the W3C annotation server at [http://localhost:8899](http://localhost:8899).

You can stop the service at any time using

```
$ docker-compose stop
```

If you want to view the logs of the running containers, you can run:
```
$ docker-compose logs -f --tail=50
```

<div class="fesk-info">
  This is process is intended for local development environments only. You shold refer to our deployment documentation to install on to a server.
</div>

## System requirements

We bundle a full annotation server into our distribution. You can change this in the `docker-compose.yaml` file if you need to. With the annotation server its recommended to run this with at least `4GB` or memory free.
