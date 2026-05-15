# 01 · Database Design

> [Versión en español disponible aquí](README-ES.md)

Initial schema design for the marketplace database. Two core tables — `company` and `transaction` — are created from raw CSV files and their relationship is documented.

**Tools:** MySQL  
**Skills:** DDL · Entity-relationship modeling · Foreign keys · Data import

---

## What's in this folder

| File | Description |
|---|---|
| `estructura_datos.sql` | CREATE TABLE statements for `company` and `transaction` |
| `bbdd_transactions.sql` | SQL analysis queries (Levels 1–3) |
| `Informe_bbdd_transactions.pdf` | Full walkthrough with diagrams and query results |

---

## Schema

Two tables connected by a 1:N relationship — one company can have many transactions.

- **company** — `id` (PK), `company_name`, `phone`, `email`, `country`, `website`
- **transaction** — `id` (PK), `credit_card_id`, `company_id` (FK → company), `user_id`, `lat`, `longitude`, `timestamp`, `amount`, `declined`

---

## Queries covered

- Countries generating sales (JOIN)
- Number of countries with active sales (JOIN + COUNT DISTINCT)
- Company with the highest average transaction value (JOIN + AVG)
- All transactions from German companies (subquery)
- Companies with above-average transaction amounts (nested subquery)
- Companies with no registered transactions (NOT IN / NOT EXISTS)
- Top 5 highest-revenue days (GROUP BY + SUM)
- Average sales per country (JOIN + AVG + ORDER BY)
- Transactions from companies in the same country as "Non Institute" (JOIN + subquery / subquery only)
- Companies with transactions between €350–€400 on specific dates (BETWEEN + IN)
- Transaction count per company flagged above or below 400 (CASE)
