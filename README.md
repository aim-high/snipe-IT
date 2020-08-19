# Setting up Snipe-IT (Docker and VM)

##Snipe-IT on Docker
[resource](https://snipe-it.readme.io/docs/docker)

Note: I'm using a Windows 10 machine but will include a way to use Linux tools for easier setup.

Requirements:
* Docker Desktop client

Optional to use Linux tools:
To open Docker, go to toolbar > Docker (right click) > Open Dashboard

1) Install Ubuntu 20.04 LTS distro and Windows Terminal from Microsoft Store
2) Launch both Ubuntu 20.04 and Windows Terminal after installed
3) Windows Terminal: click on down arrow next to new tab, select Ubuntu to open Ubuntu's command line
4) Open Docker Dashboard > Settings > General, make sure "Use the WSL 2 based engine" is checked
5) Settings > Resources > WSL Integration, make sure "Enable integration with my default WSL distro" is checked AND "Ubuntu-20.04" is on (You may need to hit Refresh).
6) Apply & Restart

Fun fact: \\wsl$  --> network shortcut path to WSL
Linux CLI tips (vi):
Shift+c to remove rest of line

Create and go to snipe-it directory
```
mkdir snipe-it
cd snipe-it/
```

### Follow Snipe-IT's Docker Set Up

on Linux command line:
Get Snipe-IT's docker image
```docker pull snipe/snipe-it```

Create my_env_file and copy and paste contents from setup.

Create and run MySQL container
```docker run --name snipe-mysql --env-file=my_env_file --mount source=snipesql-vol,target=/var/lib/mysql -d -P mysql:5.6```

Create docker-compose.yml to use docker-compose command (copy and paste contents from setup)
Create .env file and copy and paste contents from setup.

Create a new container and run it.
```docker run --rm snipe/snipe-it```

Copy and paste your APP_KEY, be sure to include the preceding base64
i.e. base64:D5oGA+zhFSVA3VwuoZoQ21RAcwBtJv/RGiqOcZ7BUvI=

Choose which port number for HTTP and HTTPS endpoints and set your APP_URL.
Initialize the app and database to redirect you to the start screen: http://IP:YOUR_PORT

Go to the web page http://IP:YOUR_PORT (i.e. http://localhost:YOUR_PORT) and go through setup!

Installation via VM
[Installation Overview](https://snipe-it.readme.io/docs/installation)

## Requirements
Ubuntu Server 20.04
Git
PHP 7.1.2 (or higher)
MySQL

```
$ sudo apt update
$ sudo apt install git
$ sudo apt install php7.2-cli
$ sudo apt install composer
```
###### Set up Git
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
