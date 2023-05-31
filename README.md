# OMS.DataEngineering
Data engineering items needed for the opportunity management system for job seekers

Create a user defined network so that we can refer to guest containers by name

```
docker network create oms-net
```

Using Rancher on Mac for Docker Desktop replacement requires a config change to allow postgres to chown

https://github.com/rancher-sandbox/rancher-desktop/issues/1209#issuecomment-1438532927

Docker command to start up database
```
docker run -d --net oms-net --name oms-db -e POSTGRES_PASSWORD=mysecretpassword -e PGDATA=/var/lib/postgresql/data/pgdata -v /Users/joe/DockerVolumes/OMS/postgres:/var/lib/postgresql/data postgres
```

Docker command to start pgAdmin
```
docker run -d --net oms-net --name oms-pgadmin -p 8080:80 -e 'PGADMIN_DEFAULT_EMAIL=user@domain.com' -e 'PGADMIN_DEFAULT_PASSWORD=SuperSecret' dpage/pgadmin4
```