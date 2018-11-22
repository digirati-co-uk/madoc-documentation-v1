---
name: Installation
warning: This repository is not yet published so may not be available.
order: 0
---

# Installation

Get started quickly with the Madoc Platform with Docker and a prebuilt database, with our modules configured.

To get started, pull down the madoc-platform repository

```
$ git clone https://github.com/digirati-co-uk/madoc-platform.git
```

Move into the repository, and run

```
$ docker-compose up -d
```

You should now be able to access the site at [http://localhost:8888](http://localhost:8888) and the W3C annotation server at [http://localhost:8889](http://localhost:8889).

You can stop the service at any time using

```
$ docker-compose down
```

<div class="fesk-info">
  This is process is intended for local development environments only. You shold refer to our deployment documentation to install on to a server.
</div>

## System requirements

We bundle a full annotation server into our distribution. You can change this in the `docker-compose.yaml` file if you need to. With the annotation server its recomendded to run this with at least `4GB` or memory free.
