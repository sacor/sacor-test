---
title: Descripción de los resultados de ML automatizado
titleSuffix: Azure Machine Learning
description: Obtenga información sobre cómo ver y entender los gráficos y las métricas de cada una de las ejecuciones de aprendizaje automático automatizado.
services: machine-learning
author: RachelKellam
ms.author: rakellam
ms.reviewer: sgilley
ms.service: machine-learning
ms.subservice: core
ms.topic: conceptual
ms.date: 12/05/2019
ms.openlocfilehash: 81f17de7627658b756edd19438a80fb32add859d
ms.sourcegitcommit: 5ab4f7a81d04a58f235071240718dfae3f1b370b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74974094"
---
# <a name="understand-automated-machine-learning-results"></a>Descripción de los resultados de aprendizaje automático automatizado

En este artículo, aprenderá a ver y a entender los gráficos y las métricas de cada una de las ejecuciones de aprendizaje automático automatizado. 

Más información sobre:
+ [Métricas, gráficos y curvas para los modelos de clasificación](#classification)
+ [Métricas, gráficos y grafos para los modelos de regresión](#regression)
+ [Interpretabilidad del modelo e importancia de las características](#explain-model)

## <a name="prerequisites"></a>Requisitos previos

* Una suscripción de Azure. Si no tiene una suscripción a Azure, cree una cuenta gratuita antes de empezar. Pruebe hoy mismo la [versión gratuita o de pago de Azure Machine Learning](https://aka.ms/AMLFree).

* Cree un experimento para su ejecución de aprendizaje automático automatizado, ya sea con el SDK o en Azure Machine Learning Studio.

    * Use el SDK para crear un [modelo de clasificación](how-to-auto-train-remote.md) o un [modelo de regresión](tutorial-auto-train-models.md).
    * Use [Azure Machine Learning Studio](how-to-create-portal-experiments.md) para crear un modelo de clasificación o regresión mediante la carga de los datos apropiados.

## <a name="view-the-run"></a>Visualización de la ejecución

Después de ejecutar un experimento de aprendizaje automático automatizado, puede encontrar un historial de las ejecuciones en el área de trabajo de aprendizaje automático. 

1. Vaya a su área de trabajo.

1. En el panel izquierdo del área de trabajo, seleccione **Experimentos**.

   ![Captura de pantalla del menú de experimentos](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-experiment-menu.png)

1. En la lista de experimentos, seleccione el que quiere explorar.

   [![Lista de experimentos](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-experiment-list.png)](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-experiment-list-expanded.png)

1. En la tabla inferior, seleccione la **ejecución**.

   [![Ejecución de experimento](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-experiment-run.png)](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-experiment-run-expanded.png)

1. En los modelos, seleccione el **nombre del algoritmo** del modelo que desea explorar más en profundidad.

   [![Modelo de experimento](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-experiment-model.png)](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-experiment-model-expanded.png)

También verá estos mismos resultados durante una ejecución si usa el `RunDetails`[widget de Jupyter](https://docs.microsoft.com/python/api/azureml-widgets/azureml.widgets?view=azure-ml-py).

## <a name="classification"></a> Resultados de la clasificación

Las métricas y los gráficos siguientes están disponibles para cada modelo de clasificación que se crea con las funcionalidades de aprendizaje automático automatizado de Azure Machine Learning.

+ [Métricas](#classification-metrics)
+ [Matriz de confusión](#confusion-matrix)
+ [Gráfico de precisión-recuperación](#precision-recall-chart)
+ [Características operativas del receptor (o ROC)](#roc)
+ [Curva de elevación](#lift-curve)
+ [Curva de beneficios](#gains-curve)
+ [Trazado de calibración](#calibration-plot)

### <a name="classification-metrics"></a>Métricas de clasificación

Las métricas siguientes se guardan en cada iteración de ejecución de una tarea de clasificación.

|Métrica|DESCRIPCIÓN|Cálculo|Parámetros adicionales
--|--|--|--|
AUC_Macro| AUC es el área bajo la Curva de característica operativa del receptor. Macro es la media aritmética del parámetro AUC para cada clase.  | [Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html) | average="macro"|
AUC_Micro| AUC es el área bajo la Curva de característica operativa del receptor. Micro se calcula de forma global mediante la combinación de los verdaderos positivos y los falsos positivos de cada clase.| [Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html) | average="micro"|
AUC_Weighted  | AUC es el área bajo la Curva de característica operativa del receptor. Weighted es la media aritmética de la puntuación para cada clase, ponderada por el número de instancias verdaderas en cada clase.| [Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html)|average="weighted"
accuracy|La precisión es el porcentaje de las etiquetas de predicción que coinciden exactamente con las etiquetas verdaderas. |[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.accuracy_score.html) |None|
average_precision_score_macro|La precisión promedio resume una curva de precisión-recuperación como la media ponderada de las precisiones conseguidas en cada umbral, donde el aumento de la recuperación del umbral anterior se usa como peso. Macro es la media aritmética de la puntuación de precisión media de cada clase.|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.average_precision_score.html)|average="macro"|
average_precision_score_micro|La precisión promedio resume una curva de precisión-recuperación como la media ponderada de las precisiones conseguidas en cada umbral, donde el aumento de la recuperación del umbral anterior se usa como peso. Micro se calcula de forma global mediante la combinación de los verdaderos positivos y los falsos positivos en cada límite.|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.average_precision_score.html)|average="micro"|
average_precision_score_weighted|La precisión promedio resume una curva de precisión-recuperación como la media ponderada de las precisiones conseguidas en cada umbral, donde el aumento de la recuperación del umbral anterior se usa como peso. Weighted es la media aritmética de la puntuación de precisión promedio para cada clase, ponderada por el número de instancias verdaderas en cada clase.|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.average_precision_score.html)|average="weighted"|
balanced_accuracy|La precisión equilibrada es la media aritmética de recuperación para cada clase.|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.recall_score.html)|average="macro"|
f1_score_macro|La puntuación F1 es la media armónica de precisión y recuperación. Macro es la media aritmética de la puntuación F1 para cada clase.|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.f1_score.html)|average="macro"|
f1_score_micro|La puntuación F1 es la media armónica de precisión y recuperación. Micro se calcula de forma global mediante el recuento del total de verdaderos positivos, falsos negativos y falsos positivos.|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.f1_score.html)|average="micro"|
f1_score_weighted|La puntuación F1 es la media armónica de precisión y recuperación. Media ponderada por frecuencia de clase de la puntuación F1 para cada clase.|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.f1_score.html)|average="weighted"|
log_loss|Se trata de la función de pérdida que se usa en la regresión logística (multinomial) y sus extensiones como las redes neuronales, definida como la verosimilitud logarítmica negativa de las etiquetas verdaderas, dadas las predicciones de un clasificador probabilístico. Para un ejemplo único con la etiqueta verdadera yt en {0,1} y la probabilidad estimada yp de que yt = 1, la pérdida logarítmica es -log P(yt&#124;yp) = -(yt log(yp) + (1 - yt) log(1 - yp)).|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.log_loss.html)|None|
norm_macro_recall|La recuperación de macro normalizada es la recuperación de macro que se ha normalizado para que el rendimiento aleatorio tenga una puntuación de 0 y el rendimiento perfecto una puntuación de 1. Esto se logra mediante norm_macro_recall := (recall_score_macro - R)/(1 - R), donde R es el valor esperado de recall_score_macro para las predicciones aleatorias (es decir, R=0,5 para clasificación binaria y R=(1/C) para problemas de clasificación de clase C).|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.recall_score.html)|average = "macro" |
precision_score_macro|La precisión es el porcentaje de elementos con predicción positiva que están etiquetados correctamente. Macro es la media aritmética de la precisión para cada clase.|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.precision_score.html)|average="macro"|
precision_score_micro|La precisión es el porcentaje de elementos con predicción positiva que están etiquetados correctamente. Micro se calcula de forma global mediante el recuento del total de verdaderos positivos y falsos positivos.|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.precision_score.html)|average="micro"|
precision_score_weighted|La precisión es el porcentaje de elementos con predicción positiva que están etiquetados correctamente. Weighted es la media aritmética de la precisión para cada clase, ponderada por el número de instancias verdaderas en cada clase.|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.precision_score.html)|average="weighted"|
recall_score_macro|La coincidencia es el porcentaje de elementos de una clase determinada que están correctamente etiquetados. Macro es la media aritmética de la recuperación para cada clase.|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.recall_score.html)|average="macro"|
recall_score_micro|La coincidencia es el porcentaje de elementos de una clase determinada que están correctamente etiquetados. Micro se calcula de forma global mediante el recuento del total de verdaderos positivos, falsos negativos y falsos positivos.|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.recall_score.html)|average="micro"|
recall_score_weighted|La coincidencia es el porcentaje de elementos de una clase determinada que están correctamente etiquetados. Weighted es la media aritmética de la recuperación para cada clase, ponderada por el número de instancias verdaderas en cada clase.|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.recall_score.html)|average="weighted"|
weighted_accuracy|La precisión ponderada es la precisión donde el peso asignado a cada ejemplo es igual a la proporción de instancias verdaderas en la clase real de ese ejemplo.|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.accuracy_score.html)|sample_weight es un vector igual a la proporción de esa clase para cada elemento en el destino|
<a name="confusion-matrix"></a>
### <a name="confusion-matrix"></a>Matriz de confusión
#### <a name="what-is-a-confusion-matrix"></a>¿Qué es una matriz de confusión?
Una matriz de confusión se usa para describir el rendimiento de un modelo de clasificación. Cada fila muestra las instancias de la clase verdadera o real en su conjunto de datos, y cada columna representa las instancias de la clase prevista por el modelo. 

