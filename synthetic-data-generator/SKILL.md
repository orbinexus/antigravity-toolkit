---
name: synthetic-data-generator
description: Generates realistic, mathematically correlated synthetic datasets, database seeders, and mock records without privacy leakage or schema violations.
---

# Synthetic Data & Realistic Database Seeder

This skill generates high-volume, realistic, and relationally consistent mock data for integration testing, demos, and database benchmarking.

## 1. Relational Consistency & Realism

1. **Foreign Key Integrity**:
   - Generate parent records (Users, Organizations) before child records (Orders, Invoices, Audit Logs).
   - Maintain realistic distributions (e.g., 20% of users generate 80% of activity).
2. **Domain-Specific Realism**:
   - Use locale-appropriate names, phone numbers, postal codes, and tax identifiers.
   - Correlate interdependent fields (e.g., city matches state/province, order total equals sum of line items).
3. **Temporal Ordering**:
   - Ensure timestamps follow logical progression: `created_at <= updated_at <= deleted_at`.

## 2. High-Performance Bulk Seeding
- Generate raw SQL multi-row `INSERT` statements or streaming CSVs rather than firing individual ORM insertions.
- Batch operations in chunks of 1,000 to 5,000 records to maximize database write throughput.
