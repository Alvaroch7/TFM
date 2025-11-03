# Trabajo Final de Máster

**Título:** *"Segmentación de Imágenes cardíacas"*  
**Autor:** Álvaro Cámara Higueras  

**Máster:** Big Data y Ciencia de Datos  
**Universidad:** Universidad Internacional de Valencia (VIU)  

---

## Descripción

Este proyecto tiene como objetivo desarrollar y validar un sistema de segmentación automática de estructuras cardíacas en imágenes médicas tridimensionales obtenidas mediante resonancia magnética, utilizando redes neuronales convolucionales basadas en la arquitectura **3D U-Net**.

El repositorio incluye los scripts de entrenamiento, predicción y evaluación del modelo, junto con las carpetas necesarias para la gestión de datos, modelos y resultados.

---

## Estructura de carpetas

- **/data** → Contiene los datos utilizados durante el entrenamiento, incluyendo el archivo `Study.vtk` (imagen de resonancia magnética) y las máscaras binarias correspondientes a cada estructura anatómica.  
- **/models** → Carpeta donde se almacenan las redes neuronales ya entrenadas y las gráficas de entrenamiento (curvas de pérdida).  
- **/output** → Contiene las salidas generadas durante la fase de predicción: imágenes, volúmenes `.vtk` y reconstrucciones 3D.  
- **/test** → Carpeta con las imágenes y máscaras reales utilizadas en la fase de validación.  
- **/output_test** → Carpeta donde se guardan los resultados de la evaluación automática realizada sobre los datos de `/test`.  

---

## Archivos principales

### 🔹 `generator (1).py`
- Genera y entrena las redes neuronales desde cero.  
- Al finalizar, guarda los modelos entrenados y sus curvas de pérdida en `/models`.  
- **No es necesario modificar nada en este archivo**, ya está completamente configurado.  
- Solo debería ejecutarse si se desea realizar un nuevo entrenamiento, ya que sobrescribe los modelos existentes.  

El archivo contiene un **diccionario de configuración** donde se puede especificar:  
- Qué red neuronal entrenar.  
- Número de épocas.  
- Activar o desactivar el entrenamiento (`True` / `False`).  

⚠️ **Importante:**  
Si se ejecuta este archivo, todo el contenido de `/models` será reemplazado. Se recomienda hacer una copia de seguridad antes de iniciar un nuevo entrenamiento.

---

### 🔹 `predict (1).py`
- Utiliza los modelos almacenados en `/models` para generar salidas automáticas:  
  - Visualización de tres imágenes en consola:  
    1. Resonancia original.  
    2. Máscara real.  
    3. Predicción del modelo.  
  - Generación de archivos volumétricos `.vtk` con las tres vistas (planta, alzado y perfil).  
  - Creación de modelos 3D en formato `.vtk` que representan las estructuras segmentadas.  

Todas las salidas se guardan automáticamente en la carpeta `/outputs`.  
El archivo está configurado para ejecutarse de manera automática, modificando únicamente el **diccionario de configuración** para:  
- Seleccionar la estructura cardíaca que se desea analizar.  
- Activar (`True`) o desactivar (`False`) la ejecución de la predicción.

---

### 🔹 `evaluation(1).ipynb`
- **Cuaderno Jupyter de validación del modelo**.  
- Carga las predicciones generadas y las máscaras reales almacenadas en la carpeta `/test`.  
- Calcula las métricas **Dice** e **IoU** para cada estructura segmentada.  
- Genera tablas comparativas y gráficos que muestran el rendimiento por estructura.  
- Incluye visualizaciones 2D/3D para la comparación cualitativa entre las predicciones y las máscaras de referencia.  
- Las salidas del proceso de validación se almacenan automáticamente en la carpeta `/output_test`.  

> 💡 **Nota:** Ejecutar este cuaderno una vez generadas las predicciones con `predict (1).py`, asegurando que las carpetas `/test` y `/output_test` estén correctamente configuradas.

---

## ⚠️ Notas importantes
- Al ejecutar la **primera celda** de cualquiera de los scripts, el entorno puede solicitar reiniciar la sesión **una sola vez**.  
- Si lo solicita de nuevo inmediatamente después, **cancelar** el segundo reinicio y continuar la ejecución con normalidad.  

---

## Contenido del repositorio

- Código fuente para entrenamiento, predicción y validación.  
- Conjunto de datos y máscaras de referencia: https://www.dropbox.com/scl/fo/98wbbhjb7xvh6fjz2mdd6/AEb_yZlzlCl7cJ3y6hD1LvQ?rlkey=ae4wovf0yja48gunzritfi28u&st=8p0kkplf&dl=0
- Modelos preentrenados y resultados de evaluación.  
- Documentación técnica y resultados de rendimiento (métricas Dice e IoU).  

---

**Contacto:**  
📧 [alvarocamara15@gmail.com](mailto:alvarocamara15@gmail.com)

