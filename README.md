# Bluffer's Guide to PHP development with Docker Compose

This doc should get you started with anything you need t quickly start things up

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

Use the hosting `db` with port `3306` and credentials from the [`docker-compose.yml`](docker-compose.yml) file.