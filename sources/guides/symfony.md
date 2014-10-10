# Swarmify PHP and Symfony

This page should get you started with PHP, Symfony and the Swarm. 

*TOC:*

* Swarmify PHP
* Dockerizing Symfony
* Swarmify Symfony

## Swarmify PHP 
To get PHP running in the Swarm is rather easy. Use the [official PHP image](https://registry.hub.docker.com/_/php/) build your own image from it, upload it and start it.

#### Start with a simple `Dockerfile`:

	# from https://registry.hub.docker.com/_/php/	
	FROM php:5.6-apache
	COPY . /var/www/html

If you look at [php:5.6-apache Dockerfile](https://github.com/docker-library/php/blob/e19f15271b1cbe9d3e5c9f0c552beca9579f0677/5.6/apache/Dockerfile) you will see that port 80 is exported and the default command is to start `httpd`.


#### Add a simple `index.php`:
	
	<? echo "<p>Hello from PHP</p>"; ?>

#### Build, test and upload the image:
	
	$ docker build -t luebken/hellophp .
	$ docker run -d -p 8080:80 luebken/hellophp
	$ curl localhost:8080
	$ docker push luebken/hellophp
 
#### Refer to that image in the `swarm.json`:

	{
	    "app_name": "hellophp",
	    "services": [
	        {
	            "service_name": "hellophp-service",
	            "components": [
	                {
	                    "component_name": "hellophp-component",
	                    "image": "luebken/hellophp",
						"ports": [ "80/tcp" ],
	                    "domains": { "hellophp.alpha.giantswarm.io": "80" }
	                }
	            ]
	        }
	    ]
	}

## Swarmify Symfony

Getting Symfony running in Docker and on the Swarm requires a couple of steps. To get a head start you can just clone our repo and use [fig](http://www.fig.sh/) to get everything up and running.

```
	$ git clone git@github.com:giantswarm/symfony-standard.git
	$ cd symfony-standard
	$ git checkout dockerize
	$ fig up
```

	TODO explain the steps

## Run a Symfony app on the Swarm
	
	TODO


