# 04. Análisis interpretativo y reflexivo

## Transparencia del modelo

El modelo es transparente en la medida en que sus predicciones fueron auditadas con técnicas XAI. PFI, SHAP y LIME permiten identificar qué variables influyen más y cómo afectan predicciones individuales.

El principal hallazgo interpretativo es que `SalarioTotalConBeneficios` domina la decisión del modelo. Esta explicación es técnicamente coherente porque la variable objetivo `GanaMas40K` se deriva del ingreso anual calculado con esa misma base salarial.

## Riesgos éticos y sociales

Aunque el modelo alcanza desempeño perfecto y métricas de equidad favorables, existen riesgos si se implementa sin controles:

1. **Riesgo de automatizar decisiones laborales sensibles**  
   Un modelo de predicción salarial podría ser mal utilizado para decisiones de contratación, promoción, compensación o segmentación de personas.

2. **Riesgo de falsa confianza por desempeño perfecto**  
   La precisión de 1.0000 puede generar la impresión de que el sistema es infalible. En realidad, el resultado se explica por la relación directa entre la etiqueta y una variable predictora.

3. **Riesgo de privacidad**  
   El dataset original contiene identificadores y nombres. Aunque se eliminan del modelo, deben protegerse si el repositorio se publica.

4. **Riesgo de variables proxy**  
   Aun cuando `Sexo` no aparezca como variable dominante, otras variables como cargo, departamento, oficina o tipo de contrato podrían actuar como proxies de diferencias estructurales.

5. **Riesgo de decisiones no explicadas**  
   Sin XAI, sería difícil detectar la dependencia excesiva del modelo respecto de una sola variable.

## Sesgo y equidad

El análisis inicial muestra una diferencia pequeña por sexo:

- Mujeres que superan USD 40K: **83.05%**.
- Hombres que superan USD 40K: **83.87%**.
- Diferencia aproximada: **0.82 puntos porcentuales**.

Tras el entrenamiento, las métricas de equidad son favorables:

- Diferencia de paridad demográfica: **0.0285**.
- Diferencia de igualdad de oportunidades: **0.0000**.

Esto sugiere que el modelo no produce diferencias severas entre grupos en el conjunto de prueba. Sin embargo, la equidad debe evaluarse de forma continua, especialmente si el modelo se aplica a datos nuevos o reales.

## ¿Qué aprendizaje se desarrolló sobre cómo el modelo toma decisiones?

El aprendizaje principal es que la explicabilidad permite pasar de una métrica general a una comprensión causal-operativa del comportamiento del modelo. El modelo no solo “acierta”; acierta porque tiene acceso a una variable que prácticamente determina la etiqueta.

## ¿Hay una variable con peso excesivo?

Sí. `SalarioTotalConBeneficios` tiene un peso excesivo. Esta situación es útil para demostrar cómo las técnicas XAI detectan dependencia de variables, pero también evidencia una limitación para uso real.

## ¿Qué pasaría si se implementa sin explicabilidad?

Sin explicabilidad, se podría concluir erróneamente que el modelo es excelente solo por sus métricas. No se detectaría que la predicción depende de una variable directamente relacionada con la etiqueta. Tampoco habría evidencia suficiente para auditar sesgos, justificar decisiones o identificar variables proxy.

## Consideraciones para mejorar el modelo

1. Entrenar una versión alternativa excluyendo `SalarioTotalConBeneficios` y variables derivadas directamente del salario objetivo.
2. Probar un `RandomForestClassifier` o modelos de clasificación explícitos.
3. Incorporar validación cruzada.
4. Evaluar estabilidad de métricas de equidad en diferentes particiones.
5. Documentar Model Card y Datasheet del dataset.
6. Mantener un protocolo de revisión humana antes de cualquier decisión sobre personas.

## Conclusión ética

El proyecto demuestra que un modelo de alto desempeño no necesariamente es suficiente. La calidad de datos, la equidad y la explicabilidad son componentes obligatorios para evitar decisiones automatizadas opacas o injustas. XAI permitió detectar tanto la coherencia del modelo como su principal limitación, fortaleciendo el enfoque de IA responsable.
