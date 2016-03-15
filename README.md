# alfresco

Alfresco Community Edition docker image

## Updates

1. Updated to version 5.1.e (201602-GA)
2. Configured Alfresco-Solr4 communication to be plain HTTP
3. Added LibreOffice external connection [LibreOffice docker image example](https://hub.docker.com/r/keensoft/libreoffice)
4. Updated docker-compose.yml file to version 2
5. Added ImageMagick configuration
6. Added AOS Module
7. Added Google Docs intregration amps
8. Added JConsole addOn

## Manual Startup

* First thing we need is a PostgreSQL database to connect to, if you haven't one already, just run it with docker

	docker run --name postgres -e POSTGRES_DB=alfresco -e POSTGRES_USER=alfresco -e POSTGRES_PASSWORD=alfresco -d postgres

* Second, we need a LibreOffice instance that Alfresco will use as a [Trasnformation server](https://hub.docker.com/r/keensoft/libreoffice/) (in TCP 8100 by default)

	docker run --name libreoffice -d keensoft/libreoffice:latest

* Third, build this docker image

	docker build -t \(your_tag\) .

* And lastly run the dockerized Alfresco 

	docker run --name \(your_name\) --link postgres:postgres --link libreoffice:libreoffice -p 8080:8080 -d \(your_tag\)
	

## Docker Compose

* You can also find a [docker-compose](https://docs.docker.com/compose/compose-file/) configuration file, which uses "depends-on" directive (Compose file version 2) to ensure components follow desired order starting and stopping services.

	docker-compose up -d 


## Access 

	http://localhost:8080/share (admin/admin)


