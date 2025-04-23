**Nom :** Le Besque Keryann

**Groupe :** B2

**Année :** Première année

**IUT Le Havre - Cours GIT**


### Compte-rendu TP3 – Travailler en équipe sur un dépôt GitHub distant
Dans ce TP, on apprend à collaborer à plusieurs sur un même projet en utilisant GitHub.
 C’est un aspect fondamental de Git, qui a été conçu dès le départ pour faciliter le travail en équipe.

Organisation en binômes
Avant de commencer, on forme des binômes.
 Chaque équipe doit désigner :
Athos : la personne qui héberge le dépôt sur son GitHub


Porthos : la personne invitée en tant que collaborateur



Objectifs du TP3
Dans ce TP, on apprend à :
Inviter un collaborateur dans un dépôt GitHub personnel


Travailler à deux sur un projet Java avec Git


Utiliser les branches pour gérer les fonctionnalités



1. Inviter un collaborateur
Athos :
Crée un nouveau dépôt sur son compte GitHub, appelé tp3


Va dans Settings > Manage access > Invite a collaborator


Demande à Porthos son nom GitHub et l’ajoute comme collaborateur


Porthos :
Accepte l’invitation reçue par mail pour collaborer au dépôt tp3


Athos et Porthos :
Se placent dans le dossier courseGIT


Clonent le dépôt avec :

git clone git@github.com:<utilisateur_athos>/tp3.git


On vérifie qu’on a bien les 3 dépôts :
ls
tp1  tp2  tp3

Synchronisation initiale
Porthos :
Copie les fichiers README.md et src/Cryptomonnaie.java depuis tp2 vers tp3


Synchronise avec :

git add .
git commit -m "Ajout des fichiers depuis tp2"
git push

Athos :
Fait un git pull dans son dossier local tp3 pour récupérer les modifications de Porthos


Les deux :
Vérifient que les fichiers locaux et distants sont bien synchronisés



2. Développement du projet Java en équipe
Objectif : créer un marché de crypto-monnaies avec portefeuilles
Concepts :
Un portefeuille contient une seule crypto-monnaie, permet les achats et transferts


Un marché est un ensemble de portefeuilles


Athos :
Copie les fichiers suivants dans tp3/src :


CryptoMarche.java


Portefeuille.java


TestCryptoMarche.java


Effectue un git add, un git commit et un git push


Porthos :
Fait un git pull pour récupérer les fichiers


Les deux :
Vérifient que tout est bien compilé


Exécutent le test :

 

java TestCryptoMarche

Résultat attendu à ce stade :

Test Portefeuille transfertDevise        ... FAIL
Test Portefeuille achatDevise            ... FAIL
Test CryptoMarche capitalEnEuros         ... FAIL
Test CryptoMarche capitalMonneaie        ... FAIL

Répartition des tâches
Athos :
Implémente dans CryptoMarche.java :


capitalEnEuros(String proprietaire)


capitalMonneaie(Cryptomonnaie monnaie)


Une fois terminé : commit + push


Porthos :
Implémente dans Portefeuille.java :


transfertDevise(Portefeuille destination, double montantJetons)


achatDevise(double montantEuros)


Une fois terminé : commit + push


Les deux :
Synchronisent leurs dépôts


Recompilent et relancent le test


Résultat attendu :

Test Portefeuille transfertDevise        ... OK
Test Portefeuille achatDevise            ... OK
Test CryptoMarche capitalEnEuros         ... OK
Test CryptoMarche capitalMonneaie        ... OK



3. Travailler avec les branches
3.1. Créer une branche de test
Les deux :
Vérifient la branche actuelle avec git branch (devrait être main)


Créent une branche de test :

git checkout -b test

Créent un fichier test.txt, l’ajoutent et le valident :

touch test.txt
git add test.txt
git commit -m "fonction de test ajoutée"

Reviennent à la branche main :

git checkout main

Modifient README.md et font :

git add README.md
git commit -m "nouveau commit sur la branche principale"

Vérifient l’historique :

git log --graph --oneline --all --decorate --topo-order

3.2. Fusionner une branche
Les deux :
Se placent dans main


Fusionnent la branche test :

git merge test

Vérifient avec :

git log --graph --oneline --all --decorate --topo-order
Supprimer le fichier test.txt :

 

git rm test.txt
git commit -m "test.txt supprimé"

4. Créer une nouvelle crypto-monnaie avec des branches
Athos :
Crée une branche AthosCoin


Implémente une classe :
Faire un commit et fusionne la branche avec main


Synchronise avec GitHub


Porthos :
Fait de même dans une branche PorthosCoin


Crée sa classe de crypto-monnaie, commit, merge, push

