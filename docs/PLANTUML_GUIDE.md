# Guide PlantUML pour le Projet

Ce guide vous explique comment utiliser PlantUML pour créer vos diagrammes UML dans le cadre du projet.

---

## 🎯 Pourquoi PlantUML ?

PlantUML est un outil qui permet de créer des diagrammes UML à partir de texte simple. Avantages :

✅ **Facilement versionnable** : Les fichiers sont du texte, donc parfaits pour Git  
✅ **Reproductible** : Le même code génère toujours le même diagramme  
✅ **Collaboratif** : Facile de voir les modifications entre versions  
✅ **Rapide** : Plus rapide que de dessiner à la souris  
✅ **Professionnel** : Rendu de qualité publication  

---

## 📖 Les 3 Diagrammes du Projet

### 1. Diagramme de Cas d'Utilisation (Semaines 2-3)

**Fichier** : `plantuml/diagramme_cas_utilisation.puml`

**Éléments clés** :
```plantuml
@startuml
' Acteurs
actor Visiteur
actor Guide

' Cas d'utilisation
usecase (Réserver un billet) as UC1
usecase (Vérifier disponibilité) as UC2

' Relations
Visiteur --> UC1
UC1 .> UC2 : <<include>>

' Note
note right of UC1
  Le visiteur choisit
  la date et l'heure
end note
@enduml
```

**À adapter pour votre projet** :
- Remplacez les acteurs par ceux de votre système
- Ajoutez vos cas d'utilisation
- Précisez les relations include/extend

### 2. Diagramme de Séquence (Semaines 4-5)

**Fichier** : `plantuml/diagramme_sequence_reservation.puml`

**Éléments clés** :
```plantuml
@startuml
' Participants avec stéréotypes
actor Utilisateur
participant ":Interface" as UI <<Boundary>>
participant ":Contrôleur" as CTRL <<Control>>
participant "objet:Classe" as OBJ <<Entity>>

' Numérotation automatique
autonumber

' Messages
Utilisateur -> UI : action()
activate UI
UI -> CTRL : traiter()
activate CTRL
CTRL -> OBJ : créer()
OBJ --> CTRL : ok
deactivate CTRL
UI --> Utilisateur : afficher()
deactivate UI
@enduml
```

**À adapter pour votre projet** :
- Sélectionnez 3-5 cas d'utilisation clés
- Identifiez les participants (Boundary, Control, Entity)
- Décrivez les interactions pas à pas

### 3. Diagramme de Classes (Semaines 6-7)

**Fichier** : `plantuml/diagramme_classes_musee.puml`

**Éléments clés** :
```plantuml
@startuml
' Classe avec attributs et méthodes
class Visiteur {
  - id : String
  - nom : String
  + peutReserver() : Boolean
}

class Reservation {
  - dateVisite : Date
  + confirmer() : void
}

' Énumération
enum TypeBillet {
  PLEIN_TARIF
  REDUIT
  GRATUIT
}

' Relations
Visiteur "1" -- "0..*" Reservation : effectue >
Reservation --> TypeBillet
Reservation "1" *-- "1..*" Billet : contient >

' Note
note right of Reservation
  Contrainte : expire
  après 15 minutes
end note
@enduml
```

**À adapter pour votre projet** :
- Identifiez vos classes métier
- Définissez attributs et méthodes principales
- Établissez les relations avec multiplicités

---

## 🛠️ Installation et Outils

### Option 1 : Éditeur en ligne (Le plus simple)

