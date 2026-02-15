# Modèle d'Analyse Fonctionnelle

**Projet** : [Nom du projet]  
**Groupe** : [Noms des membres]  
**Formation** : L2 - Conception de SI

---

## 1. Introduction

### 1.1 Contexte

Rappel bref du contexte du projet (référence au cahier des charges).

### 1.2 Objectifs de ce document

Ce document présente :
- Les besoins fonctionnels (BF) du système
- Les besoins non fonctionnels (BNF) du système
- Les diagrammes de cas d'utilisation UML

### 1.3 Méthodologie

Décrivez comment les besoins ont été identifiés :
- Interviews des parties prenantes
- Analyse de l'existant
- Ateliers de travail
- Benchmarking

---

## 2. Besoins fonctionnels (BF)

### 2.1 Catégorie : Gestion des utilisateurs

**BF-01 : Créer un compte utilisateur**
- **Description** : Le système doit permettre à un nouvel utilisateur de créer un compte avec ses informations personnelles
- **Acteur(s)** : Visiteur
- **Priorité** : Must have
- **Critère de validation** : Un nouveau compte est créé dans la base de données avec un identifiant unique

**BF-02 : Se connecter**
- **Description** : Le système doit permettre à un utilisateur enregistré de s'authentifier avec son identifiant et mot de passe
- **Acteur(s)** : Utilisateur
- **Priorité** : Must have
- **Critère de validation** : L'utilisateur accède à son espace personnel après authentification réussie

**BF-03 : Gérer son profil**
- **Description** : Le système doit permettre à un utilisateur de consulter et modifier ses informations personnelles
- **Acteur(s)** : Utilisateur
- **Priorité** : Should have
- **Critère de validation** : Les modifications sont enregistrées et visibles lors de la prochaine consultation

[Continuer avec tous les besoins fonctionnels...]

### 2.2 Catégorie : [Autre catégorie métier]

**BF-XX : [Titre]**
- **Description** : ...
- **Acteur(s)** : ...
- **Priorité** : Must have / Should have / Could have / Won't have
- **Critère de validation** : ...

---

## 3. Besoins non fonctionnels (BNF)

### 3.1 Performance

**BNF-01 : Temps de réponse**
- **Description** : Le système doit afficher les résultats d'une recherche en moins de 2 secondes
- **Catégorie** : Performance
- **Critère de mesure** : Test de charge avec 100 requêtes simultanées
- **Priorité** : Must have

**BNF-02 : Capacité**
- **Description** : Le système doit supporter au moins 1000 utilisateurs simultanés
- **Catégorie** : Performance
- **Critère de mesure** : Test de montée en charge
- **Priorité** : Should have

### 3.2 Sécurité

**BNF-03 : Authentification forte**
- **Description** : Le système doit implémenter une authentification sécurisée avec chiffrement des mots de passe
- **Catégorie** : Sécurité
- **Critère de mesure** : Utilisation de bcrypt ou équivalent, audit de sécurité
- **Priorité** : Must have

**BNF-04 : Gestion des autorisations**
- **Description** : Le système doit implémenter un contrôle d'accès basé sur les rôles (RBAC)
- **Catégorie** : Sécurité
- **Critère de mesure** : Tests d'accès non autorisés doivent échouer
- **Priorité** : Must have

**BNF-05 : Traçabilité**
- **Description** : Le système doit enregistrer toutes les actions critiques (connexions, modifications de données sensibles)
- **Catégorie** : Sécurité
- **Critère de mesure** : Logs consultables et horodatés
- **Priorité** : Should have

### 3.3 Disponibilité

**BNF-06 : Taux de disponibilité**
- **Description** : Le système doit être disponible 99% du temps
- **Catégorie** : Disponibilité
- **Critère de mesure** : Monitoring sur une période d'un mois
- **Priorité** : Should have

### 3.4 Ergonomie et utilisabilité

**BNF-07 : Interface intuitive**
- **Description** : L'interface doit être utilisable sans formation préalable pour 80% des utilisateurs cibles
- **Catégorie** : Ergonomie
- **Critère de mesure** : Tests utilisateurs
- **Priorité** : Should have

**BNF-08 : Accessibilité**
- **Description** : Le système doit respecter les normes WCAG 2.1 niveau AA
- **Catégorie** : Ergonomie
- **Critère de mesure** : Validation avec outils automatiques (WAVE, aXe)
- **Priorité** : Could have

**BNF-09 : Design responsive**
- **Description** : L'interface doit être utilisable sur desktop, tablette et mobile
- **Catégorie** : Ergonomie
- **Critère de mesure** : Tests sur différentes résolutions
- **Priorité** : Should have

### 3.5 Maintenance et évolutivité

**BNF-10 : Documentation technique**
- **Description** : Le code doit être documenté selon les standards de l'équipe
- **Catégorie** : Maintenabilité
- **Critère de mesure** : Présence de commentaires et documentation API
- **Priorité** : Should have

**BNF-11 : Modularité**
- **Description** : L'architecture doit permettre l'ajout de nouvelles fonctionnalités sans refonte majeure
- **Catégorie** : Évolutivité
- **Critère de mesure** : Analyse de l'architecture
- **Priorité** : Should have

### 3.6 Conformité réglementaire

