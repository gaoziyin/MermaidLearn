# Module 6: Git Graph & Mindmaps 🚀

> **Level: Advanced** | **Estimated Time: 2-3 hours**

## 📋 Module Overview

This module covers Git graphs for version control visualization, Mindmaps for brainstorming, Quadrant charts, and Pie charts.

---

## 📖 Chapter 6.1: Git Graphs

### Basic Git Graph

```mermaid
gitGraph
    commit
    commit
    branch develop
    checkout develop
    commit
    commit
    checkout main
    merge develop
    commit
```

### Commits with IDs and Messages

```mermaid
gitGraph
    commit id: "init"
    commit id: "feat-1" tag: "v0.1"
    branch feature
    commit id: "wip"
    commit id: "done"
    checkout main
    merge feature id: "merge-feat"
    commit id: "release" tag: "v1.0"
```

### Branching Strategies

```mermaid
gitGraph
    commit id: "initial"
    branch develop
    commit id: "dev-1"
    branch feature/login
    commit id: "login-1"
    commit id: "login-2"
    checkout develop
    merge feature/login
    branch feature/api
    commit id: "api-1"
    checkout develop
    merge feature/api
    checkout main
    merge develop tag: "v1.0"
```

### Cherry-Pick

```mermaid
gitGraph
    commit id: "A"
    commit id: "B"
    branch hotfix
    commit id: "fix-1"
    checkout main
    cherry-pick id: "fix-1"
    commit id: "C"
```

### Branch Ordering

```mermaid
%%{init: { 'gitGraph': {'mainBranchOrder': 2}} }%%
gitGraph
    commit
    branch feature order: 1
    commit
    branch develop order: 3
    commit
    checkout main
    commit
```

---

## 📖 Chapter 6.2: Mindmaps

### Basic Mindmap

```mermaid
mindmap
    root((Central Topic))
        Branch 1
            Leaf 1.1
            Leaf 1.2
        Branch 2
            Leaf 2.1
            Leaf 2.2
        Branch 3
            Leaf 3.1
```

### Node Shapes

```mermaid
mindmap
    root((Circle))
        (Rounded)
            [Square]
        ))Cloud((
            {{Hexagon}}
```

### Web Development Mindmap

```mermaid
mindmap
    root((Web Dev))
        Frontend
            HTML
            CSS
            JavaScript
                React
                Vue
                Angular
        Backend
            Node.js
            Python
            Java
        Database
            SQL
                PostgreSQL
                MySQL
            NoSQL
                MongoDB
                Redis
        DevOps
            Docker
            CI/CD
            Cloud
```

---

## 📖 Chapter 6.3: Quadrant Charts

```mermaid
quadrantChart
    title Skill Assessment
    x-axis Low Priority --> High Priority
    y-axis Low Skill --> High Skill
    quadrant-1 Develop
    quadrant-2 Expert
    quadrant-3 Ignore
    quadrant-4 Learn
    JavaScript: [0.8, 0.9]
    Python: [0.6, 0.7]
    Rust: [0.3, 0.2]
    Go: [0.7, 0.4]
```

---

## 📖 Chapter 6.4: Pie Charts

```mermaid
pie title Time Distribution
    "Coding" : 40
    "Meetings" : 20
    "Learning" : 15
    "Review" : 15
    "Other" : 10
```

### With Show Data

```mermaid
pie showData
    title Tech Stack Usage
    "React" : 45
    "Vue" : 30
    "Angular" : 25
```

---

## 🏋️ Exercises

1. Create a Git-flow branching model diagram
2. Create a mindmap for learning a new technology
3. Plot a skill priority matrix using quadrant chart
4. Show your weekly time distribution as a pie chart


```mermaid
pie title Programming language of the year
    "Python 32%" : 32
    "C 10% " : 10
    "Java 8%" : 8
    "C# 8%" : 8
    "Javascript 2%": 2
    "Other 40%": 40
```
---

## ✅ Module Checklist

- [ ] Git graphs with branches and merges
- [ ] Mindmaps with hierarchy
- [ ] Quadrant charts
- [ ] Pie charts
- [ ] Completed exercises

> **Next:** [Module 7: Styling & Theming](../7-styling-theming/README.md) →
