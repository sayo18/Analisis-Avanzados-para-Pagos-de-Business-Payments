
# Análisis de Solicitudes de Efectivo y Recuperación

## Descripción del Proyecto

Este proyecto tiene como objetivo analizar un conjunto de datos relacionados con solicitudes de adelanto de efectivo. 
El enfoque principal es explorar y limpiar los datos, realizar un análisis exploratorio y aplicar modelos predictivos 
para extraer insights sobre el comportamiento de los usuarios y las métricas clave.

## Estructura del Proyecto


### 1. Preparación y Exploración Inicial
- Revisión de los datos para comprender la estructura y el contenido de las columnas.
- Análisis exploratorio para identificar estadísticas descriptivas, patrones y posibles outliers.
- Análisis temporal para observar distribuciones basadas en fechas.

Haciendo un .info del df encontramos que deberia tener una columna de 'reason' Filled only if the CR was manually reviewed and rejected. That's the rejection's reason displayed in-app.
![image](https://github.com/user-attachments/assets/e4a5f6b0-700b-4f1a-b373-9fc4a12678e3)


Pero no parece existir

En status no aparecen los valores: 'approved', 'money_sent', 'pending', 'waiting_user_confirmation','waiting reimbursement', 'active'


cash_request_debited_date no aparece

![download](https://github.com/user-attachments/assets/f50b8314-4b56-4054-893f-401bdd887f7a)

![download](https://github.com/user-attachments/assets/83e01227-0dfa-41d1-abf4-9079ceeddf4d)


Aquí vemos que la mayoría de montos que se retiran son de 100, 25 y 50, tanto para cash request instantaneos como regulares. Esto parece sugerir que los montos se han colocado artificialmente, ya que no dependen de ningún tipo ed fee. Como podemos en la siguiente grafica todos los fees, excepto 1 son de 5.

![download](https://github.com/user-attachments/assets/602c804b-d4c0-4798-8838-35b08013eb73)

Suponemos que el valor de 5 es un porcentaje y no valor absoluto ya que no tiene sentido cobrar la misma comisión a un monto de 25 que de 100.


![download](https://github.com/user-attachments/assets/69423d1d-135b-40d5-8467-091228ec8c15)

Al analizar los valores vacios y rellenos del df vemos que las columnas user_id y deleted_account_id son complementarias.

![download](https://github.com/user-attachments/assets/c128e283-ec82-433f-b64b-53d35d7468a8)

vemos también, analizando la columna status, que basicamente solo existen 2 tipos de status: 'rejected', para CR que se han rechazado y 'money_back' para operaciones que se han realizado con exito.

![download](https://github.com/user-attachments/assets/fd166687-978a-4da8-95b1-a6d571b36c65)
![download](https://github.com/user-attachments/assets/73d69464-ec0d-4216-853b-77a1ff7bf231)
![image](https://github.com/user-attachments/assets/0dc0c01b-01aa-49e7-ace5-b5bc6dfe802e)


Para campaña de marketing las franjas mas interesantes son de martes a jueves por las mañas y las tardes. Sería interesante como ingreso pasivo mostrar anuncios en estas franjas.

### 2. Limpieza y Preprocesamiento de los Datos
- Identificación y manejo de valores faltantes, duplicados e inconsistencias.
- Estandarización de formatos y creación de cohortes basadas en fechas clave.

### 3. Análisis de Métricas
- Cálculo de métricas como la frecuencia de uso del servicio, tasas de incidentes y generación de ingresos.
- Visualización de las métricas a lo largo del tiempo mediante gráficos y diagramas.

### 4. Modelado Predictivo
- Implementación de modelos de clasificación utilizando RandomForestClassifier.
- Búsqueda de hiperparámetros para optimizar el rendimiento del modelo.
- Evaluación de resultados mediante una matriz de confusión.

### 5. Documentación y Presentación
- Resumen de hallazgos y resultados obtenidos durante el análisis.
- Organización del código y documentación en un entorno reproducible.

## Conclusiones Principales
- Se identificaron patrones clave en las solicitudes de adelanto de efectivo y las tasas de incidentes.
- El modelo de clasificación logró categorizar correctamente un porcentaje significativo de las solicitudes.
- Las cohortes definidas proporcionaron insights sobre la evolución temporal de las métricas clave.

## Visualización de Resultados
A continuación, se muestran ejemplos de visualizaciones generadas durante el análisis:

- Matriz de confusión para evaluar la precisión del modelo de clasificación.
- Gráficos de líneas y barras que ilustran el comportamiento de las cohortes a lo largo del tiempo.

## Requisitos
- Python 3.x
- Bibliotecas: Pandas, NumPy, Matplotlib, Scikit-learn

## Cómo ejecutar el proyecto
1. Clona este repositorio.
2. Instala los requisitos mediante `pip install -r requirements.txt`.
3. Ejecuta el Jupyter Notebook `Proyecto2.ipynb` para reproducir los análisis y visualizaciones.

## Contacto
Si tienes alguna pregunta o comentario sobre este proyecto, no dudes en contactarme.

