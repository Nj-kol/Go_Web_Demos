# Go Fiber Order API

## Docker

#### The database

```bash
docker container run -d -p 31433:1433 \
--name mssql17-standalone \
--network sandbox \
-e "ACCEPT_EULA=Y" \
-e "SA_PASSWORD=@mssql2017" \
-v myssql17-data:/var/opt/mssql \
-v ${HOME}/volumes/mssql/2017:/opt/mssql17 \
mcr.microsoft.com/mssql/server:2017-latest
```

#### The application

**Build the docker image**

```bash
docker build -t go-fiber-order-api .
```

**Run a docker container**

```bash
docker container run -p 3000:3000 -d \
--name go-fiber-order-api-inst \
--network sandbox \
go-fiber-order-api
```

**Housekeeping**

```bash
docker container logs go-fiber-order-api

docker container stop go-fiber-order-api
```

## Kubernetes

```bash
kubectl apply -f .

// Use
http://127.0.0.1:30274/apidocs/index.html 

// Housekeeping
kubectl get po -o wide
kubectl logs go-fiber-order-api-c674d9447-hs8bk -f
kubectl exec -it go-fiber-order-api-c674d9447-hs8bk bash
kubectl get deploy
kubectl get svc

// Teardown
kubectl delete -f .
```

## References

https://www.youtube.com/watch?v=dpx6hpr-wE8

https://dev.to/koddr/build-a-restful-api-on-go-fiber-postgresql-jwt-and-swagger-docs-in-isolated-docker-containers-475j

