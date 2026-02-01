# 📊 Análisis de Rentabilidad y Comportamiento del Consumidor: **Megaline**

En la industria de las telecomunicaciones, la rentabilidad sostenible no depende únicamente de la captación de clientes, sino de la **alineación estratégica** entre los límites de los planes y el comportamiento real del usuario. Una segmentación ineficiente puede derivar en ingresos volátiles o, peor aún, en una alta tasa de cancelación (*churn*) debido a una percepción negativa de valor por parte del suscriptor.

Este proyecto audita una base de **2,293 registros mensuales** para resolver una paradoja operativa crítica: ¿Cómo influyen las estructuras de los planes **Surf** y **Ultimate** en la estabilidad financiera de Megaline y qué tan cerca están los límites contractuales de las necesidades reales de consumo?

---

## 🎯 Objetivos Estratégicos

* **Diagnóstico de Rentabilidad:** Validar mediante inferencia estadística si la diferencia en el ingreso promedio por usuario (ARPU) entre ambos planes es producto del azar o responde a una tendencia estructural del negocio.
* **Perfilamiento Conductual:** Determinar si los límites de los planes condicionan el consumo real de servicios o si el cliente consume basándose en necesidades independientes de su contrato.
* **Validación de Estrategia Nacional:** Evaluar si el comportamiento de gasto en mercados específicos, como el área de **NY-NJ**, requiere tácticas regionales diferenciadas.

---

## 📑 Metodología de Trabajo

El análisis se desarrolló siguiendo un pipeline de datos riguroso para garantizar la integridad de las conclusiones:

1.  **Ingeniería y Limpieza de Datos:** Estandarización de tipos de datos y procesamiento de registros temporales.
2.  **Transformación de Unidades:** Aplicación de reglas de negocio (redondeo de minutos y conversión de MB a GB mensuales).
3.  **Construcción de ABT (Analytical Base Table):** Consolidación de tablas transaccionales en una estructura única por usuario/mes para el cálculo de ingresos.
4.  **Análisis Exploratorio (EDA):** Identificación de tendencias, estacionalidad y detección de *outliers* críticos.
5.  **Validación Estadística:** Ejecución de pruebas de hipótesis considerando la disparidad de varianzas y la robustez ante valores atípicos.

---

## 🚀 Hallazgos Clave

### 1. Independencia del Consumo
Los datos revelan que el límite del plan no condiciona el comportamiento del usuario. Los clientes de ambos planes consumen promedios casi idénticos de llamadas ($\approx 430$ min) e internet ($\approx 16$ GB), demostrando que el consumo es una respuesta a la necesidad real y no a la capacidad contratada.

### 2. La Paradoja del Plan Surf
Aunque el plan **Surf** inicia con una tarifa base baja ($\$20$ USD), la maduración del consumo hacia finales de año empuja el ingreso promedio hasta niveles comparables con el plan Ultimate ($\approx \$71$ USD). El **40% de los usuarios de Surf** terminan pagando una factura mensual superior a los $\$70$ USD.

### 3. Estabilidad en Ultimate
El plan **Ultimate** funciona como un generador de ingresos predecibles y estables. El usuario promedio de este segmento consume apenas el **14%** de sus minutos y el **56%** de sus datos disponibles, garantizando rentabilidad con bajo estrés operativo para la red.

---

## 🔬 Validación Estadística
Se aplicó un rigor matemático avanzado (Pruebas t de Welch) para asegurar la validez de los hallazgos:

* **Diferencia de Ingresos:** Se rechazó la Hipótesis Nula ($H_0$). Existe una diferencia estadísticamente significativa entre planes con un tamaño del efecto **mediano** ($\text{Cohen's d} = 0.56$ en datos limpios).
* **Consumo Regional:** Tras aplicar un filtrado preciso (`NY|NJ`), no se encontró evidencia de diferencias significativas entre dicha área y el resto del país ($p\text{-value} = 0.5908$).
* **Robustez:** Los resultados se validaron mediante un análisis de sensibilidad con y sin *outliers*, confirmando que la rentabilidad superior de Ultimate es estructural.

---

## 💡 Recomendaciones de Negocio

1.  **Up-Selling Asistido:** Migrar al 40% de usuarios de Surf que superan los $\$70$ USD mensuales al plan Ultimate para asegurar su lealtad y estabilizar el flujo de caja.
2.  **Ajuste de Límites:** Evaluar un incremento en el límite de datos de Surf a **20 GB**, dado que la mediana actual ($16.43$ GB) ya genera fricción constante por excedentes.
3.  **Estrategia Unificada:** Mantener una política de precios nacional, ya que la geografía no es un factor determinante en el ARPU.

---

## 🛠️ Stack Tecnológico

* **Lenguaje:** Python
* **Bibliotecas:** Pandas, NumPy, Matplotlib, Seaborn.
* **Estadística:** SciPy (Welch's t-test, Levene, Shapiro-Wilk, Cohen's d).