# Node Shapes Reference 🔷

Complete reference for all Mermaid flowchart node shapes.

---

## All Node Shapes

```mermaid
graph TD
    subgraph Basic Shapes
        A[Rectangle]
        B(Rounded Rectangle)
        C([Stadium])
        D[[Subroutine]]
    end
    
    subgraph Data Shapes
        E[(Cylinder/Database)]
        F[/Parallelogram/]
        G[\Alt Parallelogram\]
    end
    
    subgraph Decision Shapes
        H{Diamond/Rhombus}
        I{{Hexagon}}
    end
    
    subgraph Connector Shapes
        J((Circle))
        K(((Double Circle)))
        L>Asymmetric/Flag]
    end
    
    subgraph Trapezoid Shapes
        M[/Trapezoid\]
        N[\Alt Trapezoid/]
    end
```

---

## Shape Syntax Quick Reference

| Shape | Syntax | Example |
|-------|--------|---------|
| Rectangle | `[text]` | `A[Process]` |
| Rounded | `(text)` | `A(Start)` |
| Stadium | `([text])` | `A([Terminal])` |
| Subroutine | `[[text]]` | `A[[Function]]` |
| Database | `[(text)]` | `A[(MySQL)]` |
| Circle | `((text))` | `A((Hub))` |
| Double Circle | `(((text)))` | `A(((Special)))` |
| Diamond | `{text}` | `A{Decision}` |
| Hexagon | `{{text}}` | `A{{Prepare}}` |
| Flag | `>text]` | `A>Note]` |
| Parallelogram | `[/text/]` | `A[/Input/]` |
| Alt Parallelogram | `[\text\]` | `A[\Output\]` |
| Trapezoid | `[/text\]` | `A[/Manual\]` |
| Alt Trapezoid | `[\text/]` | `A[\Manual/]` |

---

## When to Use Each Shape

### Rectangle `[text]`
**Use for:** General processes, actions, operations
```mermaid
graph LR
    A[Calculate Total] --> B[Apply Discount] --> C[Generate Invoice]
```

### Rounded Rectangle `(text)`
**Use for:** Start/End points, terminals
```mermaid
graph LR
    A(Start) --> B[Process] --> C(End)
```

### Stadium `([text])`
**Use for:** Terminal points, entry/exit
```mermaid
graph LR
    A([Begin]) --> B[Work] --> C([Finish])
```

### Diamond `{text}`
**Use for:** Decisions, conditions, branching
```mermaid
graph TD
    A{Is Valid?} -->|Yes| B[Continue]
    A -->|No| C[Stop]
```

### Database/Cylinder `[(text)]`
**Use for:** Databases, data stores
```mermaid
graph LR
    A[App] --> B[(PostgreSQL)]
    A --> C[(Redis)]
```

### Parallelogram `[/text/]`
**Use for:** Input/Output operations
```mermaid
graph LR
    A[/User Input/] --> B[Process] --> C[/Display Output/]
```

### Hexagon `{{text}}`
**Use for:** Preparation, initialization
```mermaid
graph LR
    A{{Initialize}} --> B[Execute] --> C{{Cleanup}}
```

### Circle `((text))`
**Use for:** Connectors, junctions
```mermaid
graph TD
    A --> B((1))
    B --> C
    B --> D
```

### Subroutine `[[text]]`
**Use for:** External processes, functions
```mermaid
graph LR
    A[Main] --> B[[calculateTax]]
    B --> C[[formatCurrency]]
```

---

## Combining Shapes

```mermaid
graph TD
    A([Start]) --> B{{Initialize}}
    B --> C[/Get Input/]
    C --> D{Valid?}
    D -->|No| E>Error]
    E --> C
    D -->|Yes| F[[Process]]
    F --> G[(Save to DB)]
    G --> H[/Show Result/]
    H --> I([End])
```
