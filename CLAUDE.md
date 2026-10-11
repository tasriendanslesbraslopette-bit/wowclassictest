# Projet : serveur WoW privé + classe inspirée de FFXIV

## Contexte

- Serveur WoW privé.
- Base visée : AzerothCore, client WotLK 3.3.5a (build 12340). Choix à confirmer en phase 1.
- But final : un serveur stable, puis **une seule** classe custom inspirée d'un job FFXIV (choisi : Mage Rouge, voir `docs/decisions/0002-job-ffxiv.md`), plus une étude de faisabilité sur les assets.
- Mon niveau : débutant (je ne connais ni l'émulation WoW ni le C++ ; commandes guidées pas à pas). Explique les notions propres à l'émulation WoW (DBC, MPQ, extracteurs, SpellFamily…) la première fois qu'elles apparaissent.
- Infos propres à ma machine (OS, chemins du client WoW) : voir `CLAUDE.local.md`.

## État du projet

@docs/STATUS.md

## Organisation du dépôt

Structure cible, à confirmer ou ajuster en phase 2 :

```
.
├── CLAUDE.md                # ce fichier
├── docs/
│   ├── STATUS.md            # état courant, mis à jour par /fin-de-session
│   ├── decisions/           # une note par décision (NNNN-titre.md)
│   └── id-ranges.md         # plages d'IDs réservées aux ajouts custom
├── vendor/azerothcore-wotlk # clone du cœur, jamais modifié (gitignored ou submodule)
├── modules/                 # nos modules AzerothCore (C++, Lua, SQL), liés dans vendor/…/modules/
├── patches/                 # patchs du cœur, seulement si inévitable, documentés
├── client-patch/            # sources éditables des DBC/UI + script de build du patch MPQ
├── config/                  # authserver.conf, worldserver.conf, docker overrides
├── scripts/                 # build, démarrage, sauvegarde, restauration
└── backups/                 # dumps SQL (gitignored)
```

## Commandes

À remplir par Claude à la fin de la phase 2, une ligne par commande réellement testée :

- Build : [À REMPLIR]
- Démarrer / arrêter : [À REMPLIR]
- Logs : [À REMPLIR]
- Sauvegarde / restauration : [À REMPLIR]

## Règles non négociables

1. **Cœur intact** : ne jamais modifier les fichiers suivis par Git dans `vendor/azerothcore-wotlk`. Tout ajout passe par `modules/` ; AzerothCore ne compile que les modules présents dans son propre dossier `modules/`, donc on y crée un lien symbolique (ou un montage Docker) vers les nôtres — c'est le seul ajout toléré dans `vendor/`. Un patch du cœur n'est permis qu'en dernier recours, dans `patches/` avec une note dans `docs/decisions/`.
2. **Vérifier avant d'affirmer** : champs DBC, tables SQL, options CMake, API Eluna se vérifient dans le code source cloné (`vendor/`) ou la doc officielle. Ne jamais inventer un nom de champ ou de table. En cas de doute, le dire.
3. **Rien d'irréversible sans mon accord explicite** : `DROP`, suppression de volumes Docker, écrasement de config, réécriture d'historique Git, modification de mon dossier client WoW.
4. **Sauvegarde d'abord** : dump des bases avant toute migration ou import SQL massif.
5. **Pas de contenu FFXIV** : on s'inspire des mécaniques de jeu, mais on n'extrait, ne convertit ni n'intègre aucun fichier FFXIV, et on n'en reprend ni noms ni textes. Classe, sorts et visuels sont originaux ou issus de WoW.

## Façon de travailler

- Toute tâche non triviale commence en mode Plan : explorer, proposer un plan, attendre mon feu vert.
- Avancer par petites étapes vérifiables : commande, résultat attendu, moyen de vérifier.
- Un commit par étape qui fonctionne (Conventional Commits, en français).
- Face à une erreur : lire les logs pertinents, formuler une hypothèse, proposer un test qui la tranche.
- Toute décision structurante donne lieu à une note dans `docs/decisions/`.
- Réponses en français ; code, commits, commentaires et noms techniques en français.

## Briefs de phase (skills)

Chaque phase a son brief détaillé, chargé seulement quand je le lance :

- `/phase-1-base` — choix et validation de l'émulateur
- `/phase-2-serveur` — installation d'un serveur stable
- `/phase-3-classe` — prototype de la classe inspirée de FFXIV
- `/phase-3bis-assets` — étude réutiliser / recréer les assets
- `/fin-de-session` — rapport, mise à jour de `docs/STATUS.md`, commit
