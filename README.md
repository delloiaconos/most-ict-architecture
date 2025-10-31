# most-ict-architecture
MOST Spoke 5 - WP 3 ICT Architecture

This repository contains the full configuration, Docker setup, and supporting files for developing and deploying an **ICT architecture for data collection and integration** within the **MOST Spoke 5 Porject**.

The architecture is designed to enable flexible, modular, and containerized data acquisition, processing, and visualization across networked components.


## Overview

The system leverages **Docker Compose** to orchestrate multiple interoperable services that form the core of the data collection and management infrastructure.

Each component is isolated in its own container but connected through shared networks to ensure secure and scalable communication.

Typical components include:
- **Node-RED** — for data flow orchestration, processing, and integration with IoT devices or APIs.
- **Nginx** — as a lightweight reverse proxy and frontend router for web-based components.
- **InfluxDB** *(optional)* — for time-series data storage and retrieval.
- **WireGuard / VPN** *(optional)* — for secure remote data transmission.

## Running 

Make sure the external network most_net already exists:

```bash
docker network create most_net
```

Then you can bring up the stack:
```bash
docker-compose -p mostict up -d
```

or you can use:

```bash
export COMPOSE_PROJECT_NAME=mostict
docker-compose up -d
```

To stop and remove containers and networks, including volumes:

```bash
docker-compose down -v
```


If you used a custom project name (```mostict```):
```bash
docker-compose -p mostict down -v
```

## Some utility commands

### Running Nginx
```bash 
docker run --rm --entrypoint=cat nginx:1.29.3-alpine3.22 /etc/nginx/nginx.conf > nginx.conf
docker run -d -v /opt/most/nginx/nginx.conf:/etc/nginx/nginx.conf -p 80:80 --name most-nginx nginx:1.29.3-alpine3.22
docker exec most-nginx nginx -s reload
```


### Running Nodered

```bash
docker run -it -p 1880:1880 -v /opt/most/nodered:/data --name most-nodered nodered/node-red:4.1.1-22
```


# Fundings
This study was carried out within the MOST - Sustainable Mobility National Research Center and received funding from the European Union Next-GenerationEU (PIANO NAZIONALE DI RIPRESA E RESILIENZA (PNRR) - MISSIONE 4 COMPONENTE 2, INVESTIMENTO 1.4 - D.D. 1033 17/06/2022, CN00000023), Spoke 5 "Light Vehicle and Active Mobility". 
This work/code/repository reflects only the authors’ views and opinions, neither the European Union nor the European Commission can be considered responsible for them.
