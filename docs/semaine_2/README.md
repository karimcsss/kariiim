# Semaine 2 – Analyse fonctionnelle (besoins)

## 🎯 Objectifs pédagogiques

- Identifier et classifier les besoins fonctionnels et non fonctionnels
- Comprendre la notion d'acteur et son rôle dans le système
- Apprendre à structurer et prioriser les besoins

---

## 📋 Travaux à réaliser

### 1. Besoins fonctionnels (BF)

**Définition** : Services que le système doit fournir aux utilisateurs.

**Comment les identifier ?**
- Partir des objectifs définis en semaine 1
- Se poser la question : "Que doit pouvoir faire l'utilisateur ?"
- Interviewer les parties prenantes

**Structure recommandée pour chaque BF** :
```
BF-XX : [Titre court]
Description : [Description détaillée]
Acteur(s) : [Qui utilise cette fonctionnalité ?]
Priorité : [Haute / Moyenne / Basse]
```

**Exemples de catégories** :
- Gestion des utilisateurs
- Gestion des données
- Processus métier
- Reporting et consultation
- Interfaces externes

### 2. Besoins non fonctionnels (BNF)

**Définition** : Contraintes et qualités que le système doit respecter.

**Catégories de BNF** :

#### 2.1 Performance
- Temps de réponse
- Capacité (nombre d'utilisateurs simultanés)
- Volume de données

#### 2.2 Sécurité
- Authentification
- Autorisation
- Confidentialité des données
- Traçabilité

#### 2.3 Disponibilité
- Taux de disponibilité requis
- Plages horaires de service
- Plan de reprise

#### 2.4 Ergonomie
- Facilité d'utilisation
- Accessibilité
- Design responsive

#### 2.5 Maintenance
- Facilité de maintenance
- Documentation technique
- Support

#### 2.6 Conformité
- Normes à respecter
- Réglementations (RGPD, etc.)
- Standards techniques

**Structure recommandée pour chaque BNF** :
```
BNF-XX : [Titre court]
Catégorie : [Performance / Sécurité / etc.]
Description : [Description détaillée]
Critère de mesure : [Comment vérifier ?]
Priorité : [Haute / Moyenne / Basse]
```

### 3. Priorisation

Utilisez la méthode MoSCoW :
- **Must have** : Indispensable
- **Should have** : Important mais pas critique
- **Could have** : Souhaitable
- **Won't have** : Hors périmètre (cette fois)

---

## 📄 Livrable 2 (partiel) : Liste BF / BNF structurée

**Format** : Document PDF ou Markdown  
**Contenu** :

1. **Introduction**
   - Rappel du contexte
   - Méthodologie utilisée

2. **Besoins fonctionnels**
   - Liste structurée par catégories
   - Minimum 10-15 besoins
   - Chaque BF numéroté et détaillé

3. **Besoins non fonctionnels**
   - Liste structurée par catégories
   - Minimum 5-8 besoins
   - Chaque BNF numéroté et détaillé

4. **Matrice de priorisation**
   - Tableau récapitulatif avec priorités

5. **Traçabilité**
   - Lien entre BF et objectifs du système
   - Lien entre BF et acteurs

**Template** : Utilisez le [modèle d'analyse fonctionnelle](../templates/Analyse_fonctionnelle.md)

---

## ✅ Critères de qualité

- [ ] Les besoins sont clairement exprimés
- [ ] Chaque besoin est identifié de manière unique (BF-01, BNF-01)
- [ ] Les besoins fonctionnels couvrent tous les acteurs
- [ ] Les besoins non fonctionnels couvrent les principales catégories
- [ ] Les priorités sont justifiées
- [ ] Le document est cohérent avec le cahier des charges
- [ ] Les besoins sont testables/vérifiables

---

## 💡 Conseils

1. **Soyez précis** : Évitez les formulations vagues comme "le système doit être rapide"
2. **Soyez complets** : N'oubliez pas les BNF (souvent négligés)
3. **Soyez cohérents** : Vérifiez qu'il n'y a pas de contradictions
4. **Pensez utilisateur** : Écrivez du point de vue de l'utilisateur
5. **Documentez vos sources** : Interviews, documents existants, etc.

---

## 📊 Exemple de tableau récapitulatif

| ID | Catégorie | Description courte | Acteur(s) | Priorité |
|----|-----------|-------------------|-----------|----------|
| BF-01 | Authentification | Connexion au système | Tous | Must have |
| BF-02 | Gestion | Créer un nouvel utilisateur | Admin | Must have |
| ... | ... | ... | ... | ... |

---

## 🔄 Prochaine étape

→ [Semaine 3 - Diagramme des cas d'utilisation](../semaine_3/README.md)
