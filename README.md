# Proyecto: Selección de Pozos Petrolíferos para OilyGiant

## Descripción del Proyecto
El objetivo de este proyecto es identificar los mejores lugares para abrir **200 nuevos pozos de petróleo** dentro de **OilyGiant**. Se requiere crear un modelo predictivo que estime el volumen de reservas en tres regiones y permita seleccionar los pozos con el mayor beneficio potencial, considerando el riesgo de pérdidas.

El presupuesto para el desarrollo de los pozos es de **100 millones de dólares**. El objetivo es maximizar las ganancias, asegurando que los pozos seleccionados generen un beneficio promedio de al menos **500,000 USD** por pozo.

---

## Metodología

### 1. Preparación de Datos
- **Archivos de entrada**: Se trabajó con tres conjuntos de datos que contienen características de los pozos petrolíferos en tres regiones (geo_data_0, geo_data_1, geo_data_2).
- **Características de los datos**: Cada archivo incluye el identificador del pozo, tres características (f0, f1, f2) y el volumen de reservas (en miles de barriles).

### 2. Modelado y Predicción
- **Regresión Lineal**: Se utilizó **regresión lineal** para predecir el volumen de reservas de los pozos.
- **Evaluación del Modelo**:
  - Para cada conjunto de datos se calculó el **RMSE** (Error Cuadrático Medio) y el **valor promedio de las reservas**.
  - Los **200 pozos con mayores reservas estimadas** fueron seleccionados para calcular el beneficio total de cada región.

### 3. Cálculo de Beneficios
- **Parámetros económicos**:
  - Ingreso por barril de petróleo: **4.5 USD**.
  - Ingreso por unidad de producto (miles de barriles): **4500 USD**.
  - El volumen de reservas en cada pozo fue comparado con el valor mínimo requerido de **111.1 miles de barriles** para asegurar un retorno positivo.
- **Beneficio Total**:
  - Se calculó el beneficio total de cada región sumando los ingresos de los **200 pozos seleccionados**.

---

## Resultados del Modelo

### Predicciones y RMSE

#### Para geo_data_0:
- **Valor promedio de las reservas**: **150.28 miles de barriles**.
- **RMSE**: **37.75** (indica errores de hasta 37.75 miles de barriles).

#### Para geo_data_1:
- **Valor promedio de las reservas**: **137.95 miles de barriles**.
- **RMSE**: **0.89** (muy bajo, indica alta precisión).

#### Para geo_data_2:
- **Valor promedio de las reservas**: **139.96 miles de barriles**.
- **RMSE**: **40.15** (indica errores de hasta 40.15 miles de barriles).

### Beneficios y Ganancias de Cada Región

#### Para geo_data_0:
- **Reserva Total**: **30055.95 miles de barriles**.
- **Beneficio Total**: **$135,265,298**.
- **Ganancia**: **$35,265,283**.

#### Para geo_data_1:
- **Reserva Total**: **27,589.08 miles de barriles**.
- **Beneficio Total**: **$124,163,283**.
- **Ganancia**: **$24,163,283**.

#### Para geo_data_2:
- **Reserva Total**: **27,991.05 miles de barriles**.
- **Beneficio Total**: **$125,972,340**.
- **Ganancia**: **$25,972,340**.
  
![Comparacion de Beneficios Promedio por Region()

---


## Análisis de Riesgos y Beneficios

Se aplicó **bootstrapping** con 1000 muestras para calcular los intervalos de confianza al 95% y evaluar el riesgo de pérdidas en cada región.

### Resultados del Bootstrapping:

![Comparacion de Metricas por Region]()

- **Geo_data_0** o **Region 0**:
  - **Intervalo de confianza (95%)**: **$-1,335,858.30 dolares** - **$8,806,768.80 dolares**.
  - **Riesgo de pérdidas**: **6.4%**.

- **Geo_data_1** o **Region 1**:
  - **Intervalo de confianza (95%)**: **$445,079.96 dolares** - **$8,580,398.28 dolares**.
  - **Riesgo de pérdidas**: **1.2%**.

- **Geo_data_2** o **Region 2**:
  - **Intervalo de confianza (95%)**: **$-1,421,772.78 dolares** - **$9,049,861.75 dolares**.
  - **Riesgo de pérdidas**: **8.3%**.

![Intervalos_Confianza_y_riesgo]('img/Intervalos_confianza_y_riego.png')

---
## Conclusiones:

- Elegimos el conjunto de datos geo_data_1 ya que es la que nos ofrece:

- Considerando la variabilidad de los pozos y siendo algo conservadores tenemos lo siguiente:
  - **La region 1** la que nos ofrece muy buenas reservas.
  - **La region 1** la nos ofrece un buen beneficio.
  - **La region 1** buenas ganancias.

- Apesar que el modelo de la region 0 tiene el mejor RMSE, osea que el modelo logra predecir con mayor eficacia y mayores reservas, y beneficio, la region 1 es la que desde un punto de vista conservador nos ofrece mejores oportunidades de asegurar un buen retorno de inversion sin perdidas.

---

Este análisis ayuda a **OilyGiant** a tomar decisiones informadas sobre la apertura de nuevos pozos, considerando tanto el potencial de reservas como los riesgos asociados. 
