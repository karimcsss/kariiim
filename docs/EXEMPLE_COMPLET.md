# Exemples Pratiques – Système de Gestion de Musée

Ce document présente un exemple complet de projet pour illustrer chaque livrable attendu.

**Projet exemple** : Système de gestion de musée d'art contemporain

---

## 1. Extrait du Cahier des Charges

### 1.1 Contexte

Le musée d'art contemporain XYZ gère actuellement ses visites, réservations et expositions manuellement sur papier et tableur Excel. Ce processus est inefficace, source d'erreurs et ne permet pas un suivi en temps réel des visiteurs et des œuvres. La direction souhaite informatiser la gestion du musée.

### 1.2 Problématique

Comment digitaliser la gestion des visites, réservations et expositions pour améliorer l'expérience visiteur, optimiser la gestion des collections et faciliter l'organisation des événements culturels ?

### 1.3 Objectifs du système

| ID | Objectif | Description | Mesurable |
|----|----------|-------------|-----------|
| OBJ-01 | Automatiser les réservations | Permettre la réservation en ligne de billets et visites guidées | Temps de réservation < 2 min |
| OBJ-02 | Améliorer le suivi | Suivre en temps réel les visiteurs et la disponibilité des expositions | Taux de remplissage visible en temps réel |
| OBJ-03 | Faciliter la recherche | Permettre aux visiteurs de consulter les œuvres et expositions en ligne | Temps de recherche < 30s |

### 1.4 Acteurs

| Acteur | Description | Rôle |
|--------|-------------|------|
| Visiteur | Personne souhaitant visiter le musée | Réserver des billets, consulter les expositions |
| Guide | Personnel du musée assurant les visites guidées | Gérer les groupes et animer les visites |
| Conservateur | Responsable des collections et expositions | Gérer les œuvres, organiser les expositions |
| Administrateur | Responsable du système | Gérer les utilisateurs et les paramètres |

### 1.5 Périmètre

**Inclus** :
- Consultation des œuvres et expositions en ligne
- Réservation de billets (individuels et groupes)
- Gestion des visites guidées
- Gestion du catalogue des œuvres
- Gestion des expositions temporaires et permanentes
- Statistiques de fréquentation

**Exclus** :
- Gestion de la boutique du musée
- Système de paiement en ligne (phase 2)
- Application mobile (phase 2)
- Gestion de la restauration des œuvres

### 1.6 Glossaire métier

| Terme | Définition | Exemple |
|-------|------------|---------|
| Œuvre | Pièce artistique exposée dans le musée | Tableau, sculpture, installation |
| Exposition | Présentation thématique d'un ensemble d'œuvres | Durée: 3 à 6 mois |
| Visite guidée | Visite accompagnée par un guide du musée | Max 20 personnes par groupe |
| Billet | Droit d'entrée au musée | Tarif plein: 12€, réduit: 8€ |
| Collection | Ensemble d'œuvres appartenant au musée | Collection permanente vs temporaire |

---

## 2. Extrait de l'Analyse Fonctionnelle

### 2.1 Besoins Fonctionnels (exemples)

**BF-01 : S'authentifier**
- **Description** : Le système doit permettre aux utilisateurs de s'authentifier avec leur identifiant et mot de passe
- **Acteur(s)** : Visiteur, Guide, Conservateur, Administrateur
- **Priorité** : Must have
- **Critère de validation** : Connexion réussie avec redirection vers l'espace personnel

**BF-02 : Consulter les œuvres**
- **Description** : Le système doit permettre de rechercher une œuvre par titre, artiste, période ou style
- **Acteur(s)** : Visiteur, Guide, Conservateur
- **Priorité** : Must have
- **Critère de validation** : Résultats affichés en moins de 2 secondes

**BF-03 : Réserver un billet**
- **Description** : Le système doit permettre à un visiteur de réserver un billet d'entrée pour une date donnée
- **Acteur(s)** : Visiteur
- **Priorité** : Must have
- **Critère de validation** : Réservation enregistrée avec numéro de confirmation

