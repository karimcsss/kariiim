# Exemples Pratiques – Système de Gestion de Bibliothèque

Ce document présente un exemple complet de projet pour illustrer chaque livrable attendu.

**Projet exemple** : Système de gestion de bibliothèque universitaire

---

## 1. Extrait du Cahier des Charges

### 1.1 Contexte

La bibliothèque universitaire XYZ gère actuellement ses prêts de livres manuellement sur papier. Ce processus est lent, source d'erreurs et ne permet pas un suivi efficace des emprunts. La direction souhaite informatiser la gestion de la bibliothèque.

### 1.2 Problématique

Comment digitaliser la gestion des emprunts pour améliorer l'efficacité, réduire les erreurs et offrir un meilleur service aux étudiants ?

### 1.3 Objectifs du système

| ID | Objectif | Description | Mesurable |
|----|----------|-------------|-----------|
| OBJ-01 | Automatiser les emprunts | Permettre l'enregistrement électronique des emprunts | Temps de traitement < 1 min |
| OBJ-02 | Améliorer le suivi | Suivre en temps réel les livres disponibles | Taux de disponibilité = 100% |
| OBJ-03 | Faciliter la recherche | Permettre aux étudiants de chercher des livres en ligne | Temps de recherche < 30s |

### 1.4 Acteurs

| Acteur | Description | Rôle |
|--------|-------------|------|
| Étudiant | Utilisateur inscrit à l'université | Emprunter et retourner des livres |
| Bibliothécaire | Personnel de la bibliothèque | Gérer le catalogue et les emprunts |
| Administrateur | Responsable du système | Gérer les utilisateurs et les paramètres |

### 1.5 Périmètre

**Inclus** :
- Recherche de livres dans le catalogue
- Emprunt et retour de livres
- Gestion des réservations
- Calcul automatique des amendes
- Gestion du catalogue

**Exclus** :
- Gestion des achats de nouveaux livres
- Système de facturation des amendes
- Application mobile (phase 2)

### 1.6 Glossaire métier

| Terme | Définition | Exemple |
|-------|------------|---------|
| Emprunt | Action de prendre un livre pour une durée limitée | Durée standard: 14 jours |
| Réservation | Demande pour emprunter un livre actuellement indisponible | Max 3 réservations simultanées |
| Amende | Pénalité financière pour retard de retour | 0,50€ par jour de retard |
| Exemplaire | Copie physique d'un livre | Un livre peut avoir plusieurs exemplaires |

---

## 2. Extrait de l'Analyse Fonctionnelle

### 2.1 Besoins Fonctionnels (exemples)

**BF-01 : S'authentifier**
- **Description** : Le système doit permettre aux utilisateurs de s'authentifier avec leur identifiant universitaire et mot de passe
- **Acteur(s)** : Étudiant, Bibliothécaire, Administrateur
- **Priorité** : Must have
- **Critère de validation** : Connexion réussie avec redirection vers l'espace personnel

**BF-02 : Rechercher un livre**
- **Description** : Le système doit permettre de rechercher un livre par titre, auteur, ISBN ou mot-clé
- **Acteur(s)** : Étudiant, Bibliothécaire
- **Priorité** : Must have
- **Critère de validation** : Résultats affichés en moins de 2 secondes

**BF-03 : Emprunter un livre**
- **Description** : Le système doit permettre à un étudiant d'emprunter un livre disponible
- **Acteur(s)** : Étudiant (initiateur), Bibliothécaire (validation)
- **Priorité** : Must have
- **Critère de validation** : Emprunt enregistré avec date de retour calculée

**BF-04 : Réserver un livre**
- **Description** : Le système doit permettre à un étudiant de réserver un livre actuellement emprunté
- **Acteur(s)** : Étudiant
- **Priorité** : Should have
- **Critère de validation** : Réservation enregistrée, notification envoyée lors de la disponibilité

**BF-05 : Retourner un livre**
- **Description** : Le système doit permettre d'enregistrer le retour d'un livre et calculer une éventuelle amende
- **Acteur(s)** : Bibliothécaire
- **Priorité** : Must have
- **Critère de validation** : Retour enregistré, amende calculée si retard

**BF-06 : Gérer le catalogue**
- **Description** : Le système doit permettre au bibliothécaire d'ajouter, modifier ou supprimer des livres du catalogue
- **Acteur(s)** : Bibliothécaire
- **Priorité** : Must have
- **Critère de validation** : Modifications visibles immédiatement dans la recherche

