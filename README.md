# Grupo 12 — Técnicas XAI, Ética, Sesgo y Calidad de Datos

Repositorio académico desarrollado para el **Taller Colaborativo de la Semana 4** de la asignatura **Aprendizaje Automático**, correspondiente a la Maestría en Inteligencia Artificial. El proyecto integra modelado supervisado, evaluación de calidad de datos, análisis de sesgo, métricas de equidad y técnicas de explicabilidad de modelos mediante herramientas XAI.

---

## 1. Descripción general del proyecto

El repositorio presenta un caso práctico de aprendizaje automático aplicado a un dataset salarial de una cervecería. El objetivo es construir, evaluar y auditar un modelo supervisado capaz de predecir si una persona registra ingresos anuales superiores a **USD 40.000**, a partir de variables laborales, salariales y sociodemográficas.

El enfoque del trabajo no se limita al entrenamiento del modelo. También se documentan los aspectos críticos exigidos en la Semana 4:

- calidad y limpieza de datos;
- identificación de variables sensibles;
- análisis de sesgo por sexo;
- evaluación de métricas de desempeño y equidad;
- aplicación de técnicas de explicabilidad XAI;
- reflexión ética sobre el uso de modelos automatizados en decisiones laborales o salariales.

---

## 2. Objetivo general

Desarrollar un portafolio técnico reproducible que demuestre la aplicación de técnicas de explicabilidad, auditoría de sesgo y evaluación ética en un modelo de aprendizaje automático supervisado.

---

## 3. Objetivos específicos

- Preparar y revisar la calidad de un dataset salarial para uso en aprendizaje automático.
- Crear una variable objetivo binaria asociada al umbral de ingresos anuales superiores a USD 40.000.
- Entrenar un modelo supervisado y evaluar su desempeño con métricas de clasificación.
- Analizar posibles diferencias de desempeño y selección entre grupos definidos por sexo.
- Aplicar técnicas XAI como **Permutation Feature Importance**, **SHAP** y **LIME**.
- Documentar limitaciones metodológicas, riesgos éticos y oportunidades de mejora.
- Presentar los resultados de forma clara mediante notebook, documentación, reportes y página HTML de revisión.

---

## 4. Problema abordado

Se modela la variable objetivo **`GanaMas40K`**, construida a partir del ingreso anual estimado. La predicción busca clasificar si una persona supera o no el umbral de **USD 40.000 anuales**.

El caso permite revisar aspectos técnicos y éticos relevantes:

- uso de datos laborales y salariales;
- presencia de variables sociodemográficas;
- posibilidad de sesgo por sexo;
- necesidad de explicar las predicciones del modelo;
- importancia de documentar limitaciones antes de considerar cualquier uso real.

---

## 5. Dataset utilizado

Archivo principal:

```text
data/Salarios_Cerveceria_con_sexo_2025.csv
```

Resumen del dataset utilizado en el análisis:

| Elemento | Descripción |
|---|---|
| Registros analizados | 8.382 |
| Variable objetivo | `GanaMas40K` |
| Criterio de la variable objetivo | `SalarioTotalConBeneficios * 12 > 40000` |
| Clase positiva | Personas con ingreso anual superior a USD 40.000 |
| Clase negativa | Personas con ingreso anual igual o inferior a USD 40.000 |
| Variable sensible analizada | Sexo |

---

## 6. Metodología aplicada

El proyecto sigue un flujo completo de análisis:

1. **Carga y exploración de datos**  
   Revisión inicial del dataset, tipos de variables y estructura general.

2. **Calidad de datos**  
   Verificación de valores faltantes, posibles duplicados, variables identificatorias y consistencia de los campos.

3. **Preparación del modelo**  
   Construcción de la variable objetivo, selección de predictores, codificación y partición de datos.

4. **Entrenamiento supervisado**  
   Aplicación de modelos de clasificación para estimar la pertenencia a la clase positiva.

5. **Evaluación de desempeño**  
   Uso de métricas como accuracy, precision, recall, F1-score y matriz de confusión.

6. **Evaluación de equidad**  
   Revisión de métricas por grupo, diferencia de paridad demográfica e igualdad de oportunidades.

7. **Explicabilidad XAI**  
   Aplicación de técnicas globales y locales para interpretar el comportamiento del modelo.

8. **Reflexión ética**  
   Análisis de riesgos, limitaciones, posibles sesgos y recomendaciones para un uso responsable.

---

## 7. Técnicas XAI implementadas

| Técnica | Propósito |
|---|---|
| Permutation Feature Importance | Identificar la importancia global de las variables mediante cambios en el desempeño del modelo. |
| SHAP | Explicar la contribución de cada variable a las predicciones, tanto de forma global como individual. |
| LIME | Generar explicaciones locales para instancias específicas mediante aproximaciones interpretables. |

