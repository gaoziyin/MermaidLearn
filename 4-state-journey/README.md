# Module 4: State & Journey Diagrams 📈

> **Level: Intermediate** | **Estimated Time: 3-4 hours**

## 📋 Module Overview

This module covers State Diagrams for modeling system states and transitions, and User Journey Diagrams for mapping user experiences.

```mermaid
graph LR
    A[4.1 State Diagrams] --> B[4.2 User Journey]
    B --> C[✅ Module Complete]
    
    style A fill:#87CEEB
    style C fill:#FFD700
```

---

## 📖 Chapter 4.1: State Diagrams

### Basic State Diagram

```mermaid
stateDiagram-v2
    [*] --> Idle
    Idle --> Processing : Start
    Processing --> Completed : Success
    Processing --> Failed : Error
    Completed --> [*]
    Failed --> Idle : Retry
```

**Key elements:**
- `stateDiagram-v2` - Diagram type (use v2 for latest features)
- `[*]` - Start/End state
- `-->` - Transition
- `: text` - Transition label

### States and Transitions

```mermaid
stateDiagram-v2
    state "Order Placed" as placed
    state "Payment Pending" as pending
    state "Payment Received" as paid
    state "Order Shipped" as shipped
    state "Order Delivered" as delivered
    
    [*] --> placed
    placed --> pending : Checkout
    pending --> paid : Payment confirmed
    paid --> shipped : Ship order
    shipped --> delivered : Package arrived
    delivered --> [*]
```

### State Descriptions

```mermaid
stateDiagram-v2
    State1 : This is a description
    State2 : Another state with description
    
    [*] --> State1
    State1 --> State2 : Transition
    State2 --> [*]
```

### Composite States

```mermaid
stateDiagram-v2
    [*] --> Active
    
    state Active {
        [*] --> Idle
        Idle --> Running : Start
        Running --> Paused : Pause
        Paused --> Running : Resume
        Running --> Idle : Stop
    }
    
    Active --> Inactive : Shutdown
    Inactive --> Active : Boot
    Inactive --> [*]
```

### Nested States

```mermaid
stateDiagram-v2
    [*] --> Application
    
    state Application {
        [*] --> MainWindow
        
        state MainWindow {
            [*] --> Dashboard
            Dashboard --> Settings : Open Settings
            Settings --> Dashboard : Close
        }
        
        MainWindow --> Login : Logout
        Login --> MainWindow : Login Success
    }
    
    Application --> [*] : Exit
```

### Fork and Join

```mermaid
stateDiagram-v2
    state fork_state <<fork>>
    state join_state <<join>>
    
    [*] --> fork_state
    fork_state --> State2
    fork_state --> State3
    
    State2 --> join_state
    State3 --> join_state
    
    join_state --> State4
    State4 --> [*]
```

### Choice (Decision)

```mermaid
stateDiagram-v2
    state decision <<choice>>
    
    [*] --> CheckBalance
    CheckBalance --> decision
    decision --> Approve : if balance > required
    decision --> Reject : if balance < required
    Approve --> [*]
    Reject --> [*]
```

### Notes

```mermaid
stateDiagram-v2
    [*] --> Processing
    Processing --> Completed
    
    note right of Processing : This step may take a while
    note left of Completed : Final state reached
```

### Concurrency

```mermaid
stateDiagram-v2
    [*] --> Active
    
    state Active {
        [*] --> Thread1
        [*] --> Thread2
        --
        Thread1 --> Done1
        --
        Thread2 --> Done2
    }
    
    Active --> [*]
```

### Complete Example: Order Lifecycle

```mermaid
stateDiagram-v2
    [*] --> Draft
    
    state "Order States" as OrderStates {
        Draft --> Submitted : Submit
        Submitted --> Validated : Validate
        
        state if_valid <<choice>>
        Validated --> if_valid
        if_valid --> Processing : Valid
        if_valid --> Rejected : Invalid
        
        Rejected --> Draft : Edit & Resubmit
        
        state Processing {
            [*] --> PaymentPending
            PaymentPending --> PaymentReceived : Pay
            PaymentReceived --> Packaging
            Packaging --> ReadyToShip
        }
        
        Processing --> Shipped : Dispatch
    }
    
    state "Delivery" as delivery {
        Shipped --> InTransit
        InTransit --> OutForDelivery
        OutForDelivery --> Delivered
    }
    
    Delivered --> [*]
    
    note right of Draft : Customer creating order
    note right of Processing : Warehouse handling
    note right of delivery : Logistics handling
```

### Styling States

```mermaid
stateDiagram-v2
    [*] --> s1
    s1 --> s2
    s2 --> s3
    s3 --> [*]
    
    classDef success fill:#90EE90
    classDef warning fill:#FFD700
    classDef error fill:#FF6B6B
    
    class s1 success
    class s2 warning
    class s3 error
```

---

## 📖 Chapter 4.2: User Journey Diagrams

### Basic Journey

```mermaid
journey
    title My Working Day
    section Morning
      Wake up: 3: Me
      Shower: 4: Me
      Breakfast: 5: Me
      Commute: 2: Me
    section Work
      Meetings: 3: Me, Boss
      Coding: 5: Me
      Lunch: 4: Me, Colleague
      More coding: 5: Me
    section Evening
      Commute home: 2: Me
      Dinner: 5: Me, Family
      Relax: 5: Me
```

