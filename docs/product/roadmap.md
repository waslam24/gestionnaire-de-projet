# Roadmap simplifiée

## Phase 1 — V1 local (Angular + Electron)
- [ ] Mettre en place le shell Electron (main, preload) avec sécurités de base.
- [ ] Initialiser l'app Angular avec modules core/shared + routing (dashboard, projets, paramètres).
- [ ] Implémenter ProjectStoreService (localStorage) et SettingsService.
- [ ] Construire le dashboard avec filtre par statut et recherche par nom.
- [ ] Créer la fiche projet (CRUD complet) avec chemins, liens, commandes et notes.
- [ ] Ajouter les ponts Electron : ouvrir un chemin, ouvrir VS Code, ouvrir une URL, exécuter une commande shell.

## Phase 2 — Ergonomie & robustesse
- [ ] Duplication de projet, validation des formulaires et feedbacks d'exécution des commandes.
- [ ] Détection automatique du binaire VS Code selon l'OS et fallback manuel.
- [ ] Amélioration UI dark mode : composants partagés (cards, badges, inputs, tables légères).
- [ ] Tests unitaires des services et des composants critiques.

## Phase 3 — Préparation V2
- [ ] Templates de projets et scénarios prédéfinis.
- [ ] Tâches/jalons et vue "Aujourd'hui / Cette semaine".
- [ ] Palette de commande (Ctrl+K) et découverte automatique des projets.
- [ ] Connecteur backend Django/REST et import/export JSON avancé.
