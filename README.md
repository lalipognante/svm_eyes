# svm_eyes

## SVM Support Vector Machines
Dado un conjunto de muestras, podemos etiquetar las clases y entrenar una SVM para construir un modelo que prediga la clase de una nueva muestra.
SVM: separando las clases a 2 espacios lo más amplios posibles.
- Cuando las nuevas muestras se ponen en el modelo, en función de los espacios a los que pertenezcan, pueden ser clasificadas a una o la otra clase.
 
![svm-grafico](https://github.com/lalipognante/svm_eyes/blob/main/img/Ejemplos-SVM.png)

## Modelado del problema
1. Identificamos el problema → predicción → clasificación.
2. La tarea consiste en generar un modelo que dado un objeto provea la clase a la
que pertenece.
3. Diseño de la evaluación.
a) Cantidad de datos
-Entrenamiento: Para ajustar los parámetros del modelo
-Validación: Para evaluar los parámetros del modelo -> Hold Out -Evaluación: Para evaluar la herramienta y su capacidad de generalización -> Matriz de confusión y Curva ROC
 
## Presentación del proyecto
1. Recibimos un banco de imágenes de fondo de ojos “enfermos” y “sanos”.
2. Las introducimos a mobile net
3. Out: vectores de feat (Base de datos de features)
4. Lo dividimos en Train, Test y Val
5. Creamos un modelo SVM (definimos Kernel , C y Gamma)
6. Entrenamos el modelo
7. Obtuvimos dato de Accuracy
8. Realizamos métricas: Matriz de Confusión , Reporte de Clasificación y ROC
 
## División: Train, Val, Test
El subconjunto de datos de entrenamiento: utilizado para estimar los parámetros del modelo.
El subconjunto de datos de test: utilizado para comprobar el comportamiento del modelo estimado.
1. Lo dividimos en 2 → Train (70%) y Test (30%)
2. Subdividimos Train → Train (50%) y Val (20%)
![svm-training](https://github.com/lalipognante/svm_eyes/blob/main/img/training-test.png)
 
## Parámetros del SVM
### Kernel
* Lineal
* Polinómico
* Función de base radial (RBF) 
* Sigmoide
### Gamma
* (+ grande es el Gamma , + Overfitting)
* C = define la separación de mis datos
* (+ grande es el C , los datos + separados)
![svm-training](https://github.com/lalipognante/svm_eyes/blob/main/img/grafico-2.png)

## ¿Cómo elegimos el mejor modelo ?
Fuimos cambiando los parámetros, evaluando y nos quedamos con el mejor modelo:

## El mejor modelo
* model = SVC(C=100, kernel='rbf', gamma=0.000005)
* ++C --gamma
* ✓ No hay overfitting → Ya que a + gamma , + overfitting

## Métricas : Matriz de Confusión
Para ver gráficamente las predicciones:
- Tipos predicciones:
  * Verdadero Positivo (TP): (predijo + cuando era +)
  * Falso Positivo (FP): (predijo + cuando era -)
  * Verdadero Negativo (TN): (predijo - cuando era -)
  * Falso Negativo (FN): (predijo - cuando era +)

## Reporte de Clasificación
* Precisión: número de predicciones correctas (+ -) / el total de todas las predicciones
* Sensibilidad: %TP: cuantos casos positivos fueron correctamente identificados como tal
* f1-score: puntaje de precisión y sensibilidad → la mejor puntuación es 1.0 y la peor es 0.0
  - mayor es la precisión y sensibilidad
  - mayor es la puntuación de F1
![svm-report](https://github.com/lalipognante/svm_eyes/blob/main/img/report.png)
* TN+FP=252 
* TP+FN=241 
* 252+241=493

## Curva ROC: Receiver Operating Characteristic
Representación gráfica del rendimiento del clasificador, de la sensibilidad frente a la especificidad.
El mejor método posible → en un punto en la esquina superior izquierda.
* Representa 100% de sensibilidad (ningún falso negativo)
* Representa 100% de especificidad (ningún falso positivo)

## ROC en nuestro modelo
![svm-graficoss](https://github.com/lalipognante/svm_eyes/blob/main/img/curvas.png)
