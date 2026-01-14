# Module 3: Class & ER Diagrams 📈

> **Level: Intermediate** | **Estimated Time: 3-4 hours**

## 📋 Module Overview

This module covers two essential diagram types for software design: Class Diagrams for object-oriented design and Entity-Relationship Diagrams for database modeling.

```mermaid
graph LR
    A[3.1 Class Diagrams] --> B[3.2 ER Diagrams]
    B --> C[✅ Module Complete]
    
    style A fill:#87CEEB
    style C fill:#FFD700
```

---

## 📖 Chapter 3.1: Class Diagrams

### Basic Class Definition

```mermaid
classDiagram
    class Animal {
        +String name
        +int age
        +makeSound()
        +move()
    }
```

**Syntax breakdown:**
- `classDiagram` - Diagram type
- `class ClassName` - Define a class
- `+String name` - Public attribute
- `+makeSound()` - Public method

### Visibility Modifiers

```mermaid
classDiagram
    class Example {
        +publicAttribute
        -privateAttribute
        #protectedAttribute
        ~packageAttribute
        +publicMethod()
        -privateMethod()
        #protectedMethod()
        ~packageMethod()
    }
```

| Symbol | Visibility |
|--------|------------|
| `+` | Public |
| `-` | Private |
| `#` | Protected |
| `~` | Package/Internal |

### Method Parameters and Return Types

```mermaid
classDiagram
    class UserService {
        +getUser(int id) User
        +createUser(String name, String email) User
        +deleteUser(int id) bool
        +listUsers() List~User~
    }
```

### Generic Types

```mermaid
classDiagram
    class List~T~ {
        +add(T item)
        +get(int index) T
        +size() int
    }
    
    class Map~K,V~ {
        +put(K key, V value)
        +get(K key) V
    }
```

### Static and Abstract

```mermaid
classDiagram
    class MathUtils {
        +int PI$
        +add(int a, int b)$ int
        +subtract(int a, int b)$ int
    }
    
    class Shape {
        <<abstract>>
        +draw()*
        +getArea()* double
    }
```

**Notation:**
- `$` - Static member
- `*` - Abstract method
- `<<abstract>>` - Abstract class annotation

### Annotations

```mermaid
classDiagram
    class IRepository~T~ {
        <<interface>>
        +save(T entity)
        +findById(int id) T
        +delete(int id)
    }
    
    class AbstractService {
        <<abstract>>
        #repository
        +process()
    }
    
    class UserDTO {
        <<dto>>
        +name
        +email
    }
    
    class AppConfig {
        <<service>>
        +getConfig()
    }
```

Common annotations: `<<interface>>`, `<<abstract>>`, `<<service>>`, `<<enumeration>>`, `<<dto>>`

### Relationships

```mermaid
classDiagram
    classA --|> classB : Inheritance
    classC --* classD : Composition
    classE --o classF : Aggregation
    classG --> classH : Association
    classI -- classJ : Link
    classK ..> classL : Dependency
    classM ..|> classN : Realization
```

| Syntax | Relationship | Description |
|--------|--------------|-------------|
| `--|>` | Inheritance | "is a" |
| `--*` | Composition | Strong "has a" (lifecycle bound) |
| `--o` | Aggregation | Weak "has a" (independent lifecycle) |
| `-->` | Association | "uses" |
| `--` | Link | Simple connection |
| `..>` | Dependency | "depends on" |
| `..\|>` | Realization | Implements interface |

### Cardinality

```mermaid
classDiagram
    Customer "1" --> "*" Order : places
    Order "1" --> "1..*" OrderItem : contains
    OrderItem "*" --> "1" Product : refers to
```

| Notation | Meaning |
|----------|---------|
| `1` | Exactly one |
| `0..1` | Zero or one |
| `1..*` | One or more |
| `*` | Many |
| `n` | n exactly |
| `0..n` | Zero to n |

### Complete Example: E-Commerce System

```mermaid
classDiagram
    class User {
        <<entity>>
        -int id
        -String email
        -String password
        +login() bool
        +logout()
    }
    
    class Customer {
        -String address
        -String phone
        +placeOrder() Order
        +getOrderHistory() List~Order~
    }
    
    class Admin {
        -String role
        +manageProducts()
        +viewReports()
    }
    
    class Order {
        <<entity>>
        -int id
        -Date createdAt
        -String status
        +calculateTotal() double
        +cancel()
    }
    
    class OrderItem {
        -int quantity
        -double price
        +getSubtotal() double
    }
    
    class Product {
        <<entity>>
        -int id
        -String name
        -double price
        -int stock
        +updateStock(int qty)
    }
    
    User <|-- Customer
    User <|-- Admin
    Customer "1" --> "*" Order : places
    Order "1" *-- "*" OrderItem : contains
    OrderItem "*" --> "1" Product : refers to
```

### Styling Classes

```mermaid
classDiagram
    class Success {
        +good()
    }
    class Warning {
        +caution()
    }
    class Error {
        +bad()
    }
    
    style Success fill:#90EE90
    style Warning fill:#FFD700
    style Error fill:#FF6B6B
```

---

## 📖 Chapter 3.2: Entity Relationship Diagrams

### Basic ER Diagram

```mermaid
erDiagram
    CUSTOMER ||--o{ ORDER : places
    ORDER ||--|{ LINE-ITEM : contains
    PRODUCT ||--o{ LINE-ITEM : "ordered in"
```

