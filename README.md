Par binômes, vous incarnez Alice et Bob, deux écologues qui veulent développer ensemble un projet R pour leur permettre d'additionner deux nombres entiers. Le tutoriel est organisé en trois sections qui permettent d'illustrer les fonctionnalités basiques et intermédiaires du contrôle de version par git couplé au partage de code par GitHub.

# Commencer le tutoriel

 - `fork`, `clone`
 - inviter des collègues à un projet

Répartissez vous les deux rôles. Pour le contexte, Alice pratique l'écologie depuis plus longtemps que Bob, dont le projet d'additionner deux nombres est le projet principal en ce moment (à l'image d'un binôme encadrant.e/étudiant.e).

Bob a trouvé sur GitHub un projet existant qui paraît être une bonne base pour commencer son projet. C'est la page de ce tuto ! Connecté à son compte GitHub, il `fork` le répertoire du projet pour créer un répertoire identique, mais dépendant de son compte personnel. Bob peut ajouter Alice comme collaboratrice à son fork, depuis le répertoire sur GitHub, dans Paramètres > Collaborateurs > Ajouter des personnes.

Rstudio permet de `clone` le répertoire créé : importer les fichiers correspondants sur son ordinateur personnel, dans un dossier dédié. Fichier > Nouveau projet > Contrôle de version > Git : remplir l'URL du répertoire (dans le compte de Bob), puis créer le projet.

Alice et Bob clonent le projet tous les deux, chacun sur son ordinateur.

# Scénario 1 

Bob décide de développer son projet étape par étape et commence par écrire une fonction pour ajouter 2 à n'importe quel nombre. Dès qu'il a écrit cette fonction, il la partage avec Alice via GitHub.

## 1a - apporter des modifications, les partager

- créer un commit avec `add` et `commit`
- envoyer ses commits sur le serveur avec `push` et les importer avec `pull`

Bob écrit la fonction correspondante dans R/functions.R, sauvegarder puis `git add`:

Bob ajoute ainsi les modifications apportées à l'environnement de *staging*. Une fois que Bob est satisfait de cette mise à jour du projet, il peut `commit` ses modifications, en remplissant le message de commit puis cliquant sur commit.

Bob peut cliquer sur `push` pour envoyer ses commits locaux sur GitHub. Pour voir la nouvelle version du projet, Alice n'a qu'à cliquer sur `pull`.

Optionnel : après avoir `pull` les modifications de Bob, Alice fait à son tour des modifications, qu'elle peut `commit` et `push`.

## 1b - revenir à des versions antérieures

- `log`, `checkout`

Finalement, Bob se dit qu'il y a probablement plus simple à faire que d'écrire manuellement une fonction pour chaque nombre à ajouter. Dans l'onglet "Historique" (ou en lançant `git log` dans l'onglet "Terminal"), il repère le hash du commit qui correspond au projet avant qu'il n'ajoute sa fonction. `>git checkout 197c1` permet de restaurer l'état du projet à ce commit. alternativement, Bob peut utiliser l'interface graphique pour voir l'état de `R/functions.R` avant ses modifications.

Bob peut copier le code tel qu'il était initialement, puis `git checkout main` permet de restaurer le projet. Bob peut alors coller le code initial à la place de ses modifications, et `commit` ce retour en arrière s'il le souhaite.

Optionnel : `git revert <hash>` crée automatiquement un commit qui annule les modifications du commit désigné par <hash>. Si on veut revert plusieurs commits, `git revert <hash1> <hash2> <hash3>` fonctionne 

