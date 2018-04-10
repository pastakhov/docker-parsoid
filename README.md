# MediaWiki Parsoid with Docker

[![Docker Pulls](https://img.shields.io/docker/pulls/thenets/parsoid.svg?style=flat-square&maxAge=86400)](https://hub.docker.com/r/thenets/parsoid/)

This repo contains [Docker](https://docs.docker.com/) container to run the [Parsoid](https://www.mediawiki.org/wiki/Parsoid) application.

It is a part of [Containerized Mediawiki install](https://github.com/pastakhov/compose-mediawiki-ubuntu) project created by [Pavel Astakhov](https://github.com/pastakhov).

## What Is Included?
- Alpine
- Parsoid

## How to deploy
To start the [Parsoid](https://www.mediawiki.org/wiki/Parsoid) run the command below. Just pay attention to MediaWiki version and choose a compatible Parsoid version.

```
# For MediaWiki 28, 29 and 30
docker run -it -p 8080:80 -e PARSOID_DOMAIN_localhost=http://localhost/w/api.php thenets/parsoid:0.8.0

# For MediaWiki 31
docker run -it -p 8080:80 -e PARSOID_DOMAIN_localhost=http://localhost/w/api.php thenets/parsoid:0.9.0
```

## Settings

- `PARSOID_DOMAIN_{domain}` defines uri and domain for parsoid service. The '{domain}' word should be the same as `MW_REST_DOMAIN` parameter in MediaWiki web container. You can specify any number of such variables (by the number of domains for the service)
- `PARSOID_NUM_WORKERS` defines the number of worker processes to the parsoid service. Set to `0` to run everything in a single process without clustering. Use `ncpu` to run as many workers as there are CPU units.
- `PARSOID_LOGGING_LEVEL` by default `info`

The environment variable `PARSOID_DOMAIN_web=http://web/w/api.php` creates config contains:
```
mwApis:
  -
    uri: 'http://web/w/api.php'
    domain: 'web'
```
