# Guide Rapide – Projet UML

Guide de référence rapide pour les étudiants.

---

## 🗓️ Planning en un coup d'œil

| Sem. | Quoi faire ? | Livrable | Template |
|------|-------------|----------|----------|
| 1 | Analyser le sujet, identifier acteurs et périmètre | Cahier des charges (partiel) | [CDC](templates/Cahier_des_charges.md) |
| 2 | Lister les besoins fonctionnels et non fonctionnels | Liste BF/BNF | [Analyse](templates/Analyse_fonctionnelle.md) |
| 3 | Créer les diagrammes de cas d'utilisation | Analyse fonctionnelle complète | [Analyse](templates/Analyse_fonctionnelle.md) |
| 4-5 | Modéliser 3-5 UC avec diagrammes de séquence | Diagrammes de séquence | [Séquence](templates/Diagramme_sequence.md) |
| 6-7 | Créer le diagramme de classes métier | Diagramme de classes | [Classes](templates/Diagramme_classes.md) |
| 8 | Compiler le dossier final et préparer la soutenance | Dossier complet + slides | [S8](semaine_8/README.md) |

---

## ✅ Checklist par semaine

### Semaine 1
- [ ] Lire et comprendre le sujet
- [ ] Identifier les acteurs (qui interagit avec le système ?)
- [ ] Définir les objectifs (que doit faire le système ?)
- [ ] Délimiter le périmètre (inclus/exclus)
- [ ] Créer un glossaire des termes métier
- [ ] Rédiger le cahier des charges