#### <a name="what-does-automated-ml-do-with-the-confusion-matrix"></a>¿Qué hace ML automatizado con la matriz de confusión?
Por problemas de clasificación, Azure Machine Learning proporciona automáticamente una matriz de confusión para cada modelo que se crea. Para cada matriz de confusión, ML automatizado mostrará la frecuencia de cada etiqueta de predicción (columna) en comparación con la etiqueta verdadera (fila). Cuanto más oscuro sea el color, mayor será el número de la parte concreta de la matriz. 

#### <a name="what-does-a-good-model-look-like"></a>¿Qué aspecto tiene un buen modelo?
Comparamos el valor real del conjunto de datos con los valores de predicción proporcionados por el modelo. Por ello, los modelos de Machine Learning son más precisos si el modelo tiene la mayoría de sus valores en la diagonal, lo que significa que el modelo predijo el valor correcto. Si un modelo presenta desequilibrio de clases, la matriz de confusión ayudará a detectar un modelo sesgado.

##### <a name="example-1-a-classification-model-with-poor-accuracy"></a>Ejemplo 1: modelo de clasificación con baja precisión
![modelo de clasificación con baja precisión](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-confusion-matrix1.png)

##### <a name="example-2-a-classification-model-with-high-accuracy"></a>Ejemplo 2: modelo de clasificación con alta precisión 
![modelo de clasificación con alta precisión](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-confusion-matrix2.png)

