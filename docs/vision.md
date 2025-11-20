# Vision Produit : Gestionnaire de Projets Multiplateforme

## Problème à résoudre
Les développeurs et créatifs jonglent avec des dizaines de projets Angular, Django ou outils graphiques. Les chemins, environnements et informations critiques sont dispersés (VS Code, dossiers locaux, environnements virtuels, outils de design), ce qui entraîne :
- Perte de temps pour retrouver les projets ou leurs variables d'environnement.
- Risques d'erreurs (mauvais terminal, mauvaise version de Node/Python, mauvaises clés API).
- Absence de vue consolidée sur l'état d'avancement et la configuration.

## Proposition de valeur
Fournir une application unique où chaque projet est déclaré, configuré et ouvert depuis un même endroit. L'utilisateur retrouve immédiatement :
- Le statut du projet (idées, en cours, en test, livré).
- Les chemins locaux, commandes d'ouverture (VS Code, PyCharm) et scripts de démarrage.
- Les environnements (virtualenv/conda, versions Python/Node, variables sensibles). 
- Les notes, liens (ticket, design, documentation), et l'historique des décisions.

## Personas
- **Développeur full‑stack** : gère Angular + Django, multiples environnements, besoin de lancement rapide et fiable.
- **UX/UI designer** : veut attacher maquettes (Figma/Photoshop) et assets aux projets.
- **Chef de projet** : suit l'avancement, deadlines, ressources, et dépendances inter‑projets.

## Objectifs clés
- Centraliser la création et la consultation des projets avec leurs métadonnées techniques et fonctionnelles.
- Guider l'utilisateur lors de l'ouverture du projet (chemins, commandes, versions, scripts).
- Documenter l'historique et la configuration pour réduire le temps d'onboarding.
- Permettre un suivi léger (statut, jalons, tâches essentielles) sans remplacer un outil lourd de gestion.

## Portée initiale (MVP)
- Authentification de base (email/mot de passe) avec profils utilisateurs.
- CRUD Projet avec champs principaux : nom, type (Angular, Django, Design, Autre), statut, chemins locaux, commandes d'ouverture/démarrage, versions requises (Node, Python), variables d'environnement chiffrées, liens externes, notes rapides.
- Gestion des environnements : association d'un environnement (virtualenv/conda pour Python, npm/yarn/pnpm pour JS) et vérification rapide des versions installées.
- Tableau de bord listant les projets avec filtres (type, statut, technologie) et recherche full‑text.
- Page détail projet : accès aux informations clés, historique des mises à jour, liens et scripts prêts à copier.
- Système de tags et pièces jointes légères (liens vers fichiers locaux ou URL cloud).

## Évolution (Post‑MVP)
- Templates de projets (préremplir champs selon Angular/Django/Design).
- Intégration éditeurs (VS Code, JetBrains) pour ouvrir directement le projet depuis l'app.
- Suivi des tâches et jalons simples, intégration tickets (Jira/GitHub Issues).
- Export/import de la configuration projet (JSON) pour la partager entre machines.
- Notifications (rappels d'échéances, version obsolète détectée).
- Mode offline avec synchronisation.

## Architecture cible
- **Frontend** : Angular (15+), module d'auth, dashboard, pages Projet (liste, détail, édition), module Environnements, stockage local pour état offline.
- **Backend** : Django 4+/Django REST Framework ; PostgreSQL ; endpoints sécurisés JWT/Session ; stockage chiffré pour secrets ; service d'audit/historique ; validation des versions (scripts CLI).
- **Services transverses** : 
  - Gestion des secrets (champ sécurisé + chiffrement en base).
  - Service de scripts (commande d'ouverture, démarrage, migration) avec logs.
  - Moteur de recherche (PostgreSQL + trigramme) pour filtrage rapide.
- **Déploiement** : conteneurs Docker (frontend + backend + db), fichier `docker-compose` pour démarrage local.

## Expérience utilisateur
1. L'utilisateur crée un projet depuis le dashboard, choisit un template (ex. Angular), renseigne chemins, commandes et versions.
2. Depuis la liste, il filtre par type ou statut et lance l'ouverture du projet dans l'IDE ou terminal.
3. Sur la fiche projet, il consulte les variables d'environnement (révélées temporairement), les notes et l'historique des changements.
4. Les équipes peuvent enrichir les liens (tickets, designs, docs) et mettre à jour le statut.

## Indicateurs de succès
- Temps moyen pour ouvrir un projet réduit (mesuré via scripts exécutés).
- Réduction des erreurs de version/environnement signalées par les utilisateurs.
- Adoption : nombre de projets créés et actifs par utilisateur.

## Risques et mitigations
- **Sécurité des secrets** : chiffrement côté serveur, contrôle d'accès strict, audit des consultations.
- **Compatibilité multi‑OS** : normaliser les chemins et scripts (Windows/macOS/Linux) via abstraction.
- **Performance de recherche** : indexation (PG trigram) et pagination côté API.
- **Expérience offline** : prioriser cache local + synchronisation différée.

## Livrables attendus pour la première itération
- Schéma de données initial (Projets, Environnements, Liens, Notes, Tags, Utilisateurs, Historique).
- Maquettes basse fidélité (dashboard, fiche projet, modale de création).
- API REST basique (auth, projets, environnements, liens) + documentation OpenAPI.
- Application Angular avec routes Auth + Dashboard + Détail projet + Formulaire projet.
- Scripts Docker/Make pour démarrage local (backend + frontend + db).
