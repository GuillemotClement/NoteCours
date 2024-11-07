```table-of-contents
```
---
# Docker Compose

Fichier qui permet d'orchestrer différents container afin qu'il fonctionne ensemble.

Lorsque l'on lance le fichier, les container sont également lancer et communique.

-> exemple d'un fichier
### Lancer docker compose
```bash 
docker compse up
```

### Couper docker compose
```bash 
docker compose down
```

## Supprimer les build en cas de problème
```bash 
docker-compose down --rmi all --volumes --remove-orphans
```

Relancer ensuite le build -> ici problème avec un ajout de tailwind

```bash 
docker-compose up --build
```
