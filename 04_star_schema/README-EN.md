# 04 · Star Schema

> [Versión en español disponible aquí](README-ES.md)

Full database redesign using a star schema, built from raw CSV files. `transaction` becomes the central fact table surrounded by four dimension tables. A card status table is added to support operational monitoring.

**Tools:** MySQL  
**Skills:** Star schema design · CSV import · Subqueries · CTEs · Conditional logic · Data modeling

---

## What's in this folder

| File | Description |
|---|---|
| `estructura_datos.sql` | Star schema CREATE TABLE statements |
| `star_schema_queries.sql` | All queries for Levels 1–3 |
| `Informe_sprint4.pdf` | Full walkthrough with diagrams and results |

---

## Schema

`transaction` is the fact table. Four dimension tables surround it:

| Table | Role | Key fields |
|---|---|---|
| `transaction` | Fact | `id` (PK), `credit_card_id`, `company_id`, `user_id`, `product_id`, `amount`, `declined` |
| `company` | Dimension | `id` (PK), `company_name`, `country` |
| `credit_card` | Dimension | `id` (PK), `iban` |
| `user` | Dimension | `id` (PK), `name`, `surname`, `country` |
| `product` | Dimension | `id` (PK), `product_name`, `price`, `colour` |

---

## Queries covered

**Level 1**
- Users with more than 80 transactions (subquery, 2+ tables)
- Average transaction amount per IBAN for company "Donec Ltd" (2+ tables)

**Level 2**
- Card status table: `inactive` if the last 3 transactions were all declined, `active` otherwise
- Count of currently active cards

**Level 3**
- Product sales frequency — how many times each product has been sold
