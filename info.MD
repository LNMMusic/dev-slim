## NOTES
1. There was a change on the driver to handle mysql for python (mysqllibrary wasn't working properly)
The solution was using another driver which much more compatibility with Debian System on FastAPI Python's Docker
The driver was 'mysql-connnector-python' and it doesn't need to have installed any external software

2. Docker Compose Versions

    - 3.0: use mask                 ->  example: http://service-name:PORT
    - 2.0: use manual network       ->  example: http://192.168.0.##:PORT

3. Cache Server
- Working with a cache server in the Frontend with Redis DataBase needs to connect react with the driver of Redis for NodeJS but there are incompatibilities with the native endpoints of React and its integration with Redis. This means it needs to be done in a separate node server, which is similar as having the redis cache server on the backend.

- Possible solutions:
    1. Using Redis Realtime, which is a Hook of React that allows to having the front and the backend server with redis working simultaneously.
    
    2. Using localcache to store as a hashmap (key - value pair) the data. Redis stores it as a string which means objects need to be stringify. There is a library to manage the fetchs of APIs in react, called 'SWR' that allows to have context of all api's and manteining the data updated based on a lifecycle and also storing it on cache.

    3. Creating a new network with similar endpoints as the backend to store key values based on the READ requests [Method-GET], where the transaction should be lower on time, but not as fast as having it integrated with the same application, based on the extra time of requesting to the network.

<br>
<br>

___
## Upcoming Updates
**FormComponent**
This component tends to be a global component that could be used in an straigh forward mode by passing the variables to the component or using JSON Instructions. This will help to secure the data that will get from the **frontend** with its forms, into the **backend**, working as a bridge with typified programming. The html elements will have special names to having different style sheets for the forms that could be selected.