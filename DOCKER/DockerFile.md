```table-of-contents
```
# Présentation
Dockerfile est un fichier sans extension permettant de créer une image pour lancer un container Docker.
Il décrit ce que l'on veut faire dans cette image, pour créer un contenaire.
# Exemple
Dans ce dockerfile, on créer un container pour un un front en React.
```dockerfile
# on part de l'image node:alpine -> version allégé de node
FROM node:alpine

# on créer le répertoire de travail
WORKDIR /app

# on vient copier les packages json pour avoir les dépendances
COPY package*.json ./

# on lance la commande pour installer les dépendances
RUN npm install

# On expose le port pour réaliser le mappin à la création du container
EXPOSE 5173

# Commande exécutée quand le container tourne
CMD ["npm", "run", "dev"]
```
