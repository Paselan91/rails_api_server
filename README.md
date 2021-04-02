Rails API Server

mysql:
    container_name: "buzziee_mysql"
    image: mysql:8.0
    command: mysqld --character-set-server=utf8 --collation-server=utf8_unicode_ci
    volumes:
      - ./docker/db/data:/var/lib/mysql
      - ./docker/db/my.cnf:/etc/mysql/conf.d/my.cnf
    ports:
      - $MYSQL_PORT:3306
    environment:
      MYSQL_ROOT_PASSWORD: $MYSQL_ROOT_PASSWORD
      MYSQL_USER: $MYSQL_USER
      MYSQL_PASSWORD: $MYSQL_PASSWORD
      MYSQL_DATABASE: $MYSQL_DATABASE





version: '3'
services:
  mysql:
    container_name: "mysql"
    image: mysql:8.0.23
    environment:
      MYSQL_ROOT_PASSWORD: password
    volumes:
      - ./mysql:/var/lib/mysql
    command: ["--default-authentication-plugin=mysql_native_password"]
    ports:
      - 3306:3306
  app:
    container_name: "rails_api"
    build:
      context: ./
      dockerfile: ./docker/app/Dockerfile
    depends_on:
      - mysql
    environment:
      - ENV_MODE=dev
      - MYSQL_CONTAINER_NAME=buzziee_mysql
    ports:
      - $PORT:3000
    volumes:
      - ./src:/usr/src/app
    command: ["rails", "server", "-b", "0.0.0.0"]
    tty: true
