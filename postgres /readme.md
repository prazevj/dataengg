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
