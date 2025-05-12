<img src="/profile/xcraft.svg" width="300px" />

# Introduction au Framework Xcraft

Bienvenue dans l’écosystème **Xcraft** ! Si vous cherchez un framework
JavaScript/Node.js **local-first**, réactif, et modulable pour concevoir des
applications (desktop, microservices, etc.), vous êtes au bon endroit. Voici un
aperçu de sa philosophie, de ses points forts et de son écosystème, pour vous
donner envie d’aller plus loin.

---

## 1. Philosophie et Principes

### 1.1 Local-first et Réactivité

Xcraft met l’accent sur le **local-first** :

- Les actions de l’utilisateur (création, modifications, suppressions) sont
  enregistrées localement et appliquées **instantanément**.
- La synchronisation vers le serveur se fait ensuite en arrière-plan (grâce à
  **Ripley** et **Cryo**), pour éviter tout blocage si le réseau est lent ou
  indisponible.

Grâce à cette approche, l’interface reste fluide, et l’utilisateur n’a pas à se
soucier de son statut en ligne/hors-ligne : l’application fonctionne de façon
**réactive**, et tout se met à jour automatiquement dès qu’une connexion est
disponible. 

[Voir aussi notre manifeste sur la réactivité](./manifeste.md)

### 1.2 Un Modèle d’Acteurs

La logique métier de Xcraft repose sur le **modèle d’acteurs** :

- Chaque **acteur** (deux types : Goblin ou Elf) gère son propre état et expose
  des méthodes appelées “quêtes.”
- Les mutations d’état se font de manière **immuable** (inspiré de Redux),
  simplifiant les diffusions de changements et la relecture historique pour le
  débogage.
- Cela isole la logique métier, rendant l’application **plus modulable** et
  **testable**.

### 1.3 Maintenabilité et Cohérence

L’immuabilité et la division en acteurs facilitent la maintenance au quotidien :

- **Historique complet** (les actions sont enregistrées, permettant de rejouer
  ou déboguer précisément).
- **Moins d’effets de bord** : chaque acteur est autonome, communique via un bus
  de commandes et d’événements.
- **Séparation claire** de la logique (business logic) et des interfaces
  (Elf.Spirit, ou composants React) : un atout de longue durée pour la
  maintenabilité.

---

## 2. Écosystème Modulaire

### 2.1 Les Modules Clés

Xcraft se décompose en **plusieurs modules** qui se combinent pour couvrir les
différents aspects d’une application :

- **xcraft-core-goblin** : le cœur du système d’acteurs (quêtes, orchestration).
- **goblin-warehouse** : centre de gestion d’état (sessions multi-utilisateurs,
  ramasse-miettes, hiérarchie parent-enfant).
- **goblin-laboratory** : fait le lien entre la logique d’acteurs et la couche
  front-end.
- **xcraft-core-host** : environnement Electron/Node, pour créer des
  applications desktop autonomes.
- **goblin-client** : gère une session cliente (stockage des préférences,
  settings…).
- **goblin-wm** : permet d’instancier/fenêtrer des vues Electron.

Chacun peut être étendu par d’autres modules (ex. `goblin-nabu` pour la
traduction), créant un **écosystème riche** et spécialisé.

### 2.2 Un Bus d’Événements Commun

Toute la communication entre modules et acteurs se fait via un **bus**. Ainsi,
chaque module reste indépendant mais peut **échanger** facilement des commandes
et des événements pour coordonner l’application.

### 2.3 Partage de la Persistance et Migration

Les acteurs persistants (Elf.Archetype) peuvent partager la **même base SQLite**
(gérée par Cryo). Les actions qui constituent leur historique sont stockées au
sein d’une table unique, permettant la relecture et la synchronisation
(local-first).

- Cela facilite aussi la **migration** : on peut mettre à jour ou restructurer
  la base pour tous les acteurs concernés, grâce à l’historique centralisé
  d’actions.

---

## 3. Aperçu du Fonctionnement

1. **Cloner un bundle** : Les projets Xcraft se présentent souvent sous forme de
   “bundle” (un dépôt Git avec `package.json`, `app/`, `lib/`, etc.).
2. **Installer les dépendances** : `npm install`.
3. **Lancer l’application** : `npm run <appId>`, ou via un script (ex.
   `npm run dev`).
4. **Découvrir la logique d’acteurs** :
   - Les Goblins (legacy, style Redux-like)
   - Les Elfs (nouvelle génération, orientés classe).
5. **Persistance** : on observe la base locale (SQLite) où sont stockées les
   actions et les snapshots d’état.
6. **Synchro** : le moteur Ripley envoie les actions manquantes et récupère
   celles du serveur, permettant un usage hors-ligne.

---

## 4. Pourquoi Se Lancer ?

1. **Productivité** : On crée des **acteurs** isolés, faciles à maintenir et
   tester.
2. **Expérience Utilisateur Optimale** : Le local-first évite tout blocage,
   donne une **réactivité fluide**.
3. **Architecture Évolutive** : On peut démarrer en local, puis **activer la
   synchro** ou **distribuer** les acteurs sur plusieurs nœuds quand le projet
   grandit.
4. **Open-Source et Collaboratif** : L’écosystème Xcraft est issu de multiples
   projets et modules open-source, offrant une base solide et éprouvée.

---

## 5. Pour Aller Plus Loin

- **goblin-warehouse / goblin-laboratory** : Approfondir la gestion d’état, la
  façon dont l’UI (React) se connecte aux acteurs.
- **nabu-tools** : Gérer les traductions ICU.
- **goblin-builder** : Compiler/packager l’application (Electron) pour
  Windows/Mac/Linux.
- **Toolchain Avancée (WPkg)** : Compiler tout un OS Linux si nécessaire, pour
  une intégration verticale complète.

---

## Conclusion

Xcraft se distingue par :

- Sa **réactivité** hors-ligne (local-first)
- Son **modèle d’acteurs** modulaire et clair
- Son **écosystème** de modules spécialisés (warehouse, laboratory, builder…)
- Sa **maintenabilité** à long terme (immutabilité, isolation, historique
  d’actions)

Si ces valeurs et principes vous parlent, vous avez tous les atouts pour plonger
plus en détail dans Xcraft, apprendre comment créer des Elf et Goblins,
concevoir des apps desktop ou microservices, et déployer le tout avec
l’outillage complet du framework.

En somme, **Xcraft** allie la souplesse de JavaScript/Node.js et l’architecture
événementielle réactive, pour bâtir des applications résilientes et évolutives.
Bonne exploration !