Estas técnicas permiten responder preguntas clave como:

- ¿Qué variables influyen más en la predicción?
- ¿Por qué una instancia específica fue clasificada como positiva o negativa?
- ¿El modelo se apoya en variables potencialmente sensibles o indirectamente discriminatorias?

---

## 8. Estructura del repositorio

```text
Grupo12_Tecnicas_XAI_S4/
│
├── README.md
├── index.html
├── requirements.txt
│
├── data/
│   └── Salarios_Cerveceria_con_sexo_2025.csv
│
├── notebooks/
│   └── Taller_Colaborativo_S4_Grupo12.ipynb
│
├── docs/
│   ├── 00_resumen_ejecutivo.md
│   ├── 01_metodologia_y_calidad_datos.md
│   ├── 02_entrenamiento_modelo_y_metricas.md
│   ├── 03_explicabilidad_xai.md
│   ├── 04_analisis_etico_reflexivo.md
│   ├── 05_guia_presentacion_tecnica.md
│   ├── 06_limitaciones_y_mejoras.md
│   └── diccionario_datos.md
│
├── assets/
│   └── figures/
│       ├── 01_distribucion_objetivo.png
│       ├── 02_valores_faltantes.png
│       ├── 03_ingreso_promedio_por_sexo.png
│       ├── 04_brecha_umbral_40k_por_sexo.png
│       ├── 05_matriz_confusion.png
│       ├── 06_comparacion_modelos_baseline.png
│       ├── 07_metricas_equidad_por_sexo.png
│       ├── 08_permutation_feature_importance.png
│       ├── 09_shap_importancia_global.png
│       ├── 10_comparacion_pfi_shap.png
│       ├── 11_shap_waterfall_instancia_102.png
│       ├── 11_shap_waterfall_instancia_2.png
│       ├── 12_lime_instancia_102.png
│       ├── 12_lime_instancia_2.png
│       └── 13_scores_individuales.png
│
└── reports/
    ├── Informe_Tecnico_XAI_Semana4_Grupo12.docx
    ├── Presentacion_Tecnica_XAI_S4_Grupo12 v2.0.pptx
    ├── README.md
    ├── brecha_genero_dataset.csv
    ├── casos_individuales.csv
    ├── comparacion_modelos_baseline.csv
    ├── equidad_por_sexo.csv
    ├── lime_instancia_102.csv
    ├── lime_instancia_2.csv
    ├── matriz_confusion.csv
    ├── metricas_equidad_globales.csv
    ├── metricas_modelo.csv
    ├── top_variables_pfi.csv
    └── top_variables_shap.csv
```

---

## 9. Archivos principales

| Ruta | Contenido |
|---|---|
| `notebooks/Taller_Colaborativo_S4_Grupo12.ipynb` | Notebook principal con preparación de datos, entrenamiento, evaluación, equidad y XAI. |
| `data/Salarios_Cerveceria_con_sexo_2025.csv` | Dataset utilizado para el análisis. |
| `docs/00_resumen_ejecutivo.md` | Síntesis ejecutiva del trabajo. |
| `docs/01_metodologia_y_calidad_datos.md` | Descripción metodológica y revisión de calidad del dataset. |
| `docs/02_entrenamiento_modelo_y_metricas.md` | Detalle del entrenamiento y métricas de desempeño. |
| `docs/03_explicabilidad_xai.md` | Desarrollo de técnicas XAI aplicadas. |
| `docs/04_analisis_etico_reflexivo.md` | Reflexión ética, sesgo, equidad y responsabilidad. |
| `docs/06_limitaciones_y_mejoras.md` | Limitaciones identificadas y propuestas de mejora. |
| `assets/figures/` | Visualizaciones generadas para explicar resultados. |
| `reports/` | Reportes, tablas CSV, informe técnico y presentación. |
| `index.html` | Página HTML de revisión rápida para la docente o evaluador. |
| `requirements.txt` | Dependencias necesarias para ejecutar el proyecto. |

---

## 10. Resultados principales documentados

| Indicador | Resultado |
|---|---:|
| Registros analizados | 8.382 |
| Clase positiva | 83,45 % |
| Clase negativa | 16,55 % |
| Accuracy en prueba | 1,0000 |
| Precision en prueba | 1,0000 |
| Recall en prueba | 1,0000 |
| F1-score en prueba | 1,0000 |
| Diferencia de paridad demográfica | 0,0285 |
| Igualdad de oportunidades | 0,0000 |

---

## 11. Interpretación crítica de resultados

