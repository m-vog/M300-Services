# M300 Services
## TBZ M300 LB03
Laura Weber, Marc Vogelmann

### Aktueller persönlicher Wissensstand
Unser Wissensstand bezüglich containerisierung und Microservices, war zu Beginn des Modules eher gering. Da wir Mittwochnachmittags das Wahlmodul W906 haben, konnten wir uns jedoch bereits einiges an Wissen aneignen. Marc Vogelmann hat im Voraus bereits mit Kubernetes gearbeitet, jedoch immer nur als Proof of Concept und in seinem Arbeitsumfeld werden Microservices noch nicht betrieben.
Laura Weber hat im Voraus noch nicht mit Microservices gearbeitet, aber "schon davon gehört" und mit unserer Zusammenarbeit in der TBZ in einem oder anderem Modul Microservices kurz kennengelernt.

### Probleme mit Kubernetes
Wir wollten diese LB mit Kubernetes als Orchestrierungslösung erledigen, leider hatten wir einige Probleme mit Containern die persistent Volume Claims brauchen. Container wie einfache Webserver funktionierten ohne Probleme. Da diese LB aber einen höheren Anspruch hat, als einen einfachen "Hello World" Webserver und wir dem gerecht werden wollten, haben wir uns dazu entschieden mit Docker fortzufahren.

### Umgebung
Der Einfachheit halber, haben wir zusammen auf der VM von Marc Vogelmann gearbeitet (192.168.133.24) Auch der Einfachheit halber, ist alles auf dem Repository von Marc Vogelmann abgelegt und dokumentiert.
Auf der VM der TBZ-Cloud läuft ein Ubuntu 20.04 Server mit dem 4.15.0 Kernel.
Die Dockerversion ist 19.03.6.

### K1
Siehe LB02

### K2
Siehe LB02

### K3
#### Wordpress mit Docker
##### Schritt 1: docker-compose installieren
Bevor man startet, muss man `docker-compose` installieren.
```bash
Binary herunterladen:
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.26.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

Executable Berechtigung setzen
$ sudo chmod +x /usr/local/bin/docker-compose

Symlink erstellen
$ sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose

Installationserfolg überprüfen
$ docker-compose --version
docker-compose version 1.26.1, build f216ddbf
```
##### Schritt 2: Projekt definieren
1. Ein leeres Projektverzeichnis anlegen: `mkdir wordpress`
2. In das neue Verzeichnis wechseln: `cd wordpress`
3. `docker-compose.yaml`-File erstellen: `touch docker-compose.yaml`

Inhalt des `docker-compose.yaml`-File:
```perl
version: '3.3'
services:
   db:
     image: mysql:5.7
     volumes:
       - db_data:/var/lib/mysql
     restart: always
     environment:
       MYSQL_ROOT_PASSWORD: somewordpress
       MYSQL_DATABASE: wordpress
       MYSQL_USER: wordpress
       MYSQL_PASSWORD: wordpress

   wordpress:
     depends_on:
       - db
     image: wordpress:latest
     ports:
       - "8080:80"
     restart: always
     environment:
       WORDPRESS_DB_HOST: db:3306
       WORDPRESS_DB_USER: wordpress
       WORDPRESS_DB_PASSWORD: wordpress
       WORDPRESS_DB_NAME: wordpress
volumes:
    db_data: {}
```
4. Projekt bauen: `docker-compose up -d`
5. Testing: Die Website ist unter `192.168.132.24:8080` erreichbar.

![Wordpress-Site](https://github.com/m-vog/M300-Services/blob/master/LB03/img/wp.PNG)

#### Minecraftserver mit Docker
Ein fixfertiges Image ist bereits auf Dockerhub erhältlich. Mit dem folgendem Befehl, lädt man das Image herunter und startet es.

`docker run -d -it -e EULA=TRUE -p 25565:25565 -v /home/ubuntu/docker/minecraftdata:/data --name mc itzg/minecraft-server`

![minecraft server](https://github.com/m-vog/M300-Services/blob/master/LB03/img/mc.png)