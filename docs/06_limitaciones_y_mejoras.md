# 07. Limitaciones y mejoras recomendadas

## Limitación principal: posible fuga de información

La variable objetivo `GanaMas40K` se crea a partir de:

```text
IngresoAnual = SalarioTotalConBeneficios * 12
```

Sin embargo, `SalarioTotalConBeneficios` permanece como predictor. Esto genera una relación directa entre variable explicativa y etiqueta, lo que explica:

- Accuracy perfecto.
- Matriz de confusión sin errores.
- Dominancia de `num__SalarioTotalConBeneficios` en PFI, SHAP y LIME.

## Por qué esto no invalida el taller

Para un ejercicio de explicabilidad, este caso es útil porque muestra cómo XAI detecta una variable dominante y ayuda a cuestionar el diseño del modelo. En otras palabras, XAI no solo sirve para explicar decisiones, sino también para auditar la calidad metodológica del sistema.

## Mejoras recomendadas

### 1. Modelo alternativo sin fuga de información

Entrenar una segunda versión eliminando:

- `SalarioTotalConBeneficios`
- `SalarioTotal`
- variables directamente derivadas del salario si el objetivo es predecir salario futuro o clasificación salarial.

### 2. Modelo de clasificación explícito

Usar:

- `RandomForestClassifier`
- `LogisticRegression`
- `DecisionTreeClassifier`
- `SVC`

Esto alinea la técnica con la naturaleza binaria del problema.

### 3. Validación cruzada

Agregar `cross_val_score` o `StratifiedKFold` para medir estabilidad del desempeño.

### 4. Evaluación de proxies

Analizar si `Cargo`, `Departamento`, `Oficina` o `TipoContrato` actúan como proxies de sexo u otras condiciones sensibles.

### 5. Documentación responsable

Agregar una Model Card con:

- Uso previsto.
- Usos no recomendados.
- Métricas de desempeño.
- Métricas de equidad.
- Riesgos éticos.
- Limitaciones del dataset.

## Correcciones puntuales sugeridas al notebook

1. Corregir el texto de análisis de sesgo que menciona cantidades superiores a 20.000 registros por sexo. Los valores correctos del dataset cargado son 4.229 registros femeninos y 4.153 masculinos.
2. Corregir el texto que menciona 86.0% y 85.3%; los porcentajes correctos están alrededor de 83.87% masculino y 83.05% femenino.
3. En la gráfica de métricas por género, evitar valores escritos manualmente y usar los datos reales de `tabla_equidad`.
4. Justificar expresamente el uso de `RandomForestRegressor` con umbral 0.5 o reemplazarlo por un clasificador.
