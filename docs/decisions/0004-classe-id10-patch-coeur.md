# 0004 — Vraie classe Aubelame : ID 10 avec un petit patch du cœur

- **Date :** 2026-10-12
- **Statut :** acceptée (choix de Jimmy sur la carte de décision)

## Contexte

Le palier B ajoute une onzième classe jouable. L'étude d'impact de la session du PC (`docs/class-impact.md` dans le dépôt `serveur-wow`, non relue ici) conclut que l'ID 12 est impossible sans modifier le cœur (`MAX_CLASSES = 12`) et que l'ID 10 est le bon choix, mais qu'il demande quand même un petit patch du cœur : environ 20 lignes dans 3 fichiers (masque de classes jouables et tableaux de constantes). La règle 1 de `CLAUDE.md` n'autorise un patch du cœur qu'en dernier recours.

## Décision

Classe d'ID 10, avec un patch minimal du cœur, placé dans `patches/` et documenté ici. Un essai client d'environ un jour (B0) passe en premier : si le `wow.exe` modifié du pack HD refuse une classe d'ID 10, on s'arrête et on revoit le choix.

## Alternatives écartées

- Remplacer une classe désactivée (Démoniste) : aucun patch, mais la classe prend la place d'une autre (estimation de 15 à 25 jours).
- Finir le kit greffé sur le Mage : pas de nouvelle classe (estimation de 4 à 7 jours).

## Conséquences

- Le cœur n'est jamais modifié sur place : le patch vit dans `patches/` et s'applique au build.
- Sauvegarde des bases avant toute modification (règle 4).
- Les estimations (20 à 32 jours au total) sont celles de l'étude, pas des mesures.
- Questions encore ouvertes : armes, armures et races de la classe, talents natifs ou simulés, noms, usage personnel ou distribution.
