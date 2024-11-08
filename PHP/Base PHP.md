```table-of-contents
```
---
## index.php

C'est le fichier principal. C'est celui ci qui sera ouvert lorsqu'un utilisateur consulte l'adresse URL.

Dans celui ci on viens faire une require pour afficher le contenu de l'autre fichier `index.view.php`

```php
<?php  
  
require "index.view.php";
```

Le `require`permet d'ajouter le contenu du fichier dans le premier fichier.

Dans mon fichier `index.view.php`, on retrouve le template Tailwind de base.

Lorsque je vais avec le navigateur sur l'url du serveur, celui ci me retourne ma page `index.view.php`.

## Créer plusieurs pages

### Lien entre les pages

On pourras créer des liens nos pages avec la balise `<a>`

```html
<nav>
	<a href="/">Home</a>
	<a href="/about">About</a>
</nav>
```

Pour chacune des pages créer, il faudras avoir un fichier correspondant.

Dans cette solution, il faudras indiquer le fichier avec l'extension.
### Fichier
Pour chacune des pages souhaite, on viens créer un ficheir `<namePage>.php`. 
Dans ce fichier, on retrouve les variables que l'on pourras venir utiliser, ainsi que le `require` correspondant au fichier de la `view`

```php
//about.php

<?php  
  
require "about.view.php";

```



On retrouve ensuite une seconde page `<namePage>.view.php` contenant le contenu de la page à afficher.

Ainsi, pour chaque page du site, on retrouve deux fichier HTML.

C'est pas la solution définitive mais cela permet de montrer le fonctionnement.

## Partials

Les partials permettent de ne pas avoir à dupliquer du code statique.

A l'aide de PHP, on peut rendre l'affichage dynamique facilement.

### Structure basique 

Pour coder une code base propre, il est nécessaire de bien structurer les fichiers du projet.

#### views

C'est le dossier qui viens contenir tous les fichier qui sont responsable de l'affichages des éléments de la page web.

#### views/partials

Dans ce dossier, on viendras y stocker les fichier responsable de l'affichage d'une partie d'un page.
Par exemple, on retrouve généralement le `header`, le `footer`, etc.

Par exemple, pour la partie `nav` du `header`, on peut venir créer un fichier `nav.php`que l'on viens placer dans ce folder, et on y place le contenu responsable de l'affichage des liens du site.

On pourras ensuite venir importer ce fichier avec un `require`.

```php
<?php require ("partials/nav.php"); ?>
```

Il suffit ensuite d'ajouter cette ligne de code dans chaque fichier ayant besoin d'afficher cet élément.

On pourras cette manière, créer un ficheir `head.php`, contenant les meta data, un fichier `footer.php`, etc ..
### Découpage d'éléments

Lorsque plusieurs partie d'une page sont les même, on pourras venir les découper pour rendre le code plus modulaire, et venir les utiliser dans plusieurs pages sans avoir à copier/coller du code.

### Passer des variables

Dans le cas ou une partie des éléments doivent être différents selon les pages, on pourras créer une variables dans le fichier, et cette variable sera passer dans le fichier `view`.

```php
<?php  
$page = "Homepage";  
require "views/index.view.php";
```

On retrouve dans le partial, l'affichage de la variable correspondante :
```php
<header class="bg-white shadow">  
    <div class="mx-auto max-w-7xl px-4 py-6 sm:px-6 lg:px-8">  
        <h1 class="text-3xl font-bold tracking-tight text-gray-900"><?= $page ?></h1>  
    </div>
</header>
```


## MVC

### Controller

Les fichiers controllers sont responsable de demander les données à un fichier model, et une fois les données récupéré, viennent les données à la view qui pourras les afficher à l'utilisateur.