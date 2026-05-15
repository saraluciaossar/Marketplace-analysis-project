# 02 · Table Management

> [Versión en español disponible aquí](README-ES.md)

Schema evolution sprint: the database is extended with two new tables (`credit_card` and `user`), data integrity is enforced through foreign keys, and two SQL views are created for internal use.

**Tools:** MySQL  
**Skills:** DDL · DML · ALTER TABLE · Views · Referential integrity · Data cleaning

---

## What's in this folder

| File | Description |
|---|---|
| `estructura_datos.sql` | Full schema including `credit_card` and `user` tables |
| `gestion_de_tablas.sql` | All DML and DDL operations performed in this sprint |
| `Informe_gestión_de_tablas.pdf` | Step-by-step walkthrough with diagrams and screenshots |

---

## Schema evolution

The model grows from 2 to 4 tables, with `transaction` as the central fact table:

- **credit_card** — `id` (PK), `iban`, `pin`, `cvv`, `expiring_date`
- **user** — `id` (PK), `name`, `surname`, `phone`, `email`, `birth_date`, `country`, `city`, `postal_code`, `address`
- `transaction.credit_card_id` → FK to `credit_card`
- `transaction.user_id` → FK to `user`

---

## Operations covered

- Design and creation of the `credit_card` table with FK to `transaction`
- Data import for `credit_card`
- IBAN correction for card ID `CcU-2938` (UPDATE)
- New transaction insert with test data (INSERT)
- Column removal: `pan` dropped from `credit_card` (ALTER TABLE)
- Transaction deletion by ID (DELETE)
- `VistaMarketing` view — company name, country, average purchase amount (ORDER BY DESC)
- `VistaMarketing` filtered by country (Germany)
- `user` table creation and data import
- FK constraint added from `transaction.user_id` to `user.id` (with orphan row fix)
- `InformeTecnico` view — transaction ID, user name and surname, card IBAN, company name
- Extended version `InformeTecnicoTransacciones` — adds national vs. international transaction classification
