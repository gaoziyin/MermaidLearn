# Gantt & Timeline Examples 📊

---

## Gantt Chart Examples

### 1. Simple Project

```mermaid
gantt
    title Simple Project
    dateFormat YYYY-MM-DD
    
    section Planning
    Requirements    :a1, 2024-01-01, 7d
    Design          :a2, after a1, 5d
    
    section Development
    Implementation  :b1, after a2, 14d
    Testing         :b2, after b1, 7d
    
    section Deployment
    Release         :c1, after b2, 2d
```

### 2. Software Development Sprint

```mermaid
gantt
    title 2-Week Sprint
    dateFormat YYYY-MM-DD
    excludes weekends
    
    section Sprint Planning
    Sprint planning     :done, sp, 2024-01-08, 1d
    
    section Development
    User Story 1        :done, us1, 2024-01-09, 3d
    User Story 2        :active, us2, after us1, 2d
    User Story 3        :us3, after us2, 3d
    Bug fixes           :crit, bug, after us3, 2d
    
    section QA
    Testing             :test, after bug, 2d
    
    section Sprint End
    Sprint Review       :milestone, review, after test, 0d
    Retrospective       :retro, after review, 1d
```

### 3. Product Launch

```mermaid
gantt
    title Product Launch Timeline
    dateFormat YYYY-MM-DD
    
    section Preparation
    Market research         :done, mr, 2024-01-01, 14d
    Product development     :done, pd, 2024-01-08, 30d
    Beta testing            :active, bt, after pd, 14d
    Bug fixes               :bf, after bt, 7d
    
    section Marketing
    Campaign planning       :cp, 2024-01-15, 21d
    Content creation        :cc, after cp, 14d
    Pre-launch promotion    :crit, pp, after cc, 7d
    
    section Launch
    Launch day              :milestone, crit, launch, 2024-03-15, 0d
    Post-launch support     :pls, after launch, 14d
    
    section Analysis
    Metrics collection      :mc, after launch, 30d
    Performance review      :pr, after mc, 7d
```

### 4. Website Redesign

```mermaid
gantt
    title Website Redesign Project
    dateFormat YYYY-MM-DD
    axisFormat %b %d
    
    section Discovery
    Stakeholder interviews  :done, si, 2024-01-01, 5d
    Analytics review        :done, ar, 2024-01-01, 3d
    Competitor analysis     :done, ca, after ar, 4d
    Requirements doc        :done, rd, after si ca, 3d
    
    section Design
    Wireframes              :done, wf, after rd, 7d
    Visual design           :active, vd, after wf, 10d
    Prototype               :proto, after vd, 5d
    Design approval         :milestone, da, after proto, 0d
    
    section Development
    Frontend development    :crit, fe, after da, 21d
    Backend integration     :be, after da, 14d
    CMS setup               :cms, after be, 5d
    
    section Testing
    QA testing              :qa, after fe cms, 10d
    UAT                     :uat, after qa, 5d
    Bug fixes               :bugs, after uat, 5d
    
    section Launch
    Staging deployment      :stage, after bugs, 2d
    Final review            :fr, after stage, 1d
    Production launch       :milestone, crit, launch, after fr, 0d
```

### 5. Event Planning

```mermaid
gantt
    title Conference Planning
    dateFormat YYYY-MM-DD
    excludes weekends, 2024-12-25, 2024-12-26
    
    section Venue
    Venue research      :v1, 2024-06-01, 14d
    Venue booking       :crit, v2, after v1, 7d
    Contract signing    :milestone, v3, after v2, 0d
    
    section Speakers
    Speaker outreach    :s1, 2024-06-15, 21d
    Speaker confirmation:s2, after s1, 14d
    Schedule finalization:s3, after s2, 7d
    
    section Marketing
    Website launch      :m1, 2024-07-01, 14d
    Early bird tickets  :m2, after m1, 30d
    Regular tickets     :m3, after m2, 60d
    
    section Logistics
    Catering arrangement:l1, 2024-09-01, 14d
    AV setup planning   :l2, 2024-09-15, 7d
    Final checklist     :l3, 2024-10-01, 7d
    
    section Event
    Conference Day 1    :milestone, crit, e1, 2024-10-15, 0d
    Conference Day 2    :milestone, e2, 2024-10-16, 0d
```

---

## Timeline Examples

### 1. Company History

```mermaid
timeline
    title Company Milestones
    2015 : Company founded
         : First product launch
    2016 : Seed funding ($1M)
         : Team grows to 10
    2017 : Series A ($10M)
         : 100 customers
    2018 : International expansion
         : Team grows to 50
    2019 : Series B ($50M)
         : 1000 customers
    2020 : Pandemic pivot
         : Remote-first culture
    2021 : Series C ($100M)
         : 10,000 customers
    2022 : IPO preparation
    2023 : Public offering
```

### 2. Technology Evolution

```mermaid
timeline
    title Frontend Framework Evolution
    
    section Early Web
        1995 : JavaScript created
             : First dynamic web pages
        1999 : AJAX introduced
             : Asynchronous requests possible
    
    section jQuery Era
        2006 : jQuery released
             : DOM manipulation simplified
        2010 : Mobile web grows
             : Responsive design needed
    
    section Modern Frameworks
        2013 : React by Facebook
        2014 : Vue.js released
        2016 : Angular 2 rewrite
    
    section Current Trends
        2020 : React Hooks mainstream
        2022 : Server Components
        2023 : AI-assisted coding
```

### 3. Project Roadmap

```mermaid
timeline
    title Q1-Q2 2024 Product Roadmap
    
    section Q1 2024
        January : Requirements gathering
                : Technical planning
        February : Core feature development
                 : Alpha testing begins
        March : Beta release
              : User feedback collection
    
    section Q2 2024
        April : Bug fixes
              : Performance optimization
        May : Feature enhancements
            : Documentation
        June : v1.0 Launch
             : Marketing campaign
```

### 4. Personal Development

```mermaid
timeline
    title My Learning Journey
    
    section Beginner
        Month 1 : HTML & CSS basics
                : First webpage
        Month 2 : JavaScript fundamentals
                : DOM manipulation
    
    section Intermediate
        Month 3-4 : React framework
                  : State management
        Month 5-6 : Backend with Node.js
                  : Database basics
    
    section Advanced
        Month 7-9 : Full-stack projects
                  : System design
        Month 10-12 : Cloud deployment
                    : DevOps practices
```

---

## Quick Reference

### Gantt Syntax
| Element | Syntax |
|---------|--------|
| Task | `taskname :id, start, duration` |
| After | `after taskid` |
| Done | `:done, id, start, duration` |
| Active | `:active, id, start, duration` |
| Critical | `:crit, id, start, duration` |
| Milestone | `:milestone, id, date, 0d` |
| Exclude | `excludes weekends` |

### Duration Units
| Unit | Example |
|------|---------|
| Days | `7d` |
| Weeks | `2w` |
| Hours | `8h` |
