# Part-DB Docker Files

In this repo you can find the docker-compose files for an easy install of [Part-DB](https://github.com/Part-DB/Part-DB) via Docker.

## Prerequisite
For the next steps you will need a working installation of Docker and docker-compose.

## Installation via Docker-Compose (Recommended)

There are two "stability" levels available:
 * stable: Use the files in this folder if you need a very stable and bug-free version. This version maybe lacks some features...
 * latest: Use this folder if you want to use the latest features from the master (former nextgen) Branch...

 ### Instructions
 1. Copy the folder with you desired stability level in a folder on your computer (or any other device where you want to run Part-DB)
 2. Go to `docker-compose.yml` and replace in the line `MYSQL_ROOT_PASSWORD:` "changeme" with an unique password (without quotes). You will need this later during Part-DB setup, as the Database root password. If you want to run Part-DB on a TCP port other than 8888, then change the line `"8888:80"` under `ports` as desired.
 3. Start Part-DB with the command `sudo docker-compose up -d`. This will start all required servers and runs them in background. Windows users can use the batch files `server_start.bat` and `server_stop.bat` to control the server.
 4. Open a Browser and go to `localhost:8888` (or the other port you set in Step 2). You will be redirected to the Installation page of Part-DB. Choose a language and timezone, and a password for the admin user.
 5. On the Database setup page, use `database` as host, `partdb` as databasenname, and `root` as username. Databasepassword is the one you put into `docker-compose.yml` in Step 2.
 6. Finish the setup and make an database update, when asked. You now can use Part-DB.
 7. If you want to stop the server, you can do that with `docker-compose down` or `server_stop.bat`

 ## Manual installation
 If you want to create an custom setup, you can setup the needed docker containers and their connections manually. You will need the following things:
  * The Part-DB image: It can be found on [Docker Hub](https://hub.docker.com/r/jbtronics/part-db/) as `jbtronics/part-db`. The tags are the same as the stability levels for the docker-compose method
  * A container running MariaDB/MySQL, which the Part-DB container can access.
  * A port forward from Port 80 in the Part-DB container, to the desired port on your host.
  * A volume for the Part-DB container for Part-DB's data under `:/var/www/html/data`