# Class & ER Diagram Examples 📊

A collection of ready-to-use class and ER diagram examples.

---

## Class Diagram Examples

### 1. Simple Class

```mermaid
classDiagram
    class User {
        +int id
        +String name
        +String email
        +login()
        +logout()
    }
```

### 2. Inheritance

```mermaid
classDiagram
    class Animal {
        <<abstract>>
        +String name
        +int age
        +makeSound()*
        +move()
    }
    
    class Dog {
        +String breed
        +makeSound()
        +fetch()
    }
    
    class Cat {
        +bool isIndoor
        +makeSound()
        +scratch()
    }
    
    Animal <|-- Dog
    Animal <|-- Cat
```

### 3. Interface Implementation

```mermaid
classDiagram
    class IRepository~T~ {
        <<interface>>
        +save(T entity)
        +findById(int id) T
        +findAll() List~T~
        +delete(int id)
    }
    
    class UserRepository {
        -connection
        +save(User entity)
        +findById(int id) User
        +findAll() List~User~
        +delete(int id)
    }
    
    IRepository <|.. UserRepository
```

### 4. Composition vs Aggregation

```mermaid
classDiagram
    class Car {
        +String model
        +start()
    }
    
    class Engine {
        +int horsepower
        +run()
    }
    
    class Wheel {
        +int size
        +rotate()
    }
    
    class Driver {
        +String name
        +drive()
    }
    
    Car *-- Engine : composition
    Car *-- "4" Wheel : composition
    Car o-- Driver : aggregation
    
    note for Car "Engine dies with Car"
    note for Driver "Driver can exist without Car"
```

### 5. Complete E-Commerce System

```mermaid
classDiagram
    class User {
        <<abstract>>
        #int id
        #String email
        #String passwordHash
        +login() bool
        +logout()
    }
    
    class Customer {
        -String shippingAddress
        -List~Order~ orders
        +placeOrder() Order
        +getOrderHistory() List~Order~
    }
    
    class Admin {
        -String role
        +manageProducts()
        +viewReports()
    }
    
    class Product {
        -int id
        -String name
        -double price
        -int stock
        +updateStock(int qty)
        +getDetails() String
    }
    
    class Order {
        -int id
        -Date createdAt
        -String status
        -List~OrderItem~ items
        +calculateTotal() double
        +cancel()
    }
    
    class OrderItem {
        -int quantity
        -double unitPrice
        +getSubtotal() double
    }
    
    class Payment {
        <<interface>>
        +process(double amount) bool
        +refund(double amount) bool
    }
    
    class CreditCardPayment {
        -String cardNumber
        +process(double amount) bool
        +refund(double amount) bool
    }
    
    User <|-- Customer
    User <|-- Admin
    Customer "1" --> "*" Order : places
    Order "1" *-- "*" OrderItem : contains
    OrderItem "*" --> "1" Product : references
    Order "1" --> "1" Payment : uses
    Payment <|.. CreditCardPayment
```

---

## ER Diagram Examples

### 1. Simple Relationship

```mermaid
erDiagram
    CUSTOMER ||--o{ ORDER : places
    ORDER ||--|{ LINE_ITEM : contains
    PRODUCT ||--o{ LINE_ITEM : "is in"
```

### 2. Blog Database

```mermaid
erDiagram
    USER {
        int id PK
        string username UK
        string email UK
        string password_hash
        datetime created_at
    }
    
    POST {
        int id PK
        int author_id FK
        string title
        text content
        datetime published_at
    }
    
    COMMENT {
        int id PK
        int post_id FK
        int user_id FK
        text content
        datetime created_at
    }
    
    TAG {
        int id PK
        string name UK
    }
    
    POST_TAG {
        int post_id FK
        int tag_id FK
    }
    
    USER ||--o{ POST : writes
    USER ||--o{ COMMENT : makes
    POST ||--o{ COMMENT : has
    POST ||--o{ POST_TAG : ""
    TAG ||--o{ POST_TAG : ""
```

### 3. HR Database

```mermaid
erDiagram
    EMPLOYEE {
        int id PK
        string first_name
        string last_name
        string email UK
        date hire_date
        decimal salary
        int department_id FK
        int manager_id FK
    }
    
    DEPARTMENT {
        int id PK
        string name UK
        int location_id FK
    }
    
    LOCATION {
        int id PK
        string city
        string country
        string address
    }
    
    PROJECT {
        int id PK
        string name
        date start_date
        date end_date
    }
    
    EMPLOYEE_PROJECT {
        int employee_id FK
        int project_id FK
        string role
        date assigned_date
    }
    
    DEPARTMENT ||--o{ EMPLOYEE : employs
    LOCATION ||--o{ DEPARTMENT : houses
    EMPLOYEE ||--o| EMPLOYEE : manages
    EMPLOYEE ||--o{ EMPLOYEE_PROJECT : ""
    PROJECT ||--o{ EMPLOYEE_PROJECT : ""
```

### 4. E-Commerce Database

```mermaid
erDiagram
    CUSTOMER {
        int id PK
        string first_name
        string last_name
        string email UK
        string phone
    }
    
    ADDRESS {
        int id PK
        int customer_id FK
        string street
        string city
        string postal_code
        string country
        boolean is_default
    }
    
    PRODUCT {
        int id PK
        string sku UK
        string name
        text description
        decimal price
        int stock
        int category_id FK
    }
    
    CATEGORY {
        int id PK
        string name
        int parent_id FK
    }
    
    ORDER {
        int id PK
        int customer_id FK
        int shipping_address_id FK
        datetime order_date
        decimal total
        string status
    }
    
    ORDER_ITEM {
        int id PK
        int order_id FK
        int product_id FK
        int quantity
        decimal unit_price
    }
    
    CUSTOMER ||--o{ ADDRESS : has
    CUSTOMER ||--o{ ORDER : places
    ORDER }o--|| ADDRESS : "ships to"
    ORDER ||--|{ ORDER_ITEM : contains
    PRODUCT ||--o{ ORDER_ITEM : ""
    CATEGORY ||--o{ PRODUCT : contains
    CATEGORY |o--o{ CATEGORY : "parent of"
```

---

## Quick Reference

### Class Relationships
| Syntax | Meaning |
|--------|---------|
| `<\|--` | Inheritance |
| `*--` | Composition |
| `o--` | Aggregation |
| `-->` | Association |
| `<\|..` | Realization |
| `..>` | Dependency |

### ER Relationships
| Left | Right | Meaning |
|------|-------|---------|
| `\|\|` | `\|\|` | One to one |
| `\|\|` | `o{` | One to many |
| `}o` | `o{` | Many to many |
| `\|o` | `o\|` | Zero or one |
