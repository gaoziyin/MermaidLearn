# Exercise Answers 📝

## Exercise 1: Library System (Class Diagram)

```mermaid
classDiagram
    class Book {
        -int id
        -String title
        -String author
        -String ISBN
        -bool available
        +checkout() bool
        +return()
        +getDetails() String
    }
    
    class Member {
        -int memberID
        -String name
        -String email
        -List~Loan~ activeLoans
        +borrowBook(Book book) Loan
        +returnBook(Loan loan)
        +getActiveLoans() List~Loan~
    }
    
    class Loan {
        -int id
        -Date borrowDate
        -Date dueDate
        -bool returned
        +extend(int days)
        +markReturned()
        +isOverdue() bool
    }
    
    Member "1" --> "*" Loan : has
    Loan "*" --> "1" Book : for
```

---

## Exercise 2: Animal Hierarchy (Class Diagram)

```mermaid
classDiagram
    class Animal {
        <<abstract>>
        #String name
        #int age
        +makeSound()* String
        +move()* void
        +eat() void
    }
    
    class Mammal {
        <<abstract>>
        #bool hasFur
        +giveBirth()
    }
    
    class Bird {
        <<abstract>>
        #double wingspan
        +layEggs()
    }
    
    class Dog {
        -String breed
        +makeSound() String
        +move() void
        +fetch()
        +bark()
    }
    
    class Cat {
        -bool isIndoor
        +makeSound() String
        +move() void
        +scratch()
        +purr()
    }
    
    class Eagle {
        -double maxAltitude
        +makeSound() String
        +move() void
        +hunt()
    }
    
    class Penguin {
        -bool canSwim
        +makeSound() String
        +move() void
        +swim()
    }
    
    Animal <|-- Mammal
    Animal <|-- Bird
    Mammal <|-- Dog
    Mammal <|-- Cat
    Bird <|-- Eagle
    Bird <|-- Penguin
```

---

## Exercise 3: School Database (ER Diagram)

```mermaid
erDiagram
    STUDENT {
        int id PK
        string first_name
        string last_name
        string email UK
        date birth_date
        date enrollment_date
    }
    
    TEACHER {
        int id PK
        string first_name
        string last_name
        string email UK
        int department_id FK
        date hire_date
    }
    
    COURSE {
        int id PK
        string code UK
        string name
        int credits
        int department_id FK
        int teacher_id FK
    }
    
    DEPARTMENT {
        int id PK
        string name UK
        string building
        int head_teacher_id FK
    }
    
    ENROLLMENT {
        int id PK
        int student_id FK
        int course_id FK
        string semester
        int year
        string grade
    }
    
    DEPARTMENT ||--o{ TEACHER : employs
    DEPARTMENT ||--o{ COURSE : offers
    TEACHER ||--o{ COURSE : teaches
    TEACHER |o--|| DEPARTMENT : heads
    STUDENT ||--o{ ENROLLMENT : has
    COURSE ||--o{ ENROLLMENT : has
```

---

## Exercise 4: Social Media (ER Diagram)

```mermaid
erDiagram
    USER {
        int id PK
        string username UK
        string email UK
        string password_hash
        string display_name
        text bio
        string avatar_url
        datetime created_at
    }
    
    POST {
        int id PK
        int user_id FK
        text content
        string image_url
        datetime created_at
        int like_count
        int comment_count
    }
    
    COMMENT {
        int id PK
        int post_id FK
        int user_id FK
        text content
        datetime created_at
    }
    
    LIKE {
        int id PK
        int user_id FK
        int post_id FK
        datetime created_at
    }
    
    FOLLOW {
        int id PK
        int follower_id FK
        int following_id FK
        datetime created_at
    }
    
    MESSAGE {
        int id PK
        int sender_id FK
        int receiver_id FK
        text content
        datetime sent_at
        boolean is_read
    }
    
    USER ||--o{ POST : creates
    USER ||--o{ COMMENT : writes
    USER ||--o{ LIKE : gives
    POST ||--o{ COMMENT : has
    POST ||--o{ LIKE : receives
    USER ||--o{ FOLLOW : "follows as follower"
    USER ||--o{ FOLLOW : "follows as following"
    USER ||--o{ MESSAGE : sends
    USER ||--o{ MESSAGE : receives
```

---

## Bonus: Complete SaaS Application

### Class Diagram

```mermaid
classDiagram
    class Tenant {
        -int id
        -String name
        -String subdomain
        -Plan plan
        +getUsers() List~User~
        +upgrade(Plan plan)
    }
    
    class User {
        -int id
        -String email
        -Role role
        +hasPermission(String perm) bool
    }
    
    class Plan {
        <<enumeration>>
        FREE
        STARTER
        PROFESSIONAL
        ENTERPRISE
    }
    
    class Role {
        <<enumeration>>
        ADMIN
        MEMBER
        VIEWER
    }
    
    class Subscription {
        -Date startDate
        -Date endDate
        -bool autoRenew
        +isActive() bool
        +cancel()
    }
    
    Tenant "1" --> "*" User : has
    Tenant "1" --> "1" Subscription : has
    Subscription "*" --> "1" Plan : for
    User --> Role : has
```

### ER Diagram

```mermaid
erDiagram
    TENANT {
        int id PK
        string name
        string subdomain UK
        string plan
        datetime created_at
    }
    
    USER {
        int id PK
        int tenant_id FK
        string email
        string role
        datetime created_at
    }
    
    SUBSCRIPTION {
        int id PK
        int tenant_id FK
        string plan
        date start_date
        date end_date
        boolean auto_renew
    }
    
    FEATURE {
        int id PK
        string name
        text description
    }
    
    PLAN_FEATURE {
        string plan
        int feature_id FK
        int limit_value
    }
    
    TENANT ||--o{ USER : has
    TENANT ||--|| SUBSCRIPTION : has
    FEATURE ||--o{ PLAN_FEATURE : ""
```

---

## Tips

1. **Class Diagrams** - Focus on relationships and behaviors
2. **ER Diagrams** - Focus on data structure and constraints
3. **Use PK/FK/UK** - Mark keys clearly in ER diagrams
4. **Visibility matters** - Use +/-/#/~ correctly in classes
5. **Name relationships** - Add labels to clarify connections
