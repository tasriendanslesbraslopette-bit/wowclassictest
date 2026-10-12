---
name: phase-3-classe
description: "Phase 3 — prototyper une classe inspirée d'un job FFXIV, palier A (kit greffé sur une classe existante) puis palier B (vraie classe)."
disable-model-invocation: true
argument-hint: "[A|B]"
---

# Phase 3 — Classe inspirée de FFXIV (palier $ARGUMENTS)

Prérequis : phase 2 validée (voir `docs/STATUS.md`). Commencer en mode Plan. Règle 5 de `CLAUDE.md` s'applique : mécaniques inspirées, noms et textes originaux ; fichiers FFXIV en usage local et personnel seulement, jamais commités.

## Choix du job (si pas encore décidé)

Job choisi : Mage Rouge (`docs/decisions/0002-job-ffxiv.md`). Reste à décider, en palier A, un nom de classe original et la classe WoW sur laquelle greffer le kit. Si la faisabilité s'avère mauvaise, comparer avec 2 autres jobs (ex. Chevalier Noir, Danseur) sur : faisabilité dans le moteur 3.3.5a, originalité du rôle face aux classes WotLK, nombre de mécaniques à émuler, visuels WoW réutilisables.

## Traduction des mécaniques (exemple Mage Rouge — à vérifier dans le moteur)

| Mécanique | Émulation proposée |
| --- | --- |
| Double sort : chaque sort incanté rend le suivant instantané | Aura proc consommée au prochain lancer, temps d'incantation −100 % |
| Jauge mana blanc / noir, déséquilibre plafonné | Deux auras cachées à cumuls (0–100) gérées côté serveur + cadre d'UI Lua côté client |
| Combo mêlée → finisher | Sorts conditionnés par aura ; finisher selon la jauge dominante |
| Équilibrage | Valeurs de Spell.dbc + script, comparées à un mage WotLK de même niveau |

## Palier A — kit greffé (viser 1–2 semaines)

Greffer le kit sur une classe existante pour un personnage de test (sorts appris via PNJ ou commande GM), avec `mod-eluna` (moteur ALE, API à vérifier dans le code cloné) et des sorts custom dans les plages de `docs/id-ranges.md`. Question à trancher : le gameplay est-il amusant et tenable techniquement ?

## Palier B — vraie classe

Avant de coder, produire `docs/class-impact.md` : liste exhaustive des fichiers touchés, **vérifiée dans le code de `vendor/`** (chercher par ex. `MAX_CLASSES`, `CLASSMASK_ALL_PLAYABLE`, `ChrClassesEntry`, `HandleCharCreateOpcode`). Points de départ à confirmer :

- DBC (serveur + patch MPQ client) : ChrClasses, CharBaseInfo, CharStartOutfit, SkillLine / SkillRaceClassInfo, TalentTab / Talent, Spell.
- Cœur : constantes et masques de classe (en 3.3.5a l'ID 10 est inutilisé, masque = `1 << (ID - 1)`), stats par niveau, données de création.
- Client : écran de création (GlueXML), couleurs et icônes de classe, barre de ressource.

Sources éditables dans `client-patch/`, script de build du patch MPQ, jamais de fichiers d'origine commités.

## Critères de fin

- [ ] Palier A : rotation jouable, mécanique signature fonctionnelle, retour de test noté
- [ ] Palier B : création de personnage et progression 1 → 80 sans bug bloquant
- [ ] Fiche d'équilibrage chiffrée et liste des limites du moteur rencontrées
