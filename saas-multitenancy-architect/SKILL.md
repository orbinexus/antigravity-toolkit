---
name: saas-multitenancy-architect
description: Designs multi-tenant SaaS architectures, organization switching, tenant isolation via PostgreSQL Row-Level Security (RLS), and RBAC permissions.
---

# Multi-Tenant SaaS & Tenant Isolation Architect

This skill guides the construction of secure, scalable B2B multi-tenant SaaS systems, organization switching workflows, and role-based access control.

## 1. Tenant Isolation Strategies

1. **Row-Level Security (Postgres RLS)**:
   - Attach a `tenant_id` foreign key to all tenant-scoped tables.
   - Enforce RLS policies: `CREATE POLICY tenant_isolation_policy ON <table> USING (tenant_id = current_setting('app.current_tenant_id')::uuid);`
   - Set connection-local tenant contexts dynamically in database middlewares.
2. **Data Leakage Prevention**:
   - Prevent cross-tenant IDOR attacks by binding database queries to session tenant contexts rather than trust client-supplied route params.

## 2. Organization & Membership Lifecycle
- Design models for `Organization`, `User`, `Membership` (linking User to Org with specific `Role`), and `Invitation`.
- Implement safe organization switching without invalidating the user's primary session.
