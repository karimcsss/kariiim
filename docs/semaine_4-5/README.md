# Semaine 4-5 – Analyse détaillée (dynamique du système)

## 🎯 Objectifs pédagogiques

- Comprendre le fonctionnement interne du système
- Maîtriser les diagrammes de séquence UML
- Décrire les interactions entre objets/composants
- Identifier les scénarios nominaux et alternatifs

---

## 📋 Travaux à réaliser

### 1. Sélection des cas d'utilisation clés

**Critères de sélection** :
- Complexité technique
- Importance fonctionnelle
- Représentativité des interactions système
- Risques identifiés

**Sélectionnez 3 à 5 cas d'utilisation** parmi ceux définis en semaine 3.

**Exemple de sélection** :
1. Cas d'utilisation le plus critique pour le métier
2. Cas d'utilisation le plus complexe techniquement
3. Cas d'utilisation impliquant plusieurs acteurs
4. Cas d'utilisation avec interactions externes
5. (Optionnel) Cas d'utilisation représentant un risque

### 2. Rédaction des scénarios

Pour chaque cas d'utilisation sélectionné, rédigez :

#### 2.1 Scénario nominal (obligatoire)
**Définition** : Le chemin "heureux" où tout se passe bien.

**Structure** :
```
Cas d'utilisation : [Nom]
Acteur principal : [Acteur]
Préconditions : [État initial du système]

Scénario nominal :
1. L'acteur [action]
2. Le système [réaction]
3. Le système [traitement]
4. ...
n. [État final]

Postconditions : [État final du système]
```

#### 2.2 Scénarios alternatifs (optionnel mais recommandé)
**Définition** : Variations et cas d'erreur.

**Types de scénarios alternatifs** :
- Données invalides
- Ressource non disponible
- Conditions d'erreur
- Chemins alternatifs valides

**Structure** :
```
Scénario alternatif A1 : [Titre]
Divergence à l'étape : [n]
1. [Description de l'alternative]
2. ...
Résultat : [Retour au nominal / Échec / ...]
```

### 3. Diagrammes de séquence UML

Pour chaque scénario nominal, créez un diagramme de séquence.

#### Éléments du diagramme

**Participants** :
- **Acteur** : L'utilisateur ou système externe
- **Boundary** (frontière) : Interface utilisateur
- **Control** (contrôle) : Logique métier, contrôleur
- **Entity** (entité) : Objets métier, données persistantes

**Représentation** :
```
Acteur           :Interface       :Contrôleur      :Entité
  |                    |                |              |
  |---message-------->|                |              |
  |                    |----requête---->|              |
  |                    |                |---accès----->|
  |                    |                |<--données----|
  |                    |<---réponse-----|              |
  |<---affichage------|                |              |
```

**Messages** :
- **Synchrone** : Flèche pleine (→)
- **Asynchrone** : Flèche ouverte (⇢)
- **Retour** : Flèche pointillée (- - →)

**Fragments** :
- **alt** : Alternative (if/else)
- **opt** : Optionnel (if)
- **loop** : Boucle
- **par** : Parallèle

#### Étapes de création

1. **Identifier les participants** :
   - Acteur principal
   - Interfaces utilisateur
   - Composants logiques
   - Entités métier

2. **Dérouler le scénario** :
   - Partir du scénario textuel
   - Traduire chaque étape en messages
   - Respecter l'ordre chronologique

3. **Détailler les interactions** :
   - Appels de méthodes
   - Création/destruction d'objets
   - Retours de valeurs

4. **Ajouter des notes** :
   - Clarifications
   - Contraintes
   - Règles métier

---

## 📄 Livrable 3 : Diagrammes de séquence commentés

**Format** : Document PDF avec diagrammes

**Contenu** :

1. **Introduction**
   - Rappel des cas d'utilisation sélectionnés
   - Justification de la sélection

