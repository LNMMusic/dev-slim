## MODE SWITCH [Local - Docker]
This case is being used a docker version of Mask (not manual networking, instead name of each service as host)

**Database**
- Check mysql not open while using docker [both use the same port, this could be fix using mysql image on other port]

**Backend**
- Check env.env file

**Frontend**
- Check proxy on package.json
    ∟ Local:    http://localhost:8080
    ∟ Docker:   http://backend:8080

<br>
<br>

## MODE RUN
**Development**
- Run docker-compose --env-file ./docker.env up

**Production**
- Run docker-compose -f docker-compose.prod.yml --env-file ./docker.env up


**Set-Up**
- Run docker exec -it *ID-backend-python-container* /bin/bash [this command access to the subsystem where python runs]
- Run alembic revision --autogenerate -m "first"              [this command creates a driver on mysql to handle migrations]
- Run alembic upgrade head                                    [this command creates the tables based on the python models]

NOTE: The *set-up* should be run one time, due to mysql has data consistency based on remaning data on a volume [docker-memory]