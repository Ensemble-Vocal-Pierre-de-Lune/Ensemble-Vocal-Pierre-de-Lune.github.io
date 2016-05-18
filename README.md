# Code source du site web Pierre de Lune #

Ce projet contient les sources du site web.

## Fonctionnement global ##

Les sources sont en HTML ou en Markdown (extension .md). Pour passer des sources
au site tel qu'on le met en ligne, ces sources sont transformés par [Jekyll](jekyllrb.com) :

- Le Markdown est transformé en HTML
- L'index des concerts est généré à partir des pages concerts individuelles
- Certains éléments comme le menu de navigation et le logo sont insérés dans 
  chaque page (pour ne pas avoir à les dupliquer dans chaque page)

A chaque fois qu'un changement des sources est poussé dans Bitbucket (c'est-à-dire ici),
le plugin Aerobatic lance la transformation par Jekyll et déploie automatiquement le
résultat sur le site publique.

Le site est _static_ : quand un utilisateur consulte une page, le serveur qui rend la page
n'exécute aucune logique pour intercaler ou ajuster l'information affichée, la page est
simplement rendue. Cela fait qu'un concert à venir restera dans "concerts à venir" même
après que sa date soit passée. En revanche, quand on génère et déploie le site, le concert
est rangé automatiquement dans la bonne liste en fonction de sa date.

## Instructions ##

Toutes les instructions sont dans le [wiki du projet](bitbucket.org/evpdl/pdlweb/wiki/).
Pour les consulter, il faut créer un compte sur BitBucket et se faire ajouter au projet.
(Si vous lisez ceci, c'est vraisemblablement que cela est déjà le cas.)
