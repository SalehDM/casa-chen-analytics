# Análisis cualitativo e insights de negocio: Buffet Casa Chen

Este informe ejecutivo sintetiza los hallazgos críticos derivados del cuadro de mando interactivo en Looker Studio. El objetivo es diagnosticar la situación comercial del buffet y proponer planes de acción estratégicos basados en análisis estadísticos y demográficos.

---

## 1. Perfil y comportamiento del consumidor

### Diagnóstico demográfico y psicográfico
*   **Dependencia estudiantil**: El modelo de negocio está fuertemente sostenido por el sector educativo. Los **estudiantes representan el 61%** de la cuota total de mercado, concentrándose mayoritariamente en el rango juvenil de **15 a 24 años** (principalmente personas solteras, que equivalen al 50.3% del total). El 39% restante pertenece a profesionales activos.
*   **Segmento familiar**: El público casado representa el **43.1% del total**, consolidándose como el segundo grupo demográfico más grande del establecimiento.
*   **Impacto del entorno**: Se detectó una polarización crítica según el ambiente. Los clientes fumadores frecuentes valoran la experiencia con un sobresaliente **3.89**, mientras que los no fumadores son altamente críticos otorgando una media de **2.68**. 

### Alerta crítica: El problema de la retención
*   El hallazgo más alarmante del análisis radica en la fidelidad del cliente: **el 86.7% de los usuarios son catalogados como "no leales" (`Often_A_S = FALSE`)**. 
*   Solo un **13.3%** regresa habitualmente al buffet. Esto indica que el restaurante funciona como un negocio de atracción única (ensayo) pero falla drásticamente en la experiencia posterior, provocando una alta tasa de abandono (*churn rate*).

---

## 2. Preferencias de consumo y tráfico

### Análisis de popularidad por volumen
*   Las gastronomías **filipina y japonesa** lideran de forma absoluta el volumen de órdenes en el buffet.
*   **Fenómeno generacional**: La cocina japonesa experimenta un consumo masivo y casi exclusivo por parte del segmento joven de **15 a 24 años**. No registra tracción en los segmentos de mediana o avanzada edad.
*   **Baja popularidad**: La cocina **italiana** se consolida como la menos consumida en todos los segmentos del buffet.

---

## 3. Análisis de satisfacción y calidad

El buffet registra una puntuación media global de **3.2 / 5.0**. Al cruzar el volumen de consumo con las calificaciones reales y el comportamiento territorial, descubrimos discrepancias operativas severas:


| Tipo de cocina | Volumen de consumo | Calificación promedio | Desviación vs. media global (3.2) | Estado de alerta |
| :--- | :--- | :--- | :--- | :--- |
| **Japonesa** | Muy alto | **3.58** | `+0.38` 🟢 | **Éxito absoluto**: El producto estrella en volumen y satisfacción. |
| **Filipina** | Muy alto | **3.04** | `-0.16` 🔴 | **Riesgo operativo**: Mucho consumo pero baja calidad percibida. |

### Conclusiones estadísticas y territoriales
1.  **La paradoja filipina e india**: Son platos muy servidos pero peor calificados (filipina **3.04** e india **3.13**). Esto destruye la repetición del cliente debido a problemas de frescura, sazón o sobreexposición en las bandejas.
2.  **Rendimiento operativo por ubicación**: La zona de **Tamaraceite** lidera la satisfacción general (mediana de 3.5), mientras que **Mesa y López** decae notablemente (mediana de 3.0). Por su parte, **Siete Palmas** sufre una preocupante inestabilidad operativa y opiniones polarizadas, registrando una **varianza de 1.48**.
3.  **El nicho de personas divorciadas**: Aunque representan solo el 6.6% del público, este perfil califica al establecimiento con un histórico de **4.5 a 4.92 / 5.0** (`+1.29` por encima de la media), mostrando una afinidad excelente por la cocina japonesa.
4.  **Insatisfacción familiar**: El segmento de casados (43.1% del público) otorga la puntuación media más baja de todo el conjunto de datos con un preocupante **2.88**, evidenciando fallas en la experiencia familiar.

---

## Recomendaciones estratégicas para la gerencia

1.  **Activar el "Plan fidelización estudiante"**: Aprovechar que el 61% de la clientela son estudiantes apasionados por la comida japonesa para lanzar un programa de lealtad digital (vía aplicación o código QR). Ofrecer incentivos (ej. "a la 5.ª visita, buffet gratis") para revertir drásticamente el 86.7% de clientes no leales.
2.  **Auditoría operativa y ajuste de menú**: Revisar las recetas y la rotación de las cocinas filipina e india para mejorar sus puntuaciones. Si los costos no compensan, reducir el espacio de estas secciones en barra y reasignar esa materia prima a expandir la estación de sushi (cocina japonesa), que tiene el mayor retorno de satisfacción garantizado.
3.  **Estandarización territorial de procesos**: Implementar una auditoría interna cruzada para replicar los manuales operativos y de cocina de Tamaraceite (mediana 3.5) en los locales de Mesa y López y Siete Palmas, mitigando la varianza de 1.48 y estabilizando la consistencia de la marca.
4.  **Rediseñar la experiencia familiar**: Elevar la nota de 2.88 de este perfil clave acelerando los tiempos de reposición de platos calientes, habilitando zonas de mesas más amplias y tranquilas, y capacitando al personal en atención orientada a familias.
5.  **Adecuación de espacios e impacto del entorno**: Maximizar el confort y acondicionamiento de la terraza para retener al público fumador (promotores de la marca con 3.89 de nota), pero asegurando un aislamiento estructural óptimo para que el humo no penalice la experiencia gastronómica del cliente no fumador (2.68).
