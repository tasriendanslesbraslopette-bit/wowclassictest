# 0001 — Base : AzerothCore sur client 3.3.5a, installation Docker

- **Date :** 2026-10-11
- **Statut :** proposée (en attente de l'accord de Jimmy)

## Contexte

Serveur WoW privé, puis une classe custom inspirée du Mage Rouge de FFXIV. Machine de Jimmy (relevée en lecture seule le 2026-10-11) :

- Windows 10 Pro 22H2 (build 19045), Intel Core i7-13700KF (16 cœurs, 24 threads), 31,8 Go de RAM, 182 Go libres sur C:.
- Virtualisation activée dans le firmware.
- Déjà présent : Visual Studio Build Tools 2022 (17.14, MSVC 14.44).
- Absent : git, Docker, WSL2 (non installé), MySQL/MariaDB, CMake dans le PATH.
- Jimmy ne possède pas de client WoW 3.3.5a (voir « Conséquences »).

## Décision

Base : **AzerothCore**, branche `master`, client **3.3.5a (build 12340)**. Mode d'installation recommandé : **Docker Desktop avec WSL2**, dépôt cloné dans le système de fichiers WSL.

## Ce qui a été vérifié (2026-10-11)

- `git ls-remote` : `azerothcore/azerothcore-wotlk` (`master`) et `TrinityCore/TrinityCore` (branche `3.3.5`, tête `92127cd`) existent et sont accessibles.
- Page GitHub d'AzerothCore : licence GPL-2.0, cible le patch 3.3.5a, `docker-compose.yml` présent, badges de CI nopch/pch/modules/Windows/macOS/Docker.
- Wiki AzerothCore, page Requirements : MySQL 8.4 LTS recommandé ; MariaDB et MySQL 5.7/8.1 ne sont plus supportés depuis le 2024-09-19.
- Wiki AzerothCore, installation Docker : prérequis git + Docker (compose inclus) ; les données serveur (maps, vmaps, mmaps, DBC) sont téléchargées par le conteneur `ac-client-data` ; première mise en route 10 à 15 min ; sous Windows, le wiki conseille WSL2 car les volumes montés depuis NTFS sont lents ; modules à cloner dans `./modules`.
- Wiki AzerothCore, installation Windows native : Visual Studio + CMake, MySQL Server 8.4, DLL OpenSSL 3.x à copier ; le wiki ne donne pas de versions minimales sur cette page.

## Module Lua : attention au nom

`azerothcore/mod-eluna` et `azerothcore/mod-ale` pointent vers le **même commit** (`84b85cc`) d'après `git ls-remote` : `mod-eluna` sert maintenant le moteur **ALE**. Son README dit qu'il est indépendant, conçu pour AzerothCore, et **non compatible avec les scripts du projet Eluna d'origine** (et inversement). Il se compile avec `-DLUA_VERSION=luajit|lua52|lua53|lua54`. `azerothcore/mod-eluna-lua-engine` est un dépôt distinct (autre commit) ; son statut d'archivage n'a pas pu être vérifié.

Conséquence : pour la classe, on s'appuiera sur l'API d'ALE, pas sur la documentation Eluna classique. À confirmer dans le code cloné en phase 2 (règle 2).

## Non vérifié

- La date du dernier commit d'AzerothCore et l'état réel de sa CI (la page Actions montrait des exécutions en cours, sans verdict).
- L'état de TrinityCore 3.3.5 au-delà de l'existence de la branche (GitHub bloque la lecture automatisée de cette page).
- Les besoins exacts en RAM/disque d'AzerothCore (le wiki ne les donne pas sur les pages lues). La machine est très large dans tous les cas.

## Alternatives écartées

- **TrinityCore 3.3.5** : la branche existe, mais elle est moins modulaire pour nos ajouts (pas d'écosystème de modules équivalent à celui d'AzerothCore, à confirmer) ; non étudiée plus avant faute de lecture possible de sa page.
- **TrinityCore retail** : client CASC/DB2, bien plus difficile à modder.
- **AzerothCore en natif Windows** : faisable (Build Tools 2022 déjà installés) mais il faut installer et accorder git, MySQL 8.4, OpenSSL, Boost et CMake à la main, avec les DLL à faire correspondre à la version de MySQL. Plus de pièces fragiles pour un débutant.

## Conséquences

- Étape préalable à la phase 2, à faire par Jimmy : activer WSL2 et installer Docker Desktop (droits administrateur et redémarrage requis), et installer git. Je donnerai les commandes exactes.
- Le dépôt de travail vivra dans WSL (pour la vitesse des volumes). Le dossier du Bureau reste le point d'entrée pour les documents.
- **Client 3.3.5a** : le serveur n'en a pas besoin pour tourner (les données serveur sont téléchargées par le conteneur), mais Jimmy en a besoin pour se connecter et pour le patch MPQ de la phase 3. À ma connaissance Blizzard ne le vend plus (non vérifié) ; je ne le télécharge pas depuis des sources non officielles. Jimmy devra se le procurer lui-même. Il bloque les tests en jeu, pas l'installation du serveur.

## Sources

- [AzerothCore (GitHub)](https://github.com/azerothcore/azerothcore-wotlk)
- [mod-ale (GitHub)](https://github.com/azerothcore/mod-ale)
- [Wiki : Requirements](https://www.azerothcore.org/wiki/requirements)
- [Wiki : installation Docker](https://www.azerothcore.org/wiki/install-with-docker)
- [Wiki : installation Windows](https://www.azerothcore.org/wiki/windows-core-installation)
