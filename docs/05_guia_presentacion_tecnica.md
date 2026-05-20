# 06\. Guía para presentación técnica de 5 a 10 minutos

> 

## Duración sugerida

Entre 7 y 8 minutos.

## Estructura recomendada

### 1\. Introducción del problema — 1 minuto

Explicar que el proyecto busca predecir si una persona gana más de USD 40.000 anuales, pero con un enfoque responsable: calidad de datos, sesgo, mitigación y explicabilidad.

Mensaje clave:

> No basta con que un modelo acierte; también debe ser auditable, explicable y éticamente defendible.

### 2\. Dataset y calidad de datos — 1 minuto

Mencionar:

* Dataset con **8,382 registros**.
* Variables laborales, salariales y sociodemográficas.
* Valores faltantes en `HorasExtra`, `Beneficios` y `TipoContrato`.
* Eliminación de `ID`, `NombreEmpleado` y `Notas`.

Mostrar figura:

* `assets/figures/02\_valores\_faltantes.png`

### 3\. Sesgo por sexo — 1 minuto

Mencionar:

* Mujeres: **4,229 registros**.
* Hombres: **4,153 registros**.
* Diferencia pequeña en ingreso promedio y en proporción que supera USD 40K.

Mostrar figuras:

* `assets/figures/03\_ingreso\_promedio\_por\_sexo.png`
* `assets/figures/04\_brecha\_umbral\_40k\_por\_sexo.png`

### 4\. Modelo y métricas — 1.5 minutos

Explicar:

* Modelo: Random Forest Regressor con umbral 0.5.
* Train/test 80/20 con estratificación.
* Baseline clase mayoritaria vs modelo.
* El modelo alcanza métricas perfectas, pero se interpreta con cautela por posible fuga de información.

Mostrar figuras:

* `assets/figures/05\_matriz\_confusion.png`
* `assets/figures/06\_comparacion\_modelos\_baseline.png`

### 5\. Equidad — 1 minuto

Mencionar:

* Selection rate femenino: **0.8208**.
* Selection rate masculino: **0.8492**.
* Diferencia de paridad demográfica: **0.0285**.
* Diferencia de igualdad de oportunidades: **0.0000**.

Mostrar figura:

* `assets/figures/07\_metricas\_equidad\_por\_sexo.png`

### 6\. Técnicas XAI — 2 minutos

Presentar tres técnicas:

1. PFI: identifica la variable que más afecta el rendimiento.
2. SHAP: explica contribuciones globales y locales.
3. LIME: explica predicciones individuales.

Mostrar figuras:

* `assets/figures/08\_permutation\_feature\_importance.png`
* `assets/figures/09\_shap\_importancia\_global.png`
* `assets/figures/10\_comparacion\_pfi\_shap.png`
* `assets/figures/11\_shap\_waterfall\_instancia\_2.png`
* `assets/figures/12\_lime\_instancia\_2.png`

Mensaje clave:

> Las tres técnicas coinciden: el modelo depende principalmente de `SalarioTotalConBeneficios`.

### 7\. Conclusiones y recomendaciones — 1 minuto

Conclusiones:

* El modelo funciona muy bien para el dataset analizado.
* Las métricas de equidad son favorables.
* La explicabilidad revela una dependencia excesiva de la variable salarial total.
* Para producción, se requiere rediseñar el modelo sin variables que filtren la etiqueta.

Recomendaciones:

* Usar RandomForestClassifier o modelos de clasificación explícitos.
* Excluir variables derivadas del salario usado para crear la etiqueta.
* Aplicar validación cruzada.
* Mantener auditoría de equidad y XAI en cada actualización.

## Cierre sugerido

> Este taller demuestra que la IA responsable no se construye únicamente con precisión. Se construye con datos de calidad, evaluación de sesgos, explicabilidad y criterios éticos antes de tomar decisiones que puedan afectar a personas.

