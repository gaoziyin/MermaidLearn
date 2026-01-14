# Git Graph, Mindmap & Chart Examples 📊

---

## Git Graph Examples

### 1. Simple Branching

```mermaid
gitGraph
    commit
    commit
    branch develop
    commit
    commit
    checkout main
    merge develop
    commit
```

### 2. Feature Branch Workflow

```mermaid
gitGraph
    commit id: "init"
    commit id: "setup"
    branch develop
    commit id: "dev-1"
    branch feature/login
    commit id: "login-1"
    commit id: "login-2"
    checkout develop
    merge feature/login id: "merge-login"
    branch feature/dashboard
    commit id: "dash-1"
    checkout develop
    merge feature/dashboard
    checkout main
    merge develop tag: "v1.0"
```

### 3. Git Flow

```mermaid
gitGraph
    commit id: "initial" tag: "v0.1"
    branch develop
    commit id: "dev-setup"
    
    branch feature/auth
    commit id: "auth-1"
    commit id: "auth-2"
    checkout develop
    merge feature/auth
    
    branch release/1.0
    commit id: "bump-version"
    commit id: "fix-typo"
    checkout main
    merge release/1.0 tag: "v1.0"
    checkout develop
    merge release/1.0
    
    branch hotfix/1.0.1
    checkout hotfix/1.0.1
    commit id: "critical-fix"
    checkout main
    merge hotfix/1.0.1 tag: "v1.0.1"
    checkout develop
    merge hotfix/1.0.1
```

### 4. Release Tags

```mermaid
gitGraph
    commit id: "A" tag: "v0.1.0"
    commit id: "B"
    commit id: "C" tag: "v0.2.0"
    branch feature
    commit id: "D"
    commit id: "E"
    checkout main
    merge feature id: "F"
    commit id: "G" tag: "v1.0.0"
```

---

## Mindmap Examples

### 1. Web Development

```mermaid
mindmap
    root((Web Dev))
        Frontend
            HTML
                Semantic Tags
                Forms
                Accessibility
            CSS
                Flexbox
                Grid
                Animations
            JavaScript
                ES6+
                DOM
                Frameworks
                    React
                    Vue
                    Angular
        Backend
            Languages
                Node.js
                Python
                Java
            Databases
                SQL
                    PostgreSQL
                    MySQL
                NoSQL
                    MongoDB
                    Redis
            APIs
                REST
                GraphQL
        DevOps
            Version Control
                Git
                GitHub
            CI/CD
                GitHub Actions
                Jenkins
            Cloud
                AWS
                Azure
                GCP
```

### 2. Project Planning

```mermaid
mindmap
    root((Project X))
        Goals
            Increase revenue
            Improve UX
            Scale platform
        Timeline
            Q1: Research
            Q2: Development
            Q3: Testing
            Q4: Launch
        Team
            Product
            Engineering
            Design
            QA
        Risks
            Technical debt
            Resource constraints
            Market changes
```

### 3. Learning Path

```mermaid
mindmap
    root((Mermaid))
        Basics
            Flowcharts
            Direction
            Shapes
            Links
        Intermediate
            Sequence
            Class
            ER
            State
        Advanced
            Gantt
            Timeline
            Git Graph
            Mindmaps
        Master
            Styling
            Themes
            Integration
            Best Practices
```

---

## Pie Chart Examples

### 1. Time Distribution

```mermaid
pie title Weekly Time Distribution
    "Coding" : 40
    "Meetings" : 15
    "Code Review" : 10
    "Learning" : 10
    "Documentation" : 10
    "Other" : 15
```

### 2. Tech Stack Usage

```mermaid
pie showData
    title Frontend Frameworks Market Share
    "React" : 42
    "Vue" : 23
    "Angular" : 18
    "Svelte" : 8
    "Others" : 9
```

### 3. Budget Allocation

```mermaid
pie title Project Budget
    "Development" : 50
    "Infrastructure" : 20
    "Marketing" : 15
    "Support" : 10
    "Miscellaneous" : 5
```

---

## Quadrant Chart Examples

### 1. Eisenhower Matrix

```mermaid
quadrantChart
    title Eisenhower Matrix
    x-axis Urgent --> Not Urgent
    y-axis Not Important --> Important
    quadrant-1 Schedule
    quadrant-2 Do First
    quadrant-3 Delegate
    quadrant-4 Eliminate
    
    Project deadline: [0.2, 0.9]
    Email replies: [0.3, 0.3]
    Team meeting: [0.4, 0.6]
    Learning: [0.8, 0.8]
    Social media: [0.9, 0.2]
```

### 2. Skill Assessment

```mermaid
quadrantChart
    title Developer Skills
    x-axis Low Interest --> High Interest
    y-axis Low Skill --> High Skill
    quadrant-1 Focus
    quadrant-2 Strength
    quadrant-3 Avoid
    quadrant-4 Learn
    
    JavaScript: [0.9, 0.85]
    Python: [0.7, 0.6]
    Rust: [0.8, 0.3]
    PHP: [0.2, 0.5]
    Go: [0.6, 0.4]
    TypeScript: [0.85, 0.75]
```

### 3. Feature Prioritization

```mermaid
quadrantChart
    title Feature Priority Matrix
    x-axis Low Effort --> High Effort
    y-axis Low Impact --> High Impact
    quadrant-1 Plan Carefully
    quadrant-2 Quick Wins
    quadrant-3 Avoid
    quadrant-4 Strategic Projects
    
    Dark Mode: [0.2, 0.3]
    SSO: [0.7, 0.9]
    Mobile App: [0.9, 0.8]
    Bug Fix: [0.1, 0.5]
    Dashboard: [0.5, 0.7]
```

---

## Quick Reference

### Git Graph
| Command | Description |
|---------|-------------|
| `commit` | Add commit |
| `branch name` | Create branch |
| `checkout name` | Switch branch |
| `merge name` | Merge branch |
| `id: "text"` | Commit message |
| `tag: "v1.0"` | Add tag |

### Mindmap
| Element | Description |
|---------|-------------|
| `root((text))` | Circle root |
| `root[text]` | Square root |
| Indentation | Create hierarchy |

### Pie Chart
| Element | Description |
|---------|-------------|
| `pie` | Declare chart |
| `title` | Chart title |
| `showData` | Show values |
| `"Label" : value` | Data entry |
