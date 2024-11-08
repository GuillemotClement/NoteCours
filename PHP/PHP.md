```table-of-contents
```
---
## Serveur développement
Il est possible d'utiliser le serveur de développement de PHP.

Pour le lancer, on utilise la commande :

```bash
phh -S localhost:<port>
```

## SUPERGLOBAL

En PHP, on retrouve des superglobals permettant de récupérer plusieurs types de données.

### $_SERVER

### $_REQUEST

### $_SESSION

## Classe

### Static

Pour utiliser une méthode static d'une classe, il faut utiliser le nom de la classe, `::`puis le nom de la méthode.

```php
//Utils.php
<?php  
class Utils {  
    /**  
     * Affiche le type et la valeur de la variable     * @param $value  
     * @return void  
     */    public static function d($value){  
        echo "<pre>";  
        var_dump($value);  
        echo "</pre>";  
    }  
}
```

Dans le fichier ou je souhaite utiliser cette classe statique, je viens faire :

```php
<?php  
//importation de la classe
require_once "classes/utils.php";  

//utilisation de la méthode statique de la classe
Utils::d($_SERVER);  

```
