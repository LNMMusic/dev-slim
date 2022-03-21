## MODE SWITCH [Local - Docker]
This case is being used a docker version of Mask (not manual networking, instead name of each service as host)

**Backend**
- Check env.env file

**Frontend**
- Check proxy on package.json
    ∟ Local:    http://localhost:8080
    ∟ Docker:   http://backend:8080


<br>
<br>

## MODE RUN
- Run docker-compose --env-file ./docker.env up

**First Migration**
- Run docker exec -it #backend-python-container /bin/bash
- Run alembic revision --autogenerate -m "first"
- Run alembic upgrade head

This is a one time run command, then mysql db has data consistency which means tables remain

## NOTES
1. There was a change on the driver to handle mysql for python (mysqllibrary wasn't working properly)
The solution was using another driver which much more compatibility with Debian System on FastAPI Python's Docker
The driver was 'mysql-connnector-python' and it doesn't need to have installed any external software

2. Docker Compose Versions

    - 3.0: use mask                 ->  example: http://service-name:PORT
    - 2.0: use manual network       ->  example: http://192.168.0.##:PORT