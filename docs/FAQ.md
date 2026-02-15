# FAQ – Questions Fréquentes

Réponses aux questions les plus courantes des étudiants.

---

## 📋 Questions générales

### Q1 : Combien de temps dois-je consacrer au projet ?

**R :** Entre 65 et 80 heures au total sur 8 semaines, soit environ 8-10 heures par semaine. Répartissez le travail régulièrement plutôt que de tout faire à la dernière minute.

### Q2 : Puis-je travailler sur un sujet personnel ?

**R :** Cela dépend de votre encadrant. En général, vous devez traiter le sujet qui vous est affecté. Si vous avez une idée de projet personnel, proposez-la rapidement à votre encadrant pour validation.

### Q3 : Combien de pages doit faire le dossier final ?

**R :** Environ 40-60 pages pour un projet complet, mais la qualité prime sur la quantité. Un dossier de 45 pages bien fait vaut mieux que 80 pages remplies d'informations inutiles.

### Q4 : Dois-je créer un prototype ou du code ?

**R :** Non. Ce projet se concentre sur la conception (modélisation UML). Vous ne devez pas développer de code. Concentrez-vous sur les diagrammes et la documentation.

---

## 🟦 Semaine 1 - Cahier des charges

### Q5 : Comment identifier tous les acteurs ?

**R :** Posez-vous ces questions :
- Qui utilise le système ?
- Qui administre le système ?
- Quels systèmes externes interagissent avec le nôtre ?
- Qui bénéficie du système ?

Les acteurs peuvent être des personnes (utilisateurs, admins) ou des systèmes (API externe, service de paiement).

### Q6 : Comment définir le périmètre ?

**R :** Listez :
- **Inclus** : Ce que le système DOIT faire (fonctionnalités principales)
- **Exclus** : Ce que le système NE fera PAS (reporté, hors scope, déjà existant)

Soyez réaliste : un projet de 8 semaines ne peut pas tout couvrir.

### Q7 : À quoi sert le glossaire ?

**R :** Le glossaire définit le vocabulaire métier pour :
- Assurer une compréhension commune dans l'équipe
- Éviter les ambiguïtés
- Servir de base pour nommer les classes plus tard

Exemple : Qu'est-ce qu'un "client" ? Un compte ? Une personne ? Une entreprise ?

---

## 🟦 Semaine 2 - Analyse fonctionnelle

### Q8 : Quelle est la différence entre BF et BNF ?

**R :**
- **BF (Besoin Fonctionnel)** : Ce que le système FAIT (fonctionnalités)
  - Exemple : "Le système doit permettre de créer un compte"
  
- **BNF (Besoin Non Fonctionnel)** : Comment le système le fait (qualités, contraintes)
  - Exemple : "Le système doit répondre en moins de 2 secondes"

### Q9 : Combien de BF et BNF dois-je avoir ?

**R :**
- **BF** : Minimum 10-15, idéalement 15-20 pour un projet complet
- **BNF** : Minimum 5-8, couvrant différentes catégories (performance, sécurité, ergonomie, etc.)

### Q10 : Comment prioriser les besoins ?

**R :** Utilisez la méthode MoSCoW :
- **Must have** : Indispensable, sans quoi le système n'a pas de sens
- **Should have** : Important, mais le système peut fonctionner sans
- **Could have** : Souhaitable, si le temps le permet
- **Won't have** : Hors périmètre pour cette version

### Q11 : Mes BF sont-ils trop techniques ?

**R :** Les BF doivent être exprimés du point de vue métier, pas technique.

❌ Trop technique : "Créer une API REST pour gérer les utilisateurs"  
✅ Métier : "Le système doit permettre de créer un compte utilisateur"

❌ Trop technique : "Utiliser une base de données PostgreSQL"  
✅ Non fonctionnel : "Le système doit persister les données de manière fiable"

---

## 🟦 Semaine 3 - Cas d'utilisation

### Q12 : Comment nommer un cas d'utilisation ?

**R :** Utilisez un verbe à l'infinitif décrivant l'action :
- ✅ "Créer un compte"
- ✅ "Rechercher un produit"
- ✅ "Passer une commande"
- ❌ "Création de compte" (nom)
- ❌ "Gestion des commandes" (trop vague)

### Q13 : Quelle est la bonne granularité pour un UC ?

**R :** Ni trop fin, ni trop gros. Un UC représente une **transaction métier complète**.

❌ Trop fin : "Cliquer sur le bouton valider"  
✅ Correct : "Valider une commande"  
❌ Trop gros : "Gérer toutes les commandes"

Règle : Un UC = une valeur métier pour l'acteur.

### Q14 : Quand utiliser include et extend ?

**R :**
- **Include** : Le UC A inclut TOUJOURS le UC B
  - "Passer commande" include "Vérifier stock"
  - Le stock est vérifié à chaque commande

- **Extend** : Le UC B étend OPTIONNELLEMENT le UC A
  - "Passer commande" peut être étendu par "Appliquer code promo"
  - Le code promo est optionnel

