## SET-UP [Local]
This is to set up the packages used on the enviroment

**Database**
- Install mysql

**Backend**
- Run "python -m venv venv"
- Run "pip install -r requirements.txt"

**Frontend**
- Run npm install

<br>

___
## SWITCH [Local - Docker]
This case is being used a docker version of Mask (not manual networking, instead name of each service as host)

**Database**
- Check mysql not open while using docker [both use the same port, this could be fix using mysql image on other port]

**Backend**
- Check env.env file [comment variables based on the local or docker mode]

**Frontend**
- Check proxy on package.json
    ∟ Local:    http://localhost:8080
    ∟ Docker:   http://backend:8080

<br>

___
## RUN [Local]
**Development**
- Mysql:    initialize the server locally
- Backend:  "python main.py"
- Frontend: "npm start"

**Production**
Same for Mysql and Backend
- Frontend: "npm run build"
            "npm install -g serve --save"
            "npm -s build"

**Set-Up**
- Backend:  "alembic revision --autogenerate -m "first""
            "alembic upgrade head"

___
## RUN [Docker]
**Development**
- Run "docker-compose --env-file ./docker.env up"

**Production**
- Run "docker-compose -f docker-compose.prod.yml --env-file ./docker.env up"


**Set-Up**
- Run "docker exec -it *ID-backend-python-container* /bin/bash" [this command access to the subsystem where python runs]
- Run "alembic revision --autogenerate -m "first""              [this command creates a driver on mysql to handle migrations]
- Run "alembic upgrade head"                                    [this command creates the tables based on the python models]

NOTE: The *set-up* should be run one time, due to mysql has data consistency based on remaning data on a volume [docker-memory]