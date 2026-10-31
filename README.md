## OilyGiant: Optimización de Ubicación de Pozos Petroleros mediante Machine Learning

Este es un proyecto de Ciencia de Datos y Machine Learning (ML) desarrollado para la compañía minera **OilyGiant**. El objetivo es identificar la región más rentable para perforar 200 nuevos pozos petroleros, maximizando el beneficio neto y mitigando el riesgo financiero a través de modelos predictivos y simulaciones de Bootstrap.

### Problema de Negocio y Objetivos

OilyGiant planea invertir **$100,000,000 USD** en el desarrollo de 200 pozos petroleros en una de tres regiones geográficas potenciales. Dado que los promedios generales de reservas en los territorios se encuentran por debajo del punto de equilibrio financiero, realizar perforaciones al azar garantiza pérdidas económicas severas. 

Este proyecto construye un pipeline de datos para:
1. **Predecir Reservas:** Entrenar un modelo de Regresión Lineal para cada región que estime el volumen de reservas (`product`) en función de tres características geológicas del subsuelo (`f0`, `f1`, `f2`).
2. **Análisis de Rentabilidad (*Break-Even*):** Calcular el volumen mínimo de petróleo requerido por pozo para cubrir los costos de inversión y desarrollo.
3. **Evaluación de Riesgo y Beneficio:** Implementar la técnica de Bootstrap (1,000 muestras) para construir una distribución de probabilidad de las ganancias, evaluar el intervalo de confianza del 95% y descartar regiones con un riesgo de pérdida superior al **2.5%**.

### Stack Tecnológico

* **Lenguaje:** Python 3
* **Manipulación de Datos:** Pandas, NumPy
* **Machine Learning:** Scikit-Learn (LinearRegression, train_test_split, mean_squared_error)
* **Visualización de Datos:** Matplotlib, Seaborn

###  Resultados y Hallazgos Clave

#### 1. Entrenamiento del Modelo (Conjunto de Validación 75:25)
* **Región 0:** Volumen promedio predicho = 92.61 u | RMSE = 37.69 (Alta incertidumbre)
* **Región 1:** Volumen promedio predicho = 68.58 u | RMSE = **0.89** (Ajuste lineal perfecto)
* **Región 2:** Volumen promedio predicho = 94.93 u | **RMSE = 40.08** (Mayor margen de error)

#### 2. Análisis de Rentabilidad (*Break-Even*)
* **Costo de Desarrollo por Pozo Individual:** $500,000.00 USD
* **Volumen Mínimo Requerido por Pozo:** **111.11 unidades** (miles de barriles)
* *Conclusión:* Como los promedios regionales oscilan entre 68 y 95 unidades, la perforación al azar genera pérdidas seguras. El filtrado predictivo mediante Machine Learning es estrictamente obligatorio.

#### 3. Simulación de Bootstrap (1,000 Muestras)
* **Región 0:** Ganancia promedio = $4.03M USD | IC 95% = [-$1.37M, $9.02M] | Riesgo de pérdida = 5.90% (RECHAZADA)
* **Región 1:** Ganancia promedio = **$4.39M USD** | IC 95% = [**$0.31M**, **$8.45M**] | **Riesgo de pérdida = 1.60% (SELECCIONADA)**
* **Región 2:** Ganancia promedio = $3.67M USD | IC 95% = [-$1.69M, $8.77M] | Riesgo de pérdida = 8.00% (RECHAZADA)

### Decisión Final y Veredicto

**Se selecciona la Región 1 para el despliegue industrial y la perforación de los pozos.**

Aunque la Región 1 registra el promedio de reservas en bruto más bajo de todo el estudio, sus características geológicas exhiben una relación lineal perfecta con el volumen de crudo. Esto permite que el modelo de Regresión Lineal alcance un RMSE casi nulo (0.89), eliminando la incertidumbre de exploración y permitiendo a los ingenieros seleccionar de forma quirúrgica los 200 mejores pozos del lote analizado, sin incurrir en "falsos positivos". Es la **única región** que cumple con la restricción corporativa de riesgo (< 2.5%) y ofrece, al mismo tiempo, la mayor utilidad neta operativa real ($4.39 millones de USD).

---
### Ver el análisis completo
👉 [Haz clic aquí para ver el código y los gráficos interactivos](optimizacion_seleccion_de_la_region_de_desarrollo_para_OilyGiant)
