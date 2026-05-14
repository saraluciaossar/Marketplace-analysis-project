# Análisis de transacciones de un marketplace
> 📄 [English version available here](README.md)
 
Proyecto de análisis de datos end-to-end: desde archivos CSV en bruto hasta una base de datos relacional en MySQL y un dashboard interactivo en Power BI que explora cinco años de datos de ventas (2020–2024).
 
**Herramientas:** MySQL · Power BI · DAX  
**Habilidades:** Diseño de bases de datos · SQL · Modelado de datos · Storytelling con datos

![Dashboard overview](05_powerbi_dashboard/Dashboard_screenshot/overview.png)
---
 
## Qué hace este proyecto
 
Un marketplace ficticio ha estado registrando transacciones a lo largo de múltiples países, empresas, tarjetas de crédito, usuarios y productos. Este proyecto construye la infraestructura de datos desde cero y la utiliza para responder preguntas de negocio reales, incluyendo la investigación de una caída sostenida de ventas en 2023–2024.
 
---
 
## Los datos
 
Seis archivos fuente que cubren el ecosistema completo de transacciones:
 
| Dataset | Descripción |
|---|---|
| `transactions.csv` | Tabla de hechos principal — importe, fecha, tarjeta, empresa, usuario, producto |
| `companies.csv` | Empresas vendedoras y sus países |
| `credit_cards.csv` | Identificadores de tarjeta y datos de cuenta |
| `american_users.csv` / `european_users.csv` | Datos demográficos de usuarios por región |
| `products.csv` | Catálogo de productos |
 
---
 
## Qué construí
 
### 1. Base de datos relacional en MySQL
 
Diseñé y creé un esquema relacional normalizado a partir de los CSV en bruto, incluyendo diagramas entidad-relación en cada etapa. El esquema evolucionó a lo largo del proyecto a medida que se añadieron nuevas tablas (tarjetas de crédito, usuarios) y el modelo se fue extendiendo.
 
### 2. Análisis SQL
 
Respondí preguntas de negocio usando JOINs, subconsultas, vistas y operaciones DML. Algunos ejemplos:
 
- ¿Qué países están generando ventas y cuántos son?
- ¿Qué empresa tiene el valor medio de transacción más alto?
- ¿Qué empresas no han realizado ninguna transacción?
- ¿Cuáles fueron los cinco días de mayor facturación?
- ¿Cuál es la venta media por país?
- ¿Qué empresas compiten con "Non Institute" en el mismo mercado?
También construí dos vistas SQL para uso interno:
- **VistaMarketing** — nombre de empresa, país, importe medio de compra
- **InformeTecnico** — ID de transacción, nombre de usuario, IBAN de tarjeta, nombre de empresa
### 3. Rediseño en esquema estrella
 
Reestructuré la base de datos como un esquema estrella con `transactions` como tabla de hechos central y `companies`, `credit_cards`, `users` y `products` como tablas de dimensión. Añadí una tabla de estado de tarjetas para marcar tarjetas activas e inactivas en función del historial reciente de transacciones.
 
### 4. Dashboard en Power BI
 
Tres páginas analíticas que abordan el mismo dataset desde ángulos distintos:
 
**Tendencias, estacionalidad y geografía**  
Los ingresos oscilan entre $210K y $230K a lo largo de los cinco años, con 2021 como el año más fuerte (por encima del objetivo de $220K casi todo el año) y 2023 como el más débil. El norte de Europa domina la oferta, pero la demanda de usuarios está más repartida — EEUU, España y Canadá muestran más demanda que oferta local, lo que apunta a oportunidades de expansión.
 
**Segmentación de usuarios y rendimiento de productos**  
El perfil de comprador ha sido estable durante cinco años: los adultos de 40–65 años representan el 42% de los ingresos. El segmento de 18–25 años es el menos explotado, con solo el 11%. En productos, "Dooku solo" es uno de los más vendidos pero genera menos ingresos por su bajo precio unitario; "Skywalker ewok" hace lo contrario — menos ventas pero mayor ingreso por unidad.
 
**Investigando la caída de ventas 2023–2024**  
El promedio anual de ingresos cayó de $2.627K (2020–2022) a $2.579K (2023–2024). La investigación reveló dos factores que se suman: las transacciones efectivas caen de forma sostenida desde 2021 (de 10.272 a 9.913 en 2024) y la tasa de rechazo casi se duplicó, del 0,14% en 2022 al 0,38% en 2024. La caída no es uniforme — Alemania (-18,37%) y China (-14,22%) son los mercados más afectados, mientras que Canadá (+14,08%) y EEUU (+9,99%) crecen. En Alemania, una sola empresa (Ac Fermentum Incorporated, -65,52%) explica gran parte de la caída a nivel país.
 
---
 
## Conclusiones principales
 
- 2021 fue el año más fuerte; 2023 el más débil — la brecha es estructural, no estacional
- La tasa de rechazo de transacciones casi se duplicó entre 2022 y 2024
- La caída de Alemania está concentrada en una sola empresa, no es una tendencia de mercado
- EEUU, España y Canadá son mercados con demanda no cubierta y potencial de crecimiento
- El perfil de comprador principal (adultos 40–65) no ha cambiado en cinco años — el segmento 18–25 sigue sin explotar
---
 
*Proyecto desarrollado durante el bootcamp de Análisis de Datos de IT Academy, Barcelona.*
