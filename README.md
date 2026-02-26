# 🚀 Motor de Onboarding Facephi: Zero Trust Architecture

Un pipeline de validación documental y antifraude robusto, modular y tolerante a fallos, desarrollado para el **Facephi Challenge 2026**.

## 🧠 Arquitectura del Sistema: Un enfoque modular y resiliente

El motor de validación documental que presentamos huye de los scripts lineales frágiles para apostar por una arquitectura modular tolerante a fallos, imitando entornos de producción bancaria. La entrada de datos pasa primero por una capa de **Anti-Spoofing y Auto-Crop dinámico**, diseñada para evitar la fragmentación de bordes típica de las cámaras móviles de alta resolución y aislar el documento de fondos ruidosos. 

Para la extracción de la MRZ, hemos elegido **PassportEye** porque integra algoritmos de detección de ROI (Región de Interés) específicos para estándares ICAO, lo que reduce drásticamente los falsos positivos en comparación con un motor OCR genérico como Doctr. 

A continuación, el corazón del sistema, nuestro **Módulo "Cirujano"**, procesa la MRZ aplicando heurísticas avanzadas para reparar alucinaciones típicas del motor OCR. Esto incluye máscaras bidireccionales para solucionar colisiones isomórficas (como confundir ceros con letras 'O'), auto-alineación de desbordamientos y filtros de limpieza de padding perimetral. Una vez la señal está recuperada y estabilizada, un enrutador criptográfico evalúa la norma ICAO TD1/TD3 y aplica reglas de negocio específicas, como el cálculo del Módulo 23 para el DNI español. Finalmente, la validación cruzada biométrica se ejecuta mediante un motor de Deep Learning (*Doctr*) apoyado en el patrón **"Bolsa de Palabras" (Bag of Words)** y **rotación heurística**, haciéndolo agnóstico a la versión del documento y robusto ante fotos mal orientadas o formatos estructurados antiguos.

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