**BNF-12 : Conformité RGPD**
- **Description** : Le système doit respecter le RGPD (consentement, droit à l'oubli, portabilité)
- **Catégorie** : Conformité
- **Critère de mesure** : Audit de conformité
- **Priorité** : Must have

---

## 4. Matrice de priorisation

### 4.1 Tableau récapitulatif des BF

| ID | Catégorie | Description courte | Acteur(s) | Priorité | Complexité |
|----|-----------|-------------------|-----------|----------|------------|
| BF-01 | Utilisateurs | Créer un compte | Visiteur | Must have | Faible |
| BF-02 | Utilisateurs | Se connecter | Utilisateur | Must have | Faible |
| BF-03 | Utilisateurs | Gérer son profil | Utilisateur | Should have | Moyenne |
| ... | ... | ... | ... | ... | ... |

### 4.2 Tableau récapitulatif des BNF

| ID | Catégorie | Description courte | Critère | Priorité |
|----|-----------|-------------------|---------|----------|
| BNF-01 | Performance | Temps de réponse < 2s | Test de charge | Must have |
| BNF-02 | Performance | 1000 utilisateurs simultanés | Test montée en charge | Should have |
| BNF-03 | Sécurité | Authentification forte | Audit sécurité | Must have |
| ... | ... | ... | ... | ... |

---

## 5. Matrice de traçabilité

### 5.1 Lien BF ↔ Objectifs système

| Besoin | Objectif(s) concerné(s) | Commentaire |
|--------|------------------------|-------------|
| BF-01 | OBJ-01, OBJ-02 | Permet de... |
| BF-02 | OBJ-01 | Nécessaire pour... |
| ... | ... | ... |

### 5.2 Lien BF ↔ Acteurs

| Acteur | Besoins fonctionnels |
|--------|---------------------|
| Visiteur | BF-01 |
| Utilisateur | BF-02, BF-03, BF-04, ... |
| Administrateur | BF-10, BF-11, BF-12, ... |

---

## 6. Diagrammes de cas d'utilisation

### 6.1 Diagramme global

[Insérer le diagramme de cas d'utilisation global montrant tous les acteurs et tous les cas d'utilisation]

**Légende** :
- Acteurs principaux : [liste]
- Acteurs secondaires : [liste]
- Relations : include, extend, généralisation

### 6.2 Diagrammes par acteur

#### 6.2.1 Acteur : [Nom de l'acteur 1]

[Insérer le diagramme focalisé sur cet acteur]

**Cas d'utilisation associés** :
- UC-01 : [Nom]
- UC-02 : [Nom]
- ...

#### 6.2.2 Acteur : [Nom de l'acteur 2]

[Insérer le diagramme focalisé sur cet acteur]

**Cas d'utilisation associés** :
- UC-XX : [Nom]
- UC-YY : [Nom]
- ...

---

## 7. Descriptions des cas d'utilisation

### 7.1 UC-01 : [Nom du cas d'utilisation]

**Informations générales**
- **ID** : UC-01
- **Nom** : [Nom explicite]
- **Acteur(s) principal(aux)** : [Acteur]
- **Acteur(s) secondaire(s)** : [Acteur ou Système]
- **Priorité** : Must have / Should have / Could have
- **Complexité** : Faible / Moyenne / Élevée

**Description**
[Description narrative du cas d'utilisation]

**Préconditions**
- [Condition 1]
- [Condition 2]

**Postconditions**
- [Résultat 1]
- [Résultat 2]

**Scénario nominal**
1. [Étape 1]
2. [Étape 2]
3. [Étape 3]
...

**Scénarios alternatifs**
- **A1** : [Titre de l'alternatif]
  - Divergence à l'étape X
  - [Description]

**Exceptions**
- **E1** : [Cas d'erreur]
  - [Gestion de l'erreur]

**Exigences non fonctionnelles liées**
- BNF-XX : [Lien avec BNF]

[Répéter pour tous les cas d'utilisation...]

---

## 8. Matrice de traçabilité BF ↔ UC

| Besoin Fonctionnel | Cas d'Utilisation | Commentaire |
|-------------------|-------------------|-------------|
| BF-01 | UC-01 | Directement mappé |
| BF-02 | UC-02, UC-03 | Couvert par plusieurs UC |
| ... | ... | ... |

---

## 9. Règles de gestion complémentaires

**RG-01** : [Titre]
- Description : ...
- Cas d'utilisation concernés : UC-XX, UC-YY
- Contrainte : ...

**RG-02** : [Titre]
- Description : ...
- Cas d'utilisation concernés : UC-ZZ
- Contrainte : ...

---

## 10. Validation et approbation

| Rôle | Nom | Date | Commentaires |
|------|-----|------|--------------|
| Équipe projet | | | |
| Encadrant | | | |
| Maître d'ouvrage (si applicable) | | | |

---

## Annexes

### Annexe A : Conventions de nommage

- BF-XX : Besoins fonctionnels numérotés
- BNF-XX : Besoins non fonctionnels numérotés
- UC-XX : Cas d'utilisation numérotés
- RG-XX : Règles de gestion numérotées

### Annexe B : Références

- Cahier des charges du projet
- Documentation métier existante
- Standards UML 2.5
