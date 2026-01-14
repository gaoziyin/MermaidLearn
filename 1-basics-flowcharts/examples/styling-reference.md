# Styling Reference 🎨

Complete guide to styling Mermaid flowcharts.

---

## ClassDef Styling

Define reusable style classes:

```mermaid
graph LR
    A[Default]:::default
    B[Primary]:::primary
    C[Success]:::success
    D[Warning]:::warning
    E[Danger]:::danger
    
    A --> B --> C --> D --> E
    
    classDef default fill:#f9f9f9,stroke:#333,stroke-width:1px
    classDef primary fill:#4A90D9,stroke:#2E5C8A,color:#fff
    classDef success fill:#90EE90,stroke:#228B22,color:#000
    classDef warning fill:#FFD700,stroke:#FFA500,color:#000
    classDef danger fill:#FF6B6B,stroke:#DC143C,color:#fff
```

---

## Style Properties

| Property | Description | Example |
|----------|-------------|---------|
| `fill` | Background color | `fill:#ff0000` |
| `stroke` | Border color | `stroke:#333` |
| `stroke-width` | Border thickness | `stroke-width:2px` |
| `color` | Text color | `color:#fff` |
| `stroke-dasharray` | Dashed border | `stroke-dasharray:5,5` |
| `opacity` | Transparency | `opacity:0.8` |

---

## Inline Styling

Apply styles to individual nodes:

```mermaid
graph LR
    A[Node A]
    B[Node B]
    C[Node C]
    
    A --> B --> C
    
    style A fill:#f9f,stroke:#333,stroke-width:4px
    style B fill:#bbf,stroke:#333,stroke-width:2px
    style C fill:#9f9,stroke:#333,stroke-width:2px,stroke-dasharray:5,5
```

---

## Link Styling

Style connections between nodes:

```mermaid
graph LR
    A --> B --> C --> D
    
    linkStyle 0 stroke:#ff0000,stroke-width:3px
    linkStyle 1 stroke:#00ff00,stroke-width:3px
    linkStyle 2 stroke:#0000ff,stroke-width:3px,stroke-dasharray:5,5
```

**Note:** Link indices start at 0 and follow the order of definition.

---

## Applying Classes to Multiple Nodes

```mermaid
graph TD
    A[Start]:::start
    B[Step 1]:::process
    C[Step 2]:::process
    D[Step 3]:::process
    E[End]:::end
    
    A --> B --> C --> D --> E
    
    classDef start fill:#90EE90,stroke:#228B22
    classDef process fill:#87CEEB,stroke:#4169E1
    classDef end fill:#DDA0DD,stroke:#9370DB
```

Or apply to multiple nodes at once:

```
class B,C,D process
```

---

## Color Palettes

### Professional Blue

```mermaid
graph LR
    A[Primary]:::p1
    B[Secondary]:::p2
    C[Tertiary]:::p3
    D[Accent]:::p4
    
    A --> B --> C --> D
    
    classDef p1 fill:#1e3a5f,stroke:#0d1b2a,color:#fff
    classDef p2 fill:#3d5a80,stroke:#1e3a5f,color:#fff
    classDef p3 fill:#98c1d9,stroke:#3d5a80,color:#000
    classDef p4 fill:#e0fbfc,stroke:#98c1d9,color:#000
```

### Nature Green

```mermaid
graph LR
    A[Dark]:::g1
    B[Medium]:::g2
    C[Light]:::g3
    D[Pale]:::g4
    
    A --> B --> C --> D
    
    classDef g1 fill:#1b4332,stroke:#081c15,color:#fff
    classDef g2 fill:#2d6a4f,stroke:#1b4332,color:#fff
    classDef g3 fill:#52b788,stroke:#2d6a4f,color:#000
    classDef g4 fill:#d8f3dc,stroke:#52b788,color:#000
```

### Warm Sunset

```mermaid
graph LR
    A[Red]:::w1
    B[Orange]:::w2
    C[Yellow]:::w3
    D[Pink]:::w4
    
    A --> B --> C --> D
    
    classDef w1 fill:#9d0208,stroke:#6a040f,color:#fff
    classDef w2 fill:#dc2f02,stroke:#9d0208,color:#fff
    classDef w3 fill:#ffba08,stroke:#dc2f02,color:#000
    classDef w4 fill:#faa307,stroke:#ffba08,color:#000
```

---

## Subgraph Styling

```mermaid
graph TB
    subgraph sg1 [Styled Subgraph]
        A --> B
    end
    subgraph sg2 [Another Subgraph]
        C --> D
    end
    
    B --> C
    
    style sg1 fill:#e1f5fe,stroke:#01579b
    style sg2 fill:#fff3e0,stroke:#e65100
```

---

## Dark Theme Example

```mermaid
%%{init: {'theme': 'dark'}}%%
graph LR
    A[Start] --> B{Decision}
    B -->|Yes| C[Action A]
    B -->|No| D[Action B]
    C --> E[End]
    D --> E
```

---

## Complete Styling Example

```mermaid
graph TD
    A([🚀 Start]):::start --> B[Initialize]:::step
    B --> C{Config Valid?}:::decision
    C -->|No| D[⚠️ Load Defaults]:::warning
    D --> B
    C -->|Yes| E[Process Data]:::step
    E --> F{Success?}:::decision
    F -->|No| G[❌ Log Error]:::error
    G --> H[Retry Logic]:::step
    H --> E
    F -->|Yes| I[Save Results]:::step
    I --> J[(Database)]:::database
    J --> K([✅ Complete]):::success
    
    classDef start fill:#a8e6cf,stroke:#3d9970,stroke-width:2px
    classDef step fill:#dfe6e9,stroke:#636e72,stroke-width:1px
    classDef decision fill:#ffeaa7,stroke:#fdcb6e,stroke-width:2px
    classDef warning fill:#fab1a0,stroke:#e17055,stroke-width:1px
    classDef error fill:#ff7675,stroke:#d63031,stroke-width:2px,color:#fff
    classDef database fill:#74b9ff,stroke:#0984e3,stroke-width:2px
    classDef success fill:#55efc4,stroke:#00b894,stroke-width:2px
    
    linkStyle 0,1,4,7,8 stroke:#2d3436,stroke-width:2px
    linkStyle 2,3 stroke:#e17055,stroke-width:2px
    linkStyle 5,6 stroke:#d63031,stroke-width:2px
```
