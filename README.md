# challenge_telecomx_latam

Proyecto TelecomXLATAM: Análisis de Churn en Clientes de Telecomunicaciones

📄 Descripción del Proyecto

Este proyecto tiene como objetivo principal identificar los factores clave que influyen en la decisión de los clientes de una empresa de telecomunicaciones de abandonar el servicio (Churn). A través de un análisis exploratorio de datos (EDA) detallado, buscamos comprender los patrones de comportamiento, las características demográficas y el impacto de los servicios contratados, el tipo de contrato y los métodos de pago en la tasa de Churn. El análisis busca proporcionar insights accionables y recomendaciones estratégicas para mejorar la retención de clientes.

🚀 Extracción de Datos

Los datos fueron obtenidos directamente desde una API pública en formato JSON y cargados en un DataFrame de Pandas para su posterior manipulación y análisis. La URL de origen es: https://raw.githubusercontent.com/ingridcristh/challenge2-data-science-LATAM/refs/heads/main/TelecomX_Data.json

🔧 Limpieza y Tratamiento de Datos

El proceso de preparación de datos fue crucial para asegurar la calidad y fiabilidad del análisis. Los pasos clave incluyeron:

Aplanamiento de Columnas Anidadas: Las columnas que contenían diccionarios anidados (customer, phone, internet, account) fueron aplanadas, extrayendo sus claves como nuevas columnas individuales en el DataFrame principal.
Conversión y Limpieza de account_Charges.Total: Se identificó que esta columna, de tipo object, contenía valores no numéricos. Se limpiaron los espacios en blanco, se convirtieron los valores a tipo numérico (float64) y los valores NaN resultantes se imputaron con 0.
Verificación de Valores Ausentes: Se confirmó que, después de las transformaciones, no existían valores nulos en ninguna columna.
Identificación de Filas Duplicadas: Se verificó que no había filas completamente duplicadas en el DataFrame.
Corrección de Inconsistencias en Churn: La columna Churn contenía cadenas vacías (''). Las filas con estos valores inconsistentes fueron eliminadas, reduciendo el número total de entradas de 7267 a 7043.

📊 Análisis Exploratorio de Datos (EDA)

3.1 Análisis Descriptivo General
customer_SeniorCitizen: Aproximadamente el 16% de los clientes son personas mayores.
customer_tenure: La duración promedio de permanencia es de 32 meses, con una alta variabilidad. Los clientes más nuevos (25% con menos de 9 meses) son un grupo clave.
account_Charges.Monthly: El cargo mensual promedio es de  64.76,conunrangosignificativoqueindicadiversospaquetesdeservicios.∗∗∗‘accountCharges.Total‘:∗∗Eltotalgastadoporclientepromedia 2283.30, también con gran dispersión.
Churn: El 26.6% de los clientes ha abandonado el servicio, mientras que el 73.4% ha permanecido.
customer_gender: Distribución equitativa entre géneros.
Servicios: Observación de clientes sin ciertos servicios (teléfono o internet), lo que puede influir en el Churn.
account_Contract: Predominan los contratos mes a mes, seguidos por los de dos y un año.
account_PaymentMethod: El cheque electrónico es el método de pago más común.
3.2 Distribución de Churn
De los 7043 clientes, 5174 permanecen y 1869 han dejado la empresa, confirmando un problema de Churn significativo.

3.3 Churn por Variables Categóricas
Género: No hay diferencia clara en la tasa de Churn.
SeniorCitizen: Los clientes mayores tienen una tasa de Churn significativamente más alta.
Partner y Dependents: Clientes sin pareja ni dependientes son más propensos a irse.
Servicio Telefónico: La presencia o no del servicio telefónico no impacta mucho, pero los que tienen MultipleLines muestran un Churn ligeramente superior.
InternetService: Clientes con 'Fiber optic' tienen una tasa de Churn considerablemente más alta. Los que no tienen servicio de internet tienen la menor tasa de Churn.
Servicios Adicionales de Internet: La ausencia de servicios como OnlineSecurity, OnlineBackup o TechSupport se asocia con un Churn más alto.
Contract: Los contratos 'Month-to-month' tienen una tasa de Churn muy alta; los contratos de 'Two year' son los más estables.
PaperlessBilling: Clientes con facturación sin papel (Yes) tienen una tasa de Churn más alta.
PaymentMethod: El 'Electronic check' es el método de pago con la mayor tasa de Churn.
3.4 Churn por Variables Numéricas
customer_tenure: Los clientes que se van (Churn='Yes') tienen una permanencia mucho menor.
account_Charges.Monthly: Los clientes que abandonan suelen tener cargos mensuales más altos.
account_Charges.Total: Los clientes que se van tienen un total de cargos acumulados más bajo, lo cual es consistente con su menor permanencia.

💡 Conclusiones e Insights

El análisis revela que los clientes con mayor riesgo de Churn son:

Clientes nuevos y con contratos mensuales: Son los más vulnerables a la evasión.
Usuarios de Fibra Óptica sin servicios adicionales: La calidad percibida del servicio de fibra óptica y la falta de complementos de seguridad/soporte son puntos de fricción.
Clientes con altos cargos mensuales y que pagan con cheque electrónico: Insatisfacción con la relación calidad-precio y posibles problemas con el método de pago.
Demografía específica: Personas mayores y clientes sin pareja o dependientes.

📝 Recomendaciones Estratégicas

Programas de Retención para Clientes Nuevos: Implementar programas de bienvenida y seguimiento proactivo durante los primeros meses, ofreciendo incentivos para contratos más largos.
Mejora de la Experiencia con Fibra Óptica: Investigar las causas de la alta evasión en este segmento (calidad, soporte) y promover activamente los servicios de valor añadido.
Optimización de Planes y Costos: Revisar la estructura de precios para planes con altos cargos mensuales y considerar ofertas más competitivas o bundles flexibles.
Revisión del Proceso de Pago: Analizar la experiencia de los usuarios de Electronic check para identificar y resolver posibles fricciones.
Marketing y Ofertas Segmentadas: Diseñar campañas personalizadas para segmentos demográficos vulnerables (Senior Citizens, clientes sin Partner/Dependents) que aborden sus necesidades específicas.
🛠️ Tecnologías Utilizadas
Python
Pandas: Para manipulación y análisis de datos.
Matplotlib: Para la creación de visualizaciones.
Seaborn: Para la creación de visualizaciones estadísticas atractivas.
