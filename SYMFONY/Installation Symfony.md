```table-of-contents
```

## Prérequis

- PHP8.2 ou plus
- Composer
- Symfony CLI

Cette commande permet de vérifier si tous est OK pour lancer la création d'un projet Symfony

```bash
symfony check:requirements
```

## Nouveau projet
```bash
//télécharge un projet avec les modules installé
symfony new <projectName> --webapp

//télécharge un projet mini
symfony new <projectName>
```

## Lancer Symfony

Lance le serveur de développement de Symfony. On peut ensuite accéder au projet via le navigateur.

```bash
symfony server:start
```

Par défaut @ `http://localhost:8000/`.

Pour couper le serveur `Ctrl + C`

