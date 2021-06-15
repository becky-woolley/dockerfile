# dockerfile
A repository to get familiar with docker and creating dockerfiles.

A very basic flask app, hello.py, has been created, which runs in a container defined by Dockerfile.

This was done following two tutorials from the Docker docs:
 - Python: [Build Images](https://docs.docker.com/language/python/build-images/)
 - Python: [Run Conatiners](https://docs.docker.com/language/python/run-containers/)
 
### Building the image
To build the image, with the tag "python-docker", run the following command:
```
$ docker build --tag python-docker .
```

To list docker images run
```
$ docker images
```

### Running the container
To run the container in isolation, use the following command
```
$ docker run python-docker
```

However, this will mean we cannot connect to our app because the container is run in total isolation.
Instead, what we want to do is specify a port to run the application on.

The default port in the container is 5000. If we want to connect on ```localhost:5000``` then we will need to map the hosts' port 500 to the container's port 500.
```
$ docker run --publish 5000:5000 python-docker
```

If we wanted to expose port 5000 inside the container to port 3000 outside of the container, we would pass ```3000:5000``` to the ```--publish``` flag.

We can open a new terminal and run
```
$ curl localhost:5000
```
 

