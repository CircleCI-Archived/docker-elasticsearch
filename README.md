docker-elasticsearch
====================

This is a simple example of building a Docker image from a Dockerfile using CircleCI's native Docker support,
starting a new container from the built image, running some tests against the container, then deploying the 
image to Docker Hub.

##The image

The image built in this example is an ElasticSearch node. It is borrowed from the official ElasticSearch Dockerfile maintained at [dockerfile/elasticsearch](https://github.com/dockerfile/elasticsearch). 

##Building and testing with CircleCI

Building the docker image on [CircleCI](https://circleci.com/) is as simple as requiring the docker service to be present and running `docker build` as usual. A container can then be created from the image using `docker run`, and various tests can be run against the container. See the file [circle.yml](circle.yml) for details, or refer to the [CircleCI docs for Docker](https://circleci.com/docs/docker).

##Deploying to Docker Hub

This example also deploys the built image to Docker Hub after a successfully building and testing. See the `deployment` section of [circle.yml](circle.yml) for details on how this is done. Note that two environment variables need to be set on CircleCI for the deployment to work:

* DOCKER_EMAIL - The email address associated with the user with push access to the Docker Hub repository
* DOCKER_AUTH - The auth token associated with the above user (as it appears in `~/.dockercfg` after logging into Docker Hub from the command line)

##See also
* [CircleCI Home](https://circleci.com)
* [The CircleCI Docker docs](https://circleci.com/docs/docker)
* [The Docker userguide](http://docs.docker.com/userguide/)
* [Docker Hub](https://hub.docker.com/)
