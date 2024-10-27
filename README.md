# docker-compose-n8n-postgres-lt
Docker compose file to create a n8n with PostgreSQL and Localtunnel

This repository contains a Docker Compose file that sets up n8n (a workflow automation tool) using PostgreSQL as the database backend and Localtunnel to expose n8n to the public internet.

## Prerequisites

Before you begin, ensure you have Docker and Docker Compose installed on your system. For installation instructions, refer to the [official Docker documentation](https://docs.docker.com/get-docker/).

## Setup

To get started with this setup, clone this repository and navigate into the directory:
```bash
git clone https://github.com/AllanAV/docker-compose-n8n-postgres-lt.git
cd docker-compose-n8n-postgres-lt
```

## Running the Services

To start all services, run the following command in the root of this directory:
```bash
docker-compose up -d
```
This command will start all required services in the background.

## Accessing n8n

Once the services are running, you can access n8n locally by visiting [http://localhost:5678](http://localhost:5678) or externally using the unique localtunnel URL, as long as your local instance of lt remains active. Any requests will be routed to your local service at the specified port. The URL can be obtained from the Localtunnel logs, by running:
```bash
docker-compose logs -f lt
```

Look for a line similar to:
```bash
your localtunnel url is: https://yoursubdomain.loca.lt
```
Visit this URL in your web browser to access n8n.

Access to the tunnel is restricted by password, which can be retrieved by accessing https://loca.lt/mytunnelpassword
Use this password when prompted.

## Stopping the Services
To stop and remove the containers, use:

```bash
docker-compose down
```

## Updating n8n

To update n8n to the latest version, follow the steps provided in the official [n8n Docker Update documentation](https://docs.n8n.io/hosting/installation/docker/#updating).

## Credits and References:

- n8n Docker setup with PostgreSQL: [n8n official GitHub repository](https://github.com/n8n-io/n8n-hosting/tree/main/docker-compose/withPostgres)
- Localtunnel with Docker Compose tutorial: [LocalTunnel.me with Docker Compose](https://medium.com/@baldrailers/localtunnel-me-with-docker-compose-b432b1d48f7f)