##### <a name="example-3-a-classification-model-with-high-accuracy-and-high-bias-in-model-predictions"></a>Ejemplo 3: modelo de clasificación con alta precisión y alto sesgo en predicciones de modelo
![modelo de clasificación con alta precisión y alto sesgo en predicciones de modelo](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-biased-model.png)

<a name="precision-recall-chart"></a>
### <a name="precision-recall-chart"></a>Gráfico de precisión-recuperación
#### <a name="what-is-a-precision-recall-chart"></a>¿Qué es un gráfico de precisión-recuperación?
La curva de precisión-recuperación muestra la relación entre la precisión y la recuperación de un modelo. El término "precisión" representa la capacidad de un modelo de etiquetar todas las instancias correctamente. "Recuperación" representa la capacidad de un clasificador de buscar todas las instancias de una etiqueta determinada.

#### <a name="what-does-automated-ml-do-with-the-precision-recall-chart"></a>¿Qué hace ML automatizado con el gráfico de precisión-recuperación?

Con este gráfico, puede comparar las curvas de precisión-recuperación para cada modelo para determinar qué modelo tiene una relación aceptable entre la precisión y la recuperación para su problema empresarial en particular. En este gráfico se muestran la precisión-recuperación promedio macro, la precisión-recuperación promedio micro y la precisión-recuperación asociadas con todas las clases de un modelo. 

