---
name: restaurant-menu-catalog-architect
description: Models hierarchical restaurant menus, modifier groups (sizes, crusts, toppings), dietary allergens, combo sets, and real-time out-of-stock toggles.
---

# Restaurant Menu & Modifiers Catalog Architect

This skill directs schema modeling and category hierarchies for multi-brand and multi-branch restaurant menus.

## 1. Relational Schema Architecture

```text
Categories (e.g. Burgers, Pizzas, Drinks)
   └── MenuItems (e.g. Smash Burger, BBQ Chicken Pizza)
         └── ModifierGroups (e.g. Size, Cheese, Choice of Sauce)
               └── ModifierOptions (e.g. Regular +$0, Double Patty +$2.50)
```

## 2. Business Rules & Attributes
- **Modifier Group Constraints**:
  - `min_selection`: 1 (Mandatory single choice, e.g. Burger Bun type).
  - `max_selection`: 3 (Multiple choice limit, e.g. Max 3 Pizza Toppings).
- **Dietary & Allergen Flags**:
  - `is_halal`, `is_vegetarian`, `is_vegan`, `is_gluten_free`.
  - Allergen tags: `contains_peanuts`, `contains_dairy`, `contains_shellfish`.
- **Real-Time 86 / Out-of-Stock Toggle**:
  - Instant branch-level flag (`is_available: false`) that immediately deactivates the item across all digital menus, WhatsApp catalogs, and Voice bots.
