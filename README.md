# Nymph
My attempt to build a point of sale in Django using docker as my dev env.

This will be an administrative system to handle:
  * Users
  * Products
  * Sales
  * Inventory
  * Reports


## Setup Dev environment
I will explain this step by step in case I forget how to walk again.
### Requirements
* Docker installed

### Clone the repository
On your terminal, move to the directory where you want to clone the
```shell
$ git clone https://github.com/VictorAbdon/Nymph.git
```

Move into the root folder and compose with docker
```shell
$ docker-compose up
```
This will create 2 images on your system, for the web service and db (postgres).

Navigate to `localhost:8000` and the project should be running.

If you want to change the port where it runs, go to `docker-compose.yml` and change it

**That's it! you are all done!**

If you want more technical stuff, keep reading.

#### Connect to Docker container
If you want to connect to the docker container to do some extra stuff you can do it like this:
```shell
$ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                    NAMES
af30d88ca3bf        nymph_web           "python manage.py ru…"   27 minutes ago      Up 27 minutes       0.0.0.0:8000->8000/tcp   nymph_web_1
2f0a0431624e        postgres            "docker-entrypoint.s…"   29 minutes ago      Up 29 minutes       5432/tcp                 nymph_db_1
```

That will give you a list of all running containers, then you can ssh to it.
```shell
$ docker exec it <CONTAINER-ID> bash
```

If you want to do some queries over the postgresql database, once you are connected to the container you can login to `psql`
``` shell
$ psql -U postgres
```

## Deploy to production
Change the configuration under `nymph_project/settings.py` with the values you will use in prod.