El promedio macro calculará la métrica independientemente de cada clase y, a continuación, hará la media, tratando todas las clases de forma equitativa. Sin embargo, el promedio micro agregará las contribuciones de todas las clases para calcular la media. El promedio micro es preferible si hay desequilibrio de clases en el conjunto de datos.

#### <a name="what-does-a-good-model-look-like"></a>¿Qué aspecto tiene un buen modelo?
En función del objetivo del problema empresarial, la curva de precisión-recuperación ideal podría ser diferente. A continuación se proporcionan algunos ejemplos

##### <a name="example-1-a-classification-model-with-low-precision-and-low-recall"></a>Ejemplo 1: modelo de clasificación con baja precisión y baja recuperación
![modelo de clasificación con baja precisión y baja recuperación](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-precision-recall1.png)

##### <a name="example-2-a-classification-model-with-100-precision-and-100-recall"></a>Ejemplo 2: modelo de clasificación con precisión del ~100 % y recuperación del ~100 % 
![Modelo de clasificación con alta precisión y recuperación](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-precision-recall2.png)
<a name="roc"></a>
### <a name="roc-chart"></a>Gráfico ROC

#### <a name="what-is-a-roc-chart"></a>¿Qué es un gráfico ROC?
La característica operativa del receptor (o ROC) es un trazado de las etiquetas clasificadas correctamente frente a las etiquetas clasificadas incorrectamente para un modelo determinado. La curva ROC puede ser menos informativa al entrenar modelos en conjuntos de datos con gran sesgo, ya que no mostrará las etiquetas falsas positivas.

#### <a name="what-does-automated-ml-do-with-the-roc-chart"></a>¿Qué hace ML automatizado con el gráfico ROC?
ML automatizado genera la precisión-recuperación promedio macro, la precisión-recuperación promedio micro y la precisión-recuperación asociadas con todas las clases de un modelo. 

El promedio macro calculará la métrica independientemente de cada clase y, a continuación, hará la media, tratando todas las clases de forma equitativa. Sin embargo, el promedio micro agregará las contribuciones de todas las clases para calcular la media. El promedio micro es preferible si hay desequilibrio de clases en el conjunto de datos.

#### <a name="what-does-a-good-model-look-like"></a>¿Qué aspecto tiene un buen modelo?
Idealmente, el modelo tendrá el índice de verdaderos positivos más próximo al 100 % y el índice de falsos positivos más próximo al 0 %. 

##### <a name="example-1-a-classification-model-with-low-true-labels-and-high-false-labels"></a>Ejemplo 1: modelo de clasificación con bajas etiquetas verdaderas y altas etiquetas falsas
![Modelo de clasificación con bajas etiquetas verdaderas y altas etiquetas falsas](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-roc-1.png)

