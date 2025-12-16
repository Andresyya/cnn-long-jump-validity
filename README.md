# CNN-based Long Jump Validity Classification

Automatic classification of valid and invalid long jump attempts from video sequences.

---

## Descripción del proyecto

Este repositorio presenta un proyecto académico–técnico cuyo objetivo es clasificar automáticamente saltos de longitud como válidos o no válidos a partir de secuencias de video, utilizando redes neuronales convolucionales (CNN) y técnicas de visión por computadora.

El sistema fue desarrollado y entrenado completamente en Google Colab usando TensorFlow y Keras, y forma parte del núcleo computacional de una tesis de licenciatura en Física, integrando aprendizaje profundo con un análisis físico básico del movimiento humano.

---

## Objetivo

Desarrollar un modelo capaz de:

- Clasificar intentos de salto de longitud como inválidos o válidos para posteriormente aproximar la distancia del salto  
- Reducir la subjetividad del juicio humano  
- Proporcionar un sistema reproducible, accesible y automatizado  
- Mostrar la aplicación de deep learning al análisis deportivo y físico  

---

## Representación de los datos

- Cada salto se representa mediante una secuencia fija de 24 frames  
- Los frames se extraen de forma equiespaciada a lo largo del video  
- Cada imagen se redimensiona a 160 × 160 píxeles  
- Normalización aplicada mediante preprocess_input de MobileNetV2  
- Cada secuencia constituye una sola muestra de entrenamiento  

---

## Arquitectura del modelo

El modelo combina extracción espacial y agregación temporal:

Input (24, 160, 160, 3)  
TimeDistributed MobileNetV2 (preentrenada en ImageNet)  
TimeDistributed GlobalAveragePooling2D  
GlobalAveragePooling1D  
Dropout (0.3)  
Dense (1, activación sigmoidal)  

MobileNetV2 se utiliza como extractor de características con pesos congelados.  
La salida del modelo corresponde a la probabilidad de que el salto sea inválido.

---

## Entrenamiento

- Framework: TensorFlow 2.x / Keras  
- Optimizador: Adam  
- Función de pérdida: Binary Cross-Entropy  
- Métricas: Accuracy y AUC (ROC)  
- Desbalance de clases corregido mediante class_weight  
- Callbacks: EarlyStopping y ModelCheckpoint  
- Semillas fijas para asegurar reproducibilidad  

---

## Resultados

En los experimentos realizados se obtuvieron:

- Accuracy aproximada entre 75 % y 80 %  
- AUC cercana a 0.8  
- Separación consistente entre saltos válidos e inválidos  

Estos resultados muestran que es posible automatizar la evaluación de saltos de longitud utilizando arquitecturas ligeras y datos de video convencionales.

---

## Estructura del repositorio

notebooks/  
└── train_long_jump_validity_cnn.ipynb  

README.md  
  

El dataset y los modelos entrenados no se incluyen por razones de tamaño y privacidad, pero los puedo mostrar sin compromiso en entrevistas

---

## Ejecución

1. Abrir el notebook en Google Colab  
2. Instalar dependencias  

pip install tensorflow opencv-python mediapipe numpy pandas matplotlib  

3. Montar Google Drive si se requiere  
4. Ajustar la ruta del dataset  
5. Ejecutar las celdas en orden  

---

## Reproducibilidad

El experimento es determinista bajo las mismas condiciones de ejecución.  
No requiere hardware especializado y puede ejecutarse en la versión gratuita de Google Colab.

---

## Contexto académico

Este trabajo forma parte de una tesis de licenciatura en Física, enfocada en la intersección entre:

- Visión por computadora  
- Aprendizaje profundo  
- Física del movimiento  
- Análisis deportivo  

El énfasis del proyecto está en la interpretabilidad, reproducibilidad y accesibilidad.

---

## Trabajo futuro

- Incorporar modelos explícitos de tiempo (LSTM, Transformers)  
- Mejorar la corrección geométrica y perspectiva  
- Extender el sistema a otras disciplinas deportivas  
- Desplegar el modelo como aplicación de inferencia  

---

## Autor

Luis Andrés Moran Alvarado  
Licenciatura en Física  
Benemérita Universidad Autónoma de Puebla (BUAP)  
Noviembre de 2025  

---

## Licencia

Proyecto con fines académicos y educativos.  
Citar adecuadamente en caso de uso o trabajos derivados.