**PlantUML Online Editor** : [http://www.plantuml.com/plantuml/uml](http://www.plantuml.com/plantuml/uml)

1. Copiez le code PlantUML
2. Collez dans l'éditeur
3. Visualisez instantanément
4. Exportez en PNG/SVG/PDF

### Option 2 : Visual Studio Code (Recommandé)

1. **Installez VS Code** : [https://code.visualstudio.com/](https://code.visualstudio.com/)

2. **Installez l'extension PlantUML** :
   - Ouvrez VS Code
   - Allez dans Extensions (Ctrl+Shift+X)
   - Cherchez "PlantUML" de jebbs
   - Cliquez sur "Install"

3. **Utilisez l'extension** :
   - Ouvrez un fichier .puml
   - Appuyez sur `Alt+D` pour prévisualiser
   - Le diagramme s'affiche à côté du code

4. **Exportez le diagramme** :
   - Clic droit dans le diagramme
   - "Export Current Diagram"
   - Choisissez le format (PNG, SVG, PDF)

### Option 3 : IntelliJ / PyCharm

1. Installez le plugin "PlantUML integration"
2. Le diagramme s'affiche automatiquement
3. Exportez via le menu contextuel

---

## 📋 Syntaxe de Base

### Diagramme de Cas d'Utilisation

```plantuml
@startuml
' Définir un acteur
actor NomActeur
actor "Acteur avec espaces" as A2

' Définir un cas d'utilisation
usecase (Cas simple)
usecase (Cas avec\nplusieurs lignes) as UC1

' Relations
NomActeur --> (Cas simple)
NomActeur --> UC1

' Include / Extend
UC1 .> (Autre cas) : <<include>>
(Cas optionnel) .> UC1 : <<extend>>

' Héritage
actor ActeurSpécialisé
ActeurSpécialisé --|> NomActeur

' Système
rectangle "Mon Système" {
  usecase (Dans le système)
}

@enduml
```

### Diagramme de Séquence

```plantuml
@startuml
' Participants
actor Acteur
participant "Objet" as O
database BDD
control Contrôleur

' Numérotation
autonumber

' Messages
Acteur -> O : message()
activate O
O -> BDD : requête
BDD --> O : données
O --> Acteur : réponse
deactivate O

' Création
Acteur -> O ** : <<create>>

' Messages à soi-même
O -> O : traitement interne

' Conditions
alt succès
  O --> Acteur : ok
else échec
  O --> Acteur : erreur
end

' Boucles
loop pour chaque élément
  O -> BDD : traiter
end

' Notes
note right of O
  Ceci est une note
end note

@enduml
```

### Diagramme de Classes

```plantuml
@startuml
' Classe simple
class NomClasse

' Classe avec détails
class ClasseComplete {
  ' Attributs
  - attributPrivé : Type
  # attributProtégé : Type
  + attributPublic : Type
  
  ' Méthodes
  - méthodePrivée() : void
  + méthodePublique() : Type
  + méthodeAvecParams(param : Type) : Resultat
}

' Classe abstraite
abstract ClasseAbstraite {
  {abstract} méthodeAbstraite() : void
}

' Interface
interface MonInterface {
  + méthode1() : void
  + méthode2() : Type
}

' Énumération
enum MonEnum {
  VALEUR1
  VALEUR2
  VALEUR3
}

' Relations
' Association
ClasseA -- ClasseB

' Association avec multiplicités
ClasseA "1" -- "0..*" ClasseB

' Association avec rôle
ClasseA "1" -- "0..*" ClasseB : possède >

' Agrégation (losange vide)
ClasseA o-- ClasseB

' Composition (losange plein)
ClasseA *-- ClasseB

' Héritage (flèche triangle)
ClasseB --|> ClasseA

' Implémentation d'interface
ClasseC ..|> MonInterface

' Dépendance (pointillés)
ClasseD ..> ClasseE

' Notes
note right of ClasseA
  Explication ou
  règle de gestion
end note

@enduml
```

---

## 🎨 Personnalisation

### Couleurs et styles

```plantuml
@startuml
' Couleur d'une classe
class MaClasse #LightBlue

' Couleur d'un acteur
actor MonActeur #Pink

' Style global
skinparam class {
    BackgroundColor LightYellow
    BorderColor Navy
    ArrowColor Red
}

skinparam sequence {
    ParticipantBackgroundColor LightBlue
    LifeLineBorderColor Blue
}

@enduml
```

### Stéréotypes

```plantuml
@startuml
class MaClasse <<Entity>>
class AutreClasse <<Control>>
participant ":Interface" <<Boundary>>
@enduml
```

### Disposition

```plantuml
@startuml
' Forcer une disposition horizontale
left to right direction

' Grouper des éléments
package "Module A" {
  class ClasseA
  class ClasseB
}

@enduml
```

---

## ✅ Checklist pour vos Diagrammes

### Diagramme de Cas d'Utilisation
- [ ] Tous les acteurs sont identifiés
- [ ] Tous les cas d'utilisation majeurs sont présents
- [ ] Les relations include/extend sont correctes
- [ ] Le système est clairement délimité
- [ ] Des notes expliquent les points complexes

### Diagramme de Séquence
- [ ] Les participants sont correctement typés (Boundary/Control/Entity)
- [ ] La numérotation automatique est activée
- [ ] Les activations/désactivations sont cohérentes
- [ ] Les messages de retour sont présents
- [ ] Le scénario est complet du début à la fin

### Diagramme de Classes
- [ ] Toutes les classes métier sont présentes
- [ ] Les attributs ont leur visibilité et type
- [ ] Les méthodes principales sont documentées
- [ ] Les relations ont des multiplicités
- [ ] Les énumérations sont définies
- [ ] Les contraintes sont notées

---

## 💡 Astuces et Bonnes Pratiques

### 1. Commencez Simple
```plantuml
' Version 1 : Structure de base
@startuml
class A
class B
A -- B
@enduml

' Version 2 : Ajout des détails
@startuml
class A {
  - id : int
}
class B {
  - nom : String
}
A "1" -- "*" B
@enduml
```

### 2. Utilisez les Commentaires
```plantuml
@startuml
' Ceci est un commentaire
' Les commentaires aident à s'y retrouver

actor Visiteur ' Acteur principal
usecase (Réserver) as UC1 ' Cas d'utilisation important
@enduml
```

### 3. Organisez avec des Sections
```plantuml
@startuml
' ====== ACTEURS ======
actor Visiteur
actor Guide

' ====== CAS D'UTILISATION ======
usecase (Réserver)
usecase (Consulter)

' ====== RELATIONS ======
Visiteur --> (Réserver)
Guide --> (Consulter)
@enduml
```

### 4. Testez Régulièrement
- Générez le diagramme après chaque modification importante
- Vérifiez que le rendu est lisible
- Ajustez la disposition si nécessaire

### 5. Versionnez Vos Fichiers
```bash
git add plantuml/*.puml
git commit -m "Ajout diagramme de classes"
```

---

## 🆘 Problèmes Courants

### Le diagramme est illisible
**Solution** : Simplifiez ou utilisez `left to right direction`

### Les flèches se croisent
**Solution** : Réorganisez l'ordre de déclaration des éléments

### Les noms sont trop longs
**Solution** : Utilisez des alias
```plantuml
usecase (Nom très long pour le cas d'utilisation) as UC1
actor --> UC1
```

### Le rendu ne fonctionne pas
**Solution** : Vérifiez que vous avez bien `@startuml` au début et `@enduml` à la fin

---

## 📚 Ressources Complémentaires

- **Documentation officielle** : [https://plantuml.com/fr/](https://plantuml.com/fr/)
- **Galerie d'exemples** : [https://real-world-plantuml.com/](https://real-world-plantuml.com/)
- **Forum d'aide** : [https://forum.plantuml.net/](https://forum.plantuml.net/)
- **Cheat sheet PDF** : [PlantUML Cheat Sheet](https://plantuml.com/fr/guide)

---

## 🎓 Pour Aller Plus Loin

Une fois à l'aise avec PlantUML, vous pouvez :
- Créer des diagrammes d'activité
- Générer des diagrammes d'état
- Faire des diagrammes de déploiement
- Intégrer PlantUML dans vos documentations Markdown

---

**Bon travail avec PlantUML ! 🚀**