##### <a name="example-2-a-classification-model-with-high-true-labels-and-low-false-labels"></a>Ejemplo 2: modelo de clasificación con altas etiquetas verdaderas y bajas etiquetas falsas
![modelo de clasificación con altas etiquetas verdaderas y bajas etiquetas falsas](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-roc-2.png)
<a name="lift-curve"></a>
### <a name="lift-chart"></a>Gráfico de elevación
#### <a name="what-is-a-lift-chart"></a>¿Qué es un gráfico de elevación?
Los gráficos de elevación se usan para evaluar el rendimiento de un modelo de clasificación. Muestra cuánto mejor puede esperar que le vaya con el modelo generado en comparación con hacerlo sin un modelo en términos de precisión.
#### <a name="what-does-automated-ml-do-with-the-lift-chart"></a>¿Qué hace ML automatizado con el gráfico de elevación?
Puede comparar la elevación del modelo creado automáticamente con Azure Machine Learning con la línea base para ver el aumento del valor de ese modelo concreto.
#### <a name="what-does-a-good-model-look-like"></a>¿Qué aspecto tiene un buen modelo?

##### <a name="example-1-a-classification-model-that-does-worse-than-a-random-selection-model"></a>Ejemplo 1: modelo de clasificación que lo hace peor que un modelo de selección aleatoria
![modelo de clasificación que lo hace peor que un modelo de selección aleatoria](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-lift-curve1.png)
##### <a name="example-2-a-classification-model-that-performs-better-than-a-random-selection-model"></a>Ejemplo 2: modelo de clasificación con mejor rendimiento que un modelo de selección aleatoria
![Modelo de clasificación con mejor rendimiento](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-lift-curve2.png)
<a name="gains-curve"></a>
### <a name="gains-chart"></a>Gráfico de beneficios
#### <a name="what-is-a-gains-chart"></a>¿Qué es un gráfico de beneficios?

Un gráfico de beneficios evalúa el rendimiento de un modelo de clasificación por cada parte de los datos. Muestra, para cada percentil del conjunto de datos, cuánto mejor puede esperar rendir en comparación con un modelo de selección aleatoria.

#### <a name="what-does-automated-ml-do-with-the-gains-chart"></a>¿Qué hace ML automatizado con el gráfico de beneficios?
Use el gráfico de beneficios acumulados para ayudarle a elegir la fecha límite de clasificación mediante un porcentaje que corresponda a un beneficio deseado del modelo. Esta información proporciona otra manera de examinar los resultados en el gráfico de elevación que lo acompaña.

#### <a name="what-does-a-good-model-look-like"></a>¿Qué aspecto tiene un buen modelo?
##### <a name="example-1-a-classification-model-with-minimal-gain"></a>Ejemplo 1: modelo de clasificación con beneficios mínimos
![modelo de clasificación con beneficios mínimos](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-gains-curve1.png)

##### <a name="example-2-a-classification-model-with-significant-gain"></a>Ejemplo 2: modelo de clasificación con beneficios importantes
![Modelo de clasificación con beneficios importantes](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-gains-curve2.png)
<a name="calibration-plot"></a>
### <a name="calibration-chart"></a>Gráfico de calibración

#### <a name="what-is-a-calibration-chart"></a>¿Qué es un gráfico de calibración?
Un trazado de calibración se usa para mostrar la confianza de un modelo predictivo. Esto se consigue al mostrar la relación entre la probabilidad predicha y la probabilidad real, donde "probabilidad" representa la probabilidad de que una instancia determinada pertenezca a alguna etiqueta.
#### <a name="what-does-automated-ml-do-with-the-calibration-chart"></a>¿Qué hace ML automatizado con el gráfico de calibración?
Para todos los problemas de clasificación, puede revisar la línea de calibración de promedio micro, promedio macro y cada clase en un modelo predictivo determinado.

El promedio macro calculará la métrica independientemente de cada clase y, a continuación, hará la media, tratando todas las clases de forma equitativa. Sin embargo, el promedio micro agregará las contribuciones de todas las clases para calcular la media. 
#### <a name="what-does-a-good-model-look-like"></a>¿Qué aspecto tiene un buen modelo?
 Un modelo bien calibrado se alinea con y=x, donde resulta razonablemente confiable en sus predicciones. Un modelo con confianza excesiva se alinea con y=0, donde la probabilidad predicha está presente, pero no hay ninguna probabilidad real. 


