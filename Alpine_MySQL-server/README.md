## Alpine_MySQL-server

Docker image with MySQL server.

Image size : 171 MB.

This Docker image is based on Alpine Linux version 3.13.2.

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
* `MYSQL_ROOT_PASSWORD` : `root`,
* `MYSQL_DATABASE` : `app`,
* `MYSQL_USER` : `app`,
* `MYSQL_PASSWORD` : `app`,
* `MYSQL_USER_MONITORING` : `monitoring`,
* `MYSQL_PASSWORD_MONITORING` : `monitoring`

**Custom :** In the `.env` file, change the different values to suit your needs.

