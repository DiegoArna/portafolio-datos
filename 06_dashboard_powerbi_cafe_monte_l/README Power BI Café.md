# Dashboard Comercial, Operativo y Marketing — Café Monte L (Power BI)

Tablero ejecutivo interactivo construido en Power BI Desktop con datos reales de una empresa cafetalera mexicana. Integra seis fuentes de datos para monitorear ventas, producción y campañas de marketing desde una sola herramienta, con filtros dinámicos por región, canal y categoría.

> 🔗 [Ver dashboard interactivo](TU_LINK_AQUI)

---

## ¿Qué problema resuelve?

Los equipos de Ventas, Operaciones y Marketing trabajaban con reportes separados, sin visibilidad cruzada. Este dashboard unifica las tres áreas en un solo entorno, permitiendo a los líderes comerciales tomar decisiones con información oportuna y consistente.

## Preguntas de negocio que responde

- ¿Qué regiones y canales están por debajo del presupuesto de ventas?
- ¿Qué vendedores lideran en ingresos netos?
- ¿Qué planta y turno tienen mayor eficiencia de producción?
- ¿En qué SKUs se concentra la mayor merma?
- ¿Qué campañas de marketing generaron mejor CTR y más leads?

---

## Estructura del dashboard

### Página 1 — Comercial
- KPIs: Ventas Netas · Cumplimiento vs Presupuesto · Unidades Vendidas · Descuento Promedio
- Ventas Netas por Región (barras)
- Ventas vs Presupuesto Mensual (líneas)
- Ventas por Canal (dona)
- Top Vendedores (barras)
- Estado de Entregas (dona)
- Segmentadores: Región · Canal · Categoría

### Página 2 — Operativo
- KPIs: Unidades Buenas · % Merma · Eficiencia de Producción
- Producción por Planta (barras)
- Merma por SKU (barras)
- Eficiencia por Turno (columnas)
- Tiempo Muerto por Línea (barras)
- Segmentadores: Planta · Turno

### Página 3 — Marketing
- KPIs: Inversión Total · CTR · Leads Totales
- Inversión por Región (barras)
- Inversión por Canal (dona)
- Tabla de rendimiento por campaña: ID · Tipo · Inversión · Clics · Leads · CTR

---

## Fuentes de datos integradas

| Archivo | Contenido |
|---|---|
| `Ventas_Detalle_Raw.csv` | Pedidos con ingreso bruto, neto, descuentos, logística y devoluciones |
| `Catalogo_Productos.csv` | SKU, familia, precio de referencia, costo estándar y margen objetivo |
| `Catalogo_Clientes.csv` | Segmento, canal preferente, región, ejecutivo asignado y clasificación |
| `Presupuesto_Mensual.csv` | Presupuesto de ventas, margen y marketing por mes, región, canal y familia |
| `Produccion_Lotes_Raw.csv` | Lotes por planta, línea y turno con unidades, merma, horas máquina y costos |
| `Campanas_Marketing_Raw.csv` | Campañas con inversión, impresiones, clics, leads y meta de ventas |

## Modelo de datos

Las tablas se relacionan mediante:
- `Ventas` → `Catalogo_Productos` por `SKU`
- `Ventas` → `Catalogo_Clientes` por `ID_Cliente`
- `Ventas` → `Campanas_Marketing_Raw` por `Codigo_Promocion`
- `Produccion_Lotes_Raw` → `Catalogo_Productos` por `SKU`

## Medidas DAX principales

```
Ventas Netas = SUM(Ventas_Detalle_Raw[Ingreso_Neto])
Cumplimiento % = DIVIDE([Ventas Netas], [Presupuesto Ventas], 0)
% Merma = DIVIDE([Unidades Merma], SUM(Produccion_Lotes_Raw[Unidades_Producidas]), 0)
Eficiencia Producción = DIVIDE([Unidades Buenas], SUM(Produccion_Lotes_Raw[Unidades_Planeadas]), 0)
CTR = DIVIDE(SUM(Campanas_Marketing_Raw[Clics]), SUM(Campanas_Marketing_Raw[Impresiones]), 0)
```

---

## Herramientas

`Power BI Desktop` `DAX` `Power Query`

## Versión Python del análisis

Este mismo dataset fue analizado previamente en Python con pandas y Plotly.  
→ [Ver notebook](../01_dashboard_cafe_monte_l/Cafe_Monte_L_notebook.ipynb)
