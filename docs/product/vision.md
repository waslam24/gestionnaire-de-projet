# Vision produit – Gestionnaire de projets desktop

## Contexte
Cette application combine Angular (UI) et Electron (shell) pour offrir un gestionnaire de projets 100 % local, sans compte ni connexion réseau. Elle cible en priorité Windows 10+ et vise à accélérer l'ouverture des dossiers, des IDE et des commandes importantes pour quelques dizaines à centaines de projets.

## Problème à résoudre
- Les projets sont dispersés sur le disque et nécessitent d'ouvrir plusieurs outils manuellement.
- Les commandes de lancement (serveurs, builds) sont mémorisées ou réécrites à chaque fois.
- Les informations clés (statut, type, technologies, liens) sont rarement centralisées.

## Proposition de valeur
- Une fiche par projet qui regroupe identité, chemins locaux, liens principaux, commandes et notes.
- Des actions rapides (ouvrir l'explorateur, VS Code, exécuter une commande) accessibles en un clic.
- Une persistance locale (localStorage + fichiers utilisateur) compatible avec une future API Django/REST.

## Principes clés V1
- **Offline first** : aucune dépendance réseau, données stockées localement.
- **Simplicité** : CRUD projets, filtres basiques, pas de tâches/jalons/templates en V1.
- **Extensibilité** : modèles TypeScript alignés sur des structures REST pour préparer une synchro ultérieure.

## Utilisateurs cibles
- Développeurs full-stack qui alternent entre frontend Angular, backend ou scripts.
- Créatifs (vidéo/design) qui veulent centraliser chemins d'assets et commandes de rendu.
- Chefs de projet techniques qui veulent suivre le statut et ouvrir rapidement les contextes pertinents.

## Expérience attendue
1. L'utilisateur crée un projet et renseigne ses chemins, liens et commandes clés.
2. Depuis le dashboard, il filtre par statut ou recherche par nom puis ouvre le dossier ou lance VS Code.
3. Dans la fiche projet, il exécute une commande (ex. serveur dev) ou met à jour notes et objectifs.
4. Les paramètres permettent de définir le chemin de VS Code si l'auto-détection échoue.

## Capabilités futures (V2+)
- Templates de projets, tâches/jalons, scénarios et palette de commande globale.
- Découverte automatique des projets via scan de dossiers racine.
- Synchronisation via backend Django/REST avec import/export avancé.
