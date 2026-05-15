# 01 · Diseño de la base de datos

> [English version available here](README-EN.md)

Diseño e implementación inicial del esquema de la base de datos del marketplace. Se crean las dos tablas principales — `company` y `transaction` — a partir de archivos CSV y se documenta su relación.

**Herramientas:** MySQL  
**Habilidades:** DDL · Modelado entidad-relación · Claves foráneas · Importación de datos

---

## Contenido de esta carpeta

| Archivo | Descripción |
|---|---|
| `estructura_datos.sql` | Sentencias CREATE TABLE para `company` y `transaction` |
| `bbdd_transactions.sql` | Consultas SQL de análisis (Niveles 1–3) |
| `Informe_bbdd_transactions.pdf` | Documentación completa con diagramas y resultados |

---

## Esquema

Dos tablas conectadas por una relación 1:N — una empresa puede tener múltiples transacciones.

- **company** — `id` (PK), `company_name`, `phone`, `email`, `country`, `website`
- **transaction** — `id` (PK), `credit_card_id`, `company_id` (FK → company), `user_id`, `lat`, `longitude`, `timestamp`, `amount`, `declined`

---

## Consultas incluidas

- Países que están generando ventas (JOIN)
- Número de países con ventas activas (JOIN + COUNT DISTINCT)
- Compañía con la media de ventas más alta (JOIN + AVG)
- Todas las transacciones de empresas alemanas (subconsulta)
- Empresas con transacciones por encima de la media (subconsulta anidada)
- Empresas sin transacciones registradas (NOT IN / NOT EXISTS)
- Los 5 días con mayor volumen de ingresos (GROUP BY + SUM)
- Media de ventas por país (JOIN + AVG + ORDER BY)
- Transacciones de empresas en el mismo país que "Non Institute" (JOIN + subconsulta / solo subconsulta)
- Empresas con transacciones entre 350€ y 400€ en fechas concretas (BETWEEN + IN)
- Conteo de transacciones por empresa con umbral de 400 (CASE)
