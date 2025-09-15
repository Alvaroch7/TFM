# Trabajo Final de Máster

**Título:** *"Segmentación de Imágenes cardíacas"*  
**Autor:** Álvaro Cámara Higueras  

**Máster:** Big Data y Ciencia de Datos  
**Universidad:** Universidad Internacional de Valencia (VIU)  

---

## Descripción

Este proyecto es muy sencillo: consta de dos archivos **Python** y tres carpetas principales.

---

## Estructura de carpetas

- **/data**: Contiene los datos necesarios para el entrenamiento, incluyendo el archivo `Study.vtk` (imagen de resonancia magnética) y las máscaras binarias correspondientes a cada estructura.  
- **/models**: Aquí se guardan las redes neuronales ya entrenadas y sus gráficas de entrenamiento (curvas de pérdida).  
- **/outputs**: Carpeta donde se almacenan las salidas generadas durante la fase de predicción: imágenes, volúmenes en formato `.vtk` y modelos 3D.  

---

## Archivos principales

### 🔹 `generator (1).py`
- Se encarga de generar y entrenar las redes neuronales desde cero.  
- Al finalizar, guarda el modelo entrenado y su gráfica de pérdida en la carpeta `/models`.  
- **No es necesario modificar nada en este archivo**, ya está completamente configurado para funcionar.  
- No deberías ejecutarlo salvo que quieras entrenar nuevamente desde cero, ya que los modelos entrenados y sus gráficas ya están proporcionados.  

Dentro del archivo existe un **diccionario de configuración** que indica:  
- Qué red neuronal entrenar.  
- Número de épocas a utilizar.  
- Si se debe entrenar o no (`True` o `False`).  

⚠️ **Importante:**  
Si ejecutas este archivo, **se sobrescribirá todo lo que haya en `/models`**.  
Si tienes un modelo que funciona bien y quieres probar otro, recuerda guardar el anterior en otra ubicación para no perderlo.  

---

### 🔹 `predict (1).py`
- Utiliza los modelos almacenados en `/models` para generar varias salidas:  
  - Una visualización en consola con tres imágenes:  
    1. Resonancia original.  
    2. Máscara real.  
    3. Predicción de la red.  
  - Una salida volumétrica en formato `.vtk` que muestra las tres vistas (planta, alzado y perfil) del resultado de la segmentación.  
  - Una salida en formato `.vtk` en 3D que representa el modelo tridimensional (malla o superficie).  

Todo se guarda automáticamente en la carpeta `/outputs`.  

El archivo ya está configurado para funcionar automáticamente. Solo necesitas modificar el **diccionario de configuración** para:  
- Indicar qué estructura cardíaca analizar.  
- Activar (`True`) o desactivar (`False`) la ejecución de esa predicción.  

---

## ⚠️ Notas importantes
- Cuando ejecutes la **primera celda** de cada archivo, el entorno pedirá reiniciar la sesión **una vez**.  
- La segunda vez que lo solicite, debes **cancelar** el reinicio y continuar con la ejecución del resto de celdas.  

---

## Contenido

- Código fuente para el análisis de datos y modelado  
- Conjunto de datos utilizados  
- Documentación del modelo y resultados  

---

**Contacto:**  
Para dudas o sugerencias, por favor contacta con [alvarocamara15@gmail.com](mailto:alvarocamara15@gmail.com)
