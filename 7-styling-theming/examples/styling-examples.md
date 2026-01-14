# Styling & Theming Examples 🎨

---

## Theme Examples

### Default Theme

```mermaid
%%{init: {'theme': 'default'}}%%
graph LR
    A[Start] --> B{Decision}
    B -->|Yes| C[Action A]
    B -->|No| D[Action B]
    C --> E[End]
    D --> E
```

### Dark Theme

```mermaid
%%{init: {'theme': 'dark'}}%%
graph LR
    A[Start] --> B{Decision}
    B -->|Yes| C[Action A]
    B -->|No| D[Action B]
    C --> E[End]
    D --> E
```

### Forest Theme

```mermaid
%%{init: {'theme': 'forest'}}%%
graph LR
    A[Start] --> B{Decision}
    B -->|Yes| C[Action A]
    B -->|No| D[Action B]
    C --> E[End]
    D --> E
```

### Neutral Theme

```mermaid
%%{init: {'theme': 'neutral'}}%%
graph LR
    A[Start] --> B{Decision}
    B -->|Yes| C[Action A]
    B -->|No| D[Action B]
    C --> E[End]
    D --> E
```

---

## Custom Theme Variables

### Blue Corporate

```mermaid
%%{init: {
    'theme': 'base',
    'themeVariables': {
        'primaryColor': '#1e3a5f',
        'primaryTextColor': '#ffffff',
        'primaryBorderColor': '#0d1b2a',
        'lineColor': '#3d5a80',
        'secondaryColor': '#98c1d9',
        'tertiaryColor': '#e0fbfc'
    }
}}%%
graph TD
    A[Primary] --> B[Secondary]
    B --> C[Tertiary]
    C --> D{Decision}
    D --> E[End]
```

### Warm Sunset

```mermaid
%%{init: {
    'theme': 'base',
    'themeVariables': {
        'primaryColor': '#e63946',
        'primaryTextColor': '#ffffff',
        'primaryBorderColor': '#9d0208',
        'lineColor': '#f4a261',
        'secondaryColor': '#f4a261',
        'tertiaryColor': '#ffecd2'
    }
}}%%
graph TD
    A[Start] --> B[Process]
    B --> C{Check}
    C --> D[Complete]
```

### Nature Green

```mermaid
%%{init: {
    'theme': 'base',
    'themeVariables': {
        'primaryColor': '#2d6a4f',
        'primaryTextColor': '#ffffff',
        'primaryBorderColor': '#1b4332',
        'lineColor': '#40916c',
        'secondaryColor': '#74c69d',
        'tertiaryColor': '#d8f3dc'
    }
}}%%
graph LR
    A[🌱 Start] --> B[🌿 Grow]
    B --> C[🌳 Mature]
    C --> D[🍂 Complete]
```

---

## ClassDef Examples

### Status Colors

```mermaid
graph TD
    A[Pending]:::pending --> B{Validate}:::check
    B -->|Valid| C[Success]:::success
    B -->|Invalid| D[Error]:::error
    C --> E[Done]:::done
    D --> F[Retry]:::warning
    F --> A
    
    classDef pending fill:#e3f2fd,stroke:#1976d2,color:#1565c0
    classDef check fill:#fff3e0,stroke:#f57c00,color:#e65100
    classDef success fill:#e8f5e9,stroke:#4caf50,color:#2e7d32
    classDef error fill:#ffebee,stroke:#f44336,color:#c62828
    classDef warning fill:#fff8e1,stroke:#ffc107,color:#ff8f00
    classDef done fill:#f3e5f5,stroke:#9c27b0,color:#7b1fa2
```

### Semantic Classes

