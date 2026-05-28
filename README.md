# 📊 Análisis de datos y estrategia: Buffet Casa Chen (Las Canteras, Gran Canaria)


![Dashboard Preview](images/dashboard_preview.gif)

## Resumen del proyecto
Este repositorio contiene un proyecto integral de consultoría estratégica y Business Intelligence enfocado en el rendimiento operativo, la satisfacción del cliente y el comportamiento de consumo en el **Buffet Casa Chen** (Las Palmas de Gran Canaria). 

El objetivo central fue auditar, procesar y transformar datos transaccionales y de encuestas del establecimiento para corregir problemas operativos, identificar patrones demográficos de consumo y optimizar la toma de decisiones basada en datos reales de negocio.

---

## Contexto del negocio y solicitud del cliente
El restaurante **Buffet Casa Chen**, ubicado en la zona de Las Canteras (Las Palmas de Gran Canaria), se enfrentaba al reto de optimizar su estrategia de fidelización y mejorar la experiencia de sus comensales. Para abordar esta problemática, el establecimiento proporcionó una base de datos anónima con registros de sus clientes (variables demográficas, hábitos de consumo, presupuestos, tipos de cocina preferida y calificaciones detalladas del servicio y la comida).

### Solicitud del cliente
> *"Nos gustaría comprender mejor quiénes son nuestros clientes, qué tipo de cocina prefieren y qué factores influyen en que nos valoren bien o mal. Con esta información, queremos tomar decisiones que nos ayuden a mejorar la fidelización y la satisfacción general."*

*   **Comprender el perfil del cliente**: Identificar patrones demográficos clave (edad, género, ocupación) y socioeconómicos (presupuesto).
*   **Auditar la oferta gastronómica**: Detectar qué tipos de cocina tienen mayor volumen de demanda y cuáles reportan mejor satisfacción.
*   **Identificar impulsores de valor**: Aislar los factores estadísticos y operativos que influyen directamente en la valoración del buffet.
*   **Acciones prácticas**: Diseñar recomendaciones de negocio de alto impacto basadas exclusivamente en la evidencia de los datos analizados.

---

## Gestión y metodología
El proyecto se gestionó bajo un marco de trabajo colaborativo de alto rendimiento para asegurar entregables incrementales (MVP) y evitar bloqueos:
*   **Planificación**: Sprints semanales con reuniones diarias (*dailies*) de sincronización de 30 minutos.
*   **Comunicación**: Centralizada en servidores de Discord y repositorio compartido de documentación en la nube.

---

## Tecnologías y herramientas utilizadas
*   **Google Sheets**: Procesamiento analítico, funciones lógicas avanzadas, normalización y transformación de variables (*feature engineering*).
*   **Google Looker Studio**: Modelado de datos, diseño de interfaz interactiva y visualización de KPI de negocio.
*   **Markdown**: Documentación técnica estructurada.

---

## Ciclo de vida del proyecto y pipeline de datos

### 1. Auditoría y limpieza de datos (*data profiling & cleaning*)
Se realizó un proceso riguroso de auditoría analítica sobre la base de datos original para asegurar la máxima fiabilidad en las conclusiones estratégicas:
*   **Depuración de redundancias**: Eliminación de **20 registros duplicados** a nivel de fila y **9 ID redundantes** basándose en la llave primaria `User_ID`.
*   **Tratamiento de inconsistencias y nulos**: Eliminación de registros huérfanos sin datos demográficos base e imputación de valores vacíos en puntuaciones cuantitativas (`Food_Rating` y `Overall_Rating`) mediante la **mediana estadística** para neutralizar sesgos por valores atípicos (*outliers*).
*   **Estandarización textual**: Normalización de formatos inconsistentes en variables categóricas (`Gender`, `Marital_Status` y `Activity`).
*   *Para ver las fórmulas y el proceso técnico detallado, consulta el [Log técnico de limpieza de datos](docs/data_cleaning_log.md).*

### 2. Transformación y enriquecimiento (*feature engineering*)
*   **Inteligencia geográfica**: Reemplazo de códigos de área ambiguos por **códigos postales oficiales** de Las Palmas de Gran Canaria (Vegueta, Triana, Mesa y López, Tamaraceite, Siete Palmas) para habilitar mapas coropléticos interactivos.
*   **Cálculo dinámico de edad**: Conversión del año de nacimiento (`YOB`) a edad biológica actual (`Age`) para facilitar las agrupaciones y filtros demográficos por generación (Generación Z y Millennials).
*   **Mapeo de presupuesto**: Transformación de la escala numérica discreta original (`Budget Num` del 1 al 5) a etiquetas semánticas cualitativas legibles de forma directa (`Very Low` a `Very High`).

