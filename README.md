# Containerized MediaWiki parsoid service

This repo contains [Docker](https://docs.docker.com/) container to run the [Parsoid](https://www.mediawiki.org/wiki/Parsoid) application.

It is a part of [Containerized Mediawiki install](https://github.com/pastakhov/compose-mediawiki-ubuntu) project.

## Settings

- `NUM_WORKERS` defines the number of worker processes to the parsoid service. Set to `0` to run everything in a single process without clustering. Use `ncpu` to run as many workers as there are CPU units.
- `PARSOID_DOMAIN_{domain}` defines uri and domain for parsoid service. You can specify any number of such variables (by the number of domains for the service)

### Examples ###

The environment variable `PARSOID_DOMAIN_localhost=http://mywiki/w/api.php` creates config contains:
```
mwApis:
  -
    uri: 'http://mywiki/w/api.php'
    domain: 'localhost'
```
