# Cahier des charges V1 — Application desktop "Gestionnaire de projets"

## 1. Objectif
- Application locale Angular + Electron ciblant Windows 10+.
- CRUD de projets et lancement rapide des chemins, liens et commandes associés.
- Aucune authentification ni dépendance réseau.

## 2. Fonctionnalités incluses
- Gestion des projets : création, lecture, mise à jour, suppression.
- Champs principaux : nom, type, statut, priorité, technologies, descriptions, dates, note globale.
- Chemins locaux : libellé + chemin, actions Explorer et VS Code.
- Liens : libellé + URL, action Ouvrir dans le navigateur.
- Commandes : libellé + commande (+ cwd optionnel), action Exécuter.
- Dashboard : liste de projets, filtre par statut, recherche par nom, accès rapide à la fiche.
- Paramètres : chemin VS Code (optionnel) stocké en local.

## 3. Hors périmètre V1 (pour V2+)
- Templates, tâches/jalons, scénarios, palette de commande, découverte auto, focus timer.
- Import/export JSON avancé et backend Django/REST.

## 4. Modèle de données (TypeScript)
```ts
export type ProjectStatus = 'en_cours' | 'termine' | 'en_pause' | 'planifie';
export type ProjectType = 'web' | 'video' | 'script' | 'jeu' | 'autre';
export type Priority = 'basse' | 'normale' | 'haute';

export interface ProjectPath {
  id: string;
  label: string;
  path: string;
}

export interface ProjectLink {
  id: string;
  label: string;
  url: string;
}

export interface ProjectCommand {
  id: string;
  label: string;
  command: string;
  cwd?: string;
}

export interface Project {
  id: string;
  name: string;
  slug?: string;
  status: ProjectStatus;
  type: ProjectType;
  priority: Priority;
  technologies: string[];
  shortDescription?: string;
  goals?: string;
  createdAt: string;    // ISO
  updatedAt: string;    // ISO
  paths: ProjectPath[];
  links: ProjectLink[];
  commands: ProjectCommand[];
  notes?: string;
}

export interface AppSettings {
  id: 'app-settings';
  vscodePath?: string;
}
```

## 5. Architecture Angular + Electron (V1)
- **Modules Angular** : app (routing), core (services ProjectStoreService, ElectronBridgeService, SettingsService), shared (UI), features (dashboard, projects, settings).
- **Routing** : `/` dashboard, `/projects`, `/projects/new`, `/projects/:id`, `/settings`.
- **Fake backend** :
  - ProjectStoreService : BehaviorSubject, persistance localStorage (`pm.v1.projects`).
  - SettingsService : localStorage (`pm.v1.settings`).
- **Electron** :
  - IPC pour `openPath`, `openInVSCode`, `openExternal`, `runShellCommand`.
  - `window.electronAPI` exposé via preload avec `contextIsolation=true`, `nodeIntegration=false`.

## 6. UX/UI minimal
- Dark mode uniquement.
- Layout avec sidebar (Dashboard, Projets, Paramètres) + header titre.
- Dashboard : tableau/card avec nom, statut, type, priorité, technologies, dernière mise à jour, filtre statut, recherche nom, bouton "Nouveau projet".
- Fiche projet : sections Infos, Chemins, Liens, Commandes, Notes, actions Sauvegarder/Supprimer/Dupliquer.
- Paramètres : champ chemin VS Code + bouton de test.

## 7. Exigences non fonctionnelles
- Performant pour quelques centaines de projets.
- TypeScript strict, séparation UI/services/electron.
- Validation minimale des arguments côté main et restrictions de commandes à celles saisies par l'utilisateur.
