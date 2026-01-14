# Sequence Diagram Examples 📊

A collection of ready-to-use sequence diagram examples.

---

## 1. Simple Request-Response

```mermaid
sequenceDiagram
    Client->>Server: Request
    Server-->>Client: Response
```

---

## 2. REST API Call

```mermaid
sequenceDiagram
    participant C as Client
    participant API as REST API
    participant DB as Database
    
    C->>API: GET /users/123
    API->>DB: SELECT * FROM users WHERE id=123
    DB-->>API: User data
    API-->>C: 200 OK (JSON)
```

---

## 3. Authentication Flow

```mermaid
sequenceDiagram
    autonumber
    actor User
    participant App
    participant Auth as Auth Service
    participant DB as Database
    
    User->>App: Enter credentials
    App->>Auth: POST /login
    Auth->>DB: Verify credentials
    
    alt Valid credentials
        DB-->>Auth: User found
        Auth-->>App: JWT Token
        App-->>User: Login successful
    else Invalid credentials
        DB-->>Auth: User not found
        Auth-->>App: 401 Unauthorized
        App-->>User: Invalid credentials
    end
```

---

## 4. Microservices Communication

```mermaid
sequenceDiagram
    participant Gateway as API Gateway
    participant Users as User Service
    participant Orders as Order Service
    participant Payments as Payment Service
    
    Gateway->>Users: Get user info
    activate Users
    Users-->>Gateway: User data
    deactivate Users
    
    Gateway->>Orders: Create order
    activate Orders
    Orders->>Payments: Process payment
    activate Payments
    Payments-->>Orders: Payment confirmed
    deactivate Payments
    Orders-->>Gateway: Order created
    deactivate Orders
```

---

## 5. WebSocket Connection

```mermaid
sequenceDiagram
    participant Client
    participant Server
    
    Client->>Server: WebSocket handshake
    Server-->>Client: Connection established
    
    loop Every 30 seconds
        Client->>Server: Ping
        Server-->>Client: Pong
    end
    
    Note over Client,Server: Bidirectional communication
    
    Client->>Server: Send message
    Server->>Client: Push notification
    
    Client->>Server: Close connection
    Server-->>Client: Connection closed
```

---

## 6. OAuth 2.0 Flow

```mermaid
sequenceDiagram
    actor User
    participant App
    participant AuthServer as Auth Server
    participant Resource as Resource Server
    
    User->>App: Click "Login with Google"
    App->>AuthServer: Redirect to authorization
    AuthServer->>User: Show login page
    User->>AuthServer: Enter credentials
    AuthServer-->>App: Authorization code
    App->>AuthServer: Exchange code for token
    AuthServer-->>App: Access token + Refresh token
    App->>Resource: API request with token
    Resource-->>App: Protected data
    App-->>User: Show data
```

---

## 7. Database Transaction

```mermaid
sequenceDiagram
    participant App
    participant DB as Database
    
    App->>DB: BEGIN TRANSACTION
    activate DB
    
    App->>DB: INSERT INTO orders
    App->>DB: UPDATE inventory
    App->>DB: INSERT INTO audit_log
    
    alt All operations succeed
        App->>DB: COMMIT
        DB-->>App: Transaction committed
    else Any operation fails
        App->>DB: ROLLBACK
        DB-->>App: Transaction rolled back
    end
    
    deactivate DB
```

---

## 8. Event-Driven Architecture

```mermaid
sequenceDiagram
    participant Producer
    participant Queue as Message Queue
    participant Consumer1 as Consumer A
    participant Consumer2 as Consumer B
    
    Producer->>Queue: Publish event
    
    par Parallel Processing
        Queue->>Consumer1: Deliver event
        Consumer1-->>Queue: ACK
    and
        Queue->>Consumer2: Deliver event
        Consumer2-->>Queue: ACK
    end
```

---

## 9. Error Handling with Retry

```mermaid
sequenceDiagram
    participant Client
    participant API
    participant Service
    
    Client->>API: Request
    API->>Service: Call external service
    
    critical Service call
        Service-->>API: Error 500
    option Retry attempt 1
        API->>Service: Retry
        Service-->>API: Error 500
    option Retry attempt 2
        API->>Service: Retry
        Service-->>API: Success
    end
    
    API-->>Client: Response
```

---

## 10. Full E-Commerce Checkout

```mermaid
sequenceDiagram
    autonumber
    actor Customer
    participant Cart
    participant Order as Order Service
    participant Inventory
    participant Payment
    participant Notification
    
    Customer->>Cart: Checkout
    Cart->>Order: Create order
    
    Order->>Inventory: Check stock
    
    alt Items available
        Inventory-->>Order: Stock confirmed
        Order->>Payment: Process payment
        
        alt Payment successful
            Payment-->>Order: Payment confirmed
            Order->>Inventory: Reserve items
            
            par Send notifications
                Order->>Notification: Send confirmation email
            and
                Order->>Notification: Send SMS
            end
            
            Order-->>Cart: Order complete
            Cart-->>Customer: Show confirmation
        else Payment failed
            Payment-->>Order: Payment declined
            Order-->>Cart: Payment error
            Cart-->>Customer: Show payment error
        end
    else Items unavailable
        Inventory-->>Order: Out of stock
        Order-->>Cart: Stock error
        Cart-->>Customer: Show stock error
    end
```

---

## How to Use These Examples

1. Copy any example code block
2. Paste into [Mermaid Live Editor](https://mermaid.live/)
3. Modify participants and messages for your needs
4. Export as SVG or PNG if needed
