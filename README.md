# Gestionnaire de Projets Multiplateforme

Application web Angular/Django pour centraliser la création, la configuration et l'ouverture de projets techniques ou créatifs. L'objectif est de réduire le temps passé à chercher les chemins, environnements et commandes de démarrage en offrant un tableau de bord unique avec toutes les métadonnées pertinentes.

## ✨ Fonctionnalités visées
- Catalogue de projets avec filtres (type, statut, technologie) et recherche full‑text.
- Fiches projets complètes : chemins locaux, commandes d'ouverture/démarrage, versions requises (Node/Python), notes, liens, pièces jointes légères et historique.
- Gestion des environnements (virtualenv/conda, npm/yarn/pnpm) et vérification des versions installées.
- Champs sécurisés pour variables d'environnement et secrets.
- Templates de projet (Angular/Django/Design) pour préremplissage.
- Scripts rapides pour ouvrir l'IDE ou lancer les serveurs depuis l'interface.

## 🏗️ Architecture cible
- **Frontend** : Angular (15+) avec modules Auth, Dashboard, Projets (liste/détail/édition) et Environnements.
- **Backend** : Django 4+ & Django REST Framework, PostgreSQL, authentification JWT ou session, stockage chiffré des secrets.
- **Infra locale** : Docker Compose pour orchestrer frontend, backend et base de données.

## 📂 Organisation proposée
```
/gestionnaire-de-projet
├── docs/
│   ├── vision.md       # Vision produit et livrables MVP
│   └── backlog.md      # Roadmap par phases
├── frontend/           # (à créer) Application Angular
├── backend/            # (à créer) API Django + DRF
├── docker-compose.yml  # (à créer) Stack locale
└── README.md
```

## 🚀 Démarrage (à venir)
Les commandes seront ajoutées lorsque les dossiers `frontend/` et `backend/` seront initialisés. Pré-requis prévus : Node.js 18+, npm, Python 3.9+, pip/virtualenv, Docker et Docker Compose.

## 🔗 Références
- Vision produit complète : [`docs/vision.md`](docs/vision.md)
- Backlog et roadmap : [`docs/backlog.md`](docs/backlog.md)
