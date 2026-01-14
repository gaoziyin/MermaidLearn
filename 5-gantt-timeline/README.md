# Module 5: Gantt & Timeline 🚀

> **Level: Advanced** | **Estimated Time: 3-4 hours**

## 📋 Module Overview

This module covers Gantt charts for project planning and Timeline diagrams for chronological visualization.

---

## 📖 Chapter 5.1: Gantt Charts

### Basic Gantt Chart

```mermaid
gantt
    title Project Timeline
    dateFormat YYYY-MM-DD
    
    section Planning
    Research           :a1, 2024-01-01, 7d
    Requirements       :a2, after a1, 5d
    
    section Development
    Design             :b1, after a2, 10d
    Implementation     :b2, after b1, 20d
```

### Date Formats

| Format | Example | Description |
|--------|---------|-------------|
| `YYYY-MM-DD` | 2024-01-15 | ISO date |
| `DD-MM-YYYY` | 15-01-2024 | European |

**Duration units:** `d` (days), `w` (weeks), `h` (hours)

### Task Types

```mermaid
gantt
    dateFormat YYYY-MM-DD
    
    Normal task        :a1, 2024-01-01, 10d
    Active task        :active, a2, 2024-01-05, 10d
    Done task          :done, a3, 2024-01-01, 5d
    Critical task      :crit, a4, 2024-01-15, 5d
    Milestone          :milestone, m1, 2024-01-20, 0d
```

### Dependencies

```mermaid
gantt
    dateFormat YYYY-MM-DD
    
    Task A        :a, 2024-01-01, 10d
    Task B        :b, after a, 5d
    Task C        :c, after a b, 5d
```

### Exclusions

```
excludes weekends
excludes 2024-01-15
```

---

## 📖 Chapter 5.2: Timeline Diagrams

### Basic Timeline

```mermaid
timeline
    title History of Web Development
    1991 : World Wide Web invented
    1995 : JavaScript created
    2010 : HTML5 released
```

### Timeline with Sections

```mermaid
timeline
    title Company History
    
    section Startup Phase
        2018 : Company founded
        2019 : Seed funding
    
    section Growth Phase
        2020 : Series A funding
        2021 : International expansion
```

---

## 🏋️ Exercises

1. Create a 2-week sprint Gantt chart with dependencies
2. Plan a product launch over 3 months
3. Create a timeline of your favorite programming language
4. Map a personal project timeline with milestones

```mermaid
gantt
    title Tachi project milestone
    dateFormat YYYY-MM-DD
    section Working
        Project design : done, a1, 2016-1-14, 7d
        Coding : active, a2, after a1, 90d
        Testing: a3, after a2, 10d
        Publish: milestone, a4, after a3, 1d
```


---

## ✅ Module Checklist

- [ ] Gantt charts with date formats
- [ ] Task types and dependencies
- [ ] Timeline with sections
- [ ] Completed exercises

> **Next:** [Module 6: Git Graph & Mindmaps](../6-git-mindmaps/README.md) →
