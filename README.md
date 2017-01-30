# docker-yii2
mariadb, php7-fpm, nginx, phpmyadmin, yii2

```
$ git clone git@github.com:pangpond/docker-yii2.git
$ cd docker-yii2
```

edit database settings in ```docker-compose.yml```

```
environment:
    - MYSQL_ROOT_PASSWORD={ROOT_PASSWORD}
    - MYSQL_DATABASE={YOUR_DATABASE_NAME}
    - MYSQL_USER={YOUR_DATABASE_USER}
    - MYSQL_PASSWORD={YOUR_USER_PASSWORD}
```

###build and start container

```
docker-compose up -d
```

###install yii2-framework

install yii2-advanced template at ```www```

```
$ cd www
$ git clone https://github.com/yiisoft/yii2-app-advanced.git ./
$ docker-compose run --rm php composer install
$ ./init
```
edit db component config in ```main-local.php``` following setting from ```docker-compose.yml``` 

```
'components' => [
    'db' => [
        'class' => 'yii\db\Connection',
        'dsn' => 'mysql:host=db;dbname={YOUR_DATABASE_NAME}',
        'username' => '{YOUR_DATABASE_USER}',
        'password' => '{YOUR_USER_PASSWORD}',
        'charset' => 'utf8',
    ],
  ...
```

then run migrate

```
$ docker-compose run --rm php ./yii migrate
```
