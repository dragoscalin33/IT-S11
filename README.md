# Sprint 11: Visualización de Datos

Este proyecto se centra en la conexión a una base de datos MySQL, la carga de datos en DataFrames de Pandas y la creación de una serie de visualizaciones para analizar patrones en datos de transacciones, productos y clientes.

## Herramientas Utilizadas

* **Python**
* **Pandas:** Para la manipulación y análisis de datos.
* **MySQL Connector:** Para la conexión con la base de datos.
* **Matplotlib y Seaborn:** Para la visualización de datos.

---

## Nivell 1: Conexión y Visualizaciones Básicas

En este nivel, se establece la conexión con la base de datos MySQL (`creacio_base_dades`) y se cargan todas las tablas en un diccionario de DataFrames para su análisis.

### 1. Histograma (Una variable numérica)

* **Gráfico:** Histograma del importe (`amount`) de las transacciones.
* **Observación:** Muestra la distribución de los importes de las transacciones.

### 2. Gráfico de Dispersión (Dos variables numéricas)

* **Gráfico:** `sns.lmplot` comparando el precio del producto (`price`) con el importe total de la transacción (`amount`).
* **Observación:** Analiza la relación entre el precio de los productos individuales y el valor total de la cesta de la compra.

### 3. Gráfico de Violín (Numérica vs. Categórica)

* **Gráfico:** `sns.violinplot` que muestra la distribución del importe (`amount`) frente al estado de la transacción (`declined`).
* **Observación:** Compara cómo se distribuyen los importes de las transacciones que fueron aceptadas (0) frente a las que fueron denegadas (1).

### 4. Gráfico Circular (Una variable categórica)

* **Gráfico:** `plot.pie` que muestra el porcentaje de transacciones aceptadas vs. denegadas.

### 5. Gráfico de Barras (Categórica vs. Numérica)

* **Gráfico:** `plot.bar` que muestra el importe medio (`amount`) de las transacciones agrupado por país (`country`), limitado al Top 5.

### 6. Gráfico de Barras Apiladas (Dos variables categóricas)

* **Gráfico:** `pd.crosstab` (gráfico de barras apiladas) que cruza el país (`country`) con el estado de la transacción (`declined`).

### 7. Gráfico de Dispersión con Tinte (Tres variables)

* **Gráfico:** `sns.lmplot` (similar al 2.2) de `price` vs. `amount`, pero utilizando `hue='declined'` para diferenciar por color las transacciones aceptadas y denegadas.

### 8. Pairplot

* **Gráfico:** `sns.pairplot` para visualizar las relaciones y distribuciones en pares entre `amount`, `price` y `weight`.

---

## Nivell 2: Visualizaciones Avanzadas

En este nivel, se profundiza en las relaciones entre variables mediante gráficos más complejos.

### 1. Matriz de Correlación (Heatmap)

* **Preparación:** Se realiza ingeniería de características (feature engineering) extrayendo `year`, `month`, `day` y `weekday` de la columna `timestamp`.
* **Gráfico:** `sns.heatmap` para mostrar la matriz de correlación between las variables numéricas (incluyendo las nuevas fechas, importe y geolocalización).
* **Interpretación:** Se analiza la correlación (o falta de ella) entre el importe y las variables de fecha o ubicación.

### 2. Jointplot (Gráfico de Densidad)

* **Gráfico:** `sns.jointplot` con `kind='kde'` (Kernel Density Estimation) para visualizar la densidad geográfica de las transacciones usando `longitude` y `lat`.
* **Interpretación:** El gráfico muestra los puntos calientes o "clústeres" donde se concentran la mayoría de las transacciones (Europa y Norteamérica).

---

## Nivell 3: Exportación para Power BI

### 1. Preparación de Datos

* Se exportan los DataFrames principales y los fusionados (como `merged_df_1`) a archivos CSV.
* **Objetivo:** Estos archivos están listos para ser importados en Power BI para la creación de un dashboard interactivo.

### 2. Cierre de Conexión

* Finalmente, se cierra la conexión con la base de datos MySQL para liberar recursos.