---

## Hallazgos estratégicos (*deep dive*)

Tras consolidar el pipeline de datos y construir el cuadro de mando interactivo en Looker Studio, se extrajeron las siguientes realidades latentes del negocio:

*   **Análisis por ubicación**: Los comensales residentes en Tamaraceite muestran la mayor satisfacción con el buffet (mediana 3.5), mientras que los clientes de Mesa y López registran la valoración más baja (mediana 3.0). El segmento de Siete Palmas presenta opiniones altamente polarizadas con una varianza de 1.48. Se recomienda investigar las diferencias de satisfacción entre barrios, estandarizando la experiencia para fidelizar a los clientes de Siete Palmas.
*   **Psicografía y consumo**: Los clientes casados tienden a puntuar consistentemente a la baja (promedios entre 2.37 y 2.89), mientras que el consumo social de alcohol se correlaciona directamente con las mejores experiencias de usuario y notas más altas de satisfacción.
*   **Riesgo operativo (La paradoja filipina)**: La cocina filipina es una de las más consumidas en volumen, pero registra la satisfacción más baja con un **3.04 / 5.00** (-0.17 por debajo de la media global). Esto sugiere una necesidad urgente de revisar recetas, sazón o frescura de insumos en barra.
*   **Éxito de la cocina japonesa**: Se consolida como la diferenciación clave y el producto estrella del buffet, liderando los índices de satisfacción con una media de **3.58 / 5.00** (+0.36 por encima de la media global de 3.2). Está impulsada con fuerza por el segmento joven (15 a 24 años) que representa el **61% de la clientela total** y el nicho de personas divorciadas (medias de **4.5 a 4.92 / 5**).

---

## Recomendaciones de negocio

Basado en la evidencia sólida de los datos, se propusieron tres líneas de acción estratégicas para la gerencia de Casa Chen:
1.  **Fidelización digital segmentada**: Implementar campañas de marketing geolocalizadas en TikTok e Instagram para el público joven (15-24 años), utilizando la comida japonesa como gancho principal para revertir el **86.7%** de clientes no leales mediante cupones o programas de puntos por QR.
2.  **Estandarización del servicio operativo**: Realizar un análisis de expectativas para identificar qué factores causan la insatisfacción en el segmento de comensales procedentes de Siete Palmas, replicando las estrategias de atención que consolidan la alta fidelidad de los clientes de Tamaraceite.
3.  **Optimización del espacio de barra**: Reducir la variedad e inventario de la cocina italiana (la menos consumida en todos los segmentos) y reasignar esos recursos económicos y metros de barra a potenciar la estación de sushi y cocina japonesa.

---

## Estructura del repositorio

```text
/
├── data/
│   ├── BBDD Original.xlsx             # Dataset original para auditoría inicial
│   ├── Cuisine_Rating_Data.csv        # Dataset original en formato CSV optimizado para la importación
│   └── BBDD_Processed_Final.xlsx      # Base de datos final limpia y transformada
├── docs/
│   ├── analisis_cualitativo.md        # Reporte con los insights de negocio
│   └── data_cleaning_log.md           # Registro técnico detallado de limpieza y fórmulas
├── images/
│   └── dashboard_preview.gif          # Grabación animada del cuadro de mando interactivo
└── README.md                          # Presentación principal del proyecto
```

---

## Documentación y enlaces
*   [**Dashboard interactivo en Looker Studio**](https://datastudio.google.com/reporting/2c21be8f-e4ed-4a19-b67f-a6ba21d5c2b3)
*   [**Ver base de datos procesada en Google Sheets**](https://docs.google.com/spreadsheets/d/1tvt9qzrWh3UZKZekQ1xKOXhWLUJhZtAC53b4TIPGH5A/edit?usp=sharing)
*   [**Log técnico de limpieza de datos (Markdown)**](docs/data_cleaning_log.md)
*   [**Informe de análisis cualitativo (Markdown)**](docs/analisis_cualitativo.md)

---

## Equipo y colaboración
Este proyecto fue desarrollado de manera colaborativa. Todos los integrantes participaron de forma equitativa en el ciclo completo de ingeniería de datos, modelado analítico y consultoría estratégica:

*   **Alberto Domínguez** — [GitHub Profile](https://github.com/CobaltHeron)
*   **Azahara García** — [GitHub Profile](https://github.com/Azaharag1984)
*   **Saleh Daf** — [GitHub Profile](https://github.com/SalehDM)

---
*Nota: Caso de consultoría analítica integral (end-to-end) enfocado en la optimización operativa y la retención de clientes en el sector Horeca.*
