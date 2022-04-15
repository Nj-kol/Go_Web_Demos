# Go Fiber Order API

## Docker

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