### Semaine 2
- [ ] Lister tous les besoins fonctionnels (BF)
- [ ] Lister tous les besoins non fonctionnels (BNF)
- [ ] Prioriser les besoins (Must/Should/Could/Won't)
- [ ] Structurer les besoins par catégories
- [ ] Créer la matrice de traçabilité BF↔Acteurs

### Semaine 3
- [ ] Créer un cas d'utilisation pour chaque BF majeur
- [ ] Dessiner le diagramme de cas d'utilisation global
- [ ] Créer des diagrammes par acteur
- [ ] Rédiger les descriptions détaillées des UC
- [ ] Vérifier la cohérence avec les BF
- [ ] Finaliser l'analyse fonctionnelle complète

### Semaines 4-5
- [ ] Sélectionner 3 à 5 UC clés (complexes/importants)
- [ ] Rédiger les scénarios nominaux (texte)
- [ ] Identifier les participants (Boundary/Control/Entity)
- [ ] Créer les diagrammes de séquence UML
- [ ] Ajouter des scénarios alternatifs (optionnel)
- [ ] Commenter et justifier les choix
- [ ] Vérifier la cohérence avec les UC

### Semaines 6-7
- [ ] Identifier les classes à partir des diagrammes de séquence
- [ ] Définir les attributs de chaque classe
- [ ] Identifier les relations entre classes
- [ ] Préciser les multiplicités
- [ ] Créer le diagramme de classes complet
- [ ] Rédiger le dictionnaire des classes
- [ ] Vérifier la cohérence avec les séquences

### Semaine 8
- [ ] Compiler tous les livrables
- [ ] Vérifier la cohérence globale
- [ ] Créer la table des matières
- [ ] Relire et corriger (orthographe, style)
- [ ] Générer le PDF final
- [ ] Créer les slides de présentation (12-15 slides)
- [ ] Répéter la présentation (chronométrer)
- [ ] Préparer les réponses aux questions probables

---

## 🎯 Notation UML - Aide-mémoire

### Diagramme de cas d'utilisation

```
Acteur : 👤 (bonhomme)
Cas d'utilisation : (ellipse)
Association : ────
Include : ────<<include>>──→
Extend : ────<<extend>>──→
Généralisation : ────△ (triangle)
```

### Diagramme de séquence

```
Acteur : 👤
Boundary : ⊙ (interface)
Control : ⊙→ (contrôleur)
Entity : ⊙ (entité)

Message synchrone : ────→
Message asynchrone : ────⇢
Retour : - - - →
Création : <<create>>
Destruction : X

Fragments :
alt : alternative (if/else)
opt : optionnel (if)
loop : boucle
par : parallèle
```

### Diagramme de classes

```
Visibilité :
+ public
- private
# protected
~ package

Relations :
Association : ────
Agrégation : ◇────
Composition : ◆────
Héritage : ────△
Dépendance : - - - →

Multiplicités :
1 : exactement un
0..1 : zéro ou un
* : zéro ou plusieurs
1..* : un ou plusieurs
n..m : entre n et m
```

---

## 💡 Astuces

### Pour gagner du temps
1. **Utilisez les templates** : Ne partez pas de zéro
2. **Travaillez en parallèle** : Répartissez le travail dans l'équipe
3. **Vérifiez au fur et à mesure** : Ne gardez pas tout pour la fin
4. **Réutilisez** : Un bon glossaire sert tout le projet

### Pour la qualité
1. **Cohérence** : Même vocabulaire partout
2. **Simplicité** : Pas de sur-ingénierie
3. **Justification** : Expliquez vos choix
4. **Relecture** : Faites relire par un autre membre

### Pour les diagrammes
1. **Lisibilité** : Diagramme clair > diagramme complet
2. **Outils** : draw.io ou PlantUML recommandés
3. **Export** : Sauvegardez en PNG/SVG haute résolution
4. **Légende** : Ajoutez une légende si nécessaire

---

## ⚠️ Erreurs fréquentes à éviter

### Cahier des charges
❌ Périmètre flou ou trop large  
✅ Périmètre clair avec inclusions/exclusions

❌ Objectifs vagues ("améliorer la gestion")  
✅ Objectifs SMART et mesurables

### Besoins
❌ BF trop techniques ("créer une API REST")  
✅ BF métier ("permettre de rechercher un livre")

❌ BNF oubliés ou trop peu nombreux  
✅ Au moins 5-8 BNF dans différentes catégories

### Cas d'utilisation
❌ Cas d'utilisation trop fins ("cliquer sur un bouton")  
✅ Cas d'utilisation métier ("passer une commande")

❌ Trop de relations include/extend  
✅ Utilisation parcimonieuse et justifiée

### Diagrammes de séquence
❌ Participants mal identifiés  
✅ Boundary/Control/Entity clairs

❌ Pas de retours de messages  
✅ Tous les messages ont un retour

❌ Ordre chronologique incorrect  
✅ Ordre respecté de haut en bas

### Diagramme de classes
❌ Classes techniques (DAO, Service, Controller)  
✅ Classes métier uniquement

❌ Relations sans multiplicité  
✅ Toutes les relations ont des multiplicités

❌ Attributs calculés  
✅ Uniquement attributs stockés

---

## 📊 Répartition du temps recommandée

| Semaine | Temps estimé | Répartition |
|---------|--------------|-------------|
| 1 | 8-10h | 50% analyse, 30% rédaction, 20% relecture |
| 2 | 10-12h | 60% identification besoins, 40% structuration |
| 3 | 12-15h | 40% diagrammes, 40% descriptions, 20% cohérence |
| 4-5 | 15-18h | 50% diagrammes séquence, 30% scénarios, 20% commentaires |
| 6-7 | 12-15h | 50% diagramme classes, 30% descriptions, 20% cohérence |
| 8 | 10-12h | 40% compilation, 30% présentation, 30% répétitions |

**Total** : 65-80 heures sur 8 semaines (8-10h/semaine)

---

## 🔗 Liens utiles

### Documentation
- [Planning complet](../Planning_Encadrement.md)
- [Exemple complet](EXEMPLE_COMPLET.md)
- [FAQ](FAQ.md)
- [Grille d'évaluation](evaluation/Grille_Evaluation.md)

### Outils
- [draw.io](https://draw.io) - Diagrammes
- [PlantUML](https://plantuml.com) - Diagrammes en texte
- [Visual Paradigm](https://www.visual-paradigm.com) - UML pro
- [Grammarly](https://grammarly.com) - Correction

### Ressources UML
- Spécification UML 2.5 (OMG)
- "UML 2 pour les bases de données" - Christian Soutou
- "UML 2 par la pratique" - Pascal Roques

---

## 🆘 Besoin d'aide ?

1. **Consultez la FAQ** : [FAQ.md](FAQ.md)
2. **Regardez l'exemple** : [EXEMPLE_COMPLET.md](EXEMPLE_COMPLET.md)
3. **Vérifiez les templates** : `docs/templates/`
4. **Contactez l'encadrant** : En dernier recours

---

**Bon courage ! 💪**
