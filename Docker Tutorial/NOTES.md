docker run -dp 3000:3000 -w /app -v "$(pwd):/app" --network todo-app -e MYSQL_HOST=mysql -e MYSQL_USER=root -e MYSQL_PASSWORD=secret -e MYSQL_DB=todos node:12-alpine sh -c "yarn install && yarn run dev"

docker run -dp 3000:3000 -w /app -v "$(pwd):/app" --network todo-app -e MYSQL_HOST=mysql -e MYSQL_USER=root -e MYSQL_PASSWORD=secret -e MYSQL_DB=todos node:12-alpine sh -c "yarn install && yarn run dev"

docker run -dp 3000:3000 -w /app -v "$(pwd):/app" --network todo-app -e MYSQL_HOST=mysql -e MYSQL_USER=root -e MYSQL_PASSWORD=secret -e MYSQL_DB=todos node:12-alpine sh -c "apk --no-cache --virtual build-dependencies add python2 make g++ && yarn install && yarn run dev"

docker run --hostname=afe75eac7cbc --env=MYSQL_PASSWORD=secret --env=MYSQL_DB=todos --env=MYSQL_HOST=mysql --env=MYSQL_USER=root --env=PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin --env=NODE_VERSION=12.22.12 --env=YARN_VERSION=1.22.18 --volume=E:\PROJEKTER\docker-experiments:/app --network=todo-app --workdir=/app -p 3000:3000 --restart=no --runtime=runc -d node:12-alpine

docker run --hostname=e9454af5f162 --mac-address=02:42:ac:11:00:02 --env=PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin --env=NGINX_VERSION=1.23.2 --env=NJS_VERSION=0.7.7 --env=PKG_RELEASE=1 -p 80:80 --restart=no --label='maintainer=NGINX Docker Maintainers <docker-maint@nginx.com>' --runtime=runc -d docker101tutorial

----------------

docker-compose up -d
docker-compose down

----------------

version: "3.8"

services:
  app:
    image: node:12-alpine
    command: sh -c "yarn install && yarn run dev"
    ports:
      - 3000:3000
    working_dir: /app
    volumes:
      - ./:/app
    environment:
      MYSQL_HOST: mysql
      MYSQL_USER: root
      MYSQL_PASSWORD: secret
      MYSQL_DB: todos

  mysql:
    image: mysql:5.7
    volumes:
      - todo-mysql-data:/var/lib/mysql
    environment: 
      MYSQL_ROOT_PASSWORD: secret
      MYSQL_DATABASE: todos

volumes:
  todo-mysql-data: