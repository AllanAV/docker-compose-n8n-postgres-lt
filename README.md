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

IMPORTANT: Before you do that change the default users and passwords in the [.env](https://github.com/AllanAV/docker-compose-n8n-postgres-lt/blob/main/.env) file!

To start all services, run the following command in the root of this directory:
```bash
docker-compose up -d
```
This command will start all required services in the background.

## Accessing n8n

Once the services are running, you can access n8n locally by opening [http://localhost:5678](http://localhost:5678).

### with localtunnel

> **WARNING**: Use for local development and testing only. DO NOT use in production!

[https://github.com/n8n-io/localtunnel](https://github.com/n8n-io/localtunnel) redirects requests from lt servers to your local n8n instance, making n8n reachable from the web enabling the use of webhooks with all triggers of external services. 
As long as your local instance of lt remains active, any requests will be routed to your local service at the specified port. 
The URL can be obtained from the Localtunnel logs, by running:

```bash
docker-compose logs -f lt
```

Look for a line similar to:
```bash
your localtunnel url is: https://<random_subdomain>.loca.lt
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
- The official n8n documentation can be found under: [https://docs.n8n.io](https://docs.n8n.io)
- Additional information and example workflows on the n8n.io website: [https://n8n.io](https://n8n.io)