**BF-04 : Réserver une visite guidée**
- **Description** : Le système doit permettre à un visiteur de réserver une visite guidée
- **Acteur(s)** : Visiteur
- **Priorité** : Should have
- **Critère de validation** : Réservation enregistrée, notification envoyée au guide

**BF-05 : Gérer les expositions**
- **Description** : Le système doit permettre au conservateur de créer, modifier ou clôturer des expositions
- **Acteur(s)** : Conservateur
- **Priorité** : Must have
- **Critère de validation** : Exposition visible immédiatement sur le site

**BF-06 : Gérer les œuvres**
- **Description** : Le système doit permettre au conservateur d'ajouter, modifier ou retirer des œuvres du catalogue
- **Acteur(s)** : Conservateur
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
- **Description** : Le système doit être disponible 24h/24, 7j/7 pour les consultations en ligne
- **Critère de mesure** : Uptime ≥ 99%
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
Système : Gestion de Musée

Acteurs externes :
- Visiteur (à gauche)
- Guide (à gauche)
- Conservateur (à gauche)
- Administrateur (à gauche)
- Système de paiement (à droite)
- Système de notification (à droite)

Cas d'utilisation :

Pour Visiteur :
- S'inscrire
- S'authentifier
- Consulter les œuvres
- Consulter les expositions
- Réserver un billet
  <<include>> Vérifier disponibilité
  <<include>> Sélectionner la date
- Réserver une visite guidée
- Annuler une réservation <<extend>> Réserver un billet

Pour Guide :
- S'authentifier
- Consulter son planning
- Gérer les groupes de visite
- Marquer la présence des visiteurs

Pour Conservateur :
- S'authentifier
- Gérer les œuvres
  - Ajouter une œuvre
  - Modifier une œuvre
  - Retirer une œuvre
- Gérer les expositions
  - Créer une exposition
  - Modifier une exposition
  - Clôturer une exposition
- Consulter les statistiques

Pour Administrateur :
- S'authentifier (généralisation de S'authentifier)
- Gérer les utilisateurs
- Consulter les statistiques de fréquentation
- Configurer les paramètres du musée

Interactions avec systèmes externes :
- Traiter le paiement → Système de paiement
- Envoyer notification → Système de notification
```

### 2.4 Description détaillée d'un cas d'utilisation

**UC-03 : Réserver un billet**

**Informations générales**
- **ID** : UC-03
- **Acteur principal** : Visiteur
- **Acteur secondaire** : Système de paiement
- **Priorité** : Must have

**Description**
Permet à un visiteur de réserver un billet d'entrée au musée pour une date donnée.

**Préconditions**
- Le visiteur est authentifié (ou peut réserver en tant qu'invité)
- Le musée est ouvert à la date souhaitée
- Il reste des places disponibles pour cette date

**Scénario nominal**
1. Le visiteur sélectionne la date de visite souhaitée
2. Le système affiche les créneaux horaires disponibles
3. Le visiteur sélectionne un créneau horaire
4. Le visiteur choisit le type de billet (plein tarif, réduit, gratuit)
5. Le système calcule le montant total
6. Le visiteur confirme la réservation
7. Le système enregistre la réservation (statut : "en attente de paiement")
8. Le système redirige vers le système de paiement
9. Le système de paiement traite le paiement
10. Le système marque la réservation comme "confirmée"
11. Le système envoie un email de confirmation avec QR code

**Postconditions**
- Une réservation est créée dans le système
- Le billet est marqué comme "réservé"
- Le visiteur reçoit un email avec son QR code

**Scénarios alternatifs**
- **A1 - Aucune place disponible** (divergence à l'étape 2)
  - Le système affiche "Aucun créneau disponible pour cette date"
  - Le système propose d'autres dates
  - Retour à l'étape 1
  
- **A2 - Paiement refusé** (divergence à l'étape 9)
  - Le système affiche "Paiement refusé"
  - La réservation reste "en attente" pendant 15 minutes
  - Le visiteur peut retenter le paiement
  - Fin du cas d'utilisation

**Exceptions**
- **E1 - Session expirée** (étape 6)
  - Le système affiche "Session expirée"
  - Retour à l'authentification

**Exigences non fonctionnelles liées**
- BNF-01 : Temps de traitement < 2 minutes

---

## 3. Extrait des Diagrammes de Séquence

### 3.1 UC-03 : Réserver un billet (Scénario nominal)

**Participants**
- `Visiteur` : Acteur
- `:InterfaceReservation` : Boundary (écran web/mobile)
- `:ControleurReservation` : Control (logique métier)
- `:GestionVisiteur` : Control (gestion des visiteurs)
- `:GestionBillets` : Control (gestion des billets)
- `visiteur:Visiteur` : Entity
- `billet:Billet` : Entity
- `reservation:Reservation` : Entity
- `:SystemePaiement` : Système externe
- `:BaseDonnees` : Base de données

**Description textuelle du flux**

```
1. Visiteur → InterfaceReservation : sélectionnerDate(date)
2. InterfaceReservation → ControleurReservation : vérifierDisponibilité(date)
3. ControleurReservation → GestionBillets : getCreneauxDisponibles(date)
4. GestionBillets → BaseDonnees : SELECT créneaux WHERE date=...
5. BaseDonnees → GestionBillets : liste créneaux
6. GestionBillets → ControleurReservation : créneaux disponibles
7. ControleurReservation → InterfaceReservation : afficherCreneaux(créneaux)
8. InterfaceReservation → Visiteur : afficherOptionsHoraires()

