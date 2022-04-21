# Docker images

## Commands

To build docker image:

    docker build --tag ${NAME}:${TAG} --file ${PATH_TO_DOCKERFILE} ${DIRECTORY}

To create version tag:

    docket tag ${NAME}:${TAG} ${NAME}:${TAG}:${VERSION}

In command above you can pass `latest` to tag most recent version as latest

To push docker image:

    docker push ${NAME}:${TAG}:${VERSION}

You can also try to start container localy with:

    docker run -it ${NAME}:${TAG} /bin/bash
    docker run -it ${NAME}:${TAG} /bin/sh
