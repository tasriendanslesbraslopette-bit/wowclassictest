---
name: fin-de-session
description: "Clôturer une session de travail — rapport, mise à jour de docs/STATUS.md, proposition de commit."
disable-model-invocation: true
---

# Fin de session

1. Lancer `git status` et `git diff --stat` pour voir ce qui a changé.
2. Me donner un rapport court :
   - Ce qui est fait (versions, commandes testées)
   - Résultats des critères de la phase en cours
   - Problèmes ouverts et contournements
   - Décisions qui m'attendent
   - Prochaine étape proposée
3. Réécrire `docs/STATUS.md` (moins de 40 lignes, c'est importé à chaque session) : phase en cours, décisions prises (liens vers `docs/decisions/`), problèmes ouverts, prochaine étape.
4. Si une commande a été validée, mettre à jour la section « Commandes » de `CLAUDE.md`. Si une même correction m'a été demandée deux fois, proposer une ligne à ajouter à `CLAUDE.md`.
5. Proposer un message de commit (Conventional Commits, en français) et attendre mon accord avant de committer.
