# most-ict-architecture
MOST Spoke 5 - WP 3 ICT Architecture



## Utilities

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
