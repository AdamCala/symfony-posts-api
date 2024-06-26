# 🎼 Symfony 6 based posts api

## Description

A simple application that uses [ger86's symfony-docker boilerplate](https://github.com/ger86/symfony-docker) as a base. It fetches posts and users from a placeholder json api and merges them with users into a single entity serving it at /api/posts endpoint

It is composed by 3 containers:

- `nginx`, acting as the webserver.
- `php`, the PHP-FPM container with the 8.2 version of PHP.
- `db` which is the MySQL database container with a **MySQL 8.0** image.

## Prerequisites

- Docker

## Local Installation

1. Clone this repo.

2. Create the file `./.docker/.env.nginx.local` using `./.docker/.env.nginx` as template. The value of the variable `NGINX_BACKEND_DOMAIN` is the `server_name` used in NGINX.

3. Go inside folder `./docker` and run `docker compose up -d` to start containers.

4. Inside the `php` container, run `composer install` to install dependencies from `/var/www/symfony` folder.

5. Use the following value for the DATABASE_URL environment variable:

```
DATABASE_URL=mysql://app_user:helloworld@db:3306/app_db?serverVersion=8.0.33
```
You could change the name, user and password of the database in the `env` file at the root of the project.

6. Run migrations `php bin/console doctrine:migrations:migrate` in the php container

7. You can now fetch posts using the `php bin/console app:fetch-posts` command in the container terminal

8. You can access the app at `http://localhost/`