⚠️ N'abusez pas : une simple association suffit souvent.

### Q15 : Combien de cas d'utilisation dois-je avoir ?

**R :** Environ 10-20 UC pour un projet complet. Chaque BF majeur devrait avoir au moins un UC correspondant.

---

## 🟦 Semaines 4-5 - Diagrammes de séquence

### Q16 : Comment choisir les UC à modéliser en séquence ?

**R :** Sélectionnez 3 à 5 UC selon ces critères :
- **Complexité technique** : UC avec beaucoup d'interactions
- **Importance métier** : UC critique pour le système
- **Représentativité** : UC montrant des patterns différents
- **Risque** : UC avec des points difficiles

### Q17 : Quelle est la différence entre Boundary, Control et Entity ?

**R :**
- **Boundary** (Frontière) : Interface avec l'extérieur (écran, API)
  - Exemple : `:InterfaceConnexion`, `:PageCommande`
  
- **Control** (Contrôle) : Logique métier, orchestration
  - Exemple : `:GestionnaireCommande`, `:ControleurPaiement`
  
- **Entity** (Entité) : Objets métier, données persistantes
  - Exemple : `commande:Commande`, `client:Client`

### Q18 : Dois-je montrer tous les getters/setters ?

**R :** Non. Les diagrammes de séquence doivent montrer les **interactions significatives**, pas les détails d'implémentation. Évitez :
- `getterNom()`
- `setterEmail()`

Montrez plutôt :
- `authentifier(login, password)`
- `calculerTotal()`
- `validerCommande()`

### Q19 : Que faire si mon diagramme est trop chargé ?

**R :** Plusieurs options :
1. Créer plusieurs diagrammes (scénario nominal, alternatifs séparés)
2. Utiliser des fragments `ref` pour référencer d'autres diagrammes
3. Regrouper certaines interactions en une seule si elles forment un bloc cohérent
4. Vérifier que vous n'êtes pas descendu trop dans les détails techniques

---

## 🟦 Semaines 6-7 - Diagramme de classes

### Q20 : Comment identifier les classes ?

**R :** Plusieurs sources :
1. **Diagrammes de séquence** : Les "Entity" deviennent des classes
2. **Glossaire** : Les termes métier sont souvent des classes
3. **Besoins fonctionnels** : Les concepts manipulés sont des classes
4. **Analyse grammaticale** : Les noms sont des classes candidates

### Q21 : Dois-je inclure les classes techniques (DAO, Service, etc.) ?

**R :** Non. Le diagramme de classes **métier** ne contient que des concepts métier. Excluez :
- ❌ UserDAO, CommandeService, PaiementController
- ❌ HttpRequest, JsonResponse
- ❌ Logger, Configuration

Incluez seulement :
- ✅ Client, Commande, Produit
- ✅ Facture, Paiement, Livraison

### Q22 : Quelle est la différence entre agrégation et composition ?

**R :**

**Composition** (losange plein ◆) : Relation forte, cycle de vie dépendant
- La partie ne peut exister sans le tout
- Si le tout est détruit, les parties aussi
- Exemple : `Commande ◆── LigneCommande`
  - Si la commande est supprimée, les lignes le sont aussi

**Agrégation** (losange vide ◇) : Relation faible, cycle de vie indépendant
- La partie peut exister sans le tout
- Si le tout est détruit, les parties survivent
- Exemple : `Équipe ◇── Joueur`
  - Si l'équipe est dissoute, les joueurs existent toujours

### Q23 : Dois-je mettre toutes les méthodes ?

**R :** Non. Mettez uniquement les **méthodes métier importantes**. Vous pouvez omettre :
- Les getters/setters classiques
- Les méthodes évidentes (`toString()`, `equals()`)

Incluez :
- Les méthodes avec logique métier : `calculerTotal()`, `valider()`
- Les méthodes importantes pour comprendre : `estDisponible()`, `annuler()`

### Q24 : Comment gérer les multiplicités ?

**R :** Les multiplicités doivent refléter les **règles métier** :
- `1` : exactement un (toujours présent)
- `0..1` : optionnel (peut être absent)
- `1..*` : au moins un (obligatoire et multiple)
- `*` ou `0..*` : zéro ou plusieurs

Exemple :
- `Client 1 ──── * Commande` : Un client peut avoir plusieurs commandes
- `Commande 1 ──── 1..* LigneCommande` : Une commande a au moins une ligne

---

## 🟦 Semaine 8 - Consolidation

### Q25 : Dans quel ordre dois-je organiser le dossier final ?

**R :** Ordre recommandé :
1. Page de garde
2. Table des matières
3. Cahier des charges
4. Analyse fonctionnelle (BF/BNF + UC)
5. Diagrammes de séquence
6. Diagramme de classes
7. Glossaire
8. Annexes (si nécessaire)

### Q26 : Combien de slides pour la présentation ?

