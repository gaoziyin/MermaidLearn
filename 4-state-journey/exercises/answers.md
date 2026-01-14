# Exercise Answers 📝

## Exercise 1: Traffic Light (State Diagram)

```mermaid
stateDiagram-v2
    [*] --> Red
    
    Red --> Green : Timer (60s)
    Green --> Yellow : Timer (45s)
    Yellow --> Red : Timer (5s)
    
    state "Pedestrian Mode" as ped {
        [*] --> WalkSignal
        WalkSignal --> DontWalk : Timer (20s)
    }
    
    Red --> ped : Pedestrian button
    ped --> Red : Complete
    
    note right of Red : All cars stop
    note right of Green : Cars may proceed
    note right of Yellow : Prepare to stop
```

**Alternative with more detail:**

```mermaid
stateDiagram-v2
    [*] --> NormalOperation
    
    state NormalOperation {
        [*] --> Red
        Red --> Green : 60 seconds
        Green --> Yellow : 45 seconds
        Yellow --> Red : 5 seconds
    }
    
    state PedestrianCrossing {
        [*] --> AllRed
        AllRed --> Walk : 2 seconds
        Walk --> FlashingDontWalk : 15 seconds
        FlashingDontWalk --> DontWalk : 5 seconds
        DontWalk --> [*]
    }
    
    NormalOperation --> PedestrianCrossing : Button pressed
    PedestrianCrossing --> NormalOperation : Crossing complete
```

---

## Exercise 2: Document Workflow (State Diagram)

```mermaid
stateDiagram-v2
    [*] --> Draft
    
    Draft --> InReview : Submit for review
    
    state InReview {
        [*] --> PendingAssignment
        PendingAssignment --> UnderReview : Assign reviewer
        UnderReview --> ReviewComplete : Review done
    }
    
    state decision <<choice>>
    InReview --> decision
    decision --> Approved : Accepted
    decision --> Rejected : Not accepted
    
    Rejected --> Draft : Revise
    
    Approved --> Published : Publish
    Published --> Archived : Archive
    
    Draft --> Archived : Abandon
    Archived --> [*]
    
    note right of Draft : Author editing
    note right of InReview : Reviewers checking
    note right of Published : Live content
```

---

## Exercise 3: Shopping Journey

```mermaid
journey
    title Physical Store Shopping Experience
    section Arrival
        Drive to store: 3: Customer
        Find parking: 2: Customer
        Enter store: 4: Customer
        Get shopping cart: 4: Customer
    section Shopping
        Browse aisles: 4: Customer
        Find items on list: 3: Customer
        Ask for help: 4: Customer, Staff
        Discover new products: 5: Customer
        Check prices: 3: Customer
    section Checkout
        Go to checkout: 3: Customer
        Wait in line: 1: Customer
        Unload cart: 3: Customer, Staff
        Pay for items: 3: Customer, Staff
        Bag groceries: 4: Customer, Staff
    section Departure
        Push cart to car: 3: Customer
        Load car: 4: Customer
        Return cart: 2: Customer
        Drive home: 4: Customer
```

---

## Exercise 4: Job Application Journey

```mermaid
journey
    title Job Application Process
    section Discovery
        See job posting: 4: Applicant
        Research company: 4: Applicant
        Decide to apply: 5: Applicant
    section Application
        Update resume: 3: Applicant
        Write cover letter: 2: Applicant
        Fill application form: 2: Applicant
        Submit application: 4: Applicant
    section Waiting
        Wait for response: 1: Applicant
        Check email constantly: 2: Applicant
        Receive callback: 5: Applicant, Recruiter
    section Interview Process
        Phone screen: 3: Applicant, Recruiter
        Technical interview: 3: Applicant, Engineer
        Onsite interviews: 4: Applicant, Team
        Meet hiring manager: 4: Applicant, Manager
    section Decision
        Wait for decision: 1: Applicant
        Receive offer: 5: Applicant, Recruiter
        Negotiate terms: 4: Applicant, Recruiter
        Accept offer: 5: Applicant
```

---

## Bonus: Full Application Lifecycle

### State Diagram

```mermaid
stateDiagram-v2
    [*] --> Submitted
    
    Submitted --> Screening : HR reviews
    
    state Screening {
        [*] --> ResumeReview
        ResumeReview --> PhoneScreen : Qualified
        ResumeReview --> Rejected : Not qualified
        PhoneScreen --> Passed : Good call
        PhoneScreen --> Rejected : Poor fit
    }
    
    Screening --> TechnicalRound : Passed screening
    
    state TechnicalRound {
        [*] --> Assignment
        Assignment --> TechInterview : Completed
        TechInterview --> Evaluated
    }
    
    state decision <<choice>>
    TechnicalRound --> decision
    decision --> FinalRound : Strong candidate
    decision --> Rejected : Not strong enough
    
    state FinalRound {
        [*] --> TeamMeeting
        TeamMeeting --> ManagerMeeting
        ManagerMeeting --> [*]
    }
    
    state offer_decision <<choice>>
    FinalRound --> offer_decision
    offer_decision --> OfferExtended : Approved
    offer_decision --> Rejected : Not approved
    
    OfferExtended --> Hired : Accepted
    OfferExtended --> Declined : Rejected offer
    
    Rejected --> [*]
    Declined --> [*]
    Hired --> [*]
```

---

## Tips

1. **State diagrams** - Great for system/process states
2. **User journeys** - Great for emotional experiences
3. **Use scores meaningfully** - Reflect actual user sentiment
4. **Include multiple actors** - Shows collaboration points
5. **Keep sections logical** - Group related activities
