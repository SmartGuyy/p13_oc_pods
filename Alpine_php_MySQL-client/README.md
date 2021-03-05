# Alpine php + php-mysqli & MySQL-client

Docker image with php, php-mysqli and MySQL client packages.

This Docker image is based on Alpine Linux version 3.13.2.

Image size : 51 MB.


## Build locally on K8s masternode :

Use a local registry:
```
docker run -d -p 5000:5000 --restart=always --name registry registry:2
```
Now build and tag your image accordingly

```
docker build localhost:5000/php-mysql-client .
```
Note that localhost should be changed to dns name of the machine running registry container.

Now push your image to local registry:

```
docker push localhost:5000/php-mysql-client
```

Apply pod yaml :

```
kubectl apply -f POD_php-MySQL.yaml
```

## Connect to MySQL server from this image

To connect to MySQL server after pods are online, do the following command :

```
mysql -h 192.168.160.133 -u app -p app
```
Password for user "app" is "app"
Replace "192.168.160.133" with your MySQL server IP
You can find it easily with kubectl : "kubectl describe pod ..."
