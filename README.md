# Marketplace Transactions Analysis
 
> 📄 [Versión en español disponible aquí](README_es.md)
 
End-to-end data analysis project: from raw CSV files to a relational database in MySQL and an interactive Power BI dashboard exploring five years of sales data (2020–2024).
 
**Tools:** MySQL · Power BI · DAX  
**Skills:** Database design · SQL · Data modeling · Business storytelling
 
---
 
## What this project does
 
A fictional marketplace has been collecting transaction data across multiple countries, companies, credit cards, users and products. This project builds the data infrastructure from scratch and uses it to answer real business questions — including investigating a sustained sales decline in 2023–2024.
 
---
 
## The data
 
Six source files covering the full transaction ecosystem:
 
| Dataset | Description |
|---|---|
| `transactions.csv` | Core fact table — amount, date, card, company, user, product |
| `companies.csv` | Seller companies and their countries |
| `credit_cards.csv` | Card identifiers and account details |
| `american_users.csv` / `european_users.csv` | User demographics by region |
| `products.csv` | Product catalog |
 
---
 
## What I built
 
### 1. Relational database in MySQL
 
Designed and created a normalized relational schema from the raw CSVs, including entity-relationship diagrams at each stage. The schema evolved across the project as new tables were added (credit cards, users) and the model was progressively extended.
 
### 2. SQL analysis
 
Answered business questions using JOINs, subqueries, views and DML operations. Some examples:
 
- Which countries are generating sales, and how many?
- Which company has the highest average transaction value?
- Which companies have never made a transaction?
- What were the five highest-revenue days in the dataset?
- What is the average sale per country?
- Which companies compete with "Non Institute" in the same market?
Also built two SQL views for internal use:
- **VistaMarketing** — company name, country, average purchase amount
- **InformeTecnico** — transaction ID, user name, card IBAN, company name
### 3. Star schema redesign
 
Restructured the database as a star schema with `transactions` as the central fact table and `companies`, `credit_cards`, `users` and `products` as dimension tables. Added a card status table to flag active vs. inactive cards based on recent transaction history.
 
### 4. Power BI dashboard
 
Three analytical pages covering different angles of the same dataset:
 
**Trends, seasonality and geography**  
Revenue oscillates between $210K–$230K across the five years, with 2021 as the strongest year (consistently above the $220K target) and 2023 as the weakest. Northern Europe dominates supply, but user demand is more geographically distributed — the US, Spain and Canada show higher demand than local supply, pointing to potential expansion opportunities.
 
**User segmentation and product performance**  
The buyer profile has been stable for five years: adults aged 40–65 represent 42% of revenue. The 18–25 segment is the least exploited at 11%. On the product side, "Dooku solo" is one of the most sold items but generates lower revenue due to its low unit price; "Skywalker ewok" achieves the opposite — fewer sales but higher revenue per unit.
 
**Investigating the 2023–2024 sales drop**  
Average annual revenue dropped from $2,627K (2020–2022) to $2,579K (2023–2024). The investigation revealed two converging factors: effective transactions have been falling steadily since 2021 (from 10,272 to 9,913 in 2024), and the rejection rate nearly doubled from 0.14% in 2022 to 0.38% in 2024. The decline is not uniform — Germany (-18.37%) and China (-14.22%) are the hardest hit, while Canada (+14.08%) and the US (+9.99%) are growing. In Germany, a single company (Ac Fermentum Incorporated, -65.52%) accounts for most of the country-level drop.
 
---
 
## Key findings
 
- 2021 was the strongest year; 2023 the weakest — the gap is structural, not seasonal
- The transaction rejection rate nearly doubled between 2022 and 2024
- Germany's decline is concentrated in one company, not a market-wide trend
- The US, Spain and Canada represent underserved markets with growth potential
- The core buyer profile (adults 40–65) has not changed in five years — the 18–25 segment remains largely untapped
---
 
*Developed as part of the IT Academy Data Analytics Bootcamp, Barcelona.*
