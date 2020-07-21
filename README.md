# snipe-IT

[Installation Overview](https://snipe-it.readme.io/docs/installation)

Set Up Documentation (will edit as I configure)
Ubuntu Server 20.04
Git
PHP 7.1.2 (or higher)
MySQL or MariaDB

```
$ sudo apt update
$ sudo apt install git
$ sudo apt install php7.2-cli
$ sudo apt install composer
```
Set up Git
```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@domain.org"
$ git config --list 

$ mkdir Github
$ mkdir Github/snipe-it
$ cd Github
$ git clone https://github.com/snipe/snipe-it snipe-it
```

To update, run 'git pull' 

All system config variables are stored in .env
```$ cp .env.example .env```

Change APP_KEY within .env file in project's root
```$ php artisan key:generate```
