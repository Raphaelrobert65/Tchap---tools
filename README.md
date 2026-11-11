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

### 4. Générer des MXID en masse
Accessible via l’onglet **« MXID en masse »**.  
Coller jusqu’à 1 000 adresses email (une par ligne, ou séparées par virgule / point-virgule / espace).  
L’outil :
- dédoublonne les adresses et écarte les adresses invalides  
- interroge l’API une seule fois par domaine  
- génère les MXID séparés par un espace, prêts à copier-coller dans Tchap  
- permet l’export TXT ou CSV et liste les adresses non converties  

---

### 5. Préparer les commandes Bot Admin
Accessible via l’onglet **« Commandes Bot Admin »**.  
Coller un email, un MXID ou un lien Tchap : l’outil affiche les commandes prêtes à coller dans l’Admin Room, chacune avec un bouton « Copier » :

| Commande | Format |
|---|---|
| Infos du compte | `!user @mxid` |
| Désactiver | `!deactivate @mxid` |
| Réactiver | `!reactivate @mxid email` |
| Réinitialiser le mot de passe | `!reset_password @mxid` |
| Supprimer les liens OAuth | `!remove_upstream_oauth_links @mxid` |
| Changer l’email | `!replace_email @mxid nouvel_email` |
| Changer le nom affiché | `!replace_displayname @mxid Nom affiché` (sans guillemets) |

Un MXID collé est utilisé tel quel (utile quand il diffère de l’email, ex. suffixe `1`).  
Un MXID mal formé (sans `:` avant le serveur) est signalé.

Dans **MXID en masse**, la commande `!deactivate` est isolée dans une **zone sensible** séparée, fermée par défaut, avec le récapitulatif par instance.

L’outil ne se connecte jamais au Bot Admin : il prépare uniquement le texte à copier-coller.

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
2. Choisir un onglet dans l’en-tête (le dernier onglet utilisé est mémorisé) :
   - **Recherche** : domaine → instance, email → MXID, domaine → statut d’ouverture  
   - **Commandes Bot Admin** : commandes prêtes à coller dans l’Admin Room  
   - **MXID en masse** : liste d’emails → liste de MXID (et commande `!deactivate` en zone sensible)  
3. Cliquer sur une valeur (instance, MXID) pour la copier  

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
