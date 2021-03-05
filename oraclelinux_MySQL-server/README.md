## oraclelinux_MySQL-server

Docker image with MySQL server.

Image size : 406 MB.

This Docker image is based on oraclelinux slim version 7.

## Build locally on K8s masternode :

Use a local registry:
```
docker run -d -p 5000:5000 --restart=always --name registry registry:2
```
Build and tag your image accordingly

```
docker build localhost:5000/mysql-server .
```
Note that localhost should be changed to dns name of the machine running registry container.

Push your image to local registry:

```
docker push localhost:5000/mysql-server
```

Apply pod yaml :

```
kubectl apply -f POD_MySQL-server.yaml
```

## Credentials

**Default :**  
* `MYSQL_ROOT_PASSWORD` : see kubectl logs mysql-server to find generated password, then change it manually :
```
kubectl exec -it mysql-server /bin/sh
```
Then connect to database and : 
```
ALTER USER 'root'@'localhost' IDENTIFIED BY 'password';
```
