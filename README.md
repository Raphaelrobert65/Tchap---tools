# Tchap - Tools

Outil interne permettant d’exploiter rapidement les informations liées aux domaines Tchap.

## 🎯 Objectif

Faciliter l’identification des instances Tchap, la génération de MXID et la vérification du statut d’ouverture d’un domaine à partir d’une interface simple, rapide et centralisée.

---

## ⚙️ Fonctionnalités

### 1. Retrouver une instance
Saisir un domaine professionnel.  
L’outil identifie automatiquement l’instance Tchap associée.

**Exemple :**
beta.gouv.fr → agent.dinum.tchap.gouv.fr

---

### 2. Générer un MXID
Saisir une adresse email professionnelle.  
L’outil :
- extrait le domaine  
- identifie l’instance  
- génère automatiquement le MXID  

**Exemple :**
raphael.robert@beta.gouv.fr  
→ @raphael.robert-beta.gouv.fr:agent.dinum.tchap.gouv.fr

---

### 3. Vérifier si un domaine est ouvert
Saisir un domaine professionnel.  
L’outil détermine si le domaine est :

- **Ouvert sur Tchap** → instance dédiée identifiée  
- **Non ouvert** → domaine routé vers `externe`

---

## 🧠 Logique technique

L’outil repose sur l’API Matrix de Tchap :

https://matrix.agent.dinum.tchap.gouv.fr/_matrix/identity/api/v1/info

Principe :
- une requête est simulée avec un email fictif (`test@domaine`)  
- l’API retourne une instance (`hs`)  
- interprétation du résultat :
  - instance contenant `externe` → domaine non ouvert  
  - autre instance → domaine ouvert  

---

## 🖥️ Utilisation

1. Ouvrir le fichier `index.html`  
2. Utiliser directement les trois blocs :
   - Domaine → instance  
   - Email → MXID  
   - Domaine → statut d’ouverture  

Aucune installation requise.

---

## 🧩 Stack technique

- HTML5  
- CSS3 (design system custom)  
- JavaScript vanilla (aucune dépendance)  

---

## 🎨 Design

- Interface alignée avec la charte Tchap (bleu institutionnel + accents sobres)  
- UX centrée sur :
  - rapidité d’exécution  
  - lisibilité  
  - cohérence entre fonctionnalités  
- Composants homogènes (cards, inputs, résultats)  

---

## 🔒 Limites

- dépendance à l’API publique Matrix Tchap  
- pas de garantie sur la disponibilité ou l’évolution de l’endpoint  
- logique basée sur convention (`externe` = non ouvert)  

---

## 🚀 Évolutions possibles

- ajout d’un export CSV / JSON  
- détection automatique via bulk (liste de domaines)  
- intégration d’un scoring ou d’un statut enrichi  
- historisation des requêtes  
- version SaaS avec authentification  

---

## 👤 Auteur

Projet interne – Tchap / DINUM  
Design & développement : r2bizdev
