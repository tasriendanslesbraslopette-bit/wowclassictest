# 0003 — Fichiers FFXIV : usage local et personnel autorisé

- **Date :** 2026-10-12
- **Statut :** acceptée (choix de Jimmy sur la carte de décision)

## Contexte

La règle 5 de `CLAUDE.md` interdisait tout fichier FFXIV. Jimmy a demandé de la lever, puis a choisi « Les utiliser » pour les fichiers déjà extraits depuis son installation FFXIV (une rapière et des icônes d'actions du Mage Rouge, convertis en patch local).

## Décision

Les fichiers FFXIV sont autorisés pour un usage local et personnel : extraction en lecture seule depuis l'installation de Jimmy, conversion pour son client, test sur son serveur privé. Ni commit, ni push (même privé), ni partage. Noms et textes FFXIV non repris : la classe et ses sorts restent originaux.

## Risques connus

- La politique de contenu de Square Enix, telle que citée dans le brief de la phase 3bis, vise textes, images, vidéos et musiques, pas les modèles 3D ; leur contrat d'utilisateur n'a pas pu être relu à la source. Ce n'est pas un avis juridique.
- Un serveur ouvert à d'autres joueurs rendrait ces fichiers distribués : la décision ne couvre que l'usage personnel de Jimmy.
- Rendu en jeu non vérifié : orientation, taille en main, icônes.

## Conséquences

- `.gitignore` exclut `assets/ffxiv/`, `client-patch/build/` et les `.mpq` FFXIV.
- Les scripts de conversion déjà poussés sur le dépôt `serveur-wow` ne contiennent pas de données, mais ils restent à retirer si Jimmy change d'avis.
- La décision 0004 (habillage par assets WoW) reste le plan de repli.
