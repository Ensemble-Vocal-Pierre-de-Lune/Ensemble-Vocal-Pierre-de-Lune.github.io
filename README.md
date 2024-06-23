# Code source du site web Pierre de Lune #

## Qu'est-ce qu'un site statique ? ##

Le site est _static_ : quand un utilisateur consulte une page, le serveur qui rend la page
n'exécute aucune logique pour intercaler ou ajuster l'information affichée, la page est
simplement rendue. La liste des concerts est générée, non pas lors de la consultation,
mais lorsqu'on déploie : ainsi, un concert à venir restera-t-il dans "concerts à venir" 
tant qu'on n'aura pas redéployé le site, même si le concert est derrière nous dans la vraie 
vie.

## Principe de fonctionnement ##

Dans les sources, chaque page ne contient que son contenu spécifique (texte, images).
A côté de ça, on a des fichiers qui définissent les éléments communs (styles, header, menu...)
qui apparaissent dans toutes les pages. Et certaines pages contiennent des instructions,
notamment pour générer automatiquement la liste des concerts.

Pour assembler tout ça en site exploitable, on les passe dans la moulinette [Jekyll](jekyllrb.com).

Les sources sont sous contrôle de version avec l'outil `git` et hébergées par Github. Quand
on y travaille, on tire une copie (de l'ensemble de l'historique) depuis Github ; on modifie 
localement, puis on repousse la modification chez Github. 

Github fournit également le déploiement et l'hébergement web du site : à chaque fois qu'on
pousse une modification de l'historique des sources, Github exécute la moulinette Jekyll
sur la nouvelle version des sources, et met en ligne les pages web résultantes.

## Logiciels à installer ##

- git (gratuit)
- n'importe quel éditeur de texte ou environnement de développement intégré (IDE), à convenance
- Facultatif : Docker Desktop (gratuit pour utilisation personnelle et associative)

### Vérifier localement avant de publier ###

On peut faire une modification "à l'aveugle" et la déployer, sans avoir à tourner
Jekyll sur sa machine. En revanche, exécuter Jekyll est nécessaire pour vérifier le rendu avant de
la rendre publique. Installer Jekyll est assez technique ; c'est plus simple d'utiliser
Docker, qui permet de tourner Jekyll dans un environnement prédéfini et isolé.

Pour ce faire, une fois Docker Desktop
installé, à la ligne de commande :

    docker run --rm -it \
      --volume="$PWD:/srv/jekyll" \
      --volume="$PWD/vendor/bundle:/usr/local/bundle" \
      -p 4000:4000 jekyll/jekyll:latest \
      jekyll serve
