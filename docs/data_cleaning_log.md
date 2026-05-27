# Log de limpieza y transformación de datos

Este documento detalla el pipeline técnico y las operaciones lógicas ejecutadas en **Google Sheets** para transformar la base de datos cruda (`BBDD_Original.xlsx`) en el conjunto de datos optimizado, limpio y consistente (`BBDD_Processed_Final.xlsx`) para su posterior explotación en Looker Studio.

---

## Fase 1: Limpieza y normalización (*data cleaning*)

### 1. Eliminación de registros duplicados
*   **Problema**: Se detectaron múltiples filas idénticas repetidas para un mismo identificador único de usuario (ej. `User_ID` 4, 26, 41, 42, 47, 52, 59, 83, 84).
*   **Solución**: Se aplicó la función nativa de eliminación de duplicados tomando como llave primaria la columna `User_ID` para asegurar la integridad referencial.

### 2. Estandarización de variables categóricas
*   **Género (`Gender`)**: Inconsistencias críticas con términos mixtos en inglés y variantes de formato (`Male`, `male`, `boy`, `Female`, `female`, `girl`). Se unificó a un estándar binario mediante lógica condicional:
    ```sheets
    =SI(O(D2="Male", D2="male", D2="boy"), "Male", "Female")
    ```
*   **Estado civil (`Marital_Status`)**: Se eliminaron las discrepancias de capitalización (`single`, `Married`, `married`, `divorced`) aplicando una limpieza con la función `NOMPROPIO` para homogeneizar a `Single`, `Married` y `Divorced`.
*   **Ocupación (`Activity`)**: Agrupación taxonómica para consolidar variantes de estudiantes (`Student`, `student`, `Studying`) y trabajadores (`Professional`, `professional`, `Working`).

### 3. Tratamiento e imputación de valores nulos (*missing values*)
*   **Puntuaciones de calidad (*ratings*)**: Las celdas vacías en las métricas cuantitativas `Food_Rating` y `Overall_Rating` rompían las tarjetas de promedios. Se imputaron los registros vacíos utilizando la **mediana estadística** del resto de la columna para evitar sesgos por valores atípicos (*outliers*).
*   **Ubicaciones geográficas**: Los registros huérfanos con celdas vacías en la zona o barrios se validaron y rellenaron cruzando la consistencia del set de datos.

---

## Fase 2: Enriquecimiento de datos (*feature engineering*)

### 4. Inyección de inteligencia geográfica
*   **Acción**: Se eliminó la columna ambigua `Area_code` y se transformó la columna `Location` mapeando los nombres de los barrios reales a sus **códigos postales oficiales de Las Palmas de Gran Canaria**, habilitando el uso de mapas coropléticos en Looker Studio:
    *   `Vegueta` ➡️ **`ES-35001`**
    *   `Triana` ➡️ **`ES-35002`**
    *   `Mesa y López` ➡️ **`ES-35010`**
    *   `Tamaraceite` ➡️ **`ES-35018`**
    *   `Siete Palmas` ➡️ **`ES-35019`**

### 5. Cálculo dinámico de edad
*   **Acción**: La columna original del año de nacimiento (`YOB`) dificultaba la segmentación demográfica en tiempo real. Se creó la columna calculada `Age` determinando la edad biológica exacta basada en la fecha de la auditoría del proyecto:
    ```sheets
    =SI(ESNUMERO(E2), AÑO(HOY()) - E2, "")
    ```

### 6. Cuantificación y mapeo de presupuesto
*   **Acción**: Se transformó la escala numérica discreta original (`Budget Num` del 1 al 5) en etiquetas categóricas semánticas claras (`Budget`) mediante funciones `SI` anidadas o tablas de búsqueda (`BUSCARV`) para mejorar la legibilidad del cuadro de mando:
    *   `1` ➡️ **`Very Low`**
    *   `2` ➡️ **`Low`**
    *   `3` ➡️ **`Medium`**
    *   `4` ➡️ **`High`**
    *   `5` ➡️ **`Very High`**

### 7. Normalización lógica de fidelización
*   **Acción**: La columna que define la recurrencia del cliente (`Often_A_S`) contenía formatos lógicos y cadenas de texto cruzadas (`No`, `FALSE`, `Yes`, `TRUE`). Se estandarizó por completo a variables booleanas puras de tipo **`TRUE` / `FALSE`** requeridas por los motores de agregación de Business Intelligence.
