# Containerized MediaWiki parsoid service

This repo contains [Docker](https://docs.docker.com/) container to run the [Parsoid](https://www.mediawiki.org/wiki/Parsoid) application.

It is a part of [Containerized Mediawiki install](https://github.com/pastakhov/compose-mediawiki-ubuntu) project.

## Settings

- `PARSOID_DOMAIN_{domain}` defines uri and domain for parsoid service. The '{domain}' word should be the same as `MW_REST_DOMAIN` parameter in MediaWiki web container. You can specify any number of such variables (by the number of domains for the service)
- `PARSOID_NUM_WORKERS` defines the number of worker processes to the parsoid service. Set to `0` to run everything in a single process without clustering. Use `ncpu` to run as many workers as there are CPU units.
- `PARSOID_LOGGING_LEVEL` by default `info`

### Examples ###

The environment variable `PARSOID_DOMAIN_web=http://web/w/api.php` creates config contains:
```
mwApis:
  -
    uri: 'http://web/w/api.php'
    domain: 'web'
```
