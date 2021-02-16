# Subversion quick start

- Faire un nouveau checkout 

```bash
$ svn checkout http://nom.de.domaine/trunk  dossier_destination
```

- Afficher les informations
```bash
$ svn info
```
- Créer un nouveau branche 

```bash
$ svn copy ^/trunk ^/branches/development -m "Creation branche development"
```
- Créer tag

```bash
$ svn copy ^/trunk ^/tags/v1.0.0 -m  "Creation tag v1.0.0"
```

- Afficher log

```bash
$ svn  log # simple
$ # Avancé, on peut enlever les paramètres que vous ne voulez pas utiliser
$ svn  log  chemin_fichier_ou_dossier --search=luc.dupont -l 25 -r "{2021-02-05}:{2021-02-10}" # ou -r 10248:19268
```

- Afficher statut

```bash
$ svn  status # simple

$ svn  status chemin_fichier_ou_dossier 
```
- Faire un commit 

```bash
$ svn  commit  .  -m "Tache-1 : Mise à jour ...." # Commiter tous les modifications dans le dossier "."
$ svn  commit  chemin_fichier_ou_dossier [ chemin_nieme_fichier_ou_dossier ]  -m "Tache-1 : Mise à jour ...."
```
- Comparer les revisions

```bash
$ svn  diff chemin_fichier_ou_dossier -r 1589:1623 
$ # Comparaison avec interface graphique
$ svn diff --diff-cmd="meld"  -r 1589:1623 chemin_fichier # meld doit être installé pour que cela fonctionne
```
- Change de branche

```bash
$ svn  switch ^/branches/development
$ svn  switch ^/trunk
```
- Fusionner(Merge) une branche

```bash
$ # branche vers trunk (le plus utilisé fréquement)
$ svn  switch ^/trunk
$ svn  merge ^/branches/development

```

```bash
$ # trunk vers branche ( utilisé seulement pour mettre à jour la branche)
$ svn  switch ^/branches/development
$ svn  merge ^/trunk
```
- Ajouter  dans la versioning

```bash
$ svn  add . # ou
$ svn  add chemin_fichier_ou_dossier [chemin_nieme_fichier_ou_dossier]
```
