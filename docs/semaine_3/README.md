# Semaine 3 – Diagramme des cas d'utilisation

## 🎯 Objectifs pédagogiques

- Traduire les besoins en cas d'utilisation UML
- Maîtriser la notation des diagrammes de cas d'utilisation
- Comprendre les relations entre acteurs et cas d'utilisation
- Structurer les cas d'utilisation de manière cohérente

---

## 📋 Travaux à réaliser

### 1. Construction du diagramme global

**Éléments du diagramme** :
- **Acteurs** : Représentés par des bonhommes (stickman)
- **Cas d'utilisation** : Représentés par des ellipses
- **Relations** : Associations, include, extend, généralisation

**Étapes** :
1. Reporter tous les acteurs identifiés en semaines 1-2
2. Créer un cas d'utilisation pour chaque besoin fonctionnel majeur
3. Tracer les associations entre acteurs et cas d'utilisation
4. Identifier les relations entre cas d'utilisation

### 2. Relations UML

#### 2.1 Association
- Lien simple entre un acteur et un cas d'utilisation
- L'acteur peut initier ou participer au cas d'utilisation

#### 2.2 Include (inclusion)
- Un cas d'utilisation en inclut systématiquement un autre
- Notation : `<<include>>`
- Exemple : "Passer une commande" include "Vérifier stock"

#### 2.3 Extend (extension)
- Un cas d'utilisation peut optionnellement en étendre un autre
- Notation : `<<extend>>`
- Exemple : "Passer une commande" peut être étendu par "Appliquer code promo"

#### 2.4 Généralisation
- Entre acteurs : un acteur spécialisé hérite d'un acteur général
- Entre cas d'utilisation : un cas spécialisé hérite d'un cas général

### 3. Diagrammes détaillés par acteur

Pour chaque acteur principal, créez un diagramme focalisé montrant :
- L'acteur concerné
- Tous ses cas d'utilisation
- Les relations pertinentes

**Avantages** :
- Vue claire par profil utilisateur
- Facilite la validation avec les parties prenantes
- Simplifie la documentation

### 4. Descriptions textuelles

Pour chaque cas d'utilisation, rédigez une description succincte :

```
Cas d'utilisation : [Nom]
ID : UC-XX
Acteur(s) principal(aux) : [Acteur]
Acteur(s) secondaire(s) : [Acteur]
Préconditions : [Ce qui doit être vrai avant]
Postconditions : [Ce qui est vrai après]
Description : [Résumé du cas d'utilisation]
```

---

## 📄 Livrable 2 (final) : Analyse fonctionnelle complète

**Format** : Document PDF avec diagrammes (PNG/SVG embarqués)

**Contenu** :

1. **Rappel des besoins**
   - Liste BF / BNF (version consolidée)
   - Corrections éventuelles suite à retours

2. **Diagramme de cas d'utilisation global**
   - Vue d'ensemble du système
   - Tous les acteurs et cas d'utilisation
   - Légende si nécessaire

3. **Diagrammes par acteur**
   - Un diagramme par acteur principal
   - Vue focalisée et claire

4. **Descriptions textuelles**
   - Fiche descriptive pour chaque cas d'utilisation
   - Minimum 10-15 cas d'utilisation

5. **Matrice de traçabilité**
   - Lien entre BF et cas d'utilisation

| Besoin | Cas d'utilisation | Acteur(s) |
|--------|-------------------|-----------|
| BF-01 | UC-01, UC-02 | Utilisateur |
| ... | ... | ... |

---

## ✅ Critères de qualité

- [ ] Le diagramme global est lisible et bien organisé
- [ ] Tous les acteurs sont représentés
- [ ] Tous les BF majeurs ont un cas d'utilisation correspondant
- [ ] Les relations include/extend sont utilisées correctement
- [ ] Les diagrammes par acteur sont cohérents avec le global
- [ ] Les descriptions textuelles sont complètes
- [ ] La notation UML est respectée
- [ ] Le document est cohérent avec les livrables précédents

---

## 💡 Conseils

### Notation UML
1. **Nommage** : Utilisez des verbes à l'infinitif pour les cas d'utilisation
   - ✅ "Créer un compte"
   - ❌ "Création de compte"

2. **Granularité** : Ni trop fin, ni trop gros
   - ✅ "Passer une commande"
   - ❌ "Cliquer sur le bouton commander" (trop fin)
   - ❌ "Gérer le système" (trop gros)

3. **Relations** :
   - N'abusez pas des relations include/extend
   - Une association simple suffit souvent

4. **Acteurs** :
   - Placez les acteurs principaux à gauche
   - Placez les acteurs secondaires à droite
   - Placez les systèmes externes en tant qu'acteurs secondaires

### Outils recommandés
- **draw.io** : Gratuit, en ligne, templates UML
- **PlantUML** : Génération de diagrammes depuis du texte
- **Visual Paradigm** : Version étudiante gratuite
- **StarUML** : Open source
- **Lucidchart** : En ligne, collaboration

---

## 📊 Exemple de structure

```
Système : Gestion de bibliothèque

Acteurs :
- Lecteur (principal)
- Bibliothécaire (principal)
- Système de paiement (secondaire)

Cas d'utilisation :
- S'inscrire
- Se connecter
- Rechercher un livre
- Emprunter un livre <<include>> Vérifier disponibilité
- Retourner un livre
- Payer une amende <<extend>> Emprunter un livre
- Gérer le catalogue (bibliothécaire)
```

---

## 🔄 Prochaine étape

→ [Semaine 4-5 - Analyse détaillée (Diagrammes de séquence)](../semaine_4-5/README.md)
