# Proyecto: Optimización de Portafolio con Python y Excel Solver

Este proyecto demuestra un análisis de optimización de portafolio de inversión (Teoría de Markowitz) utilizando un flujo de trabajo híbrido con Python y Excel.

**Objetivo:** Encontrar la Frontera Eficiente para un portafolio de 5 acciones (Apple, Amazon, Google, JPMorgan, Microsoft) y determinar el portafolio de mínima varianza.

---

## 1. Fase de Python (Extracción y Procesamiento de Datos)

El notebook `Analisis_Portafolio.ipynb` realiza las siguientes tareas:

* **Extracción de Datos:** Utiliza `yfinance` para descargar 5 años de precios de cierre ajustados.
* **Cálculo de Retornos:** Procesa los datos con `pandas` para calcular los retornos diarios y luego anualizarlos.
* **Cálculo de Estadísticas:** Genera los dos inputs clave para el modelo:
    1.  El vector de **Retornos Promedio Anualizados**.
    2.  La **Matriz de Varianza-Covarianza Anualizada**.
* **Exportación:** Guarda estos dos resultados en el archivo `Datos_Portafolio_para_Solver.xlsx`.

## 2. Fase de Excel (Modelado y Optimización)

El archivo `Datos_Portafolio_para_Solver.xlsx` contiene el modelo financiero:

* **Motor del Modelo:** Se utilizan las fórmulas `SUMAPRODUCTO` (para el retorno) y `MMULT` (para la varianza del portafolio).
* **Optimización (Solver):**
    1.  Se utiliza el complemento **Solver** para encontrar el **Portafolio de Mínima Varianza** (minimizando la volatilidad).
    2.  Se vuelve a usar Solver repetidamente (añadiendo una restricción de retorno) para trazar los puntos de la **Frontera Eficiente**.
* **Resultado Final:** El gráfico de la Frontera Eficiente que muestra la relación óptima entre riesgo y retorno.

## Herramientas Utilizadas

* **Python** (vía Jupyter Notebooks en VS Code)
    * `pandas`
    * `yfinance`
    * `matplotlib`
* **Microsoft Excel**
    * Fórmulas matriciales (`MMULT`, `TRANSPONER`)
    * Complemento **Solver**

