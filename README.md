# Procesamiento y Limpieza de Datos: Kiva Crowdfunding 🌍💸

Este proyecto aplica las mejores prácticas de limpieza y preparación de datos sobre el dataset de **Kiva Crowdfunding**. El objetivo principal es transformar datos brutos en un conjunto estructurado y consistente, listo para análisis estadístico y modelado.

## 📝 Descripción del Proyecto

A través de un flujo de trabajo reproducible en Python (Jupyter Notebook), se han diagnosticado y corregido inconsistencias en más de 670,000 registros de préstamos. El proyecto abarca desde la normalización de tipos de datos hasta el análisis de la brecha de financiación.

## 🎯 Objetivos

- **Exploración**: Entender la calidad *raw* del dataset.
- **Limpieza**: Corregir formatos de fecha, normalizar textos y gestionar valores nulos de forma documentada.
- **Análisis**: Extraer conclusiones clave sobre el comportamiento de los microcréditos.
- **Reproducibilidad**: Garantizar que el proceso sea ejecutable de principio a fin.

## 🛠️ Tecnologías y Librerías

- **Entorno**: VS Code / Jupyter Notebooks.
- **Lenguaje**: Python 3.x.
- **Librerías clave**:
  - `pandas`: Manipulación y limpieza de datos.
  - `numpy`: Operaciones numéricas.


## 📂 Pasos Ejecutados

1.  **Importación y Diagnóstico**: Carga de datos y revisión de tipos (`info()`, `describe()`).
2.  **Tratamiento de Fechas**: Conversión de columnas de tiempo (`posted_time`, `funded_time`, etc.) a formato `datetime` y extracción de componentes temporales.
3.  **Gestión de Nulos**: 
    - Eliminación de la columna `tags` (25% de nulos).
    - Imputación de nulos en texto por "No especificado".
    - Imputación de nulos numéricos mediante la mediana.
    - Eliminación estratégica de filas con nulos críticos (0.36% en `disbursed_time`).
4.  **Normalización**: 
    - Limpieza de espacios en blanco y capitalización de textos.
    - Eliminación de columnas redundantes (`id`, `partner_id`, `country_code`).
    - Redondeo de montos financieros a dos decimales y conversión de conteos a enteros.
5.  **Análisis de Financiación**: Creación de métricas para identificar préstamos no completados y con cero financiación.

## 📊 Conclusiones Principales

Tras el procesamiento de los datos, se han obtenido los siguientes hallazgos:

* **Brecha de Financiación**: Se detectó que un **7.2% de los préstamos no llegan a completarse**. Esto indica una demanda significativa que la plataforma aún no logra cubrir totalmente.
* **Relación Solicitantes-Monto**: Existe una correlación positiva directa: a mayor número de personas solicitantes (`lender_count`), mayor es la cuantía del préstamo solicitado.
* **Geografía del Crédito**: Se identificaron los 10 países con mayor volumen de capital solicitado, permitiendo visualizar los focos de mayor actividad de microfinanzas.
* **Estacionalidad Mensual**: 
    - **Marzo** es el mes con mayor volumen (67,583 préstamos), posiblemente ligado al inicio de ciclos productivos o escolares.
    - A partir de **julio**, el volumen cae y se estabiliza.
    - Curiosamente, **enero y febrero** presentan los montos promedio más altos, a pesar de tener menos créditos concedidos.
* **Tendencia Anual**: El volumen de préstamos crece anualmente con picos en **octubre y noviembre**, sufriendo una caída drástica en diciembre. En los meses de mayor actividad, el monto promedio por préstamo disminuye, sugiriendo una diversificación hacia microcréditos de menor escala.

## 🚀 Cómo ejecutar el Notebook

1.  Clona este repositorio.
2.  Asegúrate de tener instaladas las librerías necesarias:
    ```bash
    pip install pandas numpy
    ```
3.  Coloca el archivo `kiva_loans.csv` dentro de una carpeta llamada `dataSet`.
4.  Abre el archivo `.ipynb` en VS Code o Jupyter y ejecuta todas las celdas.
5.  Al final de la ejecución, se generará un archivo con el dataset limpio en la raíz del proyecto.

## 💾 Exportación

El dataset final procesado se exporta automáticamente mediante:
```python
data.to_csv("kiva_loans_cleaned.csv", index=False)