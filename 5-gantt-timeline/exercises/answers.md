# Exercise Answers 📝

## Exercise 1: Sprint Planning (Gantt)

```mermaid
gantt
    title 2-Week Sprint
    dateFormat YYYY-MM-DD
    excludes weekends
    
    section Planning
    Sprint Planning     :done, plan, 2024-01-08, 1d
    
    section Development
    Feature A           :done, fa, 2024-01-09, 2d
    Feature B           :active, fb, after fa, 3d
    Feature C           :fc, after fb, 2d
    
    section Review
    Code Review         :crit, cr, after fc, 1d
    
    section Testing
    Unit Tests          :ut, 2024-01-09, 8d
    Integration Tests   :it, after cr, 2d
    
    section Sprint End
    Sprint Demo         :milestone, demo, 2024-01-19, 0d
```

---

## Exercise 2: Product Launch (Gantt)

```mermaid
gantt
    title Product Launch - 3 Month Plan
    dateFormat YYYY-MM-DD
    axisFormat %b %d
    
    section Marketing Prep
    Brand strategy          :done, bs, 2024-01-01, 14d
    Content creation        :done, cc, after bs, 21d
    Social media setup      :active, sm, 2024-01-15, 14d
    Press kit preparation   :pk, after cc, 7d
    Influencer outreach     :crit, io, after sm, 14d
    
    section Development
    Final features          :done, ff, 2024-01-01, 30d
    Bug fixes               :bf, after ff, 14d
    Performance testing     :pt, after bf, 7d
    Security audit          :crit, sa, after pt, 7d
    Release candidate       :milestone, rc, after sa, 0d
    
    section Beta Testing
    Private beta            :pb, 2024-02-01, 21d
    Feedback collection     :fc, after pb, 7d
    Final adjustments       :fa, after fc, 7d
    
    section Launch Activities
    Pre-launch buzz         :crit, plb, 2024-03-01, 14d
    Launch event            :milestone, crit, le, 2024-03-15, 0d
    Post-launch monitoring  :plm, after le, 14d
    
    section Support
    Customer support ready  :cs, 2024-03-01, 14d
    Documentation           :doc, 2024-02-15, 28d
    Training materials      :tm, after doc, 7d
```

---

## Exercise 3: Historical Timeline

```mermaid
timeline
    title History of JavaScript
    
    section Birth
        1995 : Created by Brendan Eich at Netscape
             : Originally called "Mocha" then "LiveScript"
             : Renamed to JavaScript for marketing
    
    section Standardization
        1997 : ECMAScript 1 standardized
        1999 : ECMAScript 3 released
             : Regular expressions added
             : Try/catch added
    
    section Dark Ages
        2000-2008 : Browser wars
                  : Fragmented implementations
                  : jQuery becomes essential (2006)
    
    section Renaissance
        2009 : ECMAScript 5 released
             : Node.js created
             : JSON native support
        2012 : TypeScript released
    
    section Modern Era
        2015 : ES6/ES2015 - Major update
             : Classes, modules, arrow functions
             : Promises, let/const
        2016 : ES2016 - Async/await preview
        2017 : ES2017 - Async/await official
    
    section Current
        2020 : Optional chaining (?.)
             : Nullish coalescing (??)
        2022 : Top-level await
             : Class fields
        2023 : Array methods
             : Hashbang grammar
```

---

## Exercise 4: Personal Project Timeline

```mermaid
timeline
    title My Portfolio Website Project
    
    section Planning
        Week 1 : Project idea conceived
               : Gathered inspiration
               : Created wireframes
    
    section Design
        Week 2 : Color palette chosen
               : Typography selected
               : High-fidelity mockups
    
    section Development
        Week 3 : HTML structure built
               : CSS styling applied
               : Responsive design
        Week 4 : JavaScript interactions
               : Contact form
               : Animations added
    
    section Content
        Week 5 : Project descriptions written
               : Images optimized
               : SEO metadata
    
    section Launch
        Week 6 : Testing completed
               : Domain purchased
               : Site deployed
               : Shared on social media
```

---

## Bonus: Complete Software Release

```mermaid
gantt
    title Software Release v2.0
    dateFormat YYYY-MM-DD
    excludes weekends, 2024-12-25, 2024-12-26, 2024-01-01
    
    section Phase 1 - Planning
    Requirements gathering      :done, req, 2024-10-01, 10d
    Technical design            :done, td, after req, 7d
    Architecture review         :done, ar, after td, 3d
    Sprint planning             :done, sp, after ar, 2d
    Planning complete           :milestone, done, pc, after sp, 0d
    
    section Phase 2 - Development
    Sprint 1 - Core features    :done, s1, 2024-10-28, 14d
    Sprint 2 - API development  :done, s2, after s1, 14d
    Sprint 3 - UI components    :active, s3, after s2, 14d
    Sprint 4 - Integration      :s4, after s3, 14d
    Development freeze          :milestone, crit, df, after s4, 0d
    
    section Phase 3 - Testing
    Unit testing                :ut, 2024-10-28, 56d
    Integration testing         :it, after s4, 10d
    Performance testing         :pt, after it, 5d
    Security testing            :crit, st, after pt, 5d
    UAT                         :uat, after st, 10d
    Testing complete            :milestone, tc, after uat, 0d
    
    section Phase 4 - Release
    Release candidate           :rc, after tc, 3d
    Documentation               :doc, 2024-12-01, 21d
    Staging deployment          :stage, after rc, 2d
    Final approval              :crit, fa, after stage doc, 1d
    Production release          :milestone, crit, prod, after fa, 0d
    
    section Phase 5 - Post-Release
    Monitoring                  :mon, after prod, 14d
    Bug fixes                   :bugs, after prod, 14d
    Retrospective               :retro, after bugs, 1d
```

---

## Tips

1. **Use milestones** - Mark important dates with `milestone`
2. **Critical path** - Use `crit` for must-do items
3. **Dependencies** - Use `after taskid` for sequencing
4. **Exclude dates** - Skip weekends and holidays
5. **Sections** - Group related tasks logically
6. **Good labels** - Make task names descriptive but concise
