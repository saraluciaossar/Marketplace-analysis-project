# 02 · Gestión de tablas

> [English version available here](README.md)

Sprint de evolución del esquema: la base de datos se amplía con dos nuevas tablas (`credit_card` y `user`), se garantiza la integridad referencial mediante claves foráneas y se crean dos vistas SQL para uso interno.

**Herramientas:** MySQL  
**Habilidades:** DDL · DML · ALTER TABLE · Vistas · Integridad referencial · Limpieza de datos

---

## Contenido de esta carpeta

| Archivo | Descripción |
|---|---|
| `estructura_datos.sql` | Esquema completo incluyendo las tablas `credit_card` y `user` |
| `gestion_de_tablas.sql` | Todas las operaciones DML y DDL realizadas en este sprint |
| `Informe_gestión_de_tablas.pdf` | Documentación paso a paso con diagramas y capturas |

---

## Evolución del esquema

El modelo crece de 2 a 4 tablas, con `transaction` como tabla de hechos central:

- **credit_card** — `id` (PK), `iban`, `pin`, `cvv`, `expiring_date`
- **user** — `id` (PK), `name`, `surname`, `phone`, `email`, `birth_date`, `country`, `city`, `postal_code`, `address`
- `transaction.credit_card_id` → FK a `credit_card`
- `transaction.user_id` → FK a `user`

---

## Operaciones incluidas

- Diseño y creación de la tabla `credit_card` con FK a `transaction`
- Importación de datos para `credit_card`
- Corrección de IBAN para la tarjeta `CcU-2938` (UPDATE)
- Inserción de nueva transacción con datos de prueba (INSERT)
- Eliminación de columna: `pan` eliminada de `credit_card` (ALTER TABLE)
- Eliminación de transacción por ID (DELETE)
- Vista `VistaMarketing` — nombre de empresa, país, media de compra (ORDER BY DESC)
- Filtrado de `VistaMarketing` por país (Alemania)
- Creación de la tabla `user` e importación de datos
- Restricción FK de `transaction.user_id` a `user.id` (con corrección de fila huérfana)
- Vista `InformeTecnico` — ID de transacción, nombre y apellido del usuario, IBAN de la tarjeta, nombre de la empresa
- Versión extendida `InformeTecnicoTransacciones` — añade clasificación de transacción nacional vs. internacional