**R :** Entre 12 et 15 slides pour une présentation de 15-20 minutes, soit environ 1-1,5 minute par slide. Structure recommandée :
- 1 slide titre
- 1-2 slides contexte/problématique
- 2-3 slides analyse fonctionnelle
- 3-4 slides diagrammes de séquence
- 3-4 slides diagramme de classes
- 1 slide conclusion

### Q27 : Comment gérer les questions pendant la soutenance ?

**R :** Conseils :
1. **Écoutez** la question jusqu'au bout
2. **Reformulez** si nécessaire pour vous assurer d'avoir compris
3. **Répondez** clairement et directement
4. **Assumez** si vous ne savez pas : "Je n'ai pas la réponse précise, mais je pense que..."
5. **Ne mentez jamais** : mieux vaut admettre une lacune qu'inventer

---

## 🛠️ Questions techniques

### Q28 : Quel outil utiliser pour les diagrammes ?

**R :** Plusieurs options :
- **draw.io** : Gratuit, en ligne, facile. Recommandé pour débuter.
- **PlantUML** : Génération depuis du texte. Bien pour versioning Git.
- **Visual Paradigm** : Professionnel, version étudiante gratuite.
- **StarUML** : Open source, interface moderne.

Choisissez celui avec lequel vous êtes le plus à l'aise.

### Q29 : Comment exporter mes diagrammes ?

**R :**
- Format PNG ou SVG pour le dossier (haute résolution : 300 DPI minimum)
- Format vectoriel (SVG, PDF) si possible pour éviter la pixellisation
- Vérifiez que les diagrammes restent lisibles une fois dans le PDF

### Q30 : Dois-je utiliser un outil de gestion de projet ?

**R :** Ce n'est pas obligatoire pour un projet de 8 semaines, mais ça peut aider :
- **Trello** : Kanban simple
- **Notion** : Documentation et suivi
- **Google Drive** : Partage de documents
- **Git/GitHub** : Versioning (si à l'aise)

---

## ⚠️ Problèmes courants

### Q31 : Mon équipe ne travaille pas de manière équitable

**R :**
1. **Communiquez** : Organisez une réunion pour clarifier les attentes
2. **Répartissez** : Assignez des responsabilités claires à chacun
3. **Suivez** : Faites des points réguliers (1x/semaine minimum)
4. **Documentez** : Gardez une trace du travail de chacun
5. **Alertez** : Informez l'encadrant tôt en cas de problème persistant

### Q32 : Je suis bloqué et je ne sais pas comment avancer

**R :**
1. **Consultez** la documentation de la semaine concernée
2. **Regardez** l'exemple complet fourni
3. **Discutez** avec votre équipe
4. **Relisez** vos livrables précédents pour retrouver la cohérence
5. **Contactez** l'encadrant avec des questions précises

### Q33 : Mes diagrammes ne sont pas cohérents entre eux

**R :** Créez une matrice de traçabilité :
- BF → UC : Chaque BF a-t-il un UC ?
- UC → Séquence : Les acteurs sont-ils les mêmes ?
- Séquence → Classes : Les entités deviennent-elles des classes ?
- Vocabulaire : Utilisez-vous les mêmes termes partout ?

### Q34 : Je n'ai pas le temps de tout finir

**R :** Priorisez :
1. **Essentiel** : Tous les livrables obligatoires
2. **Important** : Qualité et cohérence
3. **Optionnel** : Scénarios alternatifs, diagrammes partiels

Mieux vaut un projet complet et cohérent qu'un projet incomplet avec beaucoup de détails.

---

## 📚 Ressources

### Q35 : Où trouver plus d'informations sur UML ?

**R :**
- **Spécification officielle** : UML 2.5 (OMG) - Référence complète
- **Livres** :
  - "UML 2 par la pratique" - Pascal Roques
  - "UML 2 pour les bases de données" - Christian Soutou
- **En ligne** :
  - [Cours UML](https://laurent-audibert.developpez.com/Cours-UML/)
  - [Visual Paradigm Guides](https://www.visual-paradigm.com/guide/)

### Q36 : Puis-je m'inspirer d'exemples trouvés en ligne ?

**R :** Vous pouvez vous inspirer, mais :
- ✅ Utilisez des exemples pour comprendre les concepts
- ✅ Adaptez à votre propre projet
- ❌ Ne copiez pas directement
- ❌ Ne prenez pas un projet déjà fait comme le vôtre

Votre encadrant détectera facilement un projet non original.

---

## 📧 Contact

### Q37 : Quand et comment contacter l'encadrant ?

**R :**
- **Quand** : Après avoir consulté la documentation et essayé par vous-même
- **Comment** : Email avec objet clair : "[UML L2] Question sur..."
- **Quoi** : Questions précises avec contexte
- **Délai** : Attendez 48-72h pour une réponse

### Q38 : Puis-je demander une relecture avant de rendre ?

**R :** Cela dépend de l'encadrant. Généralement :
- Vous pouvez poser des questions spécifiques
- Vous ne devez pas attendre une relecture complète
- Faites relire par vos pairs d'abord

---

**Si votre question n'est pas dans cette FAQ, consultez d'abord la documentation puis contactez votre encadrant. 📧**