```mermaid
graph TD
    subgraph Input
        A[User Data]:::input
    end
    subgraph Processing
        B[Validate]:::process
        C[Transform]:::process
    end
    subgraph Storage
        D[(Database)]:::storage
    end
    subgraph Output
        E[Response]:::output
    end
    
    A --> B --> C --> D --> E
    
    classDef input fill:#e1f5fe,stroke:#0288d1,stroke-width:2px
    classDef process fill:#f3e5f5,stroke:#7b1fa2,stroke-width:2px
    classDef storage fill:#fff3e0,stroke:#f57c00,stroke-width:2px
    classDef output fill:#e8f5e9,stroke:#388e3c,stroke-width:2px
```

---

## Link Styling

```mermaid
graph LR
    A --> B --> C --> D --> E
    
    linkStyle 0 stroke:#e53935,stroke-width:3px
    linkStyle 1 stroke:#fb8c00,stroke-width:3px
    linkStyle 2 stroke:#43a047,stroke-width:3px
    linkStyle 3 stroke:#1e88e5,stroke-width:3px
```

### Dashed Links

```mermaid
graph LR
    A[Solid] --> B[Still Solid]
    B -.-> C[Dashed]
    C --> D[Back to Solid]
    
    linkStyle 0 stroke:#333,stroke-width:2px
    linkStyle 1 stroke:#999,stroke-width:2px,stroke-dasharray:5,5
    linkStyle 2 stroke:#333,stroke-width:2px
```

---

## Sequence Diagram Theming

```mermaid
%%{init: {
    'theme': 'base',
    'themeVariables': {
        'actorBkg': '#1e3a5f',
        'actorTextColor': '#ffffff',
        'actorBorder': '#0d1b2a',
        'signalColor': '#3d5a80',
        'signalTextColor': '#1e3a5f'
    }
}}%%
sequenceDiagram
    participant A as Alice
    participant B as Bob
    A->>B: Hello!
    B-->>A: Hi there!
```

---

## Flowchart Configuration

```mermaid
%%{init: {
    'flowchart': {
        'curve': 'basis',
        'padding': 20,
        'nodeSpacing': 50,
        'rankSpacing': 70
    }
}}%%
graph TD
    A[Start] --> B[Step 1]
    B --> C[Step 2]
    C --> D[Step 3]
    D --> E[End]
```

---

## Complete Styled Dashboard

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {
    'primaryColor': '#667eea',
    'primaryTextColor': '#ffffff',
    'primaryBorderColor': '#764ba2',
    'lineColor': '#667eea',
    'secondaryColor': '#f093fb',
    'tertiaryColor': '#f5f7fa'
}}}%%
graph TB
    subgraph Dashboard["📊 Analytics Dashboard"]
        direction TB
        A[📈 Revenue]:::metric
        B[👥 Users]:::metric
        C[📦 Orders]:::metric
    end
    
    subgraph Data["💾 Data Layer"]
        D[(PostgreSQL)]:::db
        E[(Redis)]:::cache
    end
    
    subgraph Services["⚙️ Services"]
        F[API Gateway]:::service
        G[Auth Service]:::service
        H[Analytics]:::service
    end
    
    Dashboard --> Services
    Services --> Data
    
    classDef metric fill:#667eea,stroke:#764ba2,color:#fff
    classDef db fill:#4db6ac,stroke:#00897b,color:#fff
    classDef cache fill:#ff8a65,stroke:#e64a19,color:#fff
    classDef service fill:#ba68c8,stroke:#8e24aa,color:#fff
```

---

## Quick Reference

### Theme Variables
| Variable | Description |
|----------|-------------|
| `primaryColor` | Main node fill |
| `primaryTextColor` | Main node text |
| `primaryBorderColor` | Main node border |
| `lineColor` | Connection lines |
| `secondaryColor` | Secondary elements |
| `tertiaryColor` | Background elements |

### Style Properties
| Property | Example |
|----------|---------|
| `fill` | `fill:#ff0000` |
| `stroke` | `stroke:#333` |
| `stroke-width` | `stroke-width:2px` |
| `color` | `color:#fff` |
| `stroke-dasharray` | `stroke-dasharray:5,5` |
