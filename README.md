# Installation

## Setup this repository first
Usage
```bash
git clone https://github.com/danixsofyan/todolist
cd todolist
```

## Setup Laravel Packages and Migrations

### Make sure you do this before setup on bash

* PHP version is on version 8
* .env File is available or exists
* Change database config on .env file
* Composer installed

### Bash Usage

```bash
composer install
cp .env.example .env
php artisan key:generate
npm install && npm run dev
npm build
php artisan migrate
php artisan serve
```

