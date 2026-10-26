---
name: restaurant-order-fsm-engine
description: Implements a conversational Finite State Machine (FSM) for multi-step restaurant ordering (item customization, modifier validation, cart calculation, delivery address).
---

# Conversational Restaurant Order State Machine (FSM)

This skill guides the design of deterministic, multi-turn conversational order-taking workflows across WhatsApp, Web Chat, and Voice AI.

## 1. FSM State Diagram & Transitions

```text
[IDLE / GREETING]
       │
       ▼
[BROWSING_MENU] ──► [ITEM_SELECTED]
                          │
                          ▼
                  [SELECTING_MODIFIERS] (Size, Crust, Extra Toppings, Dietary notes)
                          │
                          ▼
                  [CART_UPDATED] ◄──┐
                    │               │ (Add more items)
                    ├──► [CONTINUE_SHOPPING]
                    │
                    ▼
           [PROMPT_UPSELL] (Combos, Drinks, Desserts)
                    │
                    ▼
           [COLLECT_DELIVERY_INFO] (Dine-in table / Takeaway / Delivery Address)
                    │
                    ▼
           [ORDER_SUMMARY_REVIEW] (Itemized list + Tax + Delivery Fee + Total)
                    │
                    ▼
           [PAYMENT_METHOD] (Cash on Delivery / Online Card / Apple Pay)
                    │
                    ▼
           [CONFIRMED & KITCHEN_DISPATCH]
```

## 2. Cart Data Structure & Validation Rules
- Enforce mandatory modifier groups (e.g. user cannot proceed without picking a Pizza Size).
- Validate minimum and maximum selections (e.g. "Choose up to 3 free sauces").
- Recalculate totals dynamically: `Base Price + Sum(Selected Modifiers) * Quantity`.
