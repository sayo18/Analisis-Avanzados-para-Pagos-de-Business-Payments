
# Análisis de Solicitudes de Efectivo y Recuperación

## Descripción del Proyecto

Este proyecto tiene como objetivo analizar un conjunto de datos relacionados con solicitudes de adelanto de efectivo. 
El enfoque principal es explorar y limpiar los datos, realizar un análisis exploratorio y aplicar modelos predictivos 
para extraer insights sobre el comportamiento de los usuarios y las métricas clave.


## **Duración**  
Del 19 al 27 de noviembre  

## **Equipo**  
- Chris   
- Breysi  

## **Planificación del Proyecto**  

### **Día 1: Preparación**  
Comenzamos revisando el dataset para entender su estructura, identificar las columnas clave y detectar posibles problemas de calidad. Definimos los objetivos del análisis y diseñamos una metodología clara para crear las cohortes y calcular las métricas necesarias. Además, configuramos el entorno de trabajo en Python, asegurándonos de que las librerías principales como Pandas, Matplotlib y Seaborn estén listas para usar. Por último, creamos un repositorio en GitHub para facilitar la colaboración en equipo.  

### **Día 2: Análisis Exploratorio de Datos**  
Realizamos un análisis exploratorio inicial para conocer mejor los datos. Esto incluye generar estadísticas descriptivas básicas, como medias y distribuciones, y visualizar patrones a través de gráficos para detectar posibles tendencias o anomalías. Durante esta fase también identificamos problemas específicos, como valores faltantes o datos inconsistentes, que podrían afectar el análisis. 

### **Día 3: Análisis de Calidad de Datos**  
En esta etapa evaluamos la calidad del dataset, buscando valores nulos, duplicados y formatos inconsistentes. Implementamos técnicas de limpieza para corregir estos problemas, asegurándonos de que los datos sean fiables para el análisis. Por último, validamos los resultados de la limpieza mediante visualizaciones actualizadas y comparaciones estadísticas.

### **Días 4 y 5: Análisis de Cohortes y Cálculo de Métricas**  
Aquí definimos las cohortes agrupando a los usuarios según el mes de su primera transacción. Calculamos las métricas clave, como la frecuencia de transacciones, el porcentaje de usuarios que abandonan el servicio y los ingresos generados por cada cohorte. Cada miembro del equipo trabajó en una sección específica del análisis, integrando el trabajo en GitHub mediante pull requests y revisiones colaborativas. 

### **Día 6: Visualización y Generación de Insights**  
Diseñamos gráficos que muestran de manera clara y atractiva la evolución de las métricas clave en cada cohorte. A partir de estos gráficos, extraemos insights relevantes sobre el comportamiento de los usuarios y el rendimiento del servicio. Documentamos estas observaciones para incluirlas en los entregables finales. 

### **Día 7: Revisión**  
Redactamos observaciones y recomendaciones basadas en los resultados obtenidos. Finalizamos el archivo README.md para que incluya todos los apartados importantes, como la introducción, la metodología utilizada, los resultados obtenidos y las conclusiones finales del análisis.

### **Día 8: Entrega Final**  
Realizamos una revisión conjunta del repositorio en GitHub, asegurándonos de que el código, la documentación y las visualizaciones estén organizados y actualizados. Finalmente, entregamos el proyecto junto con una presentación que resume los hallazgos clave y las recomendaciones.


## **Colaboración y Uso de GitHub**  
Durante todo el proyecto utilizamos GitHub como herramienta principal para la colaboración. Cada integrante trabajó en ramas independientes, subiendo su código mediante pull requests. Estos cambios fueron revisados por el equipo antes de integrarse en la rama principal.

---

# **Análisis de Cohortes para los Pagos**

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

