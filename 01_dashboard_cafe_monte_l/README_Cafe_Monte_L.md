# Dashboard Comercial y Operativo — Café Monte L

Análisis integral de datos de ventas, producción y marketing para una empresa cafetalera. El proyecto integra seis fuentes de datos distintas en una tabla maestra y construye un dashboard interactivo con filtros dinámicos por región, canal y familia de producto.

## ¿Qué problema resuelve?

El área comercial necesitaba una herramienta que respondiera tres preguntas críticas de negocio:

1. ¿Qué regiones y canales están por debajo del presupuesto de ventas?
2. ¿Qué familias de producto tienen el margen más débil?
3. ¿Cómo se comporta la producción por planta y turno?

Este notebook responde las tres de forma interactiva, sin necesidad de exportar datos a Excel.

## Técnicas y herramientas

- **Integración de datos**: `pd.merge` encadenado para construir tabla maestra comercial-financiera desde 6 archivos CSV (Ventas, Productos, Clientes, Presupuesto, Producción, Marketing)
- **Limpieza de datos**: función `clean_numeric` para normalizar formatos monetarios y porcentuales
- **Dashboards interactivos**: `plotly.express` y `plotly.graph_objects` para gráficas, `ipywidgets` para segmentadores dinámicos
- **Tablas dinámicas**: `groupby` + `agg` para análisis de ventas vs. presupuesto por región, canal y familia
- **Análisis operativo**: KPIs de producción por planta, línea y turno
- **Exportación a PDF**: generación automática de reportes con `fpdf2`

## Estructura del proyecto

```
Cafe_Monte_L/
├── Cafe_Monte_L_notebook.ipynb   # Notebook principal
├── data/
│   ├── Ventas_Detalle_Raw.csv
│   ├── Catalogo_Productos.csv
│   ├── Catalogo_Clientes.csv
│   ├── Presupuesto.csv
│   ├── Produccion.csv
│   └── Marketing.csv
└── README.md
```

## Cómo ejecutar

```bash
pip install pandas numpy plotly ipywidgets fpdf2 Pillow
jupyter notebook Cafe_Monte_L_notebook.ipynb
```

Al iniciar el notebook, cargar los 6 archivos CSV cuando se solicite. Los segmentadores aparecerán automáticamente tras ejecutar todas las celdas.

## Resultados principales

- Dashboard comercial con análisis de ventas vs. presupuesto segmentable por región, canal y familia
- Dashboard operativo con KPIs de producción por planta y turno
- Reporte PDF exportable con todas las tablas dinámicas

## Librerías

`pandas` `numpy` `plotly` `ipywidgets` `fpdf2` `Pillow`
