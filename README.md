# Ananas Build Toolkit

## Présentation du projet

L'Ananas Build Toolkit est un framework de configuration et de déploiement de projet logiciel.

Ces principaux intérêts sont :

 * Installation aisée
 * Indifférent au(x) langage(s) de programmation utilisé(s) au sein du projet
 * Cycle de travail simple et rapide à prendre en main
 * Gestion efficace de profils de configuration multiples
 * Modulaire et extensible
 * Libre et gratuit

Il est basé sur [Ant](http://ant.apache.org) et [PHPreprocessor](https://github.com/constructions-incongrues/phpreprocessor).

## Installation et configuration

Le toolkit s'installe à l'aide de [Composer](http://getcomposer.org). 

Placez-vous à la racine du projet et créez un fichier ```composer.json``` avec le contenu suivant :

```json
{
    "repositories": [
        {
            "type": "composer",
            "url": "http://constructions-incongrues.github.com/packages"
        }
    ],
    "require": {
        "constructions-incongrues/ananas-build-toolkit": "dev-master"
    }
}
```

Installez Composer : 

```bash
curl -s http://getcomposer.org/installer | php
```

Récupérez le toolkit : 

```bash
php composer.phar update
```

Initialisez le toolkit : 

```bash
ant -f vendor/constructions-incongrues/ananas-build-toolkit/modules/toolkit/module.xml toolkit.init -Dbasedir=$PWD
```

## Utilisation

Le toolkit expose sept tâches :

### boostrap

Cette tâche installe les composants nécessaires au bon fonctionnement de chacun des modules du toolkit. Elle doit être exécutée à chaque fois qu'un nouveau module est activé. Elle est appelée automatiquement lors de l'initialisation du projet par la tâche ```init```.

Pour l'invoquer : 

```bash
ant bootstrap
```

### build

Cette tâche génère le code qui doit l'être (classes d'ORM, etc) et effectue les opérations sur le système de fichiers (création de dossiers, liens symboliques, permissions, etc).

Pour l'invoquer : 

```bash
ant build
```

### configure

Cette tâche applique la configuration aux sources du projet. Les directives configurables dans les fichier suffixé par ```-dist``` sont remplacées par les valeurs définies dans le profil de configuration.

Pour l'invoquer : 

```bash
ant configure
```

### migrate

Cette tâche gère les modifications des données du projet et de leurs structures (base de données ou autre).

Pour l'invoquer : 

```bash
ant migrate
```

### review

Cette tâche analyse la qualité du code source avant que les modifications ne soient poussées vers le dépôt.

Pour l'invoquer : 

```bash
ant review
```

### sync 

Cette tâche envoie les sources du projet vers le(s) serveur(s) distant(s).

Pour l'invoquer : 

```bash
ant sync
```

### update

Cette tâche met à jour le projet : dépendances git, Composer, etc. Elle recherche aussi les directives configurabless dans les sources et met à jour les profils de configuration.

Pour l'invoquer : 

```bash
ant update
```
