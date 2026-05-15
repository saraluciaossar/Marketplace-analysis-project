# 04 · Esquema estrella

> [English version available here](README.md)

Rediseño completo de la base de datos usando un esquema estrella, construido a partir de archivos CSV. `transaction` pasa a ser la tabla de hechos central rodeada de cuatro tablas de dimensiones. Se añade una tabla de estado de tarjetas para el seguimiento operativo.

**Herramientas:** MySQL  
**Habilidades:** Diseño de esquema estrella · Importación de CSV · Subconsultas · CTEs · Lógica condicional · Modelado de datos

---

## Contenido de esta carpeta

| Archivo | Descripción |
|---|---|
| `estructura_datos.sql` | Sentencias CREATE TABLE del esquema estrella |
| `star_schema_queries.sql` | Todas las consultas de los Niveles 1–3 |
| `Informe_sprint4.pdf` | Documentación completa con diagramas y resultados |

---

## Esquema

`transaction` es la tabla de hechos. Cuatro tablas de dimensiones la rodean:

| Tabla | Rol | Campos clave |
|---|---|---|
| `transaction` | Hechos | `id` (PK), `credit_card_id`, `company_id`, `user_id`, `product_id`, `amount`, `declined` |
| `company` | Dimensión | `id` (PK), `company_name`, `country` |
| `credit_card` | Dimensión | `id` (PK), `iban` |
| `user` | Dimensión | `id` (PK), `name`, `surname`, `country` |
| `product` | Dimensión | `id` (PK), `product_name`, `price`, `colour` |

---

## Consultas incluidas

**Nivel 1**
- Usuarios con más de 80 transacciones (subconsulta, 2+ tablas)
- Media del importe por IBAN para la empresa "Donec Ltd" (2+ tablas)

**Nivel 2**
- Tabla de estado de tarjetas: `inactivo` si las últimas 3 transacciones fueron rechazadas, `activo` en caso contrario
- Recuento de tarjetas activas

**Nivel 3**
- Frecuencia de ventas por producto — cuántas veces se ha vendido cada producto