2. **Pour chaque cas d'utilisation** :
   
   a. **Rappel du cas d'utilisation**
      - Description brève
      - Lien avec le diagramme de cas d'utilisation
   
   b. **Scénario nominal (texte)**
      - Description étape par étape
      - Préconditions et postconditions
   
   c. **Diagramme de séquence**
      - Version graphique du scénario nominal
      - Lisible et bien formaté
      - Légende si nécessaire
   
   d. **Commentaires et explications**
      - Points clés du diagramme
      - Choix de conception
      - Règles métier appliquées
   
   e. **Scénarios alternatifs** (optionnel)
      - Description textuelle
      - Diagramme si pertinent

3. **Synthèse**
   - Vue d'ensemble des interactions
   - Composants identifiés
   - Préparation pour la modélisation statique

---

## ✅ Critères de qualité

- [ ] 3 à 5 cas d'utilisation sont couverts
- [ ] Les scénarios nominaux sont complets
- [ ] Les diagrammes de séquence respectent la notation UML
- [ ] Les participants sont clairement identifiés
- [ ] L'ordre chronologique est respecté
- [ ] Les messages sont nommés et compréhensibles
- [ ] Des commentaires expliquent les choix importants
- [ ] Les diagrammes sont lisibles (pas trop chargés)
- [ ] Cohérence avec les livrables précédents

---

## 💡 Conseils

### Bonnes pratiques

1. **Simplicité** :
   - Un diagramme = un scénario
   - Ne surchargez pas les diagrammes
   - Utilisez des sous-diagrammes si nécessaire

2. **Nommage** :
   - Messages clairs : `vérifierDisponibilité()`
   - Participants explicites : `:GestionnaireCommande`
   - Évitez les abréviations obscures

3. **Niveau de détail** :
   - Ni trop abstrait (inutile)
   - Ni trop technique (code)
   - Juste ce qu'il faut pour comprendre les interactions

4. **Organisation** :
   - Acteur à gauche
   - Boundary, Control, Entity de gauche à droite
   - Alignement vertical des lignes de vie

### Erreurs courantes à éviter

❌ **À éviter** :
- Oublier les retours de messages
- Mélanger plusieurs scénarios dans un diagramme
- Ne pas identifier clairement les participants
- Diagrammes illisibles (trop petits, mal organisés)

✅ **À faire** :
- Un message = une action claire
- Utiliser les fragments (alt, loop, opt) judicieusement
- Ajouter des notes pour clarifier
- Vérifier la cohérence avec les cas d'utilisation

### Outils recommandés

- **PlantUML** : Diagrammes depuis du texte
- **draw.io** : Édition visuelle
- **Visual Paradigm** : Outils professionnels
- **Enterprise Architect** : Outils avancés

---

## 📊 Exemple simplifié

```
Cas d'utilisation : Réserver un billet
Acteur : Visiteur

Scénario nominal :
1. Le visiteur sélectionne la date de visite
2. Le système affiche les créneaux disponibles
3. Le visiteur sélectionne un créneau et un type de billet
4. Le système calcule le montant
5. Le système crée la réservation
6. Le système redirige vers le paiement
7. Le système confirme et génère le QR code

Diagramme de séquence :
Visiteur -> Interface : sélectionnerDate(date)
Interface -> GestionBillets : getCreneauxDisponibles(date)
GestionBillets -> BDCreneaux : getCreneaux(date)
BDCreneaux --> GestionBillets : listeCreneaux
GestionBillets --> Interface : créneauxDisponibles
Interface --> Visiteur : afficherCreneaux()
Visiteur -> Interface : sélectionnerCréneau(créneau, type)
Interface -> GestionReservation : créerReservation(visiteurId, créneau, type)
GestionReservation -> BDBillet : calculerMontant(type)
BDBillet --> GestionReservation : montant
GestionReservation -> BDReservation : enregistrerReservation(reservation)
BDReservation --> GestionReservation : ok
GestionReservation -> SystemePaiement : traiterPaiement(montant)
SystemePaiement --> GestionReservation : confirmé
GestionReservation --> Interface : réservationConfirmée(qrCode)
Interface --> Visiteur : afficherConfirmation()
```

---

## 🔄 Prochaine étape

→ [Semaine 6-7 - Modélisation statique (Diagramme de classes)](../semaine_6-7/README.md)
