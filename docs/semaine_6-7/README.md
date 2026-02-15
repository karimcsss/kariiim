# Semaine 6-7 – Modélisation statique (classes métier)

## 🎯 Objectifs pédagogiques

- Passer du comportement (dynamique) à la structure (statique)
- Identifier les entités métier du système
- Maîtriser les diagrammes de classes UML
- Comprendre les relations entre classes

---

## 📋 Travaux à réaliser

### 1. Identification des entités métier

**Sources d'information** :
- Glossaire métier (Semaine 1)
- Besoins fonctionnels (Semaine 2)
- Cas d'utilisation (Semaine 3)
- Diagrammes de séquence (Semaine 4-5)

**Méthode d'identification** :
1. **Analyse des diagrammes de séquence** :
   - Chaque participant "Entity" est une classe candidate
   - Les données échangées peuvent révéler des classes

2. **Analyse du vocabulaire métier** :
   - Les noms du glossaire sont souvent des classes
   - Exemples : Client, Commande, Produit, Facture

3. **Analyse des besoins** :
   - Identifier les concepts métier dans les BF
   - Repérer les objets manipulés par les cas d'utilisation

**Critères de validation** :
- ✅ La classe représente un concept métier clair
- ✅ La classe a des attributs et des comportements
- ✅ La classe n'est pas juste un processus
- ❌ Éviter les classes "utilitaires" (ex: Gestionnaire)

### 2. Définition des attributs

Pour chaque classe identifiée, listez ses attributs.

**Format** :
```
visibilité nom : type [multiplicité] = valeurParDéfaut
```

**Exemples** :
```
- nom : String
- dateNaissance : Date
+ email : String
# montant : Double [1..*]
- statut : Enum = ACTIF
```

**Visibilité** :
- `+` public : accessible de partout
- `-` private : accessible uniquement dans la classe
- `#` protected : accessible dans la classe et ses sous-classes
- `~` package : accessible dans le même package

**Types** :
- Types primitifs : Integer, String, Boolean, Date, Double
- Types métier : autres classes du modèle
- Collections : List, Set, Map avec notation [*] ou [1..*]

**Conseils** :
- Restez au niveau métier (pas technique)
- Évitez les attributs calculés
- Préférez les types métier aux types primitifs si pertinent

### 3. Identification des relations

#### 3.1 Association

**Définition** : Lien structurel entre deux classes.

**Notation** :
```
ClasseA ----------- ClasseB
       nom [mult]
```

**Multiplicités** :
- `1` : exactement un
- `0..1` : zéro ou un
- `*` ou `0..*` : zéro ou plusieurs
- `1..*` : un ou plusieurs
- `n..m` : entre n et m

**Exemples** :
```
Client -------- 0..* Commande
       passe

Commande -------- 1..* LigneCommande
         contient

Étudiant -------- 0..* Cours
         suit
```

#### 3.2 Agrégation

**Définition** : "A un" - relation partie/tout faible.

**Notation** : Losange vide du côté du tout
```
Équipe ◇-------- * Joueur
```

**Caractéristiques** :
- La partie peut exister sans le tout
- Relation moins forte que la composition

#### 3.3 Composition

**Définition** : "Contient" - relation partie/tout forte.

**Notation** : Losange plein du côté du tout
```
Commande ◆-------- * LigneCommande
```

**Caractéristiques** :
- La partie ne peut pas exister sans le tout
- Si le tout est détruit, les parties le sont aussi
- Une partie appartient à un seul tout

#### 3.4 Héritage (Généralisation)

**Définition** : "Est un" - relation de spécialisation.

**Notation** : Flèche triangulaire vers la classe parent
```
        Animal
         △
         |
    _____|_____
   |           |
 Chien       Chat
```

**Utilisation** :
- Factoriser des attributs et méthodes communs
- Représenter des concepts avec variations

#### 3.5 Dépendance

**Définition** : Une classe utilise temporairement une autre.

**Notation** : Flèche pointillée
```
ClasseA - - - - -> ClasseB
```

**Quand l'utiliser** :
- Paramètre de méthode
- Variable locale
- Import/utilisation ponctuelle

### 4. Définition des méthodes (optionnel)

**Format** :
```
visibilité nom(paramètres) : typeRetour
```

**Exemples** :
```
+ ajouterLigne(produit: Produit, quantité: Integer) : void
+ calculerTotal() : Double
- validerCommande() : Boolean
```