##### <a name="example-1-a-well-calibrated-model"></a>Ejemplo 1: modelo bien calibrado
![ modelo mejor calibrado](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-calib-curve1.png)

##### <a name="example-2-an-over-confident-model"></a>Ejemplo 2: modelo con exceso de confianza
![modelo con exceso de confianza](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-calib-curve2.png)

## <a name="regression"></a> Resultados de la regresión

Las métricas y los gráficos siguientes están disponibles para cada modelo de regresión que se crea con las funcionalidades de aprendizaje automático automatizado de Azure Machine Learning.

+ [Métricas](#reg-metrics)
+ [Predicho frente a verdadero](#pvt)
+ [Histograma de valores residuales](#histo)


### <a name="reg-metrics"></a> Métricas de regresión

Las métricas siguientes se guardan en cada iteración de ejecución de una tarea de regresión o previsión.

|Métrica|DESCRIPCIÓN|Cálculo|Parámetros adicionales
--|--|--|--|
explained_variance|La varianza explicada es la proporción que tiene en cuenta un modelo matemático la variación de un conjunto de datos determinado. Es el porcentaje de reducción de la varianza de los datos originales con respecto a la varianza de los errores. Cuando la media de los errores es 0, es igual a la varianza explicada.|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.explained_variance_score.html)|None|
r2_score|R2 es el coeficiente de determinación o el porcentaje de reducción de los errores cuadráticos en comparación con un modelo de referencia que da como resultado la media. |[Cálculo](https://scikit-learn.org/0.16/modules/generated/sklearn.metrics.r2_score.html)|None|
spearman_correlation|La correlación de Spearman es una medida no paramétrica de la monotonicidad de la relación entre dos conjuntos de datos. A diferencia de la correlación de Pearson, la correlación de Spearman no asume que los conjuntos de datos se distribuyen normalmente. Como sucede con otros coeficientes de correlación, este varía entre -1 y + 1, y 0 implica que no hay ninguna correlación. Las correlaciones de -1 o +1 implican una relación monotónica exacta. Las correlaciones positivas implican que cuando aumenta x, también lo hace y. Las correlaciones negativas implican que cuando aumenta x, y disminuye.|[Cálculo](https://docs.scipy.org/doc/scipy-0.16.1/reference/generated/scipy.stats.spearmanr.html)|None|
mean_absolute_error|El error absoluto medio es el valor esperado del valor absoluto de la diferencia entre el destino y la predicción.|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.mean_absolute_error.html)|None|
normalized_mean_absolute_error|El error medio absoluto normalizado es un error medio absoluto dividido por el intervalo de los datos|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.mean_absolute_error.html)|Se divide por el intervalo de los datos|
median_absolute_error|El error medio absoluto es la media de todas las diferencias absolutas entre el destino y la predicción. Esta pérdida es estable para los valores atípicos.|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.median_absolute_error.html)|None|
normalized_median_absolute_error|El error medio absoluto normalizado es un error medio absoluto dividido por el intervalo de los datos|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.median_absolute_error.html)|Se divide por el intervalo de los datos|
root_mean_squared_error|El error cuadrático medio es la raíz cuadrada de la diferencia cuadrática esperada entre el destino y la predicción.|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.mean_squared_error.html)|None|
normalized_root_mean_squared_error|El error cuadrático medio normalizado es el error cuadrático medio dividido por el intervalo de los datos.|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.mean_squared_error.html)|Se divide por el intervalo de los datos|
root_mean_squared_log_error|El error logarítmico cuadrático medio es la raíz cuadrada del error logarítmico cuadrático esperado.|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.mean_squared_log_error.html)|None|
normalized_root_mean_squared_log_error|El error logarítmico cuadrático medio normalizado es el error logarítmico cuadrático medio dividido por el intervalo de los datos.|[Cálculo](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.mean_squared_log_error.html)|Se divide por el intervalo de los datos|

