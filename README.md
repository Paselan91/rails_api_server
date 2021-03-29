Rails API Server

buzziee_be:
    build:
      context: ./
      dockerfile: ./docker/app/Dockerfile
    container_name: "buzziee_be"
    depends_on:
      - mysql
    environment:
      - ENV_MODE=dev
      - MYSQL_CONTAINER_NAME=buzziee_mysql
    ports:
      - $PORT:8000
    volumes:
      - .:/app
    links:
      - mysql
    command: realize start --run
    tty: true
