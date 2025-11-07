# Product Backlog - User Stories

## Story 1: Créer une nouvelle tâche

**As a** user,
**I need** to create a new task with a title and description,
**So that** I can organize my work and keep track of what needs to be done.

### Acceptance Criteria

#### Scenario 1: Créer une tâche avec titre et description
```gherkin
Given que je suis sur la page d'accueil
When je clique sur le bouton "Nouvelle tâche"
And je saisis un titre "Faire les courses"
And je saisis une description "Acheter du lait et du pain"
And je clique sur "Créer"
Then une nouvelle tâche doit apparaître dans la liste
And la tâche doit afficher le titre et la description
```

#### Scenario 2: Créer une tâche sans titre
```gherkin
Given que je suis sur le formulaire de création
When je laisse le titre vide
And je clique sur "Créer"
Then un message d'erreur doit s'afficher
And la tâche ne doit pas être créée
```

---

## Story 2: Marquer une tâche comme complétée

**As a** user,
**I need** to mark a task as completed,
**So that** I can track my progress and see what I've accomplished.

### Acceptance Criteria

#### Scenario 1: Marquer une tâche comme complétée
```gherkin
Given que j'ai une tâche "Faire les courses" dans ma liste
When je clique sur la case à cocher de la tâche
Then la tâche doit être marquée comme complétée
And la tâche doit apparaître avec un style différent (barré)
```

#### Scenario 2: Démarquer une tâche complétée
```gherkin
Given que j'ai une tâche marquée comme complétée
When je clique à nouveau sur la case à cocher
Then la tâche doit revenir à l'état non complété
And le style doit revenir à la normale
```

---

## Story 3: Supprimer une tâche

**As a** user,
**I need** to delete a task I no longer need,
**So that** I can keep my task list clean and relevant.

### Acceptance Criteria

#### Scenario 1: Supprimer une tâche avec confirmation
```gherkin
Given que j'ai une tâche "Faire les courses" dans ma liste
When je clique sur le bouton "Supprimer"
Then une boîte de dialogue de confirmation doit s'afficher
And je clique sur "Confirmer"
Then la tâche doit être supprimée de la liste
```

#### Scenario 2: Annuler la suppression
```gherkin
Given que la boîte de dialogue de confirmation est affichée
When je clique sur "Annuler"
Then la tâche doit rester dans la liste
```

---

## Story 4: Afficher la liste des tâches

**As a** user,
**I need** to see all my tasks in a clear list,
**So that** I can quickly view and manage all my tasks.

### Acceptance Criteria

#### Scenario 1: Afficher les tâches au chargement
```gherkin
Given que je suis sur la page d'accueil
When la page se charge
Then toutes mes tâches doivent s'afficher dans une liste
And chaque tâche doit afficher son titre et sa description
```

#### Scenario 2: Afficher un message quand il n'y a pas de tâches
```gherkin
Given que je n'ai pas de tâches
When je suis sur la page d'accueil
Then un message "Aucune tâche" doit s'afficher
```

---

## Story 5: Éditer une tâche existante

**As a** user,
**I need** to edit the title and description of an existing task,
**So that** I can update my tasks when circumstances change.

### Acceptance Criteria

#### Scenario 1: Éditer le titre d'une tâche
```gherkin
Given que j'ai une tâche "Faire les courses"
When je clique sur le bouton "Éditer"
And je modifie le titre en "Faire les courses au marché"
And je clique sur "Enregistrer"
Then la tâche doit être mise à jour avec le nouveau titre
```

#### Scenario 2: Éditer la description
```gherkin
Given que je suis en mode édition
When je modifie la description
And je clique sur "Enregistrer"
Then la description doit être mise à jour
```

---

## Story 6: Filtrer les tâches par statut

**As a** user,
**I need** to filter tasks by their status (complétées/non complétées),
**So that** I can focus on what I need to do or see what I've accomplished.

### Acceptance Criteria

#### Scenario 1: Afficher toutes les tâches
```gherkin
Given que je suis sur la page d'accueil
When je sélectionne le filtre "Toutes"
Then toutes les tâches doivent s'afficher
```

#### Scenario 2: Afficher uniquement les tâches complétées
```gherkin
Given que j'ai des tâches complétées et non complétées
When je sélectionne le filtre "Complétées"
Then seules les tâches complétées doivent s'afficher
```

#### Scenario 3: Afficher uniquement les tâches non complétées
```gherkin
Given que j'ai des tâches complétées et non complétées
When je sélectionne le filtre "À faire"
Then seules les tâches non complétées doivent s'afficher
```

---

## Story 7: Ajouter des priorités aux tâches

**As a** user,
**I need** to assign priority levels (haute/moyenne/basse) to my tasks,
**So that** I can focus on what's most important.

### Acceptance Criteria

#### Scenario 1: Assigner une priorité à une tâche
```gherkin
Given que je suis en train de créer une tâche
When je sélectionne une priorité "Haute"
And je clique sur "Créer"
Then la tâche doit être créée avec la priorité "Haute"
```

#### Scenario 2: Modifier la priorité d'une tâche
```gherkin
Given que j'ai une tâche avec priorité "Basse"
When je clique sur "Éditer"
And je change la priorité en "Haute"
And je clique sur "Enregistrer"
Then la priorité doit être mise à jour
```

---

## Story 8: Ajouter des dates d'échéance

**As a** user,
**I need** to set due dates for my tasks,
**So that** I can prioritize my work and meet deadlines.

### Acceptance Criteria

#### Scenario 1: Ajouter une date d'échéance
```gherkin
Given que je suis en train de créer une tâche
When je sélectionne une date d'échéance
And je clique sur "Créer"
Then la tâche doit afficher la date d'échéance
```

#### Scenario 2: Afficher les tâches en retard
```gherkin
Given que j'ai une tâche avec une date d'échéance dépassée
When je suis sur la page d'accueil
Then la tâche doit être affichée avec un style d'alerte (rouge)
```

---

## Technical Debt Story 9: Configurer l'environnement de développement

### Description
Mettre en place l'environnement de développement initial avec les outils et configurations nécessaires.

### Tasks
- [ ] Initialiser le projet React
- [ ] Configurer Tailwind CSS
- [ ] Configurer les outils de build
- [ ] Mettre en place le contrôle de version

---

## Technical Debt Story 10: Mettre en place les tests unitaires

### Description
Configurer le framework de test et créer les tests unitaires de base pour les composants.

### Tasks
- [ ] Installer et configurer le framework de test
- [ ] Créer les tests pour les composants principaux
- [ ] Mettre en place l'intégration continue
