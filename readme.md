# EXAMEN 23/10/23

Utiliza docker para poner en marcha Prestashop según esta [imagen](https://hub.docker.com/r/prestashop/prestashop/).

Describe el proceso en un documento Readme. Utiliza capturas para demostrar el funcionamiento en el navegador.

Se valorará:

* El uso de docker-compose
* Base de datos enlazados al PhpStorm
* Claridad en la explicación

## Inicio repositorio en GitHub y creo _.yml_

```bash
touch docker-compose.yml

```

## Configuracion Docker Compose

## Comprobacion
### Prestashop
![ip address](imagenes/ipaddr.png)

Buscar en el navegador DIRECCION_IP:PUERTO_HOST_PRESTASHOP
![instalacion presta](imagenes/install.png)

Instalamos Prestashop

### SQL
A. Desde el host usando el puerto 3307: 
```bash
$ docker ps   
CONTAINER ID   IMAGE                   COMMAND                  CREATED         STATUS         PORTS                                   NAMES
8840a9c35e6c   prestashop/prestashop   "docker-php-entrypoi…"   9 minutes ago   Up 9 minutes   0.0.0.0:8080->80/tcp, :::8080->80/tcp   examen_docker-prestashop-1
a90855b86e74   mysql:latest            "docker-entrypoint.s…"   9 minutes ago   Up 9 minutes   0/tcp, 3306/tcp, 33060/tcp              examen_docker-db-1
$ docker exec -it a90855b86e74 bash
```

Desde dentro del contenedor ejecutar `mysql -uroot -padmin -h localhost --port 3307`
Salida
```bash
mysql: [Warning] Using a password on the command line interface can be insecure.
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 9
Server version: 8.1.0 MySQL Community Server - GPL

Copyright (c) 2000, 2023, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 
```

B. Desde un contenedor en la red usando la URL
