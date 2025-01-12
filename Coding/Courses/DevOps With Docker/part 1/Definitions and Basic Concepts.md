_devops_ means the release, configuring, and monitoring of software is in the hands of the very people who develop it.

_Docker_ is a set of tools to deliver software in containers.
_Containers_ are packages of software that include the application and its dependencies.

## Images and Containers

Containers are _instances_ of images.

Think of a _container as a ready-to-eat meal_ that you can simply heat up and consume. An _image is the recipe or ingredients_ for that meal.

In short, an _image is like a blueprint_ or template, while a _container is an instance of that blueprint_ or template.

### Images

A Docker image is a file. An image never changes; you can not edit an existing file. Creating a new image happens by starting from a base image and adding new **layers** to it. We will talk about layers later, but you should think of _images as immutable_, they can not be changed after they are created.

If images are used to create containers, where do images come from? This image file is built from an instructional file named **Dockerfile** that is parsed when you run `docker image build`.

Dockerfile is a file that is by default called _Dockerfile_, that looks something like this
```docker
FROM <image>:<tag>

RUN <install some dependencies>

CMD <command that is executed on `docker container run`>
```

If we go back to the cooking metaphor, as Dockerfile provides the instructions needed to build an image you can think of that as the recipe for images. We're now 2 recipes deep, as _Dockerfile is the recipe for an image and an image is the recipe for a container._ The only difference is that Dockerfile is written by us, whereas image is written by our machine based on the Dockerfile!
## commands

- `docker run <name_of_image>`
- `docker image ls`