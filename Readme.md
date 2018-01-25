# Docker Orchestration for ESD Review Tool

## Installation

1. Install [Docker 1.10.3](https://docs.docker.com/engine/installation/linux/centos/).

2. Install [Docker Compose 1.6.2](https://docs.docker.com/compose/install/).

## Usage

### Development

There is a `Makefile` that will

* create `./src/` and `./data/{filestorage,blobstorage}`
* checkout `esdrt.content` and `esdrt.theme`
* set proper `facl` permissions

In `./devel`:

    $ make

Copy the `Data.fs` (if you have one) in `./data/filestorage` and then:

    $ docker-compose up -d
    $ docker-compose exec plone bash
    $ ./bin/standalone fg

If working on an empty database: head to http://localhost:8080, add a Plone site and install the following add-ons:

* `EEA Plone buildout profile`
* `esdrt.theme`
* `esdrt.content`

If working on a production database replica, go to `http://localhost:8080/Plone/memcached/manage_main` and
make sure "Servers" is set to `memcached:11211`. This will cache LDAP responses between instance restarts.


### Deployment

Deployment orchestration can be found on SVN.
