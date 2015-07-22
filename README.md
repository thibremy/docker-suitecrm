# docker-suitecrm

### Run with docker compose

``bash
  ./docker-compose up
``
### Installation step

Database information:

Hostname: mysql  
Username: suitecrm  || root  
Password: 08iBy3UYsnXZ || CjTk6WN5qCgE

Feel free to change that on docker-compose.yml

### In developpment

if you run docker on boot2docker change VIRTUAL_HOST: suitecrm.dev with your boot2docker IP.  
You can have your ip with:
```
boot2docker ip
or
docker-machine ls
```

### In production 

Create docker-compose.production.yml and change MYSQL_ROOT_PASSWORD & MYSQL_PASSWORD.  
Change VIRTUAL_HOST with your prod host.


