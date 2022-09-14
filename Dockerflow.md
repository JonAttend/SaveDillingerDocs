# Docker Flow

## Installation de Docker  
Mettez à jour votre liste existante de packages :  
`sudo apt update`

Installez quelques packages prérequis qui permettent à apt d'utiliser des packages via HTTPS :  
`sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common libssl-dev libffi-dev git wget nano`

Créez un groupe nommé docker et ajoutez-vous à ce groupe afin de ne pas avoir à taper "sudo docker" à chaque fois :  
`sudo groupadd docker`
`sudo usermod -aG docker ${USER}`

Ajoutez ensuite la clé GPG du référentiel Docker officiel à votre système :  
`curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`
`sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"`

Mettez à jour le gestionnaire de paquets avec les nouveaux dépôts installés :  
`sudo apt-get update`

Installez Docker  
`sudo apt-get install -y docker-ce containerd.io`

Installez la dernière version de Docker-compose  
`sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && sudo chmod +x /usr/local/bin/docker-compose`

Enfin, vérifié que l'installation à réussi, en regardant les versions :  
`docker version`
```js
Client: Docker Engine - Community
 Version:           20.10.17
 API version:       1.41
 Go version:        go1.17.11
 Git commit:        100c701
 Built:             Mon Jun  6 23:02:57 2022
 OS/Arch:           linux/amd64
 Context:           default
 Experimental:      true

Server: Docker Engine - Community
 Engine:
  Version:          20.10.17
  API version:      1.41 (minimum version 1.12)
  Go version:       go1.17.11
  Git commit:       a89b842
  Built:            Mon Jun  6 23:01:03 2022
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          1.6.7
  GitCommit:        0197261a30bf81f1ee8e6a4dd2dea0ef95d67ccb
 runc:
  Version:          1.1.3
  GitCommit:        v1.1.3-0-g6724737
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0
```  
`docker-compose -v`
```js
docker-compose version 1.29.2, build 5becea4c
```

## CLI Docker  

### Lister les containers
Liste les containers qui sont actuellement montés.  
`docker ps`
>👇 A noter que si aucun port n'a été défini lors du lancement du container, la colonne PORT est vide par défaut.
```js
CONTAINER ID    IMAGE    COMMAND    CREATED   STATUS  PORTS   NAMES
c00c586d4944 <image_name> "/bin/sh -c 'echo Co…" 7 days ago Exited (137) 25 hours ago <container_name> 028 d72dbf795  

```  
Liste tous les containers qui **ont été** ou sont actuellement montés.  
`docker ps -a`
>👇 A noter que l'option `-a` affiche tous les derniers containers montés sur docker, ici le container à été lancé il y'a 7 jours et c'est arrété après 25h.
```js
CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES
c00c586d4944 weather_project_devcontainer_lgebadges "/bin/sh -c 'echo Co…" 7 days ago Exited (137) 25 hours ago        weather_project_devcontainer_lgebadges_1 028 d72dbf795
```  

### Lancer un container
Permet de lancer un container à partir d'une image  
`docker run [OPTIONS] <IMAGE> [COMMAND] [ARG...]`
>👇 A noter que que si on ne fournis pas de [COMMAND] le container se lance puis s'arrête.  

Lance un container et nous connecte avec lui
`docker run -it <IMAGE> sh`  

Lancer un container avec le flag `-it` vous permet maintenant exécuter autant de commandes bash (grâce à l'argument `sh` en fin de commande) que nous le souhaitons dans le conteneur.

 `docker run -it alpine:lastest sh`

```js
/ # ls
bin   dev   etc   home  proc  root  sys   tmp   usr   var
/ # uptime
 05:45:21 up  5:58,  0 users,  load average: 0.00, 0.01, 0.04 

```  

### Supprimer les containers  
Pour supprimer un container ou les traces dans les logs de `docker ps`, utilisez l'option `rm` et le container id du container à supprimer.    
`docker rm <CONTAINER_ID>`  
>👇 Vous pouvez passez plusieurs <conteneur_id> à la suite en les séparants d'un espace.
```js
docker rm 305297d7a235 ff0a5c3750b9
305297d7a235
ff0a5c3750b9
```

### Se connecter à un container (lancé)
Pour se connecter à un container déjà lancé, utilisez la commande `docker exec` en spécifiant le nom du container et le language de script voulu.  
 `docker exec -it <NAME> sh`  
>👇 Vous pouvez noter l'apparition du prompt shell, une fois connecté.
```js
/ # 
```