![image](https://github.com/user-attachments/assets/7670a8db-3fc3-434a-8735-466e32224d8d)


### 2. Análisis de Métricas
- Cálculo de métricas como la frecuencia de uso del servicio, tasas de incidentes y generación de ingresos.
- Visualización de las métricas a lo largo del tiempo mediante gráficos y diagramas.

  ![image](https://github.com/user-attachments/assets/eccf7b65-87ab-4d0a-b1a1-0f1138830441)

  Vemos como en diciembre tenemos la mayor retirada. Esto tiene sentido ya que en navidad se retira mucho efectivo para comprar regalos. Tambien durante el verano tenemos un pico, dado que la gente se va de vacaciones. Octubre es un mes raro ya que hay valores muy altos sin aparente explicacion. Una posibilidad es Halloween.

  ![image](https://github.com/user-attachments/assets/72595c51-0be5-4b6d-b201-6678d4c6915a)


Vemos que en octubre tenemos el pico de usuarios nuevos en la app. 

![image](https://github.com/user-attachments/assets/6df98127-94f2-443e-a543-9b0346914cd8)

Vemos que hay unas 200 personas que repiten el CR para octubre.

![download](https://github.com/user-attachments/assets/26547440-497f-4aa2-a4fc-96c27f6d2cf4)

#### Análisis del top 5 de usuarios que más monto de efectivo han solicitado

![image](https://github.com/user-attachments/assets/0bbc4249-502f-4d69-b198-a02d9cb99840)

Vemos el top 5 de IDs que más retirada de efectivo han hecho, que oscila entre 15-19, pero en la columna de operaciones rechazadas vemos que la mayoria se han rechazado y unas pocas aceptadas, por lo que no los podemos considerar 'buenos' clientes.

![image](https://github.com/user-attachments/assets/ad132e92-1b3d-421d-8fa5-9f04cec83002)

Para las cuentas que se han borrado tenemos lo mismo. No parece haber una relacion entre las cuentas borradas y el total de operaciones rechazadas.

![image](https://github.com/user-attachments/assets/97a95f0c-0fac-4dd8-893c-3e5d9c53a9ea)

Si queremos hacer un plan de fidelizacion nos tenemos que fijar en la gente a la que sí se le han aceptado las peticiones (suponemos por simplicidad que esto pasas cuando la transaccion tiene el status money_back). Así obtenemos un top 10 de clientes a los que habría que hacer un seguimiento si queremos hacer un plan de fidelización.

![image](https://github.com/user-attachments/assets/9cc50261-7d87-46b5-ad0f-b0360260e1b9)

Para las IDs que se han borrado tenemos unos valores no muy alejados de los que mantienen cuenta. Se han borrado la cuenta incluso despues de haber usado la app casi tanto como la gente que sigue con cuenta.

#### Segmentación de clientes con cuentas vigentes

![image](https://github.com/user-attachments/assets/e262feec-c70c-4297-9f18-c97bbd994fe6)

De acuerdo al monto total que haya realizado un clientes, puede ser asignado a "Basico", "Bronce", "Premium" o "Platinum". Entonces podemos observar que el cliente con user_id 1946 ha realizado un monto de 1100, es el cliente con mayor monto.

#### Segmentación de clientes que han eliminado su cuenta

![image](https://github.com/user-attachments/assets/6260af64-5453-4511-a5b5-aa76d1beb1c9)

Revisamos qué tipo de cliente eran los clientes que han eliminado su cuenta, para poder analizar si eran clientes potenciales.
En la siguiente imagen observamos que de los 417 usuarios que elimaron su cuenta, había un total de 73 usuario que eran "Platinum", lo cual eran clientes potenciales.

![image](https://github.com/user-attachments/assets/55e22c7c-a5a9-463e-b680-c36878fce878)


## 3. Modelado Predictivo

En este apartado se implementó un modelo de clasificación utilizando `RandomForestClassifier` para predecir el comportamiento de las clases objetivo. Además, se llevó a cabo la búsqueda de hiperparámetros para optimizar el rendimiento del modelo.

### Implementación del Modelo
Se utilizó un bosque aleatorio con 300 árboles (`n_estimators=300`) y se fijó una semilla (`random_state=42`) para reproducibilidad. La profundidad de los árboles no se limitó para permitir una mayor flexibilidad.

![Random Forest Model](https://github.com/user-attachments/assets/c1cc78ef-49ff-48ce-bb42-7210a4d1b27a)

---

### Evaluación de Resultados

#### 1. **Precisión (Accuracy)**
La métrica de precisión mide el porcentaje de predicciones correctas. Es una medida global que indica el rendimiento general del modelo.

![Accuracy](https://github.com/user-attachments/assets/1386fa65-2425-46f6-ba97-1a5dc474175b)

#### 2. **Reporte de Clasificación (Classification Report)**
Este informe proporciona las métricas de precisión, recall y F1-score para cada clase. Es útil para evaluar cómo el modelo maneja los diferentes tipos de errores.

![Classification Report](https://github.com/user-attachments/assets/4ff6b6f3-1da2-4adf-b013-46d1f66061c6)

#### 3. **Matriz de Confusión**
La matriz de confusión muestra el número de predicciones correctas e incorrectas desglosadas por clase, proporcionando una visión detallada de los errores cometidos.

![Matriz de Confusión](https://github.com/user-attachments/assets/3080b519-b1f1-4f1e-804b-f2d1835c1df4)

---

### Análisis de Características Importantes

#### 4. **Importancia de las Características**
La importancia de las características muestra qué variables fueron más influyentes en las predicciones del modelo.

![Importancia de Características 1](https://github.com/user-attachments/assets/0f3570ac-ec6b-4a24-a2b8-34381b34a6d0)
![Importancia de Características 2](https://github.com/user-attachments/assets/2b652337-b70d-48e4-ba41-5daf20103b0b)

---

### Predicciones y Resultados

#### 5. **Predicciones Realizadas**
Aquí se muestra un ejemplo de las predicciones realizadas por el modelo sobre los datos de prueba.

![Predicciones](https://github.com/user-attachments/assets/d7b88bdd-eb75-4ead-bbd6-6d341e3485a5)

---

### Conclusión
El modelo Random Forest mostró un buen desempeño al clasificar las clases objetivo, optimizado mediante la búsqueda de hiperparámetros y evaluado con métricas clave como precisión, matriz de confusión e importancia de las características. Los resultados indican que el modelo es capaz de capturar patrones significativos en los datos, lo que lo convierte en una herramienta útil para tareas predictivas similares.



## Conclusiones Principales
- Se identificaron patrones clave en las solicitudes de adelanto de efectivo y las tasas de incidentes.
- El modelo de clasificación logró categorizar correctamente un porcentaje significativo de las solicitudes.
- Las cohortes definidas proporcionaron insights sobre la evolución temporal de las métricas clave.

## Consideraciones a futuro
- Respecto a los potenciales clientes que han borrado su cuenta podríamos haber estudiado la fee asociada a cada una de sus transacciones para tener el total de dinero que la empresa ha 'perdido' por el hecho de que estos clientes han borrado su cuenta. Suponemos que el 5 de las fees en un porcentaje y, por tanto, hay que aplicarlo a cada fee para ver el beneficio de la empresa.
- Con el modelo que hemos entrenado podriamos haber rellenado los datos faltantes de las IDs que se han borrado la cuenta con los valores más probables de retirada de efectivo para fechas concretas y ver cuanto más se ha perdido por no hacer una buena fidelizacion.

## Requisitos
- Python 3.x
- Bibliotecas: Pandas, NumPy, Matplotlib, Scikit-learn

## Cómo ejecutar el proyecto
1. Clona este repositorio.
2. Instala los requisitos mediante `pip install -r requirements.txt`.
3. Ejecuta el Jupyter Notebook `Proyecto2.ipynb` para reproducir los análisis y visualizaciones.

## Contacto
Si tienes alguna pregunta o comentario sobre este proyecto, no dudes en contactarme.

