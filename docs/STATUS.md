# État du projet

**Phase en cours :** 1 — choix de la base, note rédigée, en attente de l'accord de Jimmy.

## Décisions prises

- [0002 — Job FFXIV : Mage Rouge](decisions/0002-job-ffxiv.md) (acceptée).
- [0001 — AzerothCore, client 3.3.5a, Docker + WSL2](decisions/0001-base-emulateur.md) (proposée).

## Problèmes ouverts

- Jimmy n'a pas de client WoW 3.3.5a : à se procurer par lui-même, bloquant pour les tests en jeu et le patch MPQ, pas pour installer le serveur.
- `mod-eluna` sert désormais le moteur ALE, incompatible avec les scripts Eluna d'origine.
- Machine : WSL2, Docker et git à installer (droits admin, redémarrage).

## Prochaine étape

- Jimmy valide la décision 0001, puis activation de WSL2 + Docker Desktop + git, puis `/phase-2-serveur`.
