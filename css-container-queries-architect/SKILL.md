---
name: css-container-queries-architect
description: Architects self-contained responsive UI components using CSS Container Queries (@container) that adapt gracefully to parent widget dimensions rather than global viewports.
---

# CSS Container Queries & Micro-Layout Architect

This skill guides the design of truly modular UI components that reconfigure their layout, typography, and density based on the size of their parent container.

## 1. Container Definition & Query Rules

1. **Defining Containment Context**:
   - Establish container contexts on parent wrappers:
     ```css
     .card-container {
       container-type: inline-size;
       container-name: card;
     }
     ```
2. **Conditional Component Layouts**:
   - Query container dimensions directly:
     ```css
     @container card (min-width: 450px) {
       .card-content {
         display: grid;
         grid-template-columns: 120px 1fr;
         gap: 1.5rem;
       }
     }
     @container card (max-width: 449px) {
       .card-content {
         display: flex;
         flex-direction: column;
       }
     }
     ```

## 2. Container Query Units
- Leverage container query units (`1cqw` = 1% container width, `1cqh` = 1% container height) for dynamic typographic scaling within isolated widgets.
