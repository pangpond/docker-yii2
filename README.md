# docker-yii2
mariadb, php7-fpm, nginx, phpmyadmin, yii2

```
$ git clone git@github.com:pangpond/docker-yii2.git
$ cd docker-yii2
```

###build and start

```
docker-compose up -d
```

###install yii2-framework

install yii2-advanced template at ```www```

```
$ cd www 
$ git clone https://github.com/yiisoft/yii2-app-advanced.git ./
$ composer install
```

edit main-local.php then run migrate

```
$ docker-compose run --rm php ./yii migrate
$ docker-compose run --rm php composer install
```
