# 📜 Xcraft et le Reactive Manifesto

> Ce que le manifeste a rêvé, Xcraft l’a forgé. 🔨✨

Le [Reactive Manifesto](https://www.reactivemanifesto.org/), publié en 2014, a
introduit les fondements des systèmes modernes : **réactifs, résilients,
scalables, et pilotés par messages**.  
Chez **Xcraft**, ce manifeste a été une source d’inspiration — mais notre
framework va bien plus loin, en incarnant ces principes dans un environnement
**local-first**, **modulaire**, et **distribué**, conçu pour des applications
modernes, fluides et robustes.

---

## 🧬 Les 4 piliers comparés

### ⚡ 1. Responsive (Réactif)

> Le système doit rester rapide et fluide, même en cas de charge ou de
> déconnexion.

**Dans Xcraft** :

- Architecture **local-first** avec persistance locale immédiate.
- Synchronisation **asynchrone en arrière-plan**.
- Interface pilotée par des **acteurs transitoires** (`Elf.Spirit`) connectés
  aux données réactives.

✅ Réactivité native et constante, même hors-ligne.

---

### 🧱 2. Resilient (Résilient)

> Le système doit isoler les composants, supporter les pannes et se remettre
> rapidement.

**Dans Xcraft** :

- Modèle d’acteurs autonomes (`Goblin`/`Elf`) avec logique isolée.
- Mutations **immutables** et historisées.
- Possibilité de **rejouer l’historique** pour déboguer ou restaurer.

✅ Chaque acteur peut crasher sans faire tomber le reste du système.

---

### 🧪 3. Elastic (Scalable)

> Le système doit croître ou se réduire selon la charge, sans reconfiguration
> majeure.

**Dans Xcraft** :

- Définition d'une **topologie de services** via `app.json`.
- Lancement des Goblins dans des **sous-processus isolés**.
- **Nœud principal** agissant comme **routeur intelligent** des créations
  d’acteurs.
- **Topologie distribuée** supportant le **multi-processus** et le
  **multi-serveur**.

✅ Scalabilité horizontale native.  
💡 Bonus : combinée au local-first, elle permet de scaler à la demande.

---

### 📨 4. Message-Driven (Piloté par messages)

> Les composants échangent par messages asynchrones, pour un découplage fort.

**Dans Xcraft** :

- Un **bus de messages unifié** pour les commandes et événements.
- Logique métier 100% **événementielle**.
- Synchronisation avec systèmes tiers via des **business events** réactifs.

✅ L’événement est le citoyen de première classe.

---

## 🚀 TL;DR

| Pilier             | Reactive Manifesto                       | Xcraft (2025)                                     |
| ------------------ | ---------------------------------------- | ------------------------------------------------- |
| **Responsive**     | UI fluide, réponse rapide                | ✅ Local-first + UI pilotée par acteurs           |
| **Resilient**      | Isolation, reprise, tolérance aux pannes | ✅ Acteurs isolés, immuables, historisés          |
| **Elastic**        | Scalabilité horizontale                  | ✅ Horde, topologie multi-process et multi-nœud   |
| **Message-Driven** | Communication asynchrone                 | ✅ Bus de messages, commandes, événements métiers |

---

## 🧙 En résumé

**Xcraft** ne se contente pas de suivre le Reactive Manifesto. Il **matérialise
ses principes** dans une boîte à outils prête à l’emploi, pensée pour des
développeurs qui veulent :

- Maîtriser le **cycle de vie de leurs données**
- Rester **offline-first**, mais **cloud-ready**
- Distribuer leur logique métier sans prise de tête
- Concevoir des apps **modulaires, résilientes et scalables** par défaut
