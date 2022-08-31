# Docker Flow
## Commandes générales Docker

### Installer Docker
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

### Savoir le statut de notre suivi Git
`git status`
>👇 Si vous en 'avance' par rapport à la branch en remote.
```js
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
(use "git add <file>..." to update what will be committed)
(use "git restore <file>..." to discard changes in working directory)
        modified:   graph.js
        modified:   public/stylesheets/style.css
        modified:   routes/drive.js
        modified:   views/drive.hbs

no changes added to commit (use "git add" and/or "git commit -a")
```
>👇 Si vous êtes à jour.

