Wordpress on Raspberry Pi
===========

Use this repo to run your own wordpress site on a Raspberry pi.

From your Raspberry Pi you will need docker installed

```
curl -sSL get.docker.com | sh
```
Next install docker-compose

```
curl -s https://packagecloud.io/install/repositories/Hypriot/Schatzkiste/script.deb.sh | sudo bash
sudo apt-get update && sudo apt-get install docker-compose
```
Modify the environment variables in docker-compose and change the default site definition in .data/wp/Caddyfile

Run `docker-compose up` to begin testing

If you need to backup an existing Wordpress site you can rsync your files into .data/wp/www and put a database .sql backup file in .data/backup
