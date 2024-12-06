## Setting Up Postgres in a Local Environment with Docker

Pulling the Postgres Docker Official Image is the fastest way to get started. 
In your terminal, enter ``docker pull postgres`` to grab the latest Postgres version from Docker Hub. 

Alternatively, you can pin your preferred version with a specific tag. Though we usually associate pinning with Dockerfiles, the concept is similar to a basic pull request. 

For example, you’d enter the ``docker pull postgres:14.5`` command if you prefer postgres v14.5. Generally, we recommend using a specific version of Postgres. 
The ``:latest version`` automatically changes with each new Postgres release — and it’s hard to know if those newer versions will introduce breaking changes or vulnerabilities.

### Start a Postgres instance
Enter the following docker run command to start a new Postgres instance or container: 

``docker run --name postgres-container -e POSTGRES_PASSWORD=mysecretpassword -d postgres:14.5``

If you haven't mentioned any version details please use the below command to start the postgres container

``docker run --name postgres-container -e POSTGRES_PASSWORD=mysecretpassword -d postgres``

You can choose to setup your own ``POSTGRES_PASSWORD`` in the above command.

## Installing PgAdmin4

PgAdmin 4 is a popular web-based administration and management tool for PostgreSQL. It provides a user-friendly interface that lets you interact with your databases, execute SQL queries, monitor database performance, and much more, without having to navigate complex command lines


Input the following command into your terminal to install pgAdmin 4:

``docker pull dpage/pgadmin4``

Here is the command to run the pgAdmin 4 docker container:

``docker run --name pgadmin-container -p 5050:80 -e PGADMIN_DEFAULT_EMAIL=admin@admin.com -e PGADMIN_DEFAULT_PASSWORD=mypassword -d dpage/pgadmin4``

You can replace with your own ``PGADMIN_DEFAULT_EMAIL`` and ``PGADMIN_DEFAULT_PASSWORD`` in the above command and this will be required to login to the web page of the PgAdmin.


## Using Docker Compose

Since you’re likely using multiple services, or even a database management tool, Docker Compose can help you run instances more efficiently. With a single YAML file, you can define how your services work. Here’s an example for Postgres:

```yaml

services:
  db:
    image: postgres
    restart: always
    environment:
      POSTGRES_PASSWORD: example
    volumes:
      - pgdata:/var/lib/postgresql/data 
 
  adminer:
    image: adminer
    restart: always
    ports:
      - 8080:8080
 
volumes:
  pgdata:
```
