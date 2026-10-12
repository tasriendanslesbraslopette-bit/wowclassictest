---
name: phase-1-base
description: "Phase 1 — choisir et valider l'émulateur de base (AzerothCore 3.3.5a par défaut) au vu de ma machine et de mon niveau."
disable-model-invocation: true
---

# Phase 1 — Choix de la base

Objectif : une décision argumentée sur l'émulateur, avant toute installation. Aucune installation ni clone dans cette phase.

## Hypothèse à confirmer ou contester

AzerothCore sur client 3.3.5a : modulaire (ajouts sans patcher le cœur), CI stricte, Docker supporté, Lua via `mod-eluna`. Le client 3.3.5a est le plus simple à modder (DBC, patchs MPQ, GlueXML), ce qui compte pour ajouter une classe. Alternative principale : TrinityCore branche 3.3.5. La branche retail de TrinityCore est exclue (expérimentale, client CASC/DB2 bien plus dur à modder).

## Étapes

1. Lire `CLAUDE.local.md` et noter ce qui manque pour décider (le demander si besoin).
2. Vérifier l'état actuel des dépôts (dernier commit, CI au vert, version du client supportée) : AzerothCore, TrinityCore 3.3.5, `mod-eluna`. Signaler tout module archivé et son remplaçant (constat du 2026-10-11 : `mod-eluna` pointe désormais vers le même commit que `mod-ale`, voir `docs/decisions/0001-base-emulateur.md`).
3. Vérifier les prérequis d'installation (dépendances, RAM/disque, Docker vs natif) par rapport à ma machine.
4. Rédiger `docs/decisions/0001-base-emulateur.md` : décision, alternatives écartées et pourquoi, risques, sources consultées (liens).
5. Proposer le mode d'installation (Docker ou natif) avec sa justification.

## Critères de fin

- [ ] Note de décision rédigée, sources citées
- [ ] Mode d'installation recommandé
- [ ] `docs/STATUS.md` mis à jour (via `/fin-de-session`)
