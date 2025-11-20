# Gestionnaire de projets desktop

Application Angular + Electron, 100 % locale, pour centraliser l'ouverture et le suivi minimal de projets techniques ou créatifs.

## 🎯 Objectif V1
- CRUD projets avec identité, statut, type, priorité, technologies, descriptions et dates.
- Gestion des chemins locaux, liens et commandes clés par projet.
- Actions rapides : ouvrir l'explorateur, ouvrir VS Code, exécuter une commande.
- Dashboard avec filtre par statut et recherche par nom.
- Paramètre optionnel pour le chemin de VS Code, persistant en local.

## 🗺️ Architecture cible V1
- **Frontend** : Angular (routing `/`, `/projects`, `/projects/new`, `/projects/:id`, `/settings`).
- **Electron** : process principal sécurisé (`nodeIntegration=false`, `contextIsolation=true`) exposant `openPath`, `openInVSCode`, `openExternal`, `runShellCommand` via preload.
- **Services core** :
  - `ProjectStoreService` (BehaviorSubject + localStorage `pm.v1.projects`).
  - `SettingsService` (localStorage `pm.v1.settings`).
  - `ElectronBridgeService` pour encapsuler `window.electronAPI`.
- **UI** : dark mode, sidebar (Dashboard/Projets/Paramètres), composants partagés simples.

## 📂 Organisation
```
/gestionnaire-de-projet
├── docs/
│   ├── product/
│   │   ├── vision.md        # Vision produit desktop et principes V1/V2+
│   │   └── roadmap.md       # Roadmap simplifiée par phases
│   └── specs/
│       └── v1-functional.md # Cahier des charges détaillé (fonctions, données, architecture)
└── README.md
```

## 🚀 Prochaines étapes
1. Initialiser le squelette Electron (main + preload) et l'app Angular avec modules `core`/`shared`/`features`.
2. Implémenter le stockage local et les écrans Dashboard + fiche projet + paramètres.
3. Ajouter les IPC Electron pour les actions système et sécuriser la validation des arguments.

## 🔗 Références
- Vision produit : [`docs/product/vision.md`](docs/product/vision.md)
- Roadmap : [`docs/product/roadmap.md`](docs/product/roadmap.md)
- Cahier des charges V1 : [`docs/specs/v1-functional.md`](docs/specs/v1-functional.md)
