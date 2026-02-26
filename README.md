# 🚀 Motor de Onboarding Facephi: Zero Trust Architecture

Un pipeline de validación documental y antifraude robusto, modular y tolerante a fallos, desarrollado para el **Facephi Challenge 2026**.

## 🧠 Arquitectura del Sistema: Un enfoque modular y resiliente

El motor de validación documental que presentamos huye de los scripts lineales frágiles para apostar por una arquitectura orquestada y tolerante a fallos, imitando entornos de producción críticos.

El pipeline se divide en los siguientes módulos core:

Acondicionamiento Dinámico: Una capa previa de Auto-Crop inteligente diseñada para evitar la fragmentación de bordes típica de las cámaras móviles y aislar el soporte físico del ruido ambiental.

Extracción Híbrida Dirigida: Uso de PassportEye (visión morfológica) para localizar y leer la zona MRZ con extrema precisión bajo el estándar ICAO, combinado con docTR (Deep Learning) para lidiar con las tipografías variables y posiciones desestructuradas del anverso.

Módulo "El Cirujano" (Recuperación de Señal): El corazón matemático del sistema. Repara alucinaciones del OCR aplicando heurísticas avanzadas: máscaras bidireccionales para colisiones isomórficas (confundir 'O' con '0'), limpieza de padding y, sobre todo, recuperación matemática de dígitos corruptos aplicando la matriz de pesos ICAO (7-3-1).

Validación Cruzada y Reglas de Negocio: Un enrutador audita los datos cruzando el JSON del reverso contra el texto crudo del anverso usando el modelo "Bag of Words" con rotación heurística (0º, 90º, -90º). Además, aplica validación criptográfica (Módulo 23 del DNI español) y prevención de fraude cronológico.

El Puente Biométrico: Extracción automatizada del rostro del titular mediante Haar Cascades con auto-recorte dinámico (+20px de padding). El pipeline entrega un payload completo (JSON auditado + Crop Facial) listo para la validación biométrica 1:1 (Face Match).

## 🏆 Resultados y Robustez: Preparado para el Mundo Real

Con esta arquitectura hemos logrado construir un verdadero **Orquestador de Confianza Cero (Zero Trust)** capaz de lidiar con la imprevisibilidad del usuario final. 

* **Tolerancia a Hardware y Usuarios:** El sistema sobrevive a fotografías giradas, resoluciones excesivas, encuadres lejanos y artefactos visuales generados por el flash o sombras sobre el plástico. 
* **Resiliencia Criptográfica:** Al priorizar la recuperación inteligente de la señal por encima de la lectura estática mediante coordenadas espaciales (*Bounding Boxes* rígidos), hemos minimizado los falsos rechazos, salvando el proceso de Onboarding de errores físicos en la captura.
* **Escalabilidad:** El resultado es una solución altamente escalable, capaz de procesar sin fricción múltiples generaciones de documentos de identidad (DNI 2.0, 3.0, 4.0, Pasaportes) y preparada para una expansión directa a otros formatos de la Unión Europea.

## 🛠️ Instalación y Configuración

El proyecto está diseñado para ejecutarse en entornos como Google Colab o en local mediante Jupyter Notebook.

### 1. Clonar el repositorio
```bash
git clone [https://github.com/TU_USUARIO/Facephi-Onboarding-Challenge.git](https://github.com/TU_USUARIO/Facephi-Onboarding-Challenge.git)
cd Facephi-Onboarding-Challenge
```

### 2. Dependencias del Sistema (Linux/Colab)
El motor de lectura MRZ requiere que el binario de Tesseract OCR esté instalado en el sistema operativo subyacente:
```bash
sudo apt-get update
sudo apt-get install tesseract-ocr
```

### 3. Entorno de Python
Instala las dependencias necesarias de procesamiento, visión artificial y Deep Learning mediante el archivo `requirements.txt`:
```bash
pip install -r requirements.txt
```

## 🚀 Uso
Abre el notebook `notebooks/Unverified_FacephiChallenge2026.ipynb` y ejecuta las celdas de inicialización y definición de funciones. 

En la celda final de "EJECUCIÓN DEL SISTEMA", modifica las variables de las rutas apuntando a los documentos físicos a verificar:
```python
ruta_back = 'ruta/a/tu/imagen_reverso.jpg'
ruta_front = 'ruta/a/tu/imagen_anverso.jpg'

resultado_final = onboarding_facephi(ruta_back, ruta_front)
```
