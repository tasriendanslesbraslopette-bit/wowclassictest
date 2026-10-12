---
name: phase-2-serveur
description: "Phase 2 — installer un serveur WoW jouable, stable et reproductible à partir de l'émulateur choisi en phase 1."
disable-model-invocation: true
---

# Phase 2 — Serveur jouable et stable

Objectif : un serveur reconstructible depuis ce dépôt Git et une sauvegarde de base. Prérequis : `docs/decisions/0001-base-emulateur.md` existe. Commencer en mode Plan et présenter le plan complet avant d'agir.

## Étapes

1. **Dépôt** : `git init` si besoin, `.gitignore` vérifié (client, MPQ/DBC d'origine, données extraites, `backups/`, `CLAUDE.local.md`, secrets).
2. **Cœur** : cloner AzerothCore dans `vendor/azerothcore-wotlk` (submodule ou clone ignoré — en décider et le noter). Lister les dépendances exactes et leurs versions.
3. **Modules** : ajouter `mod-eluna` (dépôt qui sert désormais le moteur ALE, voir `docs/decisions/0001-base-emulateur.md` ; vérifier son README au clonage) ; mettre en place le lien de `modules/` vers `vendor/azerothcore-wotlk/modules/`.
4. **Compilation** : via le mode choisi en phase 1 ; script dans `scripts/build.sh`.
5. **Données client** : extraire DBC, maps, vmaps, mmaps depuis mon client (chemin dans `CLAUDE.local.md`) avec les extracteurs du projet. Mon dossier client n'est jamais modifié.
6. **Bases** : laisser l'outil de mise à jour automatique appliquer les SQL ; ne jamais exécuter de SQL « optional » sans mon accord.
7. **Configuration** : `authserver.conf` et `worldserver.conf` dans `config/`, commentés (taux XP, logs, adresse du realm). Me dire quoi mettre dans `realmlist.wtf` ; ne pas l'écrire sans accord.
8. **Exploitation** : `scripts/start.sh`, `stop.sh`, `backup.sh`, `restore.sh` ; redémarrage automatique et rotation des logs.
9. **Compte GM** : me donner la commande pour le créer moi-même (pas de mot de passe dans le dépôt ni dans le chat).
10. **CLAUDE.md** : remplir la section « Commandes » avec les commandes réellement testées.
11. **IDs custom** : proposer des plages dans `docs/id-ranges.md`, vérifiées au-dessus des IDs max des données extraites.

## Critères de fin (je teste en jeu, tu vérifies les logs)

- [ ] Création de compte, connexion, un personnage de chaque classe
- [ ] Quêtes de départ, combat, loot, marchands et entraîneurs
- [ ] Un donjon bas niveau terminé sans blocage
- [ ] Deux clients connectés, groupe et chat
- [ ] 48 h sans crash ni dérive mémoire visible
- [ ] Restauration complète depuis `backup.sh` sur une base vierge
