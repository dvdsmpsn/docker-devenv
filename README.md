# Bluffer's Guide to Docker Compose

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

## Empty the datbase and start again

	rm -rf ./docker/.data/*