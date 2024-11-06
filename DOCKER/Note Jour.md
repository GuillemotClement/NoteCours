env de dev

conteneur 1 : React
conteneur 2 : node et TS
conteneur 3 postgre

on utilise docker compose pour lancer automatiquement les container

on commence par créer le projet avec git, install des dépendant et test en local.
Dans le docker file
Une fois ok on créer l'image, on fais une copie des fichier dans l'image. (COPY, RUN npm install)
EXPOSE pour exposer le port
CMD -> commande exécuté quand le cotnainer qui tourne

dans le docker compose on indique quel imag eutilise, etc
les options permette de brancher le dossier local, et le port a rendre dispo

il faut bien penser a ignore le node module car celui ci sera dl dans le container

On aura un node module en local qui correspond a notre config et un autre dans le container spécifique à celui ci
.dockerignore pour ignorer un fichier

`docker compose up`-> lancer le compose
idéal de placer le docker compose dans le même repertoire que le dockerfile

on vient ensuite lancer cette commande pour lancer le bordel et pouvoir accéder au site du container

BACKEND

créer un folder qui contient le back
init i pour avoir le package-lock.json
use nodemon et dotenv
` npm i express nodemon dotenv`
`npm i typescript @types/node @types/express`

le dockercompose est placer a la racine. Le folder contient donc backend/frontend en folder et docker-compose.yml

npx tsc -init -> commande pour compiler le typescript

indent tree -> a passer a 16

dans chaque dossier on créer un docker file correspond au truc (front, back)

dans le service, le nom correspond au container (front-react & backend-express) dans le docker compose
Dans build, on indique le chemin vers le dockerfile qui correspond

docker exec -it <container> bash -> connection sur un container en cour d'exécution