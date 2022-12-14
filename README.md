 # <center> Git-cheatsheet</center>

Git est un logiciel de gestion de versions décentralisé. C'est un logiciel libre et gratuit, créé en 2005 par Linus Torvalds, auteur du noyau Linux, et distribué selon les termes de la licence publique générale GNU version 2. Le principal contributeur actuel de Git, et ce depuis plus de 16 ans, est Junio C Hamano.

# Sommaire 
- Configuration
- Commande de base
- Reset
- Branch
- Merge
- Rebase
- Stash
- Remote
- Tag
- Colaborate

# Configuration
GitHub fournit des clients desktop qui incluent une interface
graphique pour les manipulations les plus courantes et une "an
automatically updating command line edition of Git" pour les scénari
avancés.

 |
GitHub pour [Mac](https://mac.github.com) |
Git pour toutes les [plate-formes](http://git-scm.com)


Définit le nom que vous voulez associer à toutes vos opérations de
commit
```bash
git config --global user.name "[nom]"
```
Définit l'email que vous voulez associer à toutes vos opérations de commit

```bash
git config --global user.email "[adresse email]"
```
Active la colorisation de la  en ligne de commande

```bash
git config --global color.ui auto
```
## Commande de base
Créer un nouveau répertoire local
```bash
git init
```
Cloner un répertoire
```bash
git clone https://github.com/Sixpacks123/git-cheatsheet.git
```
Afficher l'état du répertoire de travail et de la zone de staging
```bash
git status
```
Ajouter tous les changements pour le prochain commit
```bash
git add .
```
Afficher les modifications entre les commits, un commit et l’arbre de travail, etc
```bash
git diff
```
Envoyer toutes les modifications locales 
```bash
git commit -a
```
Envoyer les modifications récentes
```bash
git commit
```
Charger le contenu d'un dépôt local vers un dépôt distant
```bash
git push
```
Rapatrier et intégrer un autre dépôt ou une branche locale
```bash
git pull
```
Montrer tous les commits, en commençant par le plus récent
```bash
git log
```
Affiche les détails du dernier commit sur la branche
```bash
git show
```
Permet d'afficher les commandes que l'on peut réaliser avec git
```bash
git help

## Reset
Revenir à un commit précédent et annuler les modifications apportées après ce commit
```bash
git reset 
```
## Branch
Liste toutes les branches locales dans le dépôt courant
```bash
git branch
```
Crée une nouvelle branche

```bash
git branch [nom-de-branche]
```
Bascule sur la branche spécifiée et met à jour le répertoire de travail

```bash
git checkout [nom-de-branche]
```
Supprime la branche spécifiée

```bash
git branch -d [nom-de-branche]
```
```mermaid
 gitGraph
    commit
    commit
    branch develop
    branch develop2
    checkout develop
    commit
    commit
    checkout develop2
    commit
    commit
```

## Merge
>Intègre tous les fichiers de développement dans une seule branche, combine deux branches et fusionne plusieurs commits en un seul historique. La fusion s'arrête en cas de conflit et git présente les fichiers en conflit. Une fois les conflits résolus, la fusion se poursuit.

D'abord, vérifiez la branche à fusionner
```bash
git checkout -b
```
```bash
git add <file>
```
Ajouter et valider les fichiers
```bash
git commit
```
```bash
git checkout master
```
Fusionner la branche avec master
```bash
git merge
```

>Intègre tous les fichiers de développement dans une seule branche, combine deux branches et fusionne plusieurs commits en un seul historique. La fusion s'arrête en cas de conflit et git présente les fichiers en conflit. Une fois les conflits résolus, la fusion se poursuit.

D'abord, vérifiez la branche à fusionner
```bash
git checkout -b 
```
Ajouter et valider les fichiers
```
git add <file>

git commit

git checkout main
```

Fusionner la branche avec main
```
git merge 
```

```mermaid
 gitGraph
       commit
       commit
       branch develop
       checkout develop
       commit
       commit
       checkout main
       merge develop
       commit
       commit
````
## Rebase

>Commit de base final. Utile avant de fusionner toutes les modifications, pour valider les modifications des différentes branches une par une (linéairement).

Combiner les commits en une base finale
```bash
git rebase <branch name>
```
S'il y a des conflits, résolvez-les et continuez le rebasage :
```bash
git rebase --continue
```
Pour ignorer toute modification :
```bash
git rebase --skip
```

>Intègre tous les fichiers de développement dans une seule branche, combine deux branches et fusionne plusieurs commits en un seul historique. La fusion s'arrête en cas de conflit et git présente les fichiers en conflit. Une fois les conflits résolus, la fusion se poursuit.

D'abord, vérifiez la branche à fusionner
```bash
git checkout -b 
```
Ajouter et valider les fichiers
```
git add <file>

git commit

git checkout main
```

Fusionner la branche avec main
```
git merge 
```

```mermaid
 gitGraph
       commit
       commit
       branch develop
       checkout develop
       commit
       commit
       checkout main
       merge develop
       commit
       commit
````
## Rebase

>Commit de base final. Utile avant de fusionner toutes les modifications, pour valider les modifications des différentes branches une par une (linéairement).

Combiner les commits en une base finale
```bash
git rebase <branch name>
```
S'il y a des conflits, résolvez-les et continuez le rebasage :
```bash
git rebase --continue
```
Pour ignorer toute modification :
```bash
git rebase --skip
```

## Stash
>Pour changer de branche sans valider dans la branche actuelle, stockez les données non validées en toute sécurité

Enregistre l'état du travail et de l'index
```bash
git stash 
```
Donner un message pendant l'enregistrement
```bash
git stash save <message> 
```
Afficher la liste du contenu stocké
```bash
git stash list
```
Valider les modifications stockées. Pour appliquer les modifications d'un stash spécifique, utilisez l'identifiant de l'index de stash avec apply
```bash
git stash apply
```
Afficher le contenu des fichiers cachés
```bash
git stash show 
```
Supprime la réserve la plus récente de la file d'attente
```bash
git stash drop 
```

## Remote

>Vérifie la configuration du serveur distant et autorise l'accès à la connexion entre distant et local.

Par défaut, il renvoie 'origin', le nom par défaut du serveur distant donné par Git
```bash
git remote
```
Répertorie les noms courts et les URL de toutes les connexions à distance disponibles
```bash
git remote -v
```
Ajouter explicitement le serveur distant aux connexions disponibles. Le nom court peut être utilisé pour les commandes git au lieu de donner l'URL entière.
```bash
git remote add <short name> <remote url>
```
Supprime le serveur distant du référentiel
```bash
git remote remove <remote url/short name>
```

## Tag
>Des références conviviales sont utilisées pour indiquer des jalons ou des points de référence dans le code

Créer une balise avec le nom donné
```bash
git tag <tag_name>
```
Répertorier toutes les balises disponibles
```bash
git tag 
```
Afficher les détails de la balise spécifiée
```bash
git tag show <tag_name>
```
Affiche les balises qui correspondent au modèle ou aux caractères spécifiés
```bash
git tag -l “.*”
```

```mermaid
 gitGraph
       commit
       commit id: "Normal" tag: "v1.0.0"
````
## Colaborate 
