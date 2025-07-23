# TelecomX_Latam_WilmerSubero

# Informe de Análisis de Evasión de Clientes (Churn)

## 🔹 Introducción

Este informe presenta un análisis exploratorio de datos sobre la evasión de clientes (Churn) de TelecomX. El objetivo es identificar los factores y patrones clave asociados con la decisión de un cliente de cancelar su servicio, con el fin de desarrollar estrategias efectivas para reducir la tasa de evasión y mejorar la retención de clientes.

## 🔹 Limpieza y Tratamiento de Datos

Se inició el proceso descargando los datos de clientes desde una URL en formato JSON utilizando las bibliotecas `requests` y `pandas`. El JSON, que presentaba una estructura anidada, fue aplanado utilizando `pd.json_normalize` para crear un DataFrame tabular (`df`).

Se realizaron las siguientes tareas de limpieza y tratamiento:
- Conversión de la columna `account.Charges.Total` a tipo numérico, manejando valores no válidos con `errors='coerce'`.
- Identificación y manejo de valores vacíos o en blanco en la columna `Churn`, los cuales fueron tratados como valores nulos (`NaN`) y posteriormente eliminados del DataFrame.
- Conversión de columnas con valores 'Yes'/'No' a tipo booleano para facilitar el análisis.
- Renombramiento de columnas a español para mayor claridad (`df.rename`).
- Creación de una nueva columna `CargosDiarios` a partir de los cargos mensuales.

## 🔹 Análisis Exploratorio de Datos

Se realizó un análisis descriptivo para comprender la distribución y estadísticas de las variables numéricas (`df.describe().T`) y la distribución de valores en las variables categóricas (`df.value_counts`).

Las visualizaciones clave generadas incluyen:

### Distribución de Evasión

Un gráfico de barras mostró la proporción de clientes que evadieron (`Sí`) frente a los que no (`No`), indicando la magnitud del problema de evasión.


### Recuento de Evasión por Variables Categóricas

Se generaron gráficos de barras para analizar la relación entre la evasión y variables como Género, Tipo de Contrato, Método de Pago, Factura Digital, Tipo de Internet, Soporte Técnico, Tiene Pareja y Tiene Dependientes. Estos gráficos revelaron diferencias notables en las tasas de evasión según las categorías de estas variables.


### Conteo de Evasión por Variables Numéricas

Se utilizaron boxplots para visualizar la distribución de variables numéricas (Antigüedad en Meses, Cargos Mensuales, Cargos Totales, Cargos Diarios) para los grupos de clientes que evadieron y los que no. Estos gráficos permitieron identificar si las métricas numéricas difieren significativamente entre los dos grupos.



## 🔹 Conclusiones e Insights

El análisis de los datos y las visualizaciones ha revelado varios factores fuertemente asociados con la evasión de clientes:

- **Antigüedad:** Los clientes con menor antigüedad son significativamente más propensos a evadir.
- **Cargos Mensuales/Diarios:** Clientes con cargos mensuales y diarios más altos muestran una mayor tasa de evasión.
- **Tipo de Contrato:** Los contratos mes a mes tienen una tasa de evasión mucho mayor que los contratos a largo plazo (uno o dos años).
- **Método de Pago:** El pago con cheque electrónico está asociado a una mayor evasión.
- **Servicio de Internet:** Los clientes con servicio de fibra óptica tienen una tasa de evasión más alta.
- **Soporte Técnico:** La ausencia de soporte técnico incrementa la probabilidad de evasión.
- **Factura Digital:** La facturación digital parece estar correlacionada con una mayor evasión.
- **Factores menos influyentes:** El género, tener pareja y tener dependientes mostraron una menor asociación con la evasión en comparación con las otras variables analizadas.

En resumen, los clientes con mayor riesgo de evasión son aquellos que son **nuevos**, tienen **altos cargos mensuales**, con contratos **mes a mes**, que usan **cheque electrónico** como método de pago, tienen servicio de **fibra óptica** y **no tienen soporte técnico**.

## 🔹 Recomendaciones

Basado en los insights obtenidos, se proponen las siguientes recomendaciones estratégicas para reducir la evasión:

1.  **Programas de Retención Temprana:** Enfocar esfuerzos en los clientes con poca antigüedad, ofreciendo incentivos o un seguimiento especial para asegurar una buena experiencia inicial.
2.  **Optimización de Precios/Planes:** Revisar la estructura de cargos mensuales, especialmente para los planes de fibra óptica, para asegurar que sean competitivos y percibidos como justos por los clientes.
3.  **Fomentar Contratos a Largo Plazo:** Ofrecer descuentos o beneficios atractivos para incentivar a los clientes a migrar de contratos mes a mes a contratos de uno o dos años.
4.  **Análisis y Mejora del Método de Pago Electrónico:** Investigar si existen problemas específicos asociados con el método de pago electrónico que puedan estar contribuyendo a la insatisfacción del cliente.
5.  **Fortalecer el Soporte Técnico:** Promocionar activamente y mejorar la calidad del servicio de soporte técnico, ya que su ausencia es un fuerte predictor de evasión. Considerar incluir soporte técnico como parte estándar de ciertos planes.
6.  **Experiencia con Fibra Óptica:** Investigar las causas detrás de la alta evasión en clientes de fibra óptica. Podría ser necesario mejorar la estabilidad del servicio, la atención al cliente para este segmento, o gestionar mejor las expectativas iniciales.
7.  **Revisar el Proceso de Factura Digital:** Aunque menos influyente, podría valer la pena investigar si hay algún problema de usabilidad o comunicación asociado con la facturación digital que contribuya a la evasión.

Implementar estas recomendaciones, enfocándose en los segmentos de mayor riesgo y las variables más influyentes, puede ayudar a TelecomX a reducir su tasa de evasión y mejorar la lealtad de sus clientes.
