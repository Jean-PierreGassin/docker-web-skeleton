
This guide will help you setup a Docker environment on a per application basis.

Docker is great for setting up multiple isolated containers which communicate with each other on a per-project basis; removing the need complicate and pollute development environments.

By default this installation uses nginx/apache, MySQL, and php-fpm (PHP 7) images - you can however change this to your liking or extend upon it.

- [Dependencies](#dependencies)
- [Installation](#installation)
	1. [docker-compose](#step-1-docker-compose)
	2. [File structure](#step-2-file-structure)
	3. [Configuration](#step-3-configuration)
	4. [Compose / Create containers](#step-4-compose-create-containers)
	5. [(Optional) - Application routing](#step-5-optional-application-routing)
- [Notes](#notes)
---

### Dependencies
If you haven't already, grab [Docker](https://www.docker.com/products/docker)

### Installation
#### Step 1 - docker-compose
if (you have [Homebrew](http://brew.sh/)) {<br>
&nbsp;&nbsp;&nbsp;&nbsp;run `brew install docker-compose`<br>
} else {<br>
	&nbsp;&nbsp;&nbsp;&nbsp;follow [these steps](https://docs.docker.com/compose/install/)
<br>}

#### Step 2 - File structure
Place your docker files inside your projects root, example structure:
```
-- docker
	-- docker-compose.yml
	-- Dockerfile
	-- site.conf
-- app
	-- public
 ```
 
#### Step 3 - Configuration
Configure your setup appropriately - you can find a list of helpful references on the Docker website:

[Compose References](https://docs.docker.com/compose/compose-file/) / [Dockerfile References](https://docs.docker.com/engine/reference/builder/)

#### Step 4 - Compose / Create containers
Run `docker-compose up` from your applications docker folder

#### Step 5 (Optional) - Application routing
Depending on your setup, you may want to configure hostnames and appropriate routing to your newly created application via /etc/hosts

### Notes
The docker containers can talk to each other via their designated names created in your docker-compose.yml file, for example the web container can talk to the db container by using db as the hostname of the MySQL connections IP address.

If you experience trouble with containers, you can remove them all and start from scratch with the following commands:
```
docker stop $(docker ps -a -q)
 
docker rm $(docker ps -a -q)
```

Or you can re-build your containers with `docker-compose up` again