**Conseil** : Ne mettez que les méthodes métier importantes. Les getters/setters peuvent être omis.

---

## 📄 Livrable 4 : Diagramme de classes métier V1

**Format** : Document PDF avec diagrammes

**Contenu** :

1. **Introduction**
   - Rappel du périmètre
   - Méthodologie d'identification des classes

2. **Dictionnaire des classes**
   - Pour chaque classe : nom, description, responsabilités
   - Tableau récapitulatif

3. **Diagramme de classes complet**
   - Toutes les classes identifiées
   - Attributs principaux
   - Relations avec multiplicités
   - Héritage si applicable
   - Légende si nécessaire

4. **Diagrammes partiels** (recommandé)
   - Par domaine fonctionnel
   - Vue plus lisible et ciblée

5. **Descriptions des relations clés**
   - Justification des choix de modélisation
   - Contraintes métier
   - Règles de gestion

6. **Traçabilité**
   - Lien entre classes et diagrammes de séquence
   - Lien entre classes et cas d'utilisation

---

## ✅ Critères de qualité

- [ ] Toutes les entités métier majeures sont identifiées
- [ ] Les classes ont des noms explicites (vocabulaire métier)
- [ ] Les attributs sont bien typés
- [ ] Les multiplicités sont précisées sur toutes les associations
- [ ] Les relations (association, agrégation, composition, héritage) sont correctement utilisées
- [ ] Le diagramme est lisible et bien organisé
- [ ] Les contraintes métier sont documentées
- [ ] Cohérence avec les livrables précédents (séquence, cas d'utilisation)
- [ ] Pas de sur-ingénierie (rester au niveau métier)

---

## 💡 Conseils

### Bonnes pratiques

1. **Nommage** :
   - Classes : nom au singulier, PascalCase (Commande, Client)
   - Attributs : camelCase (dateCommande, montantTotal)
   - Éviter les noms génériques (Objet, Element, Data)

2. **Organisation** :
   - Regrouper les classes par domaine
   - Mettre les classes principales au centre
   - Placer les classes héritières en dessous

3. **Niveau de détail** :
   - Focus sur le métier, pas sur l'implémentation
   - Pas de classes techniques (DAO, Service, Controller)
   - Pas d'attributs techniques (id, timestamp, version)

4. **Relations** :
   - Privilégier la composition pour les relations fortes
   - Utiliser l'agrégation avec parcimonie
   - Ne pas abuser de l'héritage (max 2-3 niveaux)

### Erreurs courantes à éviter

❌ **À éviter** :
- Classes trop génériques (Gestionnaire, Manager)
- Attributs calculés (totalTTC si on a totalHT et tva)
- Relations bidirectionnelles sans nécessité
- Sur-ingénierie (trop de classes pour rien)
- Mélanger métier et technique

✅ **À faire** :
- Classes représentant des concepts métier clairs
- Attributs stockés (pas calculés)
- Relations avec multiplicités précises
- Simplicité et clarté

### Patterns courants

**Pattern 1 : Commande**
```
Client ----- * Commande ◆----- * LigneCommande ----- Produit
```

**Pattern 2 : Utilisateur avec rôles**
```
        Utilisateur
             △
             |
       ______|______
      |             |
  Administrateur  Client
```

**Pattern 3 : Réservation**
```
Client ----- * Réservation ----- Ressource
                    |
                   Date
```

---

## 📊 Exemple de dictionnaire de classes

| Classe | Description | Attributs clés |
|--------|-------------|----------------|
| Client | Personne effectuant des achats | nom, email, adresse |
| Commande | Achat effectué par un client | numéro, date, statut |
| Produit | Article disponible à la vente | référence, nom, prix |
| LigneCommande | Ligne dans une commande | quantité, prixUnitaire |

---

## 🔍 Auto-évaluation

Posez-vous ces questions :
1. Chaque classe représente-t-elle un concept métier réel ?
2. Les relations reflètent-elles les règles métier ?
3. Les multiplicités sont-elles correctes ?
4. Le modèle permet-il de répondre aux cas d'utilisation ?
5. Le modèle est-il cohérent avec les diagrammes de séquence ?

---

## 🔄 Prochaine étape

→ [Semaine 8 - Consolidation & soutenance](../semaine_8/README.md)
