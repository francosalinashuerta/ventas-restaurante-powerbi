# 🍽️ Análisis de Ventas — Sector Gastronómico

## 🎯 Objetivo

Transformar un dataset de ventas de restaurante con datos incompletos en un ecosistema de BI confiable, identificando patrones de consumo, productos estrella y tendencias de crecimiento mensual.

---

## 📁 Estructura del repositorio

```
ventas-restaurante-powerbi/
│
├── restaurant_etl.ipynb           # ETL y limpieza de datos con Python
├── restaurant_sales_data.csv      # Dataset original
├── Cleaned Restaurant Sales.csv   # Dataset limpio generado tras el ETL
├── Dashboard_Sales_Restaurant.pbix # Dashboard ejecutivo en Power BI
└── README.md
```

---

## 🛠️ Stack utilizado

- **Python** — Pandas, NumPy (ETL y limpieza)
- **Power BI** — Modelado de datos, DAX, dashboard ejecutivo

---

## ⚙️ Flujo de trabajo

### Fase 1 — ETL con Python (`restaurant_etl.ipynb`)
- Inspección inicial: shape, tipos de datos, duplicados y nulos
- Normalización de tipos de datos (fechas, numéricos)
- Imputación de método de pago faltante con `ffill()`
- Reconstrucción algebraica de métricas financieras faltantes:
  - `Order Total` = `Price × Quantity` cuando ambos están disponibles
  - `Price` = `Order Total / Quantity` cuando el precio falta
  - `Quantity` = `Order Total / Price` cuando la cantidad falta
- Imputación de ítems faltantes por moda según categoría y precio
- Exportación del dataset limpio a CSV

### Fase 2 — Dashboard en Power BI
- Modelado de datos y creación de medidas DAX
- KPIs dinámicos: ventas totales, ticket promedio, número de pedidos
- Análisis de tendencia mensual con comparativa vs mes anterior
- Distribución de ingresos por categoría, método de pago y cliente

---

## 💡 Hallazgos principales

**1. Main Dishes es el motor financiero**
La categoría concentra el mayor porcentaje de los ingresos totales del negocio.

**2. Crecimiento mensual sostenido**
Se identificó un crecimiento del 6.6% en ventas respecto al mes anterior en el último período analizado.

**3. Pasta Alfredo como producto ancla**
Es el ítem más vendido por cantidad, consolidándose como el producto de mayor rotación del menú.

**4. Distribución equilibrada de métodos de pago**
Los tres métodos (efectivo, tarjeta de crédito y billetera digital) tienen participaciones similares, sin dependencia de un solo canal.

---

## 📂 Dataset

- **Fuente:** Dataset de práctica — registros de ventas de restaurante (2022–2023)
- **Registros:** 17,534 órdenes brutas / 17,104 tras limpieza
- **Facturación total:** $340,617.50 USD
- **Variables:** categoría, ítem, precio, cantidad, total, fecha, método de pago

---

## ▶️ Cómo ejecutar

1. Clona el repositorio
```bash
git clone https://github.com/francosalinashuerta/ventas-restaurante-powerbi.git
cd ventas-restaurante-powerbi
```

2. Instala las dependencias
```bash
pip install pandas numpy
```

3. Ejecuta el notebook de ETL
```bash
jupyter notebook restaurant_etl.ipynb
```

4. Abre el archivo `.pbix` en Power BI Desktop para explorar el dashboard

---

*Proyecto de análisis de datos — portafolio personal*
