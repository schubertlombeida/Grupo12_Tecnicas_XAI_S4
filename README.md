# Taller colaborativo S4 — Técnicas XAI, ética, sesgo y calidad de datos

Repositorio del **Grupo 12** para el taller práctico de la Semana 4 sobre explicabilidad, calidad de datos y sesgo en aprendizaje automático.

## Problema abordado

Se desarrolla un modelo supervisado para predecir si una persona registra ingresos anuales superiores a **USD 40.000**, usando un dataset salarial de una cervecería con variables laborales, salariales y sociodemográficas.

El proyecto no se limita a entrenar un modelo: documenta la calidad de los datos, revisa sesgos por sexo, aplica mitigación mediante ponderación, evalúa métricas de desempeño y equidad, y utiliza técnicas de explicabilidad XAI para transparentar las decisiones del modelo.

## Archivos principales

| Ruta | Contenido |
|---|---|
| `notebooks/Taller_Colaborativo_S4_Grupo12.ipynb` | Notebook principal con preparación de datos, entrenamiento, equidad y XAI. |
| `data/raw/Salarios_Cerveceria_con_sexo_2025.csv` | Dataset original utilizado en el notebook. |
| `data/processed/Salarios_Cerveceria_modelo_sin_identificadores.csv` | Dataset procesado sin ID, nombre ni notas. |
| `scripts/01_generar_visualizaciones.py` | Script reproducible para regenerar tablas y visualizaciones. |
| `docs/` | Documentación técnica, ética, XAI, rúbrica y guía de presentación. |
| `assets/figures/` | Gráficos generados para el portafolio. |
| `reports/` | Tablas de métricas, equidad, PFI, SHAP y LIME en CSV. |
| `index.html` | Página de revisión rápida para GitHub Pages o navegador local. |

## Resultados principales

- Registros analizados: **8,382**.
- Variable objetivo: `GanaMas40K`, creada a partir de `SalarioTotalConBeneficios * 12 > 40000`.
- Clase positiva: **6,995 registros (83.45%)**.
- Clase negativa: **1,387 registros (16.55%)**.
- Modelo base del notebook: **Random Forest Regressor con umbral 0.5**, usado como clasificador binario.
- Desempeño en prueba: accuracy, precision, recall y F1 iguales a **1.0000**.
- Métricas de equidad: diferencia de paridad demográfica **0.0285** e igualdad de oportunidades **0.0000**.
- Técnicas XAI documentadas: **Permutation Feature Importance, SHAP y LIME**.

## Cómo ejecutar

```bash
pip install -r requirements.txt
python scripts/01_generar_visualizaciones.py
python scripts/02_validacion_repositorio.py
```

Luego abrir el notebook:

```bash
jupyter notebook notebooks/Taller_Colaborativo_S4_Grupo12.ipynb
```

## Nota ética y de calidad

El dataset original contiene campos identificatorios (`ID` y `NombreEmpleado`). Para el modelado se eliminan esas columnas. En un repositorio público o compartido se recomienda conservar únicamente la versión procesada o verificar que los nombres sean ficticios/anónimos.

También se documenta una limitación metodológica importante: la variable objetivo se deriva de `SalarioTotalConBeneficios`, y esa variable permanece entre los predictores. Esto explica el desempeño perfecto y debe interpretarse como un caso de explicabilidad y auditoría, no como una solución lista para producción sin rediseño de variables.