### Relationship Types

```mermaid
erDiagram
    A ||--|| B : "one to one"
    C ||--o{ D : "one to many"  
    E }o--o{ F : "many to many"
    G |o--o| H : "zero or one to zero or one"
```

| Left | Right | Meaning |
|------|-------|---------|
| `\|\|` | `\|\|` | Exactly one |
| `\|o` | `o\|` | Zero or one |
| `}o` | `o{` | Zero or more |
| `}\|` | `\|{` | One or more |

### Entity Attributes

```mermaid
erDiagram
    CUSTOMER {
        int id PK
        string name
        string email UK
        string phone
        date created_at
    }
    
    ORDER {
        int id PK
        int customer_id FK
        date order_date
        decimal total
        string status
    }
    
    CUSTOMER ||--o{ ORDER : places
```

**Attribute modifiers:**
- `PK` - Primary Key
- `FK` - Foreign Key
- `UK` - Unique Key

### Data Types

Common attribute types:
- `int`, `bigint` - Integers
- `string`, `varchar` - Text
- `decimal`, `float` - Numbers
- `date`, `datetime` - Dates
- `boolean` - True/False
- `text` - Long text
- `blob` - Binary data

### Complete Example: Blog Database

```mermaid
erDiagram
    USER {
        int id PK
        string username UK
        string email UK
        string password_hash
        datetime created_at
        boolean is_active
    }
    
    POST {
        int id PK
        int author_id FK
        string title
        text content
        string slug UK
        datetime published_at
        string status
    }
    
    CATEGORY {
        int id PK
        string name UK
        string slug UK
        text description
    }
    
    TAG {
        int id PK
        string name UK
        string slug UK
    }
    
    COMMENT {
        int id PK
        int post_id FK
        int user_id FK
        text content
        datetime created_at
        boolean approved
    }
    
    POST_CATEGORY {
        int post_id FK
        int category_id FK
    }
    
    POST_TAG {
        int post_id FK
        int tag_id FK
    }
    
    USER ||--o{ POST : writes
    USER ||--o{ COMMENT : makes
    POST ||--o{ COMMENT : has
    POST ||--o{ POST_CATEGORY : ""
    CATEGORY ||--o{ POST_CATEGORY : ""
    POST ||--o{ POST_TAG : ""
    TAG ||--o{ POST_TAG : ""
```

### E-Commerce Complete Example

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
        string state
        string zip_code
        string country
        boolean is_default
    }
    
    PRODUCT {
        int id PK
        int category_id FK
        string sku UK
        string name
        text description
        decimal price
        int stock_quantity
    }
    
    CATEGORY {
        int id PK
        int parent_id FK
        string name
        text description
    }
    
    ORDER {
        int id PK
        int customer_id FK
        int shipping_address_id FK
        datetime order_date
        decimal subtotal
        decimal tax
        decimal shipping
        decimal total
        string status
    }
    
    ORDER_ITEM {
        int id PK
        int order_id FK
        int product_id FK
        int quantity
        decimal unit_price
        decimal total
    }
    
    PAYMENT {
        int id PK
        int order_id FK
        string method
        decimal amount
        string status
        datetime paid_at
    }
    
    CUSTOMER ||--o{ ADDRESS : has
    CUSTOMER ||--o{ ORDER : places
    ORDER ||--|{ ORDER_ITEM : contains
    ORDER ||--|| PAYMENT : has
    ORDER }o--|| ADDRESS : "ships to"
    PRODUCT ||--o{ ORDER_ITEM : ""
    CATEGORY ||--o{ PRODUCT : contains
    CATEGORY |o--o{ CATEGORY : "parent of"
```

---

## 🏋️ Exercises

### Exercise 1: Library System (Class Diagram)
Create a class diagram with:
- `Book` (title, author, ISBN, available)
- `Member` (name, memberID, email)
- `Loan` (book, member, dueDate, returned)
- Relationships: Member borrows Books through Loans

### Exercise 2: Animal Hierarchy (Class Diagram)
Create inheritance chain:
- Abstract `Animal` class
- `Mammal` and `Bird` subclasses
- Specific animals: `Dog`, `Cat`, `Eagle`, `Penguin`
- Use appropriate visibility and abstract methods

### Exercise 3: School Database (ER Diagram)
Design tables for:
- Students
- Teachers
- Courses
- Enrollments (students in courses)
- Departments
- Include appropriate attributes and relationships

### Exercise 4: Social Media (ER Diagram)
Design a social media database:
- Users (profile info)
- Posts (text, images)
- Comments
- Likes
- Friendships/Follows
- Show all relationships with cardinality

---

## ✅ Module Checklist

- [ ] Can create class diagrams with attributes and methods
- [ ] Understand visibility modifiers
- [ ] Know all relationship types
- [ ] Can add cardinality to relationships
- [ ] Can use annotations
- [ ] Can create ER diagrams
- [ ] Understand ER relationship notation
- [ ] Can define entity attributes with types and keys
- [ ] Completed all exercises

---

## 🔗 Resources

- [Mermaid Class Diagram Docs](https://mermaid.js.org/syntax/classDiagram.html)
- [Mermaid ER Diagram Docs](https://mermaid.js.org/syntax/entityRelationshipDiagram.html)

---

> **Next Module:** [Module 4: State & Journey Diagrams](../4-state-journey/README.md) →
