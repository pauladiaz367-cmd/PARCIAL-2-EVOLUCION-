# PARCIAL-2-EVOLUCION-Grupo 5 — Algoritmo de Colonia Artificial de Abejas (ABC)

**Notebook:** [Colab Grupo 5 - ABC](https://colab.research.google.com/drive/1CHUu9lhBlIp33Lv5osxFD82KRf4akXFL)  
**Proyecto:** Selección de genes para clasificación binaria  
**Fecha:** 12 de noviembre de 2025  
**Integrantes:** Maria Paula Diaz Melo
                 Valentina Gisselle Castañeda Diaz 

   📊 Descripción general

Este proyecto implementa el algoritmo **Artificial Bee Colony (ABC)** para resolver un problema de **selección de características genéticas** en un conjunto de datos con etiquetas binarias (0/1).  
El objetivo es **maximizar la capacidad de discriminación entre clases**, optimizando la combinación de genes mediante una analogía con el proceso de **forrajeo de abejas**.

---

## 🧬 Datos utilizados

- **Archivos de entrada:**
  - `expression.csv`: matriz de expresión génica (filas = muestras, columnas = genes).  
  - `expression_labels.csv`: etiquetas de clase (0 = control, 1 = caso).  
  - `matriz_forrajeo_abejas.xlsx`: matriz que representa la **dinámica de búsqueda y explotación** de recursos por las abejas artificiales.  
    - Cada fila corresponde a una abeja empleada y cada columna refleja una **dimensión del espacio de búsqueda** (por ejemplo, genes seleccionados o explorados).  
    - Los valores numéricos expresan el **nivel de exploración (movimiento)** o **explotación (refinamiento)** de las soluciones en cada ciclo.  
    - Esta matriz se utiliza para **visualizar la evolución del comportamiento colectivo** y analizar cómo las abejas convergen hacia las regiones más prometedoras del espacio de soluciones.

- **Preprocesamiento:**
  - Normalización min-max.
  - Filtrado de genes con baja varianza.
  - Representación binaria de subconjuntos de genes mediante una **máscara 0/1**.

---

## 🧮 Función de aptitud (fitness)

\[
\text{Fitness} = \text{Fisher Score agregado} - \lambda \times |S|
\]

donde  
- \( S \) = subconjunto seleccionado de genes,  
- \( \lambda \approx 0.01 \) penaliza subconjuntos demasiado grandes.  
El objetivo es **maximizar** el valor de fitness.

---

## 🐝 Hiperparámetros del algoritmo ABC

| Parámetro | Valor usado |
|------------|--------------|
| Número de abejas empleadas (SN) | 30 |
| Límite de abandono (`limit`) | 20 |
| Ciclos máximos | 300 |
| Representación | Vector binario (longitud = número de genes) |
| Operaciones clave | Empleada → Observadora → Exploradora |
| Condición de paro | Ciclos máximos **o** 30 sin mejora |

---

## 🔁 Reproducibilidad

- Se usa `np.random.default_rng(SEED)` para fijar semillas.  
- Se realizaron **3 corridas independientes** con semillas distintas.  
- Se reporta el **promedio ± desviación estándar** del fitness final.  
- Se documentan versiones de librerías (`NumPy`, `pandas`, `matplotlib`).

---

## 📈 Resultados principales

- **Curva de convergencia:** muestra mejora del fitness en las primeras 150 iteraciones y estabilización posterior.  
- **Subset óptimo:** promedio de 18–22 genes seleccionados.  
- **Fitness promedio final:** ≈ 0.87 ± 0.03.  
- **Visualización:** gráfico del progreso del mejor fitness y número de genes seleccionados por ciclo.

---

## ▶️ Cómo ejecutar

1. Abrir el [notebook en Google Colab](https://colab.research.google.com/drive/1CHUu9lhBlIp33Lv5osxFD82KRf4akXFL).  
2. Subir los archivos `expression.csv`, `expression_labels.csv` y `matriz_forrajeo_abejas.xlsx` a la carpeta de trabajo.  
3. Ejecutar todas las celdas en orden desde “Cargar datos” hasta “Resultados finales”.  

---

## 🎥 Video explicativo

El video del Grupo 5 presenta:
- Analogía entre el **forrajeo de abejas** y la **búsqueda de soluciones óptimas**.  
- Descripción paso a paso del **seudocódigo del ABC**.  
- Ejecución práctica del notebook en Colab.  
- Interpretación de los resultados y conclusiones.

---


