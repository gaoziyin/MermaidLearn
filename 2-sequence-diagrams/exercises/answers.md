# Exercise Answers 📝

## Exercise 1: Simple API Call

```mermaid
sequenceDiagram
    participant C as Client
    participant A as API
    participant D as Database
    
    C->>A: GET /users
    A->>D: Query users
    D-->>A: Results
    A-->>C: JSON Response
```

**With more detail:**

```mermaid
sequenceDiagram
    autonumber
    participant Client
    participant API as REST API
    participant DB as Database
    
    Client->>API: GET /users
    activate API
    API->>DB: SELECT * FROM users
    activate DB
    DB-->>API: User records
    deactivate DB
    API-->>Client: 200 OK [{users}]
    deactivate API
```

---

## Exercise 2: Authentication Flow

```mermaid
sequenceDiagram
    autonumber
    actor User
    participant Frontend
    participant Auth as Auth Service
    participant DB as Database
    
    User->>Frontend: Enter credentials
    Frontend->>Auth: POST /login
    Auth->>DB: Validate credentials
    
    alt Valid credentials
        DB-->>Auth: User found
        Auth-->>Frontend: JWT Token
        Frontend-->>User: Redirect to dashboard
    else Invalid credentials
        DB-->>Auth: Invalid
        Auth-->>Frontend: 401 Unauthorized
        Frontend-->>User: Show error message
    end
```

---

## Exercise 3: Microservices

```mermaid
sequenceDiagram
    participant GW as API Gateway
    participant US as User Service
    participant PS as Product Service
    
    GW->>US: Get user info
    activate US
    
    par Parallel Requests
        GW->>PS: Get product list
        activate PS
    end
    
    US-->>GW: User data
    deactivate US
    PS-->>GW: Product data
    deactivate PS
    
    Note over GW: Combine responses
    GW-->>GW: Merge data
```

---

## Exercise 4: WebSocket Connection

```mermaid
sequenceDiagram
    participant C as Client
    participant S as Server
    
    C->>S: WebSocket Connect
    S-->>C: Connection Acknowledged
    
    loop Every 30 seconds
        C->>S: Heartbeat ping
        S-->>C: Heartbeat pong
    end
    
    C->>S: Disconnect
    S-->>C: Connection Closed
```

---

## Bonus: Complete Order Processing

```mermaid
sequenceDiagram
    autonumber
    actor Customer
    participant Web as Web App
    participant API as Order API
    participant Inv as Inventory
    participant Pay as Payment
    participant Ship as Shipping
    participant Email as Email Service
    
    Customer->>Web: Place Order
    Web->>API: POST /orders
    
    API->>Inv: Check availability
    
    alt Items in stock
        Inv-->>API: Available
        
        API->>Pay: Process payment
        
        alt Payment success
            Pay-->>API: Confirmed
            API->>Inv: Reserve items
            API->>Ship: Create shipment
            
            par Notifications
                API->>Email: Send confirmation
            and
                Ship->>Email: Send tracking
            end
            
            API-->>Web: Order confirmed
            Web-->>Customer: Show confirmation
        else Payment failed
            Pay-->>API: Declined
            API-->>Web: Payment error
            Web-->>Customer: Show error
        end
    else Out of stock
        Inv-->>API: Unavailable
        API-->>Web: Stock error
        Web-->>Customer: Item unavailable
    end
```

---

## Tips for Sequence Diagrams

1. **Use autonumber** - Makes it easier to reference steps
2. **Activate/deactivate** - Shows processing time clearly
3. **Use aliases** - Keep participant names short but descriptive
4. **Group with alt/par** - Show branching and parallel logic
5. **Add notes** - Clarify complex interactions
6. **Keep it readable** - Don't add too many participants
