# Express-Dockerized
This README was written for OSX, but this repository is platform agnostic.

### Prerequisites:

Install Docker & boot2docker.
Make sure boot2docker is running:

`boot2docker status`

Install the Node docker image

`docker pull node`


This repository was tested with the Node `0.10-onbuild` image.

<hr>

### Instructions

#### Config
This is a Node.js application. Therefore, the packages listed in packages.json need to be installed. In order to accomplish this, in Project-root and ExpressApp directories run:
`npm install`


Now, you need to build an image from this Repo and docker-file, Navigate to the project's root directory and issue the following command:

`docker build -t $USERNAME/bare-express-app .`

You should now see your docker image listed when you run `docker images`


#### Deploy
To run your container:

`docker run -d -P --name ExpressApp $USERNAME/bare-express-app`

Find the ip address of the boot2docker VM:
`boot2docker ip` : XXX.XXX.XX.XXX

Find the port your app is running on:
`docker port ExpressApp`, it should say something like `3000/tcp -> 0.0.0.0:34873`

In your browser, type the boot2docker ip, followed by the container port:
ex: `XXX.XXX.XX.XXX:34873`

You should now see the Welcome To Express home-page!