**Syntax breakdown:**
- `journey` - Diagram type
- `title` - Diagram title
- `section Name` - Group of tasks
- `Task: score: actors` - Task with satisfaction score (1-5) and participants

### Score System

The score represents satisfaction/happiness:
- 🔴 **1** - Very unhappy
- 🟠 **2** - Unhappy
- 🟡 **3** - Neutral
- 🟢 **4** - Happy
- 💚 **5** - Very happy

### E-Commerce User Journey

```mermaid
journey
    title Online Shopping Experience
    section Discovery
      Search for product: 4: Customer
      Browse categories: 3: Customer
      Find desired item: 5: Customer
    section Evaluation
      Read reviews: 4: Customer
      Check specifications: 4: Customer
      Compare prices: 3: Customer
    section Purchase
      Add to cart: 5: Customer
      Proceed to checkout: 4: Customer
      Enter payment info: 2: Customer
      Confirm order: 4: Customer
    section Delivery
      Wait for delivery: 3: Customer
      Receive package: 5: Customer
      Unbox product: 5: Customer
    section Post-Purchase
      Use product: 5: Customer
      Write review: 4: Customer
```

### App Onboarding Journey

```mermaid
journey
    title Mobile App Onboarding
    section Download
      Find app in store: 4: User
      Read reviews: 4: User
      Download app: 5: User
    section Registration
      Open app: 5: User
      View intro slides: 3: User
      Create account: 2: User
      Verify email: 2: User
    section Setup
      Set preferences: 4: User
      Connect accounts: 3: User
      Complete profile: 3: User
    section First Use
      Explore features: 4: User
      Complete first task: 5: User
      Get achievement: 5: User
```

### Customer Support Journey

```mermaid
journey
    title Customer Support Experience
    section Issue Discovery
      Encounter problem: 1: Customer
      Try self-help: 2: Customer
      Search FAQ: 3: Customer
    section Contact Support
      Find contact options: 3: Customer
      Wait in queue: 1: Customer
      Connect with agent: 3: Customer, Agent
    section Resolution
      Explain issue: 3: Customer, Agent
      Troubleshoot together: 4: Customer, Agent
      Issue resolved: 5: Customer, Agent
    section Follow-up
      Receive confirmation: 4: Customer
      Rate experience: 4: Customer
```

### Multi-Actor Journey

```mermaid
journey
    title Team Project Delivery
    section Planning
      Receive requirements: 4: PM, Dev, Designer
      Estimate effort: 3: PM, Dev
      Create timeline: 4: PM
    section Design
      Create wireframes: 5: Designer
      Design review: 4: PM, Dev, Designer
      Finalize designs: 5: Designer
    section Development
      Setup environment: 3: Dev
      Implement features: 4: Dev
      Code review: 4: Dev
    section Testing
      Unit testing: 4: Dev
      QA testing: 3: QA
      Bug fixes: 2: Dev
    section Delivery
      Deploy to staging: 4: Dev
      Client review: 3: PM, Client
      Deploy to production: 5: Dev, PM
```

---

## 🏋️ Exercises

### Exercise 1: Traffic Light (State Diagram)
Create a state diagram for a traffic light:
- States: Red, Yellow, Green
- Transitions with timers
- Include pedestrian button interrupt

```mermaid
stateDiagram-v2
  [*] --> Green : open
  Green --> Yellow: 3s
  Yellow --> Red: 60s
  Red --> Green: 40s


  classDef green fill: #90FF01
  classDef yellow fill: #DFCD12
  classDef red fill: #FF3333

  class Green green
  class Yellow yellow
  class Red red

```

### Exercise 2: Document Workflow (State Diagram)
Create states for a document:
- Draft, In Review, Approved, Rejected, Published, Archived
- Include decision points and possible loops

```mermaid
stateDiagram-v2  
  [*] --> Draft: start
  state pre-publish {
    state isOk <<choice>>
    Draft --> Review: review
    Review --> isOk
    isOk --> Approved: passed
    isOk --> Rejected: failed
    Approved --> Published
    Rejected --> Review
  }

  Published --> Archived
  
```

### Exercise 3: Shopping Journey
Create a user journey for:
- Physical store shopping experience
- Include sections: Arrival, Shopping, Checkout, Departure
- Multiple actors: Customer, Staff

### Exercise 4: Job Application Journey
Map the job application process:
- From finding a job post to getting hired (or rejected)
- Include emotional highs and lows
- Multiple actors: Applicant, Recruiter, Hiring Manager

---

## ✅ Module Checklist

- [ ] Can create basic state diagrams
- [ ] Understand start and end states
- [ ] Can create composite/nested states
- [ ] Know how to use fork, join, and choice
- [ ] Can add notes to states
- [ ] Can create user journey diagrams
- [ ] Understand the scoring system
- [ ] Can define sections and actors
- [ ] Completed all exercises

---

## 🔗 Resources

- [Mermaid State Diagram Docs](https://mermaid.js.org/syntax/stateDiagram.html)
- [Mermaid User Journey Docs](https://mermaid.js.org/syntax/userJourney.html)

---

> **Next Module:** [Module 5: Gantt & Timeline](../5-gantt-timeline/README.md) →
