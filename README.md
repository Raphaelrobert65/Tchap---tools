# Tchap - Tools

Tchap - Tools est un outil web simple et rapide permettant d’interagir avec l’écosystème Tchap (basé sur Matrix).

Il permet d’automatiser deux actions clés :
- 🔍 retrouver l’instance Tchap associée à un domaine
- 🆔 générer un MXID à partir d’un email professionnel

---

## 🎯 Objectif

Simplifier les usages techniques autour de Tchap pour :
- les équipes support
- les équipes IT
- les utilisateurs avancés
- les contextes de déploiement ou d’investigation

---

## 🚀 Fonctionnalités

### 1. Recherche d’instance

À partir d’un domaine (ex : `beta.gouv.fr`), l’outil permet de :
- récupérer l’instance Tchap associée (homeserver)
- identifier le type d’instance :
  - Agent
  - Externe
  - Autre

---

### 2. Génération de MXID

À partir d’un email professionnel (ex : `prenom.nom@beta.gouv.fr`), l’outil :
1. extrait le domaine
2. interroge l’API Tchap
3. récupère l’instance associée
4. génère automatiquement le MXID

Exemple :

Email : raphael.robert@beta.gouv.fr  
Instance : agent.dinum.tchap.gouv.fr  
MXID : @raphael.robert-beta.gouv.fr:agent.dinum.tchap.gouv.fr  

---

## ⚙️ Fonctionnement technique

### API utilisée

https://matrix.agent.dinum.tchap.gouv.fr/_matrix/identity/api/v1/info

---

### Logique de récupération d’instance

1. domaine → test@domaine  
2. appel API  
3. récupération de data.hs (homeserver)  

---

### Logique de génération du MXID

email → remplacement du @ par -  
→ ajout de :instance  

Format final :

@prenom.nom-domaine:instance  

---

## 🧱 Architecture

Le code est structuré en modules JavaScript :

- Api → appels à l’API Tchap
- Validator → validation des entrées
- Parser → extraction du domaine
- Builder → construction du MXID
- Mapper → typologie des instances
- Renderer → affichage UI
- UI → gestion des interactions (loading, copy)

---

## 🎨 UX & Design

- Interface simple et lisible
- Couleurs inspirées de Tchap (bleu nuit / doré)
- Résultats en cartes
- Boutons de copie rapide
- Gestion des états (chargement, erreur, succès)

---

## 📦 Installation

Aucune dépendance.

Cloner le repo :

git clone https://github.com/TON-USERNAME/tchap-tools.git

Ouvrir :

index.html

---

## 🌐 Déploiement

Compatible avec :
- GitHub Pages
- Netlify
- Vercel
- tout hébergement statique

---

## ⚠️ Limites

- Le MXID est reconstruit via une convention métier
- Ne garantit pas l’existence réelle du compte
- Dépendance à l’API Tchap

---

## 🔜 Évolutions possibles

- mode batch (liste d’emails)
- export CSV / Excel
- historique des recherches
- amélioration UX (toast, feedback)
- ajout backend

---

## 👤 Auteur

Projet développé pour simplifier les usages autour de Tchap en contexte professionnel.

---

## 📄 Licence

Usage interne / expérimental.
Libre d’adaptation.
