# Commande
```bash
//lancer un container
docker run <imageName>

//afficher les images
docker images

//afficher les container en fonctionnement
docker ps

//afficher tous les container
docker ps -a

//stoper un container
docker stop <containerName>

//supprimer un container
docker container rm <containerName>

//supprimer une image non utilisé
docker image rm <imageName>

//supprimé image et container non utilisé
docker system prune -a

//lancer un container stoppé
docker start <containerName>

//connection et ouverture terminal d'un container en fonction
docker exec -it <containerName> bin/sh
```

# Container
## Créer un container

```bash 
docker run <imageName>
```

## Container interactif
```bash
docker run -it --name <nameContainer> ubuntu
```
`-it` : permet de lancer le container et d'intéragir avec via le terminal
`nameContainer` : c'est le nom que l'on définis pour le container

## Sortir du container
```bash
exit
```

## Créer une image d'un container
```bash
docker commit <ID ou namecontainer> <nameNewImage>
```
# Réseau
On pourras binder les ports pour pouvoir accéder à l'appli 
`docker run -p <PORT HOTE>:<PORT CONTAINER> image`

De cette manière, une fois le container lancer, on pourras accéder via le navigateur a l'application 
```bash
# container qui expose son port 80 sur le port 5175 de notre hôte
docker run -d --name my-nginx -p 5175:80 nginx
# -d pour detached mode
# -p pour mapper un port
# --name pour specifier un nom à notre container
```
Ici, le serveur NGINX tourne dans un environnement isolé. Avec le mapping de port, on peut rendre accessible le port depuis l'exterieur

# Volume
On pourras binder un folder pour le rendre disponible dans le container.
```bash
# on créé le code du site sur notre hôte
mkdir ~/mon-site
echo "Bienvenue sur mon site via Docker"  > ~/mon-site/index.html 

# on lance le container ngnix avec un mapping vers le dossier contenant notre code
docker run -d --name my-nginx -p 8080:80 -v ~/mon-site:/usr/share/nginx/html nginx
```

# DOCKERFILE
```bash 
# Exemple de Dockerfile pour builder une image qui servira à lancer un container avec un json server

# on specifie une image de base et sa version
# ici on utilise une image avec node et npm
FROM node:latest

# on créé un repertoire dans l'image
# ce sera notre repetoire de départ : là ou sera executée les prochaines commandes
WORKDIR /home/app

# on execute des commandes avec RUN
# ici on télécharge le package json server depuis npm
RUN npm i -g json-server

# On copie le fichier json qui contient les données dans l'image
COPY /db.json /home/app/

# on specifie la commande à lancer à la création du container basé sur cette image
# cette commande n'est pas executée au build du dockerfile mais uniquement au run du container qui utilisera l'image créé au build
CMD json-server db.json --host 0.0.0.0
```

## Créer l'image du dockerfile
```bash
docker build < repertoire contenant le docker file > -t < nom image >

# exemple 
# ici on met . pour specifier que le dockefile est dans le dossier courrant
docker build . -t myjsonserveurfriends
```