```table-of-contents
```
---
# Voir toutes les branche d'un repo

```git 
git branch -a
```

Pour ensuite changer de branche pour la branche distante

```git
git checkout -b <nom_de_la_branche_locale> origin/<nom_de_la_branche_distant>
```

# Liaison depot distant

```bash
git remote add <alias> <@urlDepot>
```

`alias` : alias donné au dépot distant.
`@urlDepot` : url du depot distant

```bash
git remote add correction https://github.com/O-clock-Pooka/S02-coclockworking-SoleneOclock.git
```

Ici on vient créer une liaison avec le depot distant.

## Vérifier ajout du depot distant

```bassh
git remote -v
```

Permet d'obtenir la liste des depot distant

# Récupérer les modification distant

```bash
git pull <alias> <brancheName>
```
`alias` : correspond au nom donné dans le `git remote add`
`brancheName` : correspond au nom de la branche que l'on veut recupérer sur le depot distant

# Problème de merge
Dans le cas ou lors du pull, une erreur surviens (fusion), alors je lance la commande 
```bash 
git pull --no-rebase <alias> <branche>
```

# Suppression de branche

### Suppression repo local

```bash
git branch -d <nameBranch>

//ou si branche non fusionné
git branch -D <nameBranche>
```

### Suppression branche distante

```bash
git push origin --delete <namebranche>
```
