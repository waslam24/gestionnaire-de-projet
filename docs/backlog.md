# Backlog & Roadmap

## Phase 0 — Préparation (Semaine 1)
- [ ] Définir le modèle de données initial (Projet, Environnement, Lien, Note, Tag, Utilisateur, Historique).
- [ ] Rédiger l'OpenAPI contract (auth, projets, environnements, liens).
- [ ] Maquettes basse fidélité (dashboard, fiche projet, formulaire projet).
- [ ] Setup dépôt mono-repo (frontend Angular, backend Django, config Docker Compose).

## Phase 1 — Fondations (Semaines 2-3)
- [ ] Backend Django + DRF : modèles, migrations, endpoints CRUD projets/environnements/liens/notes/tags.
- [ ] Authentification (JWT ou session) + gestion des profils utilisateurs.
- [ ] Chiffrement basique des secrets (champ secure + chiffrement applicatif).
- [ ] Frontend Angular : routing Auth + Dashboard + Détail projet + Formulaire projet.
- [ ] Recherche simple (texte) + filtres (type, statut, technologie) côté API & UI.
- [ ] Docker Compose (backend, frontend, PostgreSQL) + scripts `make up/down`.

## Phase 2 — Productivité (Semaines 4-5)
- [ ] Templates de projet (Angular/Django/Design) pour préremplir chemins, commandes et versions.
- [ ] Historique des modifications (trail) et activité récente sur les projets.
- [ ] Service de scripts (ouvrir IDE, lancer serveurs) avec logs.
- [ ] Pièces jointes légères : stockage de liens vers fichiers locaux ou cloud.
- [ ] Vérifications de versions (Node, Python) déclenchables depuis l'UI.

## Phase 3 — Collaboration (Semaines 6-7)
- [ ] Partage/export/import de configuration projet (JSON sécurisé).
- [ ] Intégration éditeurs (VS Code, JetBrains) et outils de design (Figma, Photoshop) pour ouverture directe.
- [ ] Tâches/jalons simples + intégration tickets (Jira/GitHub Issues) en consultation.
- [ ] Notifications (rappels d'échéances, version obsolète détectée).

## Dette et qualité continue
- [ ] Tests automatisés backend (pytest + coverage) et frontend (Jest/Karma).
- [ ] Observabilité : logging structuré, traces pour scripts exécutés.
- [ ] Sécurité : rotation des secrets, MFA pour l'auth, revocation tokens.
- [ ] UX : améliorations d'accessibilité, mode offline + synchronisation.
