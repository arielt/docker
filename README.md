# Docker

Collection of Dockerfiles used in different projects.

## Useful commands

Build an image in Dockerfile's folder:

    docker build -t <Image Name>:<Tag> .

Stop and remove all docker containers:

    docker stop $(docker ps -a -q)
    docker rm $(docker ps -a -q)

Remove all dangling images:

    docker rmi $(docker images -f dangling=true -q)

Remove all images:

    docker rmi $(docker images -a -q)

Log into running container's shell:

    docker exec -it <Container Name> bash

Start container in interactive mode:

    docker run --rm --name <Container Name> -it <Image Name> bash
