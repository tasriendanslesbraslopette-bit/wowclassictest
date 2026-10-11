# Démarrer avec Claude Code

Ce kit remplace le long prompt par des fichiers que Claude Code charge tout seul. Vous n'avez plus rien à recoller.

## Ce qui est chargé, et quand

| Fichier | Chargé | Rôle |
| --- | --- | --- |
| `CLAUDE.md` | À chaque session | Contexte, règles non négociables, façon de travailler |
| `CLAUDE.local.md` | À chaque session, jamais commité | Votre machine et le chemin du client |
| `docs/STATUS.md` | À chaque session (importé par `CLAUDE.md`) | Où en est le projet |
| `.claude/skills/*` | Seulement quand vous tapez la commande | Brief détaillé de chaque phase |
| `.claude/settings.json` | À chaque session | Garde-fous techniques (permissions) |

Les règles de `CLAUDE.md` guident Claude mais ne sont pas une barrière stricte ; les permissions de `.claude/settings.json`, elles, sont appliquées par Claude Code. Par exemple, l'édition de `vendor/` y est bloquée.

## Mise en route (une fois)

1. Créez un dossier de projet, copiez-y le contenu du kit (dossiers cachés `.claude/` et `.gitignore` compris), puis `git init`.
2. Complétez les `[À COMPLÉTER]` de `CLAUDE.md` (votre niveau) et de `CLAUDE.local.md` (votre machine).
3. Facultatif mais conseillé : protégez votre dossier client WoW en créant `.claude/settings.local.json` avec une règle `ask` sur son chemin absolu, par exemple `"Edit(//home/moi/Games/WoW-3.3.5a/**)"`.
4. Lancez `claude` à la racine du projet, puis `/context` : `CLAUDE.md` et `CLAUDE.local.md` doivent apparaître sous « Memory files ».
5. Premier commit du kit.

## Rythme de travail

1. Une phase = une ou plusieurs sessions. Ouvrez la session avec la commande de phase : `/phase-1-base`, `/phase-2-serveur`, `/phase-3-classe A`, `/phase-3-classe B`, `/phase-3bis-assets`.
2. Pour les grosses étapes, passez en mode Plan (Maj+Tab jusqu'à « Plan ») : Claude explore et propose sans rien modifier, vous validez ensuite.
3. Fermez chaque session par `/fin-de-session` : rapport, `docs/STATUS.md` à jour, commit proposé.
4. Entre deux phases, repartez d'un contexte propre avec `/clear` ; `STATUS.md` assure la continuité.
5. Quand vous corrigez Claude deux fois sur la même chose, ajoutez la règle à `CLAUDE.md` (ou demandez-lui de le faire). Gardez ce fichier sous 200 lignes.

## Ordre conseillé

`/phase-1-base` → `/phase-2-serveur` → jalon « serveur stable 48 h » → `/phase-3-classe A` et `/phase-3bis-assets` en parallèle (deux sessions séparées) → bilan go / no-go → `/phase-3-classe B`.
