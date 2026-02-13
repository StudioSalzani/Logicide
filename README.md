# MURDLE — Jeu d'enquête et de déduction

Un jeu de logique à la Cluedo, jouable directement dans le navigateur, en un seul fichier HTML.

## Jouer

Ouvrez simplement `index.html` dans un navigateur — aucune dépendance, aucun serveur requis.

Ou hébergez-le sur GitHub Pages : `Settings → Pages → Deploy from branch (main / root)`.

## Règles

Un meurtre a été commis. Trois catégories d'éléments sont en jeu :
- **Suspects** — qui a commis le crime ?
- **Armes** — quel objet a été utilisé ?
- **Lieux** — où le crime a-t-il eu lieu ?

### La grille de déduction
La grille croise chaque entité avec les autres. Pour chaque case :
- **1 clic** → `◆` (confirmé)
- **2 clics** → `✕` (exclu)
- **3 clics** → effacé

Quand vous confirmez une case, le jeu exclut automatiquement les autres possibilités sur la même ligne/colonne.

### Les indices
Chaque affaire fournit des indices logiques dans l'onglet **Indices**. Cliquez sur un indice pour le marquer comme utilisé.

### L'accusation
Une fois certain de votre déduction, rendez-vous dans l'onglet **Accusation**. Vous n'avez **qu'une seule chance** — une mauvaise accusation met fin à l'enquête.

### Le temps
Un minuteur décompte. Si le temps s'écoule, l'affaire reste non résolue.

## Niveaux de difficulté

| Niveau | Suspects | Armes | Lieux | Temps |
|---|---|---|---|---|
| Novice | 3 | 3 | 3 | 10 min |
| Inspecteur | 4 | 4 | 4 | 15 min |
| Détective | 5 | 5 | 5 | 20 min |

## Structure

```
murdle/
└── index.html    — Jeu complet (HTML + CSS + JS inline)
```

Tout le jeu tient en un seul fichier HTML, sans dépendance externe mis à part les polices Google Fonts.

## Ajouter des affaires

Les affaires sont définies dans l'objet `CASES` du script JavaScript. Pour en ajouter une :

```js
CASES.nouveauNiveau = {
  id: "0999",
  title: "Le Titre de l'Affaire",
  desc: "Description narrative du crime.",
  suspects: [
    { name: "Nom Suspect", desc: "Profession / Âge" },
    // ...
  ],
  weapons: ["Arme 1", "Arme 2", "Arme 3"],
  places:  ["Lieu 1", "Lieu 2", "Lieu 3"],
  clues: [
    "Premier indice logique.",
    // ...
  ],
  solution: { suspect: "Nom Suspect", weapon: "Arme 1", place: "Lieu 2" },
  time: 600, // secondes
};
```

## Design

Design system minimaliste : noir et blanc, police Cormorant Garamond pour les titres, IBM Plex Mono pour les étiquettes, Inter pour le corps du texte. Accent parchmin doré (`#c8b896`) uniquement pour les états actifs.
