# GitHub Project Setup Guide

## Instructions Complètes pour le Projet Final Agile

Ce guide fournit les instructions étape par étape pour configurer votre projet GitHub avec toutes les exigences du projet final.

---

## Étape 1 : Créer le Dépôt GitHub

1. Allez sur [github.com](https://github.com) et connectez-vous
2. Cliquez sur le bouton **"New"** pour créer un nouveau dépôt
3. Nommez le dépôt : **`projet-final-agile`**
4. Ajoutez une description : **"Agile Project Management with Kanban Board"**
5. Sélectionnez **"Public"** pour que le tableau soit visible
6. Cliquez sur **"Create repository"**

---

## Étape 2 : Pousser le Code Local vers GitHub

```bash
cd /home/ubuntu/projet-final-agile

# Ajouter le dépôt distant
git remote add origin https://github.com/YOUR_USERNAME/projet-final-agile.git

# Renommer la branche principale si nécessaire
git branch -M main

# Pousser le code
git push -u origin main
```

Remplacez `YOUR_USERNAME` par votre nom d'utilisateur GitHub.

---

## Étape 3 : Configurer les Labels

Allez dans **Settings → Labels** et créez les labels suivants :

### Labels de Type
| Label | Couleur | Description |
|-------|---------|-------------|
| `story` | `#0075ca` | User story |
| `feature` | `#7cb342` | Nouvelle fonctionnalité |
| `bug` | `#d73a49` | Correction de bug |
| `technical-debt` | `#e11d21` | Dette technique |

### Labels de Domaine
| Label | Couleur | Description |
|-------|---------|-------------|
| `backlog` | `#cccccc` | Product backlog |
| `infrastructure` | `#9e42f5` | Infrastructure/DevOps |
| `testing` | `#ffa500` | Tests |
| `documentation` | `#ffff00` | Documentation |

### Labels de Priorité
| Label | Couleur | Description |
|-------|---------|-------------|
| `high-priority` | `#d73a49` | Priorité haute |
| `medium-priority` | `#ffa500` | Priorité moyenne |
| `low-priority` | `#ffff00` | Priorité basse |

---

## Étape 4 : Créer les Issues (Stories)

### Méthode 1 : Via l'Interface GitHub

1. Allez dans l'onglet **"Issues"**
2. Cliquez sur **"New issue"**
3. Utilisez le template **"User Story"** (créé automatiquement)
4. Remplissez les champs :
   - **Title** : `[STORY] Créer une nouvelle tâche`
   - **Body** : Copiez le contenu du fichier `STORIES.md`
   - **Labels** : Sélectionnez `story`, `feature`, `backlog`
   - **Assignees** : Assignez-vous à vous-même
5. Cliquez sur **"Submit new issue"**

Répétez pour les 10 stories du fichier `STORIES.md`.

### Méthode 2 : Via Script GitHub CLI

```bash
# Installer GitHub CLI si nécessaire
# brew install gh (macOS) ou apt install gh (Linux)

# Authentifier
gh auth login

# Créer les issues
gh issue create --title "[STORY] Créer une nouvelle tâche" \
  --body "$(cat STORIES.md | head -50)" \
  --label "story,feature,backlog"
```

---

## Étape 5 : Créer le Milestone (Sprint)

1. Allez dans **Issues → Milestones**
2. Cliquez sur **"New milestone"**
3. Remplissez les informations :
   - **Title** : `Sprint 1 - Task Management MVP`
   - **Description** : `Implement core task management features with priority and due date support`
   - **Due date** : Sélectionnez une date 2 semaines à partir d'aujourd'hui
4. Cliquez sur **"Create milestone"**

---

## Étape 6 : Assigner les Stories au Sprint

Pour chaque issue créée :

1. Ouvrez l'issue
2. À droite, sous **"Milestone"**, sélectionnez **"Sprint 1 - Task Management MVP"**
3. Sous **"Assignees"**, assignez-vous à vous-même
4. Sous **"Labels"**, ajoutez les labels appropriés

---

## Étape 7 : Ajouter les Estimations

GitHub n'a pas de champ natif pour les estimations. Utilisez l'une des méthodes suivantes :

### Méthode 1 : Dans le Titre de l'Issue
```
[STORY] Créer une nouvelle tâche (5 pts)
```

### Méthode 2 : Dans la Description
Ajoutez une section "Estimate" :
```markdown
## Estimate
5 story points
```

### Méthode 3 : Utiliser les Projets GitHub

1. Allez dans **Projects**
2. Cliquez sur **"New project"**
3. Sélectionnez **"Table"** comme template
4. Nommez-le **"Sprint 1 Planning"**
5. Ajoutez une colonne **"Estimate"** de type "Number"
6. Ajoutez les stories et remplissez les estimations

---

## Étape 8 : Configurer le Tableau Kanban

### Via GitHub Projects (Recommandé)

1. Allez dans **Projects**
2. Cliquez sur **"New project"**
3. Sélectionnez **"Board"** comme template
4. Nommez-le **"Sprint 1 Kanban"**
5. Configurez les colonnes :
   - Backlog
   - To Do
   - In Progress
   - In Review
   - Done

6. Ajoutez les issues au projet
7. Déplacez-les entre les colonnes selon leur statut

### Configuration des Colonnes

| Colonne | Limite WIP | Critères |
|---------|-----------|----------|
| Backlog | Illimitée | Stories non commencées |
| To Do | 15 | Stories du sprint, non commencées |
| In Progress | 5 | Stories en cours, assignées |
| In Review | 5 | Stories complétées, en révision |
| Done | Illimitée | Stories complétées et testées |

---

## Étape 9 : Créer le Burndown Chart

Le burndown chart a déjà été créé et sauvegardé dans le dépôt : `burndown-chart.png`

Pour l'afficher dans votre README :

1. Ouvrez **README.md**
2. Ajoutez la section suivante :

```markdown
## Sprint 1 - Burndown Chart

![Burndown Chart](burndown-chart.png)

### Interprétation
- **Ligne bleue (pointillée)** : Burndown planifié
- **Ligne verte (solide)** : Burndown réel
- **Zone verte** : Indique si l'équipe est en avance
```

---

## Étape 10 : Labéliser les Stories Techniques comme "Technical Debt"

Pour les stories 9 et 10 :

1. Ouvrez l'issue **"Configurer l'environnement de développement"**
2. Sous **"Labels"**, ajoutez :
   - `technical-debt`
   - `infrastructure`

3. Ouvrez l'issue **"Mettre en place les tests unitaires"**
4. Sous **"Labels"**, ajoutez :
   - `technical-debt`
   - `testing`

---

## Résumé des Fichiers Créés

| Fichier | Description |
|---------|-------------|
| `.github/ISSUE_TEMPLATE/user-story.md` | Template pour les user stories |
| `.github/ISSUE_TEMPLATE/bug-report.md` | Template pour les bug reports |
| `STORIES.md` | Toutes les user stories avec critères Gherkin |
| `SPRINT_PLANNING.md` | Planification du sprint avec estimations |
| `KANBAN_BOARD.md` | Configuration du tableau Kanban |
| `burndown-chart.png` | Graphique de burndown du sprint |
| `GITHUB_SETUP_GUIDE.md` | Ce guide (instructions complètes) |

---

## Checklist de Vérification

- [ ] Dépôt GitHub créé et code poussé
- [ ] Labels créés dans GitHub
- [ ] 10 issues créées avec les templates
- [ ] Milestone "Sprint 1" créé
- [ ] Toutes les issues assignées au milestone
- [ ] Toutes les issues assignées à vous-même
- [ ] Labels appropriés ajoutés à chaque issue
- [ ] Estimations ajoutées (dans le titre ou description)
- [ ] Tableau Kanban créé avec 5 colonnes
- [ ] Stories 9 et 10 labélisées comme "technical-debt"
- [ ] Burndown chart visible dans le README
- [ ] Toutes les stories déplacées en "In Progress"

---

## Liens Utiles

- [GitHub Issues Documentation](https://docs.github.com/en/issues)
- [GitHub Projects Documentation](https://docs.github.com/en/issues/planning-and-tracking-with-projects)
- [GitHub Milestones Documentation](https://docs.github.com/en/issues/using-labels-and-milestones-to-track-work)
- [Gherkin Syntax Guide](https://cucumber.io/docs/gherkin/)
- [Agile User Stories Best Practices](https://www.atlassian.com/agile/user-stories)

---

## Support

Pour toute question ou problème :

1. Consultez la documentation GitHub officielle
2. Vérifiez que tous les fichiers sont correctement commités
3. Assurez-vous que le dépôt est public pour que le tableau soit visible

---

**Date de création** : 2025-11-07
**Version** : 1.0
**Auteur** : Manus AI Assistant
