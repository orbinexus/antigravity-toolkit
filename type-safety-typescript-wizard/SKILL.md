---
name: type-safety-typescript-wizard
description: Eliminates any types, implements advanced generics, discriminated unions, template literals, and strict runtime validation.
---

# Bulletproof TypeScript & Type-Safety Wizard

This skill eliminates type-related runtime bugs through advanced TypeScript type gymnastics, zero-any policies, and runtime schema synchronization.

## 1. Type Architecture & Narrowing

1. **Zero-Any Policy**:
   - Strictly prohibit `any`. Use `unknown` when incoming data structure is undetermined, forcing runtime type narrowing (`typeof`, `instanceof`, user-defined type guards).
2. **Discriminated Unions**:
   - Model distinct state variants with explicit literal tags (e.g. `status: 'idle' | 'loading' | 'success' | 'error'`).
   - Use exhaustive `never` checks in `switch` statements to guarantee unhandled state cases trigger compile-time errors.
3. **Advanced Generics & Template Literals**:
   - Leverage `extends`, `keyof`, `infer`, and mapped types (`Partial`, `Pick`, `Omit`, `Record`) for DRY type models.
   - Use template literal types (e.g. `type Route = \`/\${string}\``) for strict URL and event routing contracts.

## 2. Runtime Schema Validation (Zod / Valibot)
- Parse all external boundaries (API responses, form inputs, environment variables) through Zod/Valibot schemas:
  `const User = z.object({ ... }); type User = z.infer<typeof User>;`
- Guarantees compile-time types match 100% of runtime reality.
