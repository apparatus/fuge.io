---
layout: main.html
---

# Getting started

## Install
To install, use npm to install globally.

```
npm install -g fuge
```

## Scaffold Generator
The scaffold generator creates a fully functional microservice system that is ready to run. Once generated you can add additional services manually or by using the service generator.

By default, fuge generates services in node.js using the Seneca microservices framework and the hapi web framework for the API layer.

To generate a fuge microservice system scaffold run:

```
mkdir mysystem
cd mysystem
fuge generate system
```

Fuge will ask you for some simple questions and then generate a system for you. The generated system looks as follows:

```
├── fuge
│   ├── compose-dev.yml
│   ├── docker-compose.yml
│   └── fuge-config.json
├── service1
│	└── Dockerfile
├── service2
│	└── Dockerfile
└── api
│	└── Dockerfile
├── static
└	└── Dockerfile
```

The structure has the following key files:

* fuge - contains configuration files
  * compose-dev.yml - a docker-compose yaml file that serves as the main configuration reference for the system
  * docker-compose.yml - a docker-compose yaml file that has a pre-configured fuge environment
  * fuge-config.json - contains fuge specific settings and overrides not supported by docker-compose
* service1 - contains a microservice using the Seneca framework
* service2 - contains a microservice using the Seneca framework
* api - contains a hapi or express REST api (based on your selection during initalization)
* static - contains a static file server for your front-end code. maps the api service to /api.

To start the generated system, execute:

```
fuge shell ./fuge/compose-dev.yml
```

You can then start services with `start`:
```
fuge> start
```

This will spin up the site and the two related microservices. Point your browser to http://localhost:10000/ to open the front end and exercise the microservices.

Fuge watches your code for changes and will automatically restart the front end and services as you make changes, providing a rapid development environment for integration testing and debugging.

To generate a new service you can run:

```
fuge generate service
```

Fuge will create a new service for you and will optionally add it into your compose-dev.yml.