### <a name="pvt"></a> Predicho frente a Gráfico verdadero
#### <a name="what-is-a-predicted-vs-true-chart"></a>¿Qué es un gráfico predicho frente a un gráfico verdadero?
Predicho frente a True (Predicho frente verdadero), muestra la relación entre un valor predicho y su valor verdadero correlacionado para un problema de regresión. Este gráfico se puede usar para medir el rendimiento de un modelo, ya que cuanto más se acerquen los valores predichos a la línea y=x, mejor será la precisión de un modelo predictivo.

#### <a name="what-does-automated-ml-do-with-the-predicted-vs-true-chart"></a>¿Qué hace ML automatizado con el gráfico predicho frente al gráfico verdadero?
Después de cada ejecución, puede ver un gráfico de predicción frente a verdadero para cada modelo de regresión. Para proteger la privacidad de los datos, los valores se agrupan juntos y el tamaño de cada ubicación se muestra como un gráfico de barras en la parte inferior del área del gráfico. Puede comparar el modelo predictivo, donde el área de sombreado más claro muestra los márgenes de error, con el valor ideal donde se debería ubicar el modelo.

#### <a name="what-does-a-good-model-look-like"></a>¿Qué aspecto tiene un buen modelo?
##### <a name="example-1-a-classification-model-with-low-accuracy"></a>Ejemplo 1: modelo de clasificación con baja precisión
![Modelo de regresión con baja precisión en las predicciones](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-regression1.png)

##### <a name="example-2-a-regression-model-with-high-accuracy"></a>Ejemplo 2: modelo de regresión con alta precisión 
[![Modelo de regresión con alta precisión en sus predicciones](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-regression2.png)](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-regression2-expanded.png)



### <a name="histo"></a> Histograma del gráfico de valores residuales
#### <a name="what-is-a-residuals-chart"></a>¿Qué es un gráfico de valores residuales?
Un valor residual representa la y observada – la y predicha. Para mostrar un margen de error con poco sesgo, el histograma de valores residuales debe tener la forma de una curva de campana, centrada en 0. 
#### <a name="what-does-automated-ml-do-with-the-residuals-chart"></a>¿Qué hace ML automatizado con el gráfico de valores residuales?
ML automatizado proporciona automáticamente un gráfico de valores residuales para mostrar la distribución de los errores en las predicciones.
#### <a name="what-does-a-good-model-look-like"></a>¿Qué aspecto tiene un buen modelo?
Un buen modelo normalmente tendrá una curva de campana o errores en torno a cero.

##### <a name="example-1-a-regression-model-with-bias-in-its-errors"></a>Ejemplo 1: modelo de regresión con sesgo en sus errores
![Modelo de regresión de SA con sesgo en sus errores](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-regression3.png)

##### <a name="example-2-a-regression-model-with-more-even-distribution-of-errors"></a>Ejemplo 2: modelo de regresión con una distribución más uniforme de los errores
![modelo de regresión con una distribución más uniforme de los errores](./media/how-to-understand-automated-ml/azure-machine-learning-auto-ml-regression4.png)

## <a name="explain-model"></a> Interpretabilidad del modelo e importancia de las características
ML automatizado proporciona un panel de interoperabilidad de aprendizaje automático de las ejecuciones.
Para más información sobre cómo habilitar las características de interpretabilidad, consulte los [procedimientos](how-to-machine-learning-interpretability-automl.md) sobre cómo habilitar la interpretabilidad en experimentos de ML automatizado.

## <a name="next-steps"></a>Pasos siguientes

+ Obtenga más información sobre el [aprendizaje automático automatizado](concept-automated-ml.md) en Azure Machine Learning.
+ Pruebe los cuadernos de ejemplo de la [explicación del modelo de Machine Learning automatizado](https://github.com/Azure/MachineLearningNotebooks/tree/master/how-to-use-azureml/explain-model).