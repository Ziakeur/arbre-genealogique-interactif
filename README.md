# Ascendance Aurélien VINCENT — version publique

**En ligne : https://ziakeur.github.io/arbre-genealogique-interactif/**
Dépôt : https://github.com/Ziakeur/arbre-genealogique-interactif (public, un seul fichier).

Page unique et autonome (`index.html`, 12 Mo, images embarquées), servie par GitHub Pages.

## Ce qui est masqué

Pour toute **personne vivante** : aucune date — naissance ni mariage — et aucun numéro d'acte.
Le nom et le lieu restent. Deux mentions, à ne jamais confondre :

- **« date masquée »** : l'information est **connue et documentée** dans le dossier, retirée
  volontairement de la version publique ;
- **« date inconnue »** : **lacune réelle** du dossier.

La page porte `<meta name="robots" content="noindex, nofollow">`.

## Mise à jour

`index.html` est un **fichier dérivé** : ne jamais l'éditer à la main. Repartir de
`..\Arbre_interactif_ascendance.html` et rejouer les trois scripts de masquage
(`patch.py`, `patch2.py`, `patch3.py` — 70 remplacements avec assertion d'unicité), puis :

    node --check   (sur le bloc <script> extrait)
    audit des jetons 1998 / 2003 / 13-04-1963 / 30-05-1964 / 03-07-1935 / 14-06-1997 / 1489 / 1170

⚑ **`GENYEARS` doit garder une année à quatre chiffres par colonne** : `GENSPAN` la lit par
expression régulière, et une étiquette sans chiffres (« vivant ») fait planter tout le rendu —
la page reste noire. Colonnes I et II : « v. 2000 » et « v. 1960 ».

Publication (le pont `device_bash` a le réseau et `git` ; `*.github.io` en revanche n'est pas
joignable depuis le pont ni depuis le conteneur — la vérification se fait dans le navigateur) :

    git clone https://github.com/Ziakeur/genealogie.git ~/repo   # hors du dossier partagé !
    cp index.html ~/repo/ && cd ~/repo
    git add -A && git commit --amend -m "arbre" 
    git push --force https://x-access-token:<jeton>@github.com/Ziakeur/genealogie.git main

⚑ **Ne pas créer le dépôt git dans ce dossier** : le pont ne peut pas supprimer de fichiers,
git y laisse des verrous (`HEAD.lock`, `index.lock`) qui bloquent l'opération suivante.
Historique volontairement gardé à **un seul commit** (`--amend` + `--force`) : 12 Mo par version.
