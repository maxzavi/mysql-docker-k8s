# Deploy mysql and admin using docker

Create mysql instance in docker:

```cmd
docker run -e MYSQL_ROOT_PASSWORD=admin -p 3306:3306 -d mysql
```

Get Container ID, usign docker ps, and IP using **docker inspect** and container Id:

```cmd
docker inspect -f \
'{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' \
196d4e2fbb48
```

Create phpmyadmin container, using IP get in last step:
```cmd
docker run  -p 80:80 -e PMA_HOST=172.17.0.2 -d phpmyadmin/phpmyadmin 
```

Persist mysql using volume:

```cmd
docker run -e MYSQL_ROOT_PASSWORD=admin -p 3306:3306  -v volmysql:/var/lib/mysql -d mysql
```

First, make sure the volume **volmysql** is empty

In case **Public Key Retrieval is not allowed** , set property **allowPublicKeyRetrieval=true**


reference in Azure devops https://mzavaletav.visualstudio.com/tallerk8s/_git/SpringBootMSMySql01


