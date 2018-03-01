# glsdk-deploy
Travis deployment definition for the Grand Lyon Software Development Kit (glsdk)

## How does it work ?
This project contains different things that are needed to automate the application deployment:
* A docker-compose.yml file that describes the entire environment and that can be used anywhere to start the application (see [Docker Compose documentation](https://docs.docker.com/compose/overview/))
* An integration folder containing a set of files necessary to deploy on the integration environment
* A travis file that uses everything described above to de automatically deploy the application on the integration environment

## What to do if I want to add another environment ?
Just copy the integration folder, make the changes you need and run docker-compose by passing the new environment name as environment variable. Example: `ENVIRONMENT=production docker-compose up -d`.

## What do I have to change in the environment folder ?
Right now, the folder contains :
* A bunch of `*.env` files containing environment variables needed by the application to work on a specific environment
* A `docker-certs` folder containing a bunch of certificates and an encrypted key to connect to the Docker deamon of the remote environment (more information on how to encrypt files with Travis [here](https://docs.travis-ci.com/user/encrypting-files/).