# Generador y Discriminador para Fashion MNIST con GAN 👗👚👟

Este proyecto implementa un modelo Generativo Antagónico (GAN) para generar imágenes de prendas de ropa y accesorios utilizando el conjunto de datos *Fashion MNIST*. El objetivo es entrenar un generador capaz de crear imágenes realistas a partir de ruido aleatorio, mientras que el discriminador aprende a distinguir entre imágenes reales y generadas. 🤖

## Requisitos 📦
Para ejecutar este proyecto, necesitas tener las siguientes librerías instaladas:
- **Python 3.x**
- **TensorFlow 2.x**
- **NumPy**
- **Matplotlib**
- **PIL (Python Imaging Library)**
- **imageio**

Se pueden instalar estas dependencias con `pip install tensorflow numpy matplotlib pillow imageio`

## Descripción del Modelo 📋
El proyecto consiste en dos componentes principales:
1. **Generador** 🎨: Este modelo toma un vector de ruido aleatorio y lo transforma en una imagen de 28x28 píxeles con una sola capa de canal (en escala de grises). A través de un proceso de convolución transpuesta, el generador crea imágenes que imitan las prendas de ropa y accesorios en el conjunto de datos *Fashion MNIST*.
2. **Discriminador** 🧐: El discriminador es una red neuronal convolucional que clasifica las imágenes entre reales (provenientes del conjunto de datos) y falsas (producidas por el generador). Su tarea es aprender a identificar si una imagen es genuina o generada, proporcionando retroalimentación para mejorar el generador.

## Estructura del Modelo GAN
- **Generador**: Utiliza capas densas y convolución transpuesta para generar imágenes a partir de ruido aleatorio.
- **Discriminador**: Usa convolución para analizar las imágenes y una capa densa para clasificar las imágenes como reales o falsas.

## Optimización ⚙️
Ambos modelos (generador y discriminador) se optimizan con el optimizador **Adam**, que es ampliamente utilizado por su eficiencia y capacidad para adaptarse a los gradientes de los modelos. La **entropía cruzada binaria** es la función de pérdida utilizada en este proyecto, ya que mide la diferencia entre las predicciones del discriminador y las etiquetas reales o falsas. Esto permite que tanto el generador como el discriminador aprendan de sus errores y mejoren en sus respectivas tareas:
- **Generador**: Su objetivo es engañar al discriminador para que clasifique las imágenes generadas como reales.
- **Discriminador**: Su tarea es clasificar correctamente las imágenes reales y generadas, distinguiendo las imágenes verdaderas de las falsas.

## Entrenamiento 🚀
### Parámetros de Entrenamiento 🔧
- **EPOCHS**: Número de épocas para entrenar el modelo.
- **LATENT_DIM**: Dimensión del vector de ruido utilizado como entrada del generador.
- **BATCH_SIZE**: Número de imágenes procesadas por lote durante el entrenamiento.

Durante el entrenamiento, el generador y el discriminador compiten en un juego de cero-suma. El discriminador intenta clasificar correctamente las imágenes reales y generadas, mientras que el generador intenta engañar al discriminador creando imágenes que parezcan reales. Las pérdidas de ambos modelos se calculan usando *Binary Cross-Entropy*.

### Progreso del Entrenamiento 📈
Al final de cada época, se genera un conjunto de imágenes producidas por el generador, que se muestran para visualizar el progreso. El modelo guarda las imágenes generadas en cada época y permite visualizar cómo mejoran con el tiempo.


## Uso del modelo
1. **Entrenar el modelo**: Para comenzar el entrenamiento, solo necesitas ejecutar la función `train()` con el conjunto de datos y la cantidad de épocas que deseas entrenar.
```python
train(train_dataset, EPOCHS)
```
2. **Ver las imágenes generadas**: Después de entrenar el modelo, puedes visualizar las imágenes generadas por el generador en la última época. Esto se hace mediante la función `display_image()`.
```python
display_image(EPOCHS - 1)
```
3. **Guardar el modelo** 💾: Al final del entrenamiento, el generador y el discriminador se guardan en archivos `.keras` para su posterior uso o fine-tuning.

## Resultados 📸
El entrenamiento puede tomar varias horas dependiendo de la capacidad de la GPU o TPU utilizada. Los resultados generados en cada época son guardados en archivos de imagen, que se pueden visualizar durante y después del entrenamiento.

## Licencia 📜
Este proyecto está bajo la Licencia MIT. Para más detalles, consulta el archivo `LICENSE`.

