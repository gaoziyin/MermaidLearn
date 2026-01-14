# State & Journey Diagram Examples 📊

---

## State Diagram Examples

### 1. Simple State Machine

```mermaid
stateDiagram-v2
    [*] --> Idle
    Idle --> Running : Start
    Running --> Idle : Stop
    Running --> [*] : Complete
```

### 2. Traffic Light

```mermaid
stateDiagram-v2
    [*] --> Red
    Red --> Green : Timer (60s)
    Green --> Yellow : Timer (45s)
    Yellow --> Red : Timer (5s)
    
    note right of Red : Stop
    note right of Green : Go
    note right of Yellow : Caution
```

### 3. Order Lifecycle

```mermaid
stateDiagram-v2
    [*] --> Pending
    Pending --> Confirmed : Payment received
    Confirmed --> Processing : Start processing
    Processing --> Shipped : Dispatch
    Shipped --> Delivered : Arrive
    Delivered --> [*]
    
    Pending --> Cancelled : Cancel order
    Confirmed --> Cancelled : Cancel order
    Cancelled --> [*]
```

### 4. User Authentication

```mermaid
stateDiagram-v2
    [*] --> LoggedOut
    
    LoggedOut --> Authenticating : Submit credentials
    
    state Authenticating {
        [*] --> ValidatingCredentials
        ValidatingCredentials --> CheckingMFA : Valid
        ValidatingCredentials --> Failed : Invalid
        CheckingMFA --> Verified : MFA passed
        CheckingMFA --> Failed : MFA failed
    }
    
    Authenticating --> LoggedIn : Verified
    Authenticating --> LoggedOut : Failed
    
    LoggedIn --> LoggedOut : Logout
    LoggedIn --> [*] : Session expired
```

### 5. Document Workflow

```mermaid
stateDiagram-v2
    [*] --> Draft
    
    Draft --> InReview : Submit
    
    state InReview {
        [*] --> PendingReview
        PendingReview --> UnderReview : Reviewer assigned
        UnderReview --> ChangesRequested : Request changes
        UnderReview --> ReviewComplete : Approve
        ChangesRequested --> UnderReview : Resubmit
    }
    
    InReview --> Approved : Review complete
    InReview --> Draft : Major revision
    
    Approved --> Published : Publish
    Published --> Archived : Archive
    Archived --> [*]
```

### 6. Parallel States (Fork/Join)

```mermaid
stateDiagram-v2
    state fork_state <<fork>>
    state join_state <<join>>
    
    [*] --> fork_state
    fork_state --> ValidateData
    fork_state --> CheckInventory
    fork_state --> VerifyPayment
    
    ValidateData --> join_state
    CheckInventory --> join_state
    VerifyPayment --> join_state
    
    join_state --> ProcessOrder
    ProcessOrder --> [*]
```

---

## User Journey Examples

### 1. Morning Routine

```mermaid
journey
    title My Morning Routine
    section Wake Up
        Alarm rings: 2: Me
        Snooze alarm: 1: Me
        Finally wake up: 3: Me
    section Get Ready
        Shower: 4: Me
        Get dressed: 4: Me
        Make breakfast: 5: Me
    section Commute
        Leave house: 4: Me
        Wait for bus: 2: Me
        Arrive at work: 4: Me
```

### 2. Online Shopping

```mermaid
journey
    title Online Shopping Experience
    section Discovery
        Search for product: 4: Customer
        Browse results: 3: Customer
        Find perfect item: 5: Customer
    section Evaluation
        Read reviews: 4: Customer
        Check price: 3: Customer
        Compare options: 3: Customer
    section Purchase
        Add to cart: 5: Customer
        Enter shipping info: 2: Customer
        Enter payment: 2: Customer
        Confirm order: 4: Customer
    section Delivery
        Wait for shipping: 2: Customer
        Receive package: 5: Customer
        Open and enjoy: 5: Customer
```

### 3. Job Interview Process

```mermaid
journey
    title Job Interview Journey
    section Application
        Find job posting: 4: Candidate
        Submit application: 3: Candidate
        Wait for response: 2: Candidate
    section Phone Screen
        Schedule call: 4: Candidate, Recruiter
        Phone interview: 3: Candidate, Recruiter
        Wait for feedback: 2: Candidate
    section Technical
        Receive assignment: 3: Candidate
        Complete homework: 4: Candidate
        Technical interview: 3: Candidate, Engineer
    section Final Round
        Meet the team: 4: Candidate, Team
        Culture fit interview: 4: Candidate, Manager
        Receive offer: 5: Candidate, Recruiter
```

### 4. Restaurant Experience

```mermaid
journey
    title Restaurant Dining Experience
    section Arrival
        Find parking: 2: Guest
        Enter restaurant: 4: Guest
        Wait for table: 2: Guest
        Get seated: 4: Guest, Server
    section Ordering
        Review menu: 4: Guest
        Ask questions: 3: Guest, Server
        Place order: 4: Guest, Server
    section Dining
        Receive drinks: 5: Guest, Server
        Wait for food: 3: Guest
        Enjoy meal: 5: Guest
        Request check: 4: Guest, Server
    section Departure
        Pay bill: 3: Guest
        Leave tip: 4: Guest
        Leave restaurant: 4: Guest
```

### 5. Customer Support

```mermaid
journey
    title Customer Support Experience
    section Problem
        Encounter issue: 1: Customer
        Search for help: 3: Customer
        Can't find answer: 2: Customer
    section Contact
        Find support chat: 3: Customer
        Wait for agent: 1: Customer
        Connect to agent: 4: Customer, Agent
    section Resolution
        Explain problem: 3: Customer, Agent
        Agent investigates: 3: Agent
        Problem solved: 5: Customer, Agent
    section Followup
        Receive confirmation: 4: Customer
        Rate experience: 4: Customer
```

---

## Quick Reference

### State Diagram Elements
| Element | Syntax |
|---------|--------|
| Start | `[*] -->` |
| End | `--> [*]` |
| State | `StateName` |
| Transition | `-->` |
| Label | `: label` |
| Composite | `state Name { }` |
| Fork | `<<fork>>` |
| Join | `<<join>>` |
| Choice | `<<choice>>` |

### Journey Elements
| Element | Description |
|---------|-------------|
| `title` | Diagram title |
| `section` | Group of tasks |
| Task format | `Task: score: actors` |
| Score range | 1 (bad) to 5 (great) |