El desempeño perfecto del modelo debe analizarse con cautela. La variable objetivo se construye a partir del ingreso anual estimado, y el dataset conserva variables salariales altamente relacionadas con dicha variable objetivo. Por tanto, existe una posible situación de **fuga de información** o dependencia directa entre predictores y variable objetivo.

Esta limitación no invalida el valor académico del ejercicio, pero exige interpretar el resultado como un caso de práctica para:

- auditoría de calidad de datos;
- identificación de sesgo;
- explicabilidad del modelo;
- reflexión ética;
- documentación de riesgos metodológicos.

Para un escenario productivo real, sería necesario rediseñar la variable objetivo, excluir predictores directamente derivados del salario final y validar el modelo con datos externos o temporales.

---

## 12. Consideraciones éticas

El proyecto reconoce que los modelos aplicados a contextos laborales o salariales pueden producir impactos sensibles. Por ello, se recomienda:

- eliminar variables identificatorias como ID y nombre antes del modelado;
- justificar el uso de variables sociodemográficas;
- evaluar métricas de equidad entre grupos;
- evitar decisiones automatizadas sin supervisión humana;
- documentar limitaciones del modelo;
- utilizar técnicas de explicabilidad para mejorar transparencia;
- no usar el modelo como herramienta real de decisión laboral sin rediseño, validación externa y revisión ética formal.

---

## 13. Reproducción del proyecto

### 13.1 Crear entorno virtual

En Windows:

```bash
python -m venv .venv
.venv\Scripts\activate
```

En macOS o Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 13.2 Instalar dependencias

```bash
pip install -r requirements.txt
```

### 13.3 Ejecutar el notebook

```bash
jupyter notebook notebooks/Taller_Colaborativo_S4_Grupo12.ipynb
```

También puede abrirse desde JupyterLab, Visual Studio Code o Google Colab, cargando previamente el dataset desde la carpeta `data/`.

---

## 14. Dependencias principales

El archivo `requirements.txt` incluye las bibliotecas necesarias para análisis de datos, modelado, visualización, explicabilidad y equidad:

- pandas
- numpy
- scikit-learn
- matplotlib
- seaborn
- shap
- lime
- fairlearn
- jupyter
- ipykernel

---

## 15. Página de revisión rápida

El archivo `index.html` permite revisar el portafolio de forma visual y rápida, incluyendo:

- resumen del proyecto;
- métricas principales;
- enlaces a la documentación;
- visualizaciones clave;
- resultados de XAI y equidad.

Para visualizarlo localmente, abrir el archivo:

```text
index.html
```

También puede publicarse mediante GitHub Pages si el repositorio tiene habilitada esa opción.

---

## 16. Cumplimiento académico

El repositorio contiene los productos esperados para una entrega técnica y documentada:

| Entregable | Ubicación |
|---|---|
| Notebook reproducible | `notebooks/Taller_Colaborativo_S4_Grupo12.ipynb` |
| Dataset | `data/Salarios_Cerveceria_con_sexo_2025.csv` |
| Reportes tabulares | `reports/*.csv` |
| Visualizaciones | `assets/figures/*.png` |
| Documentación técnica | `docs/*.md` |
| Informe técnico | `reports/Informe_Tecnico_XAI_Semana4_Grupo12.docx` |
| Presentación | `reports/Presentacion_Tecnica_XAI_S4_Grupo12 v2.0.pptx` |
| Página de revisión | `index.html` |
| Dependencias | `requirements.txt` |

---

## 17. Limitaciones y mejoras futuras

Limitaciones identificadas:

- posible fuga de información por variables salariales relacionadas directamente con la variable objetivo;
- uso de un dataset académico o simulado;
- resultados perfectos que requieren validación crítica;
- análisis de equidad limitado principalmente a la variable sexo;
- necesidad de validación externa con nuevos datos.

Mejoras sugeridas:

- rediseñar la variable objetivo;
- excluir variables que revelen directamente el resultado;
- incorporar validación temporal o externa;
- ampliar el análisis de equidad a otros grupos relevantes;
- comparar modelos más simples e interpretables;
- fortalecer la documentación con Model Cards y Datasheets for Datasets.

---

## 18. Conclusión

Este repositorio demuestra que un proyecto de Machine Learning responsable no debe concentrarse únicamente en la precisión del modelo. La calidad de los datos, la equidad, la explicabilidad y la documentación ética son componentes esenciales para construir soluciones confiables, auditables y socialmente responsables.

El trabajo del Grupo 12 evidencia la aplicación práctica de técnicas XAI y de evaluación de sesgo en un caso supervisado, generando un portafolio técnico útil para revisión académica, discusión ética y aprendizaje aplicado.