### 2.2 Besoins Non Fonctionnels (exemples)

**BNF-01 : Temps de réponse**
- **Catégorie** : Performance
- **Description** : Les résultats de recherche doivent s'afficher en moins de 2 secondes
- **Critère de mesure** : Tests de charge avec 100 requêtes simultanées
- **Priorité** : Must have

**BNF-02 : Disponibilité**
- **Catégorie** : Disponibilité
- **Description** : Le système doit être disponible de 7h à 23h, 7j/7
- **Critère de mesure** : Uptime ≥ 98%
- **Priorité** : Should have

**BNF-03 : Sécurité des données**
- **Catégorie** : Sécurité
- **Description** : Les mots de passe doivent être chiffrés (bcrypt)
- **Critère de mesure** : Audit de sécurité
- **Priorité** : Must have

**BNF-04 : Intuitivité**
- **Catégorie** : Ergonomie
- **Description** : Un nouvel utilisateur doit pouvoir effectuer une recherche sans formation
- **Critère de mesure** : Tests utilisateurs (taux de réussite ≥ 90%)
- **Priorité** : Should have

**BNF-05 : Conformité RGPD**
- **Catégorie** : Conformité
- **Description** : Le système doit respecter le RGPD (consentement, droit à l'oubli)
- **Critère de mesure** : Audit de conformité
- **Priorité** : Must have

### 2.3 Diagramme de cas d'utilisation (description textuelle)

```
Système : Gestion de Bibliothèque

Acteurs externes :
- Étudiant (à gauche)
- Bibliothécaire (à gauche)
- Administrateur (à gauche)
- Système de notification (à droite)

Cas d'utilisation :

Pour Étudiant :
- S'authentifier
- Rechercher un livre
- Consulter son compte
- Emprunter un livre
  <<include>> Vérifier disponibilité
  <<include>> Vérifier quota (max 5 emprunts)
- Réserver un livre
- Renouveler un emprunt <<extend>> Emprunter un livre

Pour Bibliothécaire :
- S'authentifier
- Enregistrer un retour
  <<include>> Calculer amende
- Valider un emprunt
- Gérer le catalogue
  - Ajouter un livre
  - Modifier un livre
  - Supprimer un livre

Pour Administrateur :
- S'authentifier (généralisation de S'authentifier)
- Gérer les utilisateurs
- Consulter les statistiques
- Configurer les paramètres

Interactions avec système externe :
- Envoyer notification → Système de notification
```

### 2.4 Description détaillée d'un cas d'utilisation

**UC-03 : Emprunter un livre**

**Informations générales**
- **ID** : UC-03
- **Acteur principal** : Étudiant
- **Acteur secondaire** : Bibliothécaire
- **Priorité** : Must have

**Description**
Permet à un étudiant d'emprunter un livre disponible à la bibliothèque.

**Préconditions**
- L'étudiant est authentifié
- L'étudiant n'a pas atteint son quota d'emprunts (max 5)
- L'étudiant n'a pas d'amende impayée > 10€

**Scénario nominal**
1. L'étudiant scanne sa carte étudiante
2. Le système affiche les informations de l'étudiant
3. Le bibliothécaire scanne le code-barres du livre
4. Le système vérifie la disponibilité du livre
5. Le système vérifie le quota d'emprunts de l'étudiant
6. Le système enregistre l'emprunt avec date de retour (J+14)
7. Le système affiche la confirmation avec la date de retour
8. Le système imprime un ticket de prêt

**Postconditions**
- Un emprunt est créé dans le système
- Le livre est marqué comme "emprunté"
- La date de retour est J+14

**Scénarios alternatifs**
- **A1 - Livre indisponible** (divergence à l'étape 4)
  - Le système affiche "Livre indisponible"
  - Le système propose de réserver le livre
  - Si l'étudiant accepte → UC-04 : Réserver un livre
  
- **A2 - Quota atteint** (divergence à l'étape 5)
  - Le système affiche "Quota d'emprunts atteint (5/5)"
  - L'emprunt est refusé
  - Fin du cas d'utilisation

**Exceptions**
- **E1 - Carte étudiante invalide** (étape 1)
  - Le système affiche "Carte non reconnue"
  - Retour à l'étape 1

**Exigences non fonctionnelles liées**
- BNF-01 : Temps de traitement < 1 minute

---

## 3. Extrait des Diagrammes de Séquence

### 3.1 UC-03 : Emprunter un livre (Scénario nominal)

**Participants**
- `Étudiant` : Acteur
- `:InterfaceEmprunt` : Boundary (écran du bibliothécaire)
- `:ControleurEmprunt` : Control (logique métier)
- `:GestionLecteur` : Control (gestion des étudiants)
- `:GestionCatalogue` : Control (gestion des livres)
- `lecture:Lecteur` : Entity
- `livre:Livre` : Entity
- `emprunt:Emprunt` : Entity
- `:BaseDonnees` : Base de données

**Description textuelle du flux**

```
1. Étudiant → InterfaceEmprunt : scannerCarteEtudiante(carteId)
2. InterfaceEmprunt → ControleurEmprunt : démarrerEmprunt(carteId)
3. ControleurEmprunt → GestionLecteur : getLecteur(carteId)
4. GestionLecteur → BaseDonnees : SELECT lecteur WHERE id=carteId
5. BaseDonnees → GestionLecteur : données lecteur
6. GestionLecteur → lecture:Lecteur : <<create>>
7. GestionLecteur → ControleurEmprunt : lecteur
8. ControleurEmprunt → InterfaceEmprunt : lecteurTrouvé(infos)
9. InterfaceEmprunt → Étudiant : afficherInfosLecteur()

10. Bibliothécaire → InterfaceEmprunt : scannerLivre(isbn)
11. InterfaceEmprunt → ControleurEmprunt : ajouterLivre(isbn)
12. ControleurEmprunt → GestionCatalogue : getLivre(isbn)
13. GestionCatalogue → BaseDonnees : SELECT livre WHERE isbn=...
14. BaseDonnees → GestionCatalogue : données livre
15. GestionCatalogue → livre:Livre : <<create>>
16. GestionCatalogue → ControleurEmprunt : livre

17. ControleurEmprunt → livre:Livre : estDisponible()
18. livre → ControleurEmprunt : true

19. ControleurEmprunt → lecteur:Lecteur : vérifierQuota()
20. lecteur → ControleurEmprunt : quotaOK (3/5)

21. ControleurEmprunt → emprunt:Emprunt : <<create>>(lecteur, livre)
22. emprunt → emprunt : calculerDateRetour() [J+14]
23. ControleurEmprunt → BaseDonnees : INSERT emprunt
24. BaseDonnees → ControleurEmprunt : ok

25. ControleurEmprunt → livre:Livre : marquerEmprunté()
26. livre → BaseDonnees : UPDATE livre SET statut='EMPRUNTE'
27. BaseDonnees → livre : ok

28. ControleurEmprunt → InterfaceEmprunt : empruntCréé(dateRetour)
29. InterfaceEmprunt → Étudiant : afficherConfirmation(dateRetour)
30. InterfaceEmprunt : imprimerTicket(emprunt)
```

**Points clés à commenter dans le diagramme**

1. **Séparation des responsabilités** : 
   - InterfaceEmprunt gère l'affichage
   - ControleurEmprunt orchestre le processus
   - GestionLecteur et GestionCatalogue gèrent leurs domaines respectifs

2. **Vérifications** (étapes 17-20) :
   - Disponibilité du livre
   - Quota de l'étudiant
   - Application des règles métier

3. **Création de l'emprunt** (étapes 21-24) :
   - Création de l'objet Emprunt
   - Calcul de la date de retour (règle: J+14)
   - Persistance en base de données

4. **Mise à jour du statut** (étapes 25-27) :
   - Le livre est marqué comme emprunté
   - Cohérence des données assurée

---

## 4. Extrait du Diagramme de Classes

### 4.1 Dictionnaire des classes principales

**Classe : Lecteur**
- **Description** : Représente un étudiant ou membre du personnel autorisé à emprunter des livres
- **Responsabilités** : Gérer les informations personnelles, vérifier le quota d'emprunts
- **Attributs** :
  - `- id : String` - Identifiant unique (numéro étudiant)
  - `- nom : String` - Nom complet
  - `- email : String` - Adresse email
  - `- type : TypeLecteur` - Type (ETUDIANT, ENSEIGNANT, PERSONNEL)
  - `- dateInscription : Date` - Date d'inscription
  - `- maxEmprunts : Integer` - Nombre max d'emprunts simultanés (5 pour étudiants)
- **Méthodes** :
  - `+ peutEmprunter() : Boolean` - Vérifie si le lecteur peut emprunter
  - `+ getNombreEmpruntsActifs() : Integer` - Compte les emprunts en cours

**Classe : Livre**
- **Description** : Représente un ouvrage du catalogue (métadonnées)
- **Responsabilités** : Stocker les informations bibliographiques
- **Attributs** :
  - `- isbn : String` - Code ISBN unique
  - `- titre : String` - Titre du livre
  - `- auteur : String` - Auteur principal
  - `- editeur : String` - Maison d'édition
  - `- anneePublication : Integer` - Année de publication
  - `- categorie : Categorie` - Catégorie (ROMAN, SCIENCES, etc.)
- **Méthodes** :
  - `+ getExemplairesDisponibles() : Integer` - Nombre d'exemplaires disponibles

**Classe : Exemplaire**
- **Description** : Représente une copie physique d'un livre
- **Responsabilités** : Gérer le statut et la localisation d'une copie
- **Attributs** :
  - `- codeExemplaire : String` - Code unique de l'exemplaire
  - `- statut : StatutExemplaire` - DISPONIBLE, EMPRUNTE, RESERVE, PERDU
  - `- dateAcquisition : Date` - Date d'achat
  - `- localisation : String` - Rayon de rangement
- **Méthodes** :
  - `+ estDisponible() : Boolean` - Vérifie si l'exemplaire est disponible

**Classe : Emprunt**
- **Description** : Représente un prêt de livre à un lecteur
- **Responsabilités** : Gérer le cycle de vie d'un emprunt
- **Attributs** :
  - `- id : Integer` - Identifiant unique
  - `- dateEmprunt : Date` - Date de début
  - `- dateRetourPrevue : Date` - Date de retour prévue (J+14)
  - `- dateRetourEffective : Date` - Date de retour réel (null si en cours)
  - `- statut : StatutEmprunt` - EN_COURS, TERMINE, EN_RETARD
- **Méthodes** :
  - `+ calculerAmende() : Double` - Calcule l'amende en cas de retard
  - `+ estEnRetard() : Boolean` - Vérifie si l'emprunt est en retard
  - `+ prolonger() : void` - Prolonge l'emprunt de 7 jours

**Classe : Reservation**
- **Description** : Représente une demande de réservation d'un livre
- **Responsabilités** : Gérer la file d'attente pour un livre
- **Attributs** :
  - `- id : Integer` - Identifiant unique
  - `- dateReservation : Date` - Date de la demande
  - `- statut : StatutReservation` - EN_ATTENTE, NOTIFIE, ANNULEE
  - `- dateExpiration : Date` - Date limite pour retirer le livre
- **Méthodes** :
  - `+ notifierDisponibilite() : void` - Envoie une notification
  - `+ annuler() : void` - Annule la réservation

**Classe : Amende**
- **Description** : Représente une pénalité financière
- **Responsabilités** : Calculer et suivre les amendes
- **Attributs** :
  - `- id : Integer` - Identifiant unique
  - `- montant : Double` - Montant en euros
  - `- motif : String` - Raison de l'amende
  - `- dateCreation : Date` - Date de création
  - `- estPayee : Boolean` - Statut de paiement
- **Méthodes** :
  - `+ marquerPayee() : void` - Marque l'amende comme payée

### 4.2 Relations principales

**Lecteur ←→ Emprunt**
- **Type** : Association
- **Multiplicité** : `Lecteur 1 ──── 0..* Emprunt`
- **Rôle** : Un lecteur effectue plusieurs emprunts
- **Sémantique** : Un emprunt est toujours lié à un et un seul lecteur

**Livre ←→ Exemplaire**
- **Type** : Composition
- **Multiplicité** : `Livre 1 ◆──── 1..* Exemplaire`
- **Rôle** : Un livre possède plusieurs exemplaires
- **Sémantique** : Un exemplaire ne peut exister sans son livre parent

**Emprunt ←→ Exemplaire**
- **Type** : Association
- **Multiplicité** : `Emprunt * ──── 1 Exemplaire`
- **Rôle** : Un emprunt concerne un exemplaire
- **Sémantique** : Un exemplaire peut avoir plusieurs emprunts dans son historique

**Lecteur ←→ Reservation**
- **Type** : Association
- **Multiplicité** : `Lecteur 1 ──── 0..3 Reservation`
- **Rôle** : Un lecteur peut avoir jusqu'à 3 réservations
- **Contrainte** : max = 3

**Livre ←→ Reservation**
- **Type** : Association
- **Multiplicité** : `Livre 1 ──── 0..* Reservation`
- **Rôle** : Un livre peut avoir plusieurs réservations en attente

**Emprunt ←→ Amende**
- **Type** : Association
- **Multiplicité** : `Emprunt 1 ──── 0..1 Amende`
- **Rôle** : Un emprunt peut générer au plus une amende
- **Sémantique** : Amende créée en cas de retard

**Lecteur ←→ Amende**
- **Type** : Association dérivée
- **Multiplicité** : `Lecteur 1 ──── 0..* Amende`
- **Rôle** : Un lecteur peut avoir plusieurs amendes
- **Navigation** : Via les emprunts

### 4.3 Énumérations

**TypeLecteur**
- ETUDIANT
- ENSEIGNANT
- PERSONNEL

**StatutExemplaire**
- DISPONIBLE
- EMPRUNTE
- RESERVE
- EN_REPARATION
- PERDU

**StatutEmprunt**
- EN_COURS
- TERMINE
- EN_RETARD
- PROLONGE

**StatutReservation**
- EN_ATTENTE
- NOTIFIE
- RETIREE
- ANNULEE
- EXPIREE

**Categorie**
- ROMAN
- SCIENCES
- HISTOIRE
- ART
- TECHNIQUE
- AUTRES

### 4.4 Règles de gestion appliquées

**RG-01 : Durée standard d'emprunt**
- Un emprunt a une durée de 14 jours
- Implémentation : Méthode `Emprunt.calculerDateRetour()`

**RG-02 : Quota d'emprunts**
- Un étudiant peut emprunter maximum 5 livres simultanément
- Implémentation : Attribut `Lecteur.maxEmprunts` et méthode `peutEmprunter()`

**RG-03 : Calcul des amendes**
- 0,50€ par jour de retard
- Implémentation : Méthode `Emprunt.calculerAmende()`

**RG-04 : Blocage si amende > 10€**
- Un lecteur avec une amende > 10€ ne peut plus emprunter
- Implémentation : Méthode `Lecteur.peutEmprunter()` vérifie le total des amendes

**RG-05 : Maximum de réservations**
- Un lecteur peut avoir maximum 3 réservations simultanées
- Implémentation : Multiplicité 0..3 dans la relation Lecteur-Reservation

---

## 5. Matrices de traçabilité

### 5.1 BF → UC → Classes

| Besoin | Cas d'utilisation | Classes impliquées |
|--------|-------------------|-------------------|
| BF-01 | UC-01 : S'authentifier | Lecteur |
| BF-02 | UC-02 : Rechercher un livre | Livre, Exemplaire |
| BF-03 | UC-03 : Emprunter un livre | Lecteur, Emprunt, Exemplaire, Livre |
| BF-04 | UC-04 : Réserver un livre | Lecteur, Reservation, Livre |
| BF-05 | UC-05 : Retourner un livre | Emprunt, Exemplaire, Amende |

### 5.2 UC → Diagrammes de séquence

| Cas d'utilisation | Diagramme fourni | Participants clés |
|-------------------|------------------|-------------------|
| UC-03 : Emprunter un livre | ✓ | Lecteur, Livre, Emprunt, Exemplaire |
| UC-04 : Réserver un livre | ✓ | Lecteur, Livre, Reservation |
| UC-05 : Retourner un livre | ✓ | Emprunt, Exemplaire, Amende |

---

## 6. Points clés de cohérence

✅ **Vocabulaire uniforme** : 
- "Lecteur" utilisé partout (pas "Utilisateur" ou "Étudiant")
- "Exemplaire" pour la copie physique, "Livre" pour les métadonnées

✅ **Acteurs cohérents** :
- Les acteurs du CDC se retrouvent dans les UC
- Les acteurs des UC apparaissent dans les diagrammes de séquence

✅ **Règles de gestion appliquées** :
- Durée de 14 jours : dans CDC, BF, scénarios, et méthode `calculerDateRetour()`
- Quota de 5 : dans CDC, BF, scénarios, et attribut `maxEmprunts`

✅ **Entités tracées** :
- Les entités des diagrammes de séquence deviennent les classes
- Les interactions révèlent les relations entre classes

---

## Conclusion

Cet exemple montre :
1. Comment structurer chaque livrable
2. Le niveau de détail attendu
3. La cohérence entre tous les artefacts
4. L'application pratique des concepts UML

**Utilisez cet exemple comme référence, mais adaptez-le à votre propre projet !**
