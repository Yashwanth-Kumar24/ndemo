# Guide
## Follow this document after cloning it to run 3-tier arch app.

-  Clone the repository and move to ToDoApp directory
- Execute below commands in ToDoApp dir

### Pre-requisites:
- Docker (https://docs.docker.com/engine/install/)



### Steps:-
#### Create network
- `docker network create todoapp`



#### Create postgres
- `docker run -d -e POSTGRES_PASSWORD=postgres -e POSTGRES_USER=postgres -e POSTGRES_DB=todoAppDB --name postgres --network todoapp postgres`



#### Login into the container.
- `docker exec -it postgres psql todoAppDB postgres`

- Run the script present in `db_script` file inside the psql cli (from previous step)


##### Create redis
- `docker run -d --name redis --network todoapp redis /bin/bash -c "redis-server --appendonly yes --requirepass redis"`



#### Enter the container names for postgres and redis in Dotnet/appsettings.json before building the image
#### create image for dotnet API by moving in dotnet dir
- `cd Dotnet`
- `docker build -t dotnet-image .`
- `cd ../`

#### Run container, supply the port you want the api to run on.
`docker run -d --name apiapp --network todoapp -p 5000:80 dotnet-image`

- once done, check api app on http://localhost:5000/swagger
- To test db and redis connections, go to localhost:5000/swagger (port given as you) and test by executing GET and POST calls
- FOR Postgres GET execute, POST {"name":"string"}


- Before building image for angular web app provide the API url in src/environments/environment.ts file (localhost:port port as given in apiapp container)

#### Create the image for Angular web app by buidling image in Angular dir
- `cd Angular`
- `docker build -t webapp-image .`
- `cd ../`