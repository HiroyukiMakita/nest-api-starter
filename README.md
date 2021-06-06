# nest-api-starter

## description

This repository is for create api use NestJS in docker-compose.

## build

Create env file.

```
# run in docker directory
$ cd docker

$ cat .env.example > .env
```

Run build.

```
# run in docker directory
$ cd docker

# if can use make command
$ make build

# or

# few no use make command
$ docker-compose build
```

## create new nest project in project root <br>(run in container)

```
# run in docker directory
$ cd docker

# if can use make command
$ make up && make create-nest-app-current

# or

# few no use make command
$ docker-compose up -d && \
  docker-compose exec nest bash -c "\
  cd /var/www/html && \
  nest new nest-app && \
  shopt -s dotglob && \
  mv -n nest-app/* . && \
  shopt -u dotglob && \
  rm -r nest-app"
```

## nest app start

Access [http://127.0.0.1:8000](http://127.0.0.1:8000) after run this command.

```
# run in docker directory
$ cd docker

# if can use make command
$ make start-nest

# or

# few no use make command
$ docker-compose exec nest bash -c "\
  cd /var/www/html && \
  npm start && \
  bash"
```
