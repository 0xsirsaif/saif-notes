Docker
=======

* ``docker ps`` list running containers
* ``docker ps -a [or --all]`` list all containers
* ``docker cp [from] containerid:[to]`` copy to containers

Notes: Test-drivenio: `Docker best practices <https://testdriven.io/blog/docker-best-practices/>`_ 
-----------------------------------------------------------------------------------------------------

Multi-stage: Builder Pattern
******************************
* `alexellis blog <https://blog.alexellis.io/mutli-stage-docker-builds/>`_ 
* keeping the image size down.
* Before multi-stage: Each instruction in the Dockerfile adds a layer to the image, and you need to remember to clean up any artifacts you don’t need before moving on to the next layer.
* With multi-stage builds, you use multiple FROM statements in your Dockerfile. Each FROM instruction can use a different base, and each of them begins a new stage of the build. You can selectively copy artifacts from one stage to another, leaving behind everything you don’t want in the final image. You only need the single Dockerfile. You don’t need a separate build script, either.  You don’t need to create any intermediate images and you don’t need to extract any artifacts to your local system at all.
* Stop at specific build: ``docker build --target [stage name]``
* Use an external image as a stage: [local image name, a tag available locally or on a Docker registry, or a tag ID.]

Order Dockerfile Commands Appropriately
****************************************
* Docker caches each step (or layer) in a particular Dockerfile to speed up subsequent builds. When a step changes, the cache will be invalidated not only for that particular step but all succeeding steps.
* Always put layers that are likely to change as low as possible in the Dockerfile.

Use Smaller Base images
*************************
* Which Docker base image should you use? __ Unfortunately, it depends.While the Alpine flavor, based on Alpine Linux, is the smallest, it can often lead to increased build times if you can't find compiled binaries that work with it.
* In the end, it's all about balance. When in doubt, start with a ``*-slim`` flavor, especially in development mode.
* Also, don't forget to update your base images regularly to improve security and boost performance.

Minimize the Number of Layers
******************************
* ``docker history [docker-img-name]``
* Combine ``ADD``, ``RUN`` and ``COPY`` commands as mush as possible. using the ``&&`` operator for examble. 

Use Unprivileged Containers?
*****************************

Cache Python Packages to the Docker Host
*****************************************
* When a requirements file is changed, the image needs to be rebuilt to install the new packages. You can avoid this by mapping the pip cache directory to a directory on the host machine. So for each rebuild, the cached versions persist and can improve the build speed.


Run Only One Process Per Container
***********************************

Prefer Array Over String Syntax
*********************************
* You can write the CMD and ENTRYPOINT commands in your Dockerfiles in both array (exec) or string (shell) formats
* Using the string form causes Docker to run your process using bash, which doesn't handle signals properly.
* Compose always uses the JSON form, so don't worry if you override the command or entrypoint in your Compose file.
* ``CTRL-C`` won't kill the process. Instead, you'll see ``^C^C^C^C^C^C^C^C^C^C^C``.

Understand the Difference Between ENTRYPOINT and CMD
*****************************************************
* An ``ENTRYPOINT`` allows you to configure a container that will run as an executable.
* Command line arguments to ``docker run <image>`` will be appended after all elements in an ``exec`` form ``ENTRYPOINT``, and will override all elements specified using CMD. This allows arguments to be passed to the entry point
* The ``CMD`` is easily overridden. Whereas to override the ``ENTRYPOINT`` command, one must specify the ``--entrypoint`` option
* Thus, ``CMD`` can be used to pass arguments to the ``ENTRYPOINT`` command.
* If you need to write a starter script for a single executable, you can ensure that the final executable receives the Unix signals by using ``exec`` and ``gosu`` commands: ``exec "$@"`` is an array-like construct of all positional parameters.