9. Visiteur → InterfaceReservation : sélectionnerCréneau(créneau)
10. Visiteur → InterfaceReservation : sélectionnerTypeBillet(type, quantité)
11. InterfaceReservation → ControleurReservation : calculerMontant(type, quantité)
12. ControleurReservation → billet:Billet : <<create>>(type, quantité, montant)
13. billet → billet : calculerPrix()
14. ControleurReservation → InterfaceReservation : afficherMontant(total)
15. InterfaceReservation → Visiteur : afficherRecapitulatif()

16. Visiteur → InterfaceReservation : confirmerReservation()
17. InterfaceReservation → ControleurReservation : créerReservation(visiteur, billet, créneau)
18. ControleurReservation → GestionVisiteur : getVisiteur(visiteurId)
19. GestionVisiteur → BaseDonnees : SELECT visiteur WHERE id=...
20. BaseDonnees → GestionVisiteur : données visiteur
21. GestionVisiteur → visiteur:Visiteur : <<create>>
22. GestionVisiteur → ControleurReservation : visiteur

23. ControleurReservation → reservation:Reservation : <<create>>(visiteur, billet, créneau)
24. reservation → reservation : générerNuméroConfirmation()
25. ControleurReservation → BaseDonnees : INSERT reservation (statut='EN_ATTENTE')
26. BaseDonnees → ControleurReservation : ok

27. ControleurReservation → SystemePaiement : traiterPaiement(montant, visiteur)
28. SystemePaiement → ControleurReservation : paiementAccepté

29. ControleurReservation → reservation:Reservation : confirmer()
30. reservation → BaseDonnees : UPDATE reservation SET statut='CONFIRMÉE'
31. BaseDonnees → reservation : ok

32. ControleurReservation → reservation:Reservation : générerQRCode()
33. reservation → reservation : créerQRCode()

