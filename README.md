docker-maven
============

# Supported tags and respective Dockerfile links

* [3.2](https://github.com/carlossg/docker-maven/blob/master/jdk-7/Dockerfile), [3](https://github.com/carlossg/docker-maven/blob/master/jdk-7/Dockerfile), [3.2-jdk-7](https://github.com/carlossg/docker-maven/blob/master/jdk-7/Dockerfile), [3-jdk-7](https://github.com/carlossg/docker-maven/blob/master/jdk-7/Dockerfile)
* [3.2-onbuild](https://github.com/carlossg/docker-maven/blob/master/jdk-7/onbuild/Dockerfile), [3-onbuild](https://github.com/carlossg/docker-maven/blob/master/jdk-7/onbuild/Dockerfile), [3.2-jdk-7-onbuild](https://github.com/carlossg/docker-maven/blob/master/jdk-7/onbuild/Dockerfile), [3-jdk-7-onbuild](https://github.com/carlossg/docker-maven/blob/master/jdk-7/onbuild/Dockerfile)
* [3.2-jdk-6](https://github.com/carlossg/docker-maven/blob/master/jdk-6/Dockerfile), [3-jdk-6](https://github.com/carlossg/docker-maven/blob/master/jdk-6/Dockerfile)
* [3.2-jdk-6-onbuild](https://github.com/carlossg/docker-maven/blob/master/jdk-6/onbuild/Dockerfile), [3-jdk-6-onbuild](https://github.com/carlossg/docker-maven/blob/master/jdk-6/onbuild/Dockerfile)
* [3.2-jdk-8](https://github.com/carlossg/docker-maven/blob/master/jdk-8/Dockerfile), [3-jdk-8](https://github.com/carlossg/docker-maven/blob/master/jdk-8/Dockerfile)
* [3.2-jdk-8-onbuild](https://github.com/carlossg/docker-maven/blob/master/jdk-8/onbuild/Dockerfile), [3-jdk-8-onbuild](https://github.com/carlossg/docker-maven/blob/master/jdk-8/onbuild/Dockerfile)

# What is Maven?

[Apache Maven](http://maven.apache.org) is a software project management and comprehension tool.
Based on the concept of a project object model (POM),
Maven can manage a project's build,
reporting and documentation from a central piece of information.


# How to use this image

## Create a Dockerfile in your Maven project

    FROM maven:3.2-jdk-7-onbuild
    CMD ["do-something-with-built-packages"]

Put this file in the root of your project, next to the pom.xml.

This image includes multiple ONBUILD triggers which should be all you need to bootstrap.
The build will `COPY . /usr/src/app` and `RUN mvn install`.

You can then build and run the image:

    docker build -t my-maven .
    docker run -it --name my-maven-script my-maven


## Run a single Maven command

For many simple projects, you may find it inconvenient to write a complete `Dockerfile`.
In such cases, you can run a Maven project by using the Maven Docker image directly,
passing any Maven goals to `docker run`:

    docker run -it --rm --name my-maven-project -v "$(pwd)":/usr/src/mymaven -w /usr/src/mymaven maven:3.2-jdk-7 clean install


# User Feedback

## Issues

If you have any problems with or questions about this image, please contact us
through a [GitHub issue](https://github.com/carlossg/docker-maven/issues).

You can also reach many of the official image maintainers via the `#docker-library` IRC channel on Freenode.

## Contributing

You are invited to contribute new features, fixes, or updates, large or small; we are always thrilled to receive pull requests, and do our best to process them as fast as we can.

Before you start to code, we recommend discussing your plans through a [GitHub issue](https://github.com/carlossg/docker-maven/issues),
especially for more ambitious contributions.
This gives other contributors a chance to point you in the right direction,
give you feedback on your design, and help you find out if someone else is working on the same thing.
