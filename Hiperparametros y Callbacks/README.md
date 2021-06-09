# <center>Optimización de Hiperparámetros en NN con uso de  Callbacks</center>
Se usa el dataset: telecust.csv que parece complicado de mejorar

**Métodos estudiados:**

1. [GRID con bucle](#id1)
2. [Sci-kit Learn GridSearhCV](#id2)
3. [Sci-kit Learn RandomizedSearchCV](#id3)
4. [Keras RandomSearch](#id4)
5. [Keras Hyperband](#id5)

Estudio y comparación de estos métodos de optimizar hiperparámetros.
Se consideran hiperparámetros en este estudio todos los que influyen en obtener el mejor resultado final, es decir, en hallar el modelo con mejor precisión.

Se incluyen:
- Parámetros de arquitectura o estructura de la red
    + [Numero de capas](#id6)
    + [Número de neuronas por capa](#id6) (en todas el mismo por no complicarlo)
- Parámetros de entrenamiento del modelo
    + [Epochs](#id6)
    + [Batch size](#id6)
- Parámetros de la red (hiperp. propiamente dichos)
    + [Función de activación de capa de entrada](#id6)
    + [Función de activación de capas ocultas](#id6)
    + [Optimizador del modelo](#id6) (aunque suele ser un hiperparámetro se ha fijado como Adam)

Se ha hecho uso de 2 **CALLBACKS** para mejorar la precisión y acelerar el proceso, que puede ser muy largo en los de fuerza bruta
1. Método [EarlyStopping](#id7) : para evitar overfit/variance
2. Método [ModelCheckpoint](#id7) : para grabar el modelo que ha conseguido mejor precisión durante la iteración

# CONCLUSIONES
- El método **GRID con bucle** es el que mejor modelo encuentra, pero al hacerlo con todos las combinaciones lleva mucho tiempo. No incluye K-fold CV y usa el conjunto de test del 20%, para validar modelos durante la iteración. El overfit se trata de evitar, no con CV sino con los callbacks: EarlyStopping y ModelCheckPoints.
- El método **GridSearchCV** de Sci-kit Learn, que también es por fuerza bruta, consigue peores resultados porque incluye 5-fold CV. Eso significa quitar otro 20% al conjunto de train para validar los modelos, con lo que se entrenan los modelos con solo un 64% y los resultados son peores.
- El método **RandomizedSearchCV** de Sci-kit Learn, es un buen compromiso entre duración y resultado. Explorar un número mayor de 10 de conjuntos de parámetros al azar no mejora el resultado. Sin embargo un cv de 5 en lugar de 3 si que lo mejora, al entrenar los modelos con más datos.
- El método **RandomSearch** de Keras, no resulta práctico porque optimiza epochs y batch por su cuenta. Al obtener el mejor modelo se vuelve a entrenar con todo el train set pero no se conoce que epochs y batch dieron el mejor resultado. habría que optimizarlos de nuevo.
- El método **Hyperband** de Keras, también es un buen compromiso entre resultado y tiempo. Tampoco se conoce el batch que usa, pero se puede sacar con la información mostrada con verbose=1. El epoch se puede conocer si se usa el callback EarlyStopping, porque es con el que se para.
