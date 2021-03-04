## Alpine_MySQL-server
Image size : 171 MB

## Versions

Alpine : `3.7`   
MySQL : `mariaDB-10.1.28-r1`

## Build locally on K8s masternode :

Use a local registry:
```
docker run -d -p 5000:5000 --restart=always --name registry registry:2
```
Now build and tag your image accordingly

```
docker build localhost:5000/mysql-server .
```
Note that localhost should be changed to dns name of the machine running registry container.

Now push your image to local registry:

```
docker push localhost:5000/mysql-server
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

