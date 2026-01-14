# Flowchart Examples 📊

A collection of ready-to-use flowchart examples.

---

## 1. Basic Flow

```mermaid
graph LR
    A[Start] --> B[Process] --> C[End]
```

---

## 2. Decision Flow

```mermaid
graph TD
    A[Start] --> B{Condition?}
    B -->|Yes| C[Action A]
    B -->|No| D[Action B]
    C --> E[End]
    D --> E
```

---

## 3. Loop Flow

```mermaid
graph TD
    A[Start] --> B[Initialize]
    B --> C{Condition Met?}
    C -->|No| D[Process]
    D --> E[Increment]
    E --> C
    C -->|Yes| F[End]
```

---

## 4. Parallel Processing

```mermaid
graph TD
    A[Start] --> B[Task 1]
    A --> C[Task 2]
    A --> D[Task 3]
    B --> E[Merge]
    C --> E
    D --> E
    E --> F[End]
```

---

## 5. Error Handling

```mermaid
graph TD
    A[Start] --> B[Try Operation]
    B --> C{Success?}
    C -->|Yes| D[Continue]
    C -->|No| E[Log Error]
    E --> F{Retry?}
    F -->|Yes| B
    F -->|No| G[Fail Gracefully]
    D --> H[End]
    G --> H
```

---

## 6. API Request Flow

```mermaid
graph TD
    A[Client Request] --> B[API Gateway]
    B --> C{Authenticated?}
    C -->|No| D[401 Unauthorized]
    C -->|Yes| E[Route to Service]
    E --> F{Valid Request?}
    F -->|No| G[400 Bad Request]
    F -->|Yes| H[Process Request]
    H --> I{Success?}
    I -->|Yes| J[200 OK]
    I -->|No| K[500 Server Error]
```

---

## 7. Git Workflow

```mermaid
graph LR
    A[Working Directory] -->|git add| B[Staging Area]
    B -->|git commit| C[Local Repository]
    C -->|git push| D[Remote Repository]
    D -->|git pull| C
    C -->|git checkout| A
```

---

## 8. CI/CD Pipeline

```mermaid
graph LR
    subgraph Build
        A[Code Commit] --> B[Install Dependencies]
        B --> C[Run Linting]
        C --> D[Run Tests]
    end
    
    subgraph Deploy
        D --> E{Tests Pass?}
        E -->|Yes| F[Build Docker Image]
        E -->|No| G[Notify Developer]
        F --> H[Push to Registry]
        H --> I[Deploy to Staging]
        I --> J{Staging OK?}
        J -->|Yes| K[Deploy to Production]
        J -->|No| G
    end
```

---

## 9. User Authentication

```mermaid
graph TD
    A[Login Page] --> B[Enter Credentials]
    B --> C[Submit Form]
    C --> D{Valid Credentials?}
    D -->|No| E[Show Error]
    E --> B
    D -->|Yes| F{2FA Enabled?}
    F -->|No| H[Create Session]
    F -->|Yes| G[Enter 2FA Code]
    G --> I{Valid Code?}
    I -->|No| J[Show Error]
    J --> G
    I -->|Yes| H
    H --> K[Redirect to Dashboard]
```

---

## 10. E-commerce Checkout

```mermaid
graph TD
    A[🛒 Shopping Cart] --> B[Review Items]
    B --> C{Items Available?}
    C -->|No| D[Remove Unavailable]
    D --> B
    C -->|Yes| E[Enter Shipping Info]
    E --> F[Select Payment Method]
    F --> G{Payment Valid?}
    G -->|No| H[Show Payment Error]
    H --> F
    G -->|Yes| I[Process Payment]
    I --> J{Payment Success?}
    J -->|No| K[Refund & Notify]
    J -->|Yes| L[Create Order]
    L --> M[Send Confirmation Email]
    M --> N[📦 Order Complete]
```

---

## How to Use These Examples

1. Copy any example code block
2. Paste into [Mermaid Live Editor](https://mermaid.live/)
3. Modify to fit your needs
4. Export as SVG or PNG if needed
