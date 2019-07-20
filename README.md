# Bluffer's Guide to PHP development with Docker Compose

This doc should get you started with anything you need t quickly start things up

## Getting started

You will need a new folder structure:

```
__PROJECT_ROOT__/
__PROJECT_ROOT__/app                # To contain all your app's source code
__PROJECT_ROOT__/app/public         # The root of your PHP app
__PROJECT_ROOT__/docker-devenv      # The root of this repository (this README is located in this folder)
```

YOu can achieve this wityh the following...

```
mkdir exampleproject
cd exampleproject
mkdir app
git clone git@gitlab.com:uon-pd/some-example-php-project.git     # assuming this is the correct URL
mv some-example-php-project public                               # rename the cloned project's directory
cd ..
git clone git@gitlab.com:uon-pd/docker-devenv.git
git checkout feature/support-separate-repo-for-php-code
```

## Make sure Docker is running first

No Docker, no Docker Compose. Sort it.

## Startup

**Docs:** [docker-compose up](https://docs.docker.com/compose/reference/up/)

If you've not called this before, it will do a build and then start up all the containers

On subsequent runs, the build is already done, so it will start up super quick.

    docker-compose up -d

## Shutdown

**Docs:** [docker-compose down](https://docs.docker.com/compose/reference/down/)

    docker-compose down --remove-orphans

## Rebuild everything after config changes

**Docs:** [docker-compose build](https://docs.docker.com/compose/reference/build/)

    docker-compose build

## What's going on?

**Docs:** [docker-compose ps](https://docs.docker.com/compose/reference/ps/)

    docker-compose ps

## Empty the database and start again

    rm -rf ./docker/.data/*

## Using a separate repo for the PHP code

I've set this up so that I have the following structure

    <project-root>/
    <project-root>/app
    <project-root>/app/public                   # a separate repository for your php code
    <project-root>/docker-devenv                # this repo https://github.com/dvdsmpsn/docker-devenv/tree/feature/support-separate-repo-for-php-code
    <project-root>/docker-devenv/docker/.data   # docker setup for the mysql data directory  - content is ignored by the repo
    <project-root>/docker-devenv/docker/nginx   # docker setup for the separate nginx container
    <project-root>/docker-devenv/docker/php     # docker setup for the separate php container

## Connecting to the DB from PHP

Use the host name `db` with port `3306` and credentials from the [`docker-compose.yml`](docker-compose.yml) file.
