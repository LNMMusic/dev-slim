## MODE SWITCH [Docker - React]
**Backend**
- Comment .env

## DB MIGRATIONS
- Run docker-compose up --env-file ./docker.env

**First Migration**
- Run docker exec -it #backend-python-container /bin/bash
- Run alembic revision --autogenerate -m "first"
- Run alembic upgrade head

This is a one time run command, then mysql db has data consistency which means tables remain

## NOTES
There was a change on the driver to handle mysql for python (mysqllibrary wasn't working properly)
The solution was using another driver which much more compatibility with Debian System on FastAPI Python Docker
The driver was 'mysql-connnector-python' and it doesn't need to have installed any external software