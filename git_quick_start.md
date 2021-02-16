# GIT QUICKSTART TUTORIAL FR

## Configuration de base
- Nom d'utilisateur
```bash
$ git config --global user.name "Dupont Jean"
```
- Adresse Email
```bash
$ git config --global user.email "dupont_jean@gmail.com"
```

- Ne pas Ecraser votre projet s'il y a une modification encours
 sur le depot en ligne --> important
```bash
$ git config --global branch.autosetuprebase always
```
- Gerer les mauvaises commit due aux incompatibilite entre GNU\Linux et Windows
 (necessaire pour les developpeurs qui utilise des systemes d'exploitation differents)

    - Pour Windows
```bash
$ git config global core.autocrlf true
```

    - Pour Unix,Linux
```bash
$ git config global core.autocrlf input
```

- Couleur pour l'apparence
```bash
$ git config --global color.ui true
```
```bash
$ git config --global color.status auto
```
```bash
$ git config --global color.branch auto
```
- Editeur par defaut
```bash
$ git config --global core.editor vim
```
- Configurer l'outil de fusion
```bash
$ git config --global merge.tool vimdiff
```
- Lister votre configuration finalement 
```bash
$ git config --list
```

## Creer un depot en ligne(effectue seulement une fois):
-Creer un dossier ex: projet.git sur gitlab ou github
-Initialiser le projet par un "git --bare init" c'est deja fournit
par gitlab ou github lorsque vous creer un dossier sur le depot 
en ligne ou gitlab/github vous invite de lancer quelque commande
qu'il va vous donner ou indiquer sur sa page. Mais pour le depot d'un
projet purement local voici la commande:

```bash
$ mkdir projet.git
```
```bash
$ cd projet.git/
```
```bash
$ git --bare init # initialiser le depot local
```

## Initialiser votre projet personnel
```bash
$ cd calculatrice_project
```
```bash
$ git init
```
- Et apres cela(commandes tres reccurents qu'on doit faire 
tout au long de votre projet):
```bash
$ git status -s

$ git add . # ou bien  git add --all, ou git add <nom_du_fichier>

$ git status -s

$ git commit -m 'Ici la descritpion de votre commit'

$ git log # Pour visualiser le log du commit effectue
```

## Envoyer votre projet sur le depot en ligne
-Configurer tout d'abord l'url de votre depot en ligne
(!!! C'est seulement effectue une fois or ou vous changez
de depots gitlab vers github ou vers bitbucket)
```bash
$ git remote add origin  dupont_jean@gitlab.com:projet.git 
	# peut etre aussi: https://www.gitlab.com/dupont_jean/projet.git,
	# veuillez renseigner sur gitlab ou github or a propos
	# de cette commande
```
- Envoyer votre projet enfin
```bash
$ git push origin master 
```
## Cloner unprojet sur  depot en ligne vers un depot local
```bash
$ git clone  dupont_jean@gitlab.com:projet.git  # ou https://gitlab.com/dupont_jean/projet.git
```
## Visualiser un detail sur un commit
```bash
$ git show cead14255ad5c530897 # <---id du commit affiche sur : git log 
```
## Regarder une modification
```bash
$ git diff
```
## Avant de faire votre commit( cad faire un "git push origin master" sur  depot en ligne),
 il faut mettre a jour  votre projet depuis le depot distant s'il y a une modification
 encours faite par un autre developpeur.  

```bash
$ git pull --rebase # ou "git pull" mais attention si ce n'est pas configurer comme 
		    # on a fait au dessus "git pull" causera un conflit sur votre
		    # fichier
```

## Pour tester git sur un hote local :
- Creer un repertoire dans /var/www/depot_git
- Puis creer un dossier pour chaque utilisateur du depot dans le dossier depot_git
 ex:depot_git/dupont_jean
- Creer un dossier racine de votre projet dans le dossier dupont_jean. Ex: dupont_jean/calculator_project.git
 Executer la commande suivante:
```bash
$ cd /var/www/depot_git/dupont_jean/calculator_project.git

$ git --bare init
```

- Vous pouvez envoyer votre projet enfin.
```bash
$ cd calc_proj  # Votre projet calculator en local

$ git init

$ git remote add origin  http://localhost/depot_git/dupont_jean/calculator_project.git

$ git status -s

$ git add .

$ git commit -m "Mon commit"

$ git push origin master # Envoi de votre projet sur  http://localhost/depot_git/dupont_jean/calculator_project.git
```

## Stash Operation(git stash): c'est utilise dans le cas ou votre patron par exemple
vous dit de creer une fonctionalite tchat or que vous avez travail sur une 
fonctionnalite blog (qui n'est pas encore stable). vous devez stasher la fonctionalite blog
avant de faire le tchat. Veuillez renseigner sur le sujet



**************************************************LES TAGS********************************************************
## Tag Operation :
Exemple de tag:
-Oracle : 11g,10c4
-Android : Kitkat,Lollipop
-Autre : - v1.0.7
	 - Release_1.0.7
	 - 1.0.7

Signification:
- Tag numerique/alphanumerique
v1.0.7,11g(implicitement c'est 11g0),Release_1.0.7, 1.0.7 sont le meme principe de codification
Son format est : X.X.X ou text_X.X.X
 Exemple : le 1.0.7 
.. le "1" veut dire changement d'architecture(dans la majorite des cas) cad :
    changement du structure  du dossier projet (architecture ou squellette du projet proprement dit),
    du syntax (pour certains framework ex syntax d'Angularjs != Angularjs 2(Angular 2) ) 
.. le "0" veut dire ajout de nouvelle : fonctionnalite ou fonction ou methode.
    exemple: 
    Avant la methode disponible pour une classe Voiture est avancer() donc :
	 +++> Voiture:avancer() 
    ajout d'une nouvelle methode reculer() pour la classe Voiture, et apres ca devient:
	 +++> Voiture::avancer()
	 +++> Voiture::reculer()
.. le "7" veut dire modification au sein d'une methode:
   exemple: pour Voiture::reculer()
   -Avant:
    reculer(){
	 &"Une seule instruction ";
    }
	
   - Apres:
```java
    reculer(){  
         &"Une seule instruction ";
         &"Ajout du nouvelle instruction "; <-------------------!!!!!!!!! Ajout d'une nouvelle ligne de code
    }
```

Meme principe pour le cas 11g(11g0): 0-9 suivi de a-z et de 0-9:
  exemple: 6k13, 3ac5

Resume:
 Ex: 6k13
 6: Nouvelle Architecture
 k: Nouvelle Fonctionnalite
 13:Performance: Correction des bug,amelioration d'un algorithme d'instruction  dans une methode 

- Tag Alphabetique:
  Nom choisit(qui doit etre ordonnee alphabetiquement[pas obligatoirement]. Ex: Kitkat(K),
  Lollipop(L),Marshmallow(M),Nougat(N),Oreo(O))  selon votre guise ou choix. Ces noms sont 
  inspirer du dessert sur le Fast Food, Alimentation a la Marchandise generale aux Etat-unis
  (Mc Donald specialement).


## Revenons a git:
```bash
$ cd projet/

$ git tag -a 'v0.0.1' -m 'Description du tag' HEAD
```
- Commiter un tag vers le depot distant
```bash
$ git push origin tag  v0.0.1
```
- Visualiser un tag
```bash
$ git pull 

$ git tag -l #lister tous les tags

$ git show v0.0.1
```
- Supprimer un tag
```bash
$ git tag

$ git tag -d v0.0.1

$ git push origin :v0.0.1
```
*********************************************************************************************************************


## Branche
- Ajouter une nouvelle branche
```bash
$ git branch new_branch
```
- Lister les branches
```bash
$ git branch
```
- Changer des branches
```bash
$ git checkout new_branch 
```
- Supprimer une branche
```bash
$ git branch

$ git checkout master

$ git branch -D new_branch
```
- Renommer une branche
```bash
$ git branch

$ git branch -m new_branch renamed_branch
```

- Fusionner une branche a la branche master
```bash
$ git checkout master

$ git merge renamed_branch # cad renamed_branch ====> master

```

RETENEZ BIEN IL FAUT TOUJOURS TRAVAILLER DANS UN AUTRE BRANCHE QUE MASTER POUR EVITER DES CONFLITS

**************************************************************************************************

## QUAND VOUS REPEREZ UN BUG SUR UN PROJET, DEMARCHE A FAIRE: (IMPORTANT)

- On ne touche pas une tache d'un autre developpeur (car il y a un autre developpeur qui s'occupe pour 
 la correction d'un bug sur un projet s'il y en a. Ou peut etre une personne volontaire ou qui le trouve
 ce bug en premier qui la corrige).

- Aller sur le site web de votre depot: gitlab ou github,....

- Reperer la fonctionnalite **ISSUES**: create issue ou new issue selon votre plateforme

- Remplisser le formulaire: title,description,bug type,......

- NOMENCLATURE DU COMMIT SUR LES BUG CORRIGES(Si vous avez corriger des bugs ou problemes )

On doit ajouter le mot cle: "fixes #id,..." au debut du description du commit
#id c'est l'id des issues ex: #4, #568899 ,regarder l'exemple pour l'illustration
```bash
$ git commit -a -m 'fixes #1, Vous pouvez mettre votre texte apres cela'
```
*****************************************************************************************************

## Faire un FORK sur un projet(But : Participer au developpement d'un projet existant par ex: Cakephp,Debian,...)

- Allez sur l'URL du depots,

- Reperez le bouton "Fork", puis cliquer, cela ajoutera automatiquement une copie entiere du projet(non-officiel)

- Cloner l'URL de votre fork

- Creer une autre branche que master

- Apres que vous avez termine de developper sur cette branche nomme par ex: my_branch
 vous commitez la branche my_branch sur le depot de votre fork, comme ceci:
```bash
$ git push origin my_branch
```
- Demander l'avis de l'auteur pour fusionner le fork  a la version originelle par le bouton
 "Compare & pull request" (Reperez bien car ca varie selon le plateforme que vous utiliser )
 
- Selectionner la branche a fusionner sur le depot officielle(evidemment c'est master),puis la branche
  de votre fork(ici c'est my_branch)

- Ecrire un titre et commentaire puis validez l'action

******************************************************************************
		TRAVAILLEZ EN EQUIPE AVEC GIT-FLOW

Le differente branche utiliser sur git-flow
- master
- develop
- release
- hotfix 
- feature

## master :
 La version stable en production de votre projet. Il est tres conseille de ne
 pas faire beaucoup de commit sur cette branche. Les commits faites sont seulement 
 lorsqu'il y a un changement de version ou de correction de bug

## develop : 
   sur cette branche qu'on fusionne tous les projets effectues par les
   developeurs s'ils ont ete accepte par le chef de projet. Cela la version
   instable de l'application qui est develope sur cette branche. Si le projet
   sur cette branche est fonctionnel on peut passer sur la branche release  

## release
   La branche release est destine pour developper une application qui est
   deja fonctionnelle et pret a etre fusionner sur la branche master pour
   mettre en production. La modification subit sur le projet dans cette 
   branche doit etre legere. Ex: derniere amelioration sur la  mise en
   page d'un site web.C'est a dire que la mise en page est deja satisfaisant
   mais au cours de developement vous arriver a trouver une idee(Pourquoi 
   ne pas mettre un petite animation sur cette contenu avant de mettre en  
   production?).Si vous rencontrer une situation comme cela, c'est la
   branche release qui est utilisee.
   
   Et a la fin, vous mettez un  tag sur le projet.  

## feature
  Sur cette branche qu'on developpe toutes les fonctionnalites de votre projet
  avant d'etre rassembler sur  la branche develop. Par Exemple: on va developer
  un petit blog d'un  reseau sociaux. il y a 3 developeurs A,B,C. La tache de A s'occupe
  sur la  gestion d'utilisateur(authentification,inscription,
  apparence de l'accueil du site,... ),
  le B s'occupe sur l'article et commentaire, et le C s'occupe sur l'envoi
  des messages. Donc on doit creer 3 feature pour le developpeur A,B,C.
  Pour: 
      A : feature/user-management
      B : feature/post
      C : feature/message 
  Quand toutes ces taches sont termines, on fusionne sur la branche develop
  et subit une certaine rectification.

## hotfix
 C'est pour la correction rapide du projet(Oh!! J'ai fait des fautes de frappe sur cette paragraphe
 ,je dois la rectifie tout de suite). La branche hotfix est faite pour vous si vous rencontrez une 
 telle situation. Puis Fusionner avec master si votre correction est finie.
 

- Exemple pour initialiser un projet sur git flow 
```bash
$ mkdir proj 

$ cd proj

$ touch README.md

$ git init

$ git add .

$ git commit -m "First commit"

$ git branch

$ git flow init
```

- Terminer  de travailler sur  la branche feature/homepage (page d'accueil du site) 
  fusionner la branche feature/homepage sur develop  
```bash
$ git flow feature finish homepage
```
- Envoyer un mise a jour de la branche feature/homepage du depot distant 
```bash
$ git branch

$ git add .

$ git commit -m "Ajout du fichier html"

$ git remote add origin ../remote    # ../remote est un dossier cad depot local 

$ git flow feature publish homepage  # commiter la branch feature/homepage 
				     # sur le depot distant
```
- Update feature/homepage
```bash
$ git pull origin feature/homepage
```
- Fusionner avec la branche feature/homepage  develop
```bash
$ git flow feature finish homepage
```
- Creer un release
```bash
$ git flow release start v0.0.1
```

- Fusionner la branche release/v0.0.1 avec master
```bash
$ git flow release finish v0.0.1         #il y a des info a completer
```
- Commiter les branches modifie vers un depot distant
```bash
$ git push --tags # pour v0.0.1

$ git push origin develop

$ git push origin master
```

- Creer un une branche hotfix
```bash
$ git flow hotfix start title  # creation de branche hotfix/title

$ git add index.html

$ git commit -m "Changement du titre"
```
- Fusionner la branche hotfix/title a la branche master
```bash
$  git flow hotfix finish title #Il ya une information a completer
```
- Regarder l'Historique des commits
```bash
$ git log --grap --online --first-parent develop
```
ou
```bash
$ git log --graph --online
```



