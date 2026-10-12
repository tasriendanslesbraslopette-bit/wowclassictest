---
name: phase-3bis-assets
description: "Phase 3bis — étude de faisabilité : réutiliser, convertir ou recréer les assets FFXIV pour le moteur WoW 3.3.5a, avec preuve de concept sur un modèle libre."
disable-model-invocation: true
---

# Phase 3bis — Assets : réutiliser ou recréer ?

Peut tourner en parallèle de la phase 3. Livrable : `docs/assets-feasibility.md`, qui commence par la réponse en une phrase.

## Hypothèse à confirmer ou infirmer avec des faits

La conversion directe d'assets FFXIV est techniquement partielle et coûteuse, et juridiquement non couverte : la politique d'utilisation des contenus FFXIV ne vise que textes, images, captures, vidéos et musiques, à titre non commercial ([source](https://support.na.square-enix.com/rule.php?id=5382&tag=authc)). D'où l'hypothèse : recréer des assets originaux ou recombiner les assets WoW.

**Ce que tu ne fais pas** : extraire, télécharger, convertir ou intégrer des fichiers FFXIV. L'étude est documentaire, et la preuve de concept utilise un modèle CC0 ou créé par moi.

## Étapes

1. Décrire le pipeline théorique : outils d'export FFXIV (TexTools, Meddle, Penumbra Model IO) → Blender → M2/.skin + BLP (WoW Blender Studio, bibliothèques comme `wow-m2`) → déclaration DBC (ItemDisplayInfo, SpellVisual/SpellVisualKit, CreatureDisplayInfo) → patch MPQ. Vérifier l'état actuel de chaque outil.
2. Remplir la grille :

| Type d'asset | Obstacle technique principal | Effort | Verdict |
| --- | --- | --- | --- |
| Icônes de sorts | Conversion BLP 64×64 | | |
| Arme (ex. rapière) | Polycount ; matériaux FFXIV multi-cartes vs shaders 3.3.5a simples | | |
| Armure portée | Re-skinning sur chaque modèle race/sexe WoW, géosets | | |
| Effets de sorts | Format VFX FFXIV non convertible → particules/rubans M2 | | |
| Animations | Squelettes et format Havok incompatibles → retargeting complet | | |
| Sons | Conversion simple ; même contrainte juridique | | |

3. Preuve de concept : une rapière CC0 (ou que je fournis) importée en jeu via Blender → M2 → DBC → patch MPQ. Mesurer le temps passé à chaque étape.
4. Lister les assets WoW 3.3.5a réutilisables pour habiller la classe test (visuels de sorts recolorables, armes, icônes).

## Critères de fin

- [ ] Grille remplie et justifiée
- [ ] Preuve de concept visible en jeu, temps mesurés
- [ ] Recommandation finale + liste d'assets WoW réutilisables
