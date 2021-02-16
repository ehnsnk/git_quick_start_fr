# Subversion quick start

- Faire un nouveau checkout 

```bash
$ svn checkout http://nom.de.domaine/trunk  dossier_destistation
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
$ svn  log  chemin_fichier_ou_dossier --search=luc.dupont -l 25 -r "{2021-02-05}:{2021-02-10}" # ou -r 10248:19268
```

- Afficher statut

```bash
$ svn  status chemin_fichier_ou_dossier 
```
- Faire un commit 

```bash
$ svn  commit  chemin_fichier_ou_dossier [ chemin_nieme_fichier_ou_dossier ]  -m "Tache-1 : Mise à jour ...."
```
- Comparer les revisions

```bash
$ svn  diff chemin_fichier_ou_dossier -r 1589:1623 
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