34. ControleurReservation → InterfaceReservation : réservationConfirmée(numéro, qrCode)
35. InterfaceReservation → Visiteur : afficherConfirmation()
36. InterfaceReservation : envoyerEmailConfirmation(visiteur, qrCode)
```

**Points clés à commenter dans le diagramme**

1. **Séparation des responsabilités** : 
   - InterfaceReservation gère l'affichage
   - ControleurReservation orchestre le processus
   - GestionVisiteur et GestionBillets gèrent leurs domaines respectifs

2. **Vérifications** (étapes 2-7) :
   - Disponibilité des créneaux pour la date choisie
   - Calcul du montant selon le type de billet
   - Application des règles tarifaires

3. **Création de la réservation** (étapes 23-26) :
   - Création de l'objet Reservation
   - Génération d'un numéro de confirmation unique
   - Persistance en base de données (statut initial: EN_ATTENTE)

4. **Traitement du paiement** (étapes 27-31) :
   - Interaction avec le système de paiement externe
   - Mise à jour du statut après confirmation
   - Génération du QR code pour l'entrée

5. **Notification** (étape 36) :
   - Email automatique avec confirmation et QR code
   - Cohérence des données assurée

---

## 4. Extrait du Diagramme de Classes

### 4.1 Dictionnaire des classes principales

**Classe : Visiteur**
- **Description** : Représente une personne visitant le musée
- **Responsabilités** : Gérer les informations personnelles, historique de visites
- **Attributs** :
  - `- id : String` - Identifiant unique
  - `- nom : String` - Nom complet
  - `- email : String` - Adresse email
  - `- telephone : String` - Numéro de téléphone
  - `- typeVisiteur : TypeVisiteur` - Type (INDIVIDUEL, GROUPE, SCOLAIRE)
  - `- dateInscription : Date` - Date d'inscription
- **Méthodes** :
  - `+ peutReserver() : Boolean` - Vérifie si le visiteur peut réserver
  - `+ getHistoriqueVisites() : List<Visite>` - Retourne l'historique des visites

**Classe : Oeuvre**
- **Description** : Représente une pièce artistique du musée
- **Responsabilités** : Stocker les informations sur l'œuvre
- **Attributs** :
  - `- id : String` - Identifiant unique
  - `- titre : String` - Titre de l'œuvre
  - `- artiste : String` - Nom de l'artiste
  - `- annee : Integer` - Année de création
  - `- technique : String` - Technique utilisée (huile, sculpture, etc.)
  - `- dimensions : String` - Dimensions de l'œuvre
  - `- description : Text` - Description détaillée
  - `- style : StyleArtistique` - Style (CONTEMPORAIN, MODERNE, etc.)
- **Méthodes** :
  - `+ estExposee() : Boolean` - Vérifie si l'œuvre est actuellement exposée
  - `+ getExposition() : Exposition` - Retourne l'exposition courante

**Classe : Exposition**
- **Description** : Représente une exposition thématique au musée
- **Responsabilités** : Gérer les œuvres exposées et les dates
- **Attributs** :
  - `- id : Integer` - Identifiant unique
  - `- titre : String` - Titre de l'exposition
  - `- description : Text` - Description thématique
  - `- dateDebut : Date` - Date d'ouverture
  - `- dateFin : Date` - Date de clôture
  - `- type : TypeExposition` - PERMANENTE, TEMPORAIRE
  - `- capaciteMax : Integer` - Nombre max de visiteurs simultanés
- **Méthodes** :
  - `+ estActive() : Boolean` - Vérifie si l'exposition est en cours
  - `+ getNombreVisiteurs() : Integer` - Nombre de visiteurs actuels

**Classe : Billet**
- **Description** : Représente un droit d'entrée au musée
- **Responsabilités** : Gérer les informations tarifaires et la validité
- **Attributs** :
  - `- id : Integer` - Identifiant unique
  - `- type : TypeBillet` - PLEIN_TARIF, REDUIT, GRATUIT, GROUPE
  - `- prix : Double` - Prix du billet
  - `- dateValidite : Date` - Date de validité
  - `- qrCode : String` - Code QR pour l'entrée
  - `- statut : StatutBillet` - VALIDE, UTILISE, ANNULE
- **Méthodes** :
  - `+ estValide() : Boolean` - Vérifie si le billet est valide
  - `+ utiliser() : void` - Marque le billet comme utilisé

**Classe : Reservation**
- **Description** : Représente une réservation de billet
- **Responsabilités** : Gérer le processus de réservation
- **Attributs** :
  - `- id : Integer` - Identifiant unique
  - `- numeroConfirmation : String` - Numéro de confirmation unique
  - `- dateReservation : Date` - Date de la réservation
  - `- dateVisite : Date` - Date de la visite prévue
  - `- creneauHoraire : String` - Créneau horaire (ex: 10h-12h)
  - `- statut : StatutReservation` - EN_ATTENTE, CONFIRMEE, ANNULEE
- **Méthodes** :
  - `+ confirmer() : void` - Confirme la réservation
  - `+ annuler() : void` - Annule la réservation
  - `+ générerQRCode() : String` - Génère le QR code

**Classe : VisiteGuidee**
- **Description** : Représente une visite accompagnée d'un guide
- **Responsabilités** : Gérer les visites de groupe avec guide
- **Attributs** :
  - `- id : Integer` - Identifiant unique
  - `- dateVisite : Date` - Date et heure de la visite
  - `- theme : String` - Thème de la visite
  - `- langue : String` - Langue de la visite
  - `- capaciteMax : Integer` - Nombre max de participants (20)
  - `- duree : Integer` - Durée en minutes (60 ou 90)
- **Méthodes** :
  - `+ ajouterParticipant(visiteur) : Boolean` - Ajoute un participant
  - `+ estComplete() : Boolean` - Vérifie si le groupe est complet
**Classe : Guide**
- **Description** : Représente un guide du musée
- **Responsabilités** : Animer les visites guidées
- **Attributs** :
  - `- id : String` - Identifiant unique
  - `- nom : String` - Nom complet
  - `- email : String` - Adresse email
  - `- langues : List<String>` - Langues parlées
  - `- specialites : List<String>` - Spécialités (art contemporain, etc.)
- **Méthodes** :
  - `+ estDisponible(date) : Boolean` - Vérifie la disponibilité
  - `+ getVisitesAVenir() : List<VisiteGuidee>` - Retourne les visites planifiées

### 4.2 Relations principales

**Visiteur ←→ Reservation**
- **Type** : Association
- **Multiplicité** : `Visiteur 1 ──── 0..* Reservation`
- **Rôle** : Un visiteur effectue plusieurs réservations
- **Sémantique** : Une réservation est toujours liée à un et un seul visiteur

**Reservation ←→ Billet**
- **Type** : Composition
- **Multiplicité** : `Reservation 1 ◆──── 1..* Billet`
- **Rôle** : Une réservation contient un ou plusieurs billets
- **Sémantique** : Un billet ne peut exister sans sa réservation parent

**Exposition ←→ Oeuvre**
- **Type** : Association (many-to-many)
- **Multiplicité** : `Exposition * ──── 0..* Oeuvre`
- **Rôle** : Une exposition présente plusieurs œuvres, une œuvre peut être dans plusieurs expositions
- **Sémantique** : Une œuvre peut être exposée dans plusieurs expositions au fil du temps

**VisiteGuidee ←→ Guide**
- **Type** : Association
- **Multiplicité** : `VisiteGuidee * ──── 1 Guide`
- **Rôle** : Une visite guidée est animée par un guide
- **Sémantique** : Un guide peut animer plusieurs visites

**VisiteGuidee ←→ Visiteur**
- **Type** : Association (many-to-many)
- **Multiplicité** : `VisiteGuidee * ──── 0..20 Visiteur`
- **Rôle** : Une visite peut accueillir jusqu'à 20 visiteurs
- **Contrainte** : max = 20 participants

**VisiteGuidee ←→ Exposition**
- **Type** : Association
- **Multiplicité** : `VisiteGuidee * ──── 1 Exposition`
- **Rôle** : Une visite guidée se déroule dans une exposition
- **Sémantique** : Chaque visite est liée à une exposition spécifique

### 4.3 Énumérations

**TypeVisiteur**
- INDIVIDUEL
- GROUPE
- SCOLAIRE
- PROFESSIONNEL

**TypeBillet**
- PLEIN_TARIF
- REDUIT
- GRATUIT
- GROUPE

**StatutBillet**
- VALIDE
- UTILISE
- ANNULE
- EXPIRE

**StatutReservation**
- EN_ATTENTE
- CONFIRMEE
- ANNULEE
- EXPIREE

**TypeExposition**
- PERMANENTE
- TEMPORAIRE

**StyleArtistique**
- CONTEMPORAIN
- MODERNE
- CLASSIQUE
- ABSTRAIT
- IMPRESSIONNISTE
- AUTRES

### 4.4 Règles de gestion appliquées

**RG-01 : Tarification**
- Tarif plein: 12€, réduit: 8€, gratuit pour -18 ans
- Implémentation : Méthode `Billet.calculerPrix()`

**RG-02 : Capacité maximum des expositions**
- Chaque exposition a une capacité maximale de visiteurs simultanés
- Implémentation : Attribut `Exposition.capaciteMax` et méthode `peutAccueillir()`

**RG-03 : Taille des groupes de visite guidée**
- Maximum 20 personnes par visite guidée
- Implémentation : Multiplicité 0..20 dans la relation VisiteGuidee-Visiteur

**RG-04 : Validité des réservations**
- Une réservation non confirmée expire après 15 minutes
- Implémentation : Vérification dans `Reservation.estValide()`

**RG-05 : Unicité du QR code**
- Chaque billet a un QR code unique
- Implémentation : Génération dans `Reservation.générerQRCode()`

---

## 5. Matrices de traçabilité

### 5.1 BF → UC → Classes

| Besoin | Cas d'utilisation | Classes impliquées |
|--------|-------------------|-------------------|
| BF-01 | UC-01 : S'authentifier | Visiteur, Guide, Conservateur |
| BF-02 | UC-02 : Consulter les œuvres | Oeuvre, Exposition |
| BF-03 | UC-03 : Réserver un billet | Visiteur, Reservation, Billet |
| BF-04 | UC-04 : Réserver une visite guidée | Visiteur, VisiteGuidee, Guide |
| BF-05 | UC-05 : Gérer les expositions | Exposition, Oeuvre, Conservateur |
| BF-06 | UC-06 : Gérer les œuvres | Oeuvre, Conservateur |

### 5.2 UC → Diagrammes de séquence

| Cas d'utilisation | Diagramme fourni | Participants clés |
|-------------------|------------------|-------------------|
| UC-03 : Réserver un billet | ✓ | Visiteur, Reservation, Billet, Système de paiement |
| UC-04 : Réserver une visite guidée | ✓ | Visiteur, VisiteGuidee, Guide |
| UC-05 : Gérer les expositions | ✓ | Conservateur, Exposition, Oeuvre |

---

## 6. Points clés de cohérence

✅ **Vocabulaire uniforme** : 
- "Visiteur" utilisé partout (pas "Client" ou "Utilisateur")
- "Oeuvre" pour la pièce artistique, "Exposition" pour la présentation thématique
- "Billet" pour le droit d'entrée, "Reservation" pour la demande

✅ **Acteurs cohérents** :
- Les acteurs du CDC se retrouvent dans les UC
- Les acteurs des UC apparaissent dans les diagrammes de séquence

✅ **Règles de gestion appliquées** :
- Tarifs (12€ plein, 8€ réduit) : dans CDC, BF, scénarios, et méthode `calculerPrix()`
- Capacité des groupes (20 max) : dans CDC, BF, scénarios, et multiplicité VisiteGuidee-Visiteur
- Validité des réservations (15 min) : dans BNF, scénarios, et méthode `estValide()`

✅ **Entités tracées** :
- Les entités des diagrammes de séquence deviennent les classes
- Les interactions révèlent les relations entre classes

---

## Conclusion

Cet exemple de système de gestion de musée montre :
1. Comment structurer chaque livrable
2. Le niveau de détail attendu
3. La cohérence entre tous les artefacts
4. L'application pratique des concepts UML dans le contexte culturel

**Utilisez cet exemple comme référence, mais adaptez-le à votre propre projet de musée !**
