# Marketing Bancario (con contexto social/económico)

Este documento contiene la descripción, estructura y detalles de los atributos del conjunto de datos de Marketing Bancario, utilizado para el Examen Final Transversal (EFT).

---

## 1. Información General

* **Creadores del dataset:** Sérgio Moro (ISCTE-IUL), Paulo Cortez (Univ. Minho) y Paulo Rita (ISCTE-IUL) @ 2014.
* **Uso anterior:** El conjunto de datos completo (`bank-additional-full.csv`) fue descrito y analizado en:
  > S. Moro, P. Cortez y P. Rita. *A data-driven approach to predict the success of bank telemarketing*. Decision Support Systems (2014), doi:[10.1016/j.dss.2014.03.001](https://doi.org/10.1016/j.dss.2014.03.001).

---

## 2. Descripción y Contexto

Este conjunto de datos se basa en el dataset **"Bank Marketing"** del repositorio UCI Machine Learning. 

Los datos han sido enriquecidos con la adición de cinco características socioeconómicas nacionales (de Portugal, con una población de aproximadamente 10 millones) publicadas por el Banco de Portugal.

> [!NOTE]
> Este conjunto de datos no incluye la totalidad de los atributos originales debido a políticas y consideraciones de privacidad.

### Archivos de Datos Incluidos
1. `bank-additional-full.csv`: Contiene la totalidad de los ejemplos (**41,188 instancias**), ordenados cronológicamente desde mayo de 2008 hasta noviembre de 2010.
2. `bank-additional.csv`: Contiene una muestra aleatoria del **10%** de los ejemplos (**4,119 instancias**). Se proporciona para realizar pruebas rápidas o algoritmos con alto costo computacional (como SVM).

**Objetivo de clasificación:** Predecir si el cliente suscribirá o no un depósito a plazo fijo en el banco (variable objetivo/salida `y`).

---

## 3. Estructura de Atributos

El dataset contiene **20 variables de entrada** y **1 variable de salida**.

A continuación se detallan y organizan las variables clasificadas por categorías:

### A. Datos del Cliente del Banco

| # | Atributo (CSV) | Nombre en Español | Tipo de Dato | Valores Permitidos / Descripción |
|---|---|---|---|---|
| 1 | `age` | Edad | Numérico | Edad del cliente en años. |
| 2 | `job` | Trabajo | Categórico | Tipo de trabajo: `"admin."` (administrador), `"blue-collar"` (obrero), `"entrepreneur"` (empresario), `"housemaid"` (empleado doméstico), `"management"` (gerente), `"retired"` (jubilado), `"self-employed"` (autónomo), `"services"` (servicios), `"student"` (estudiante), `"technician"` (técnico), `"unemployed"` (desempleado), `"unknown"` (desconocido). |
| 3 | `marital` | Estado civil | Categórico | Estado civil: `"divorced"` (divorciado/viudo), `"married"` (casado), `"single"` (soltero), `"unknown"` (desconocido). |
| 4 | `education` | Educación | Categórico | Nivel educativo: `"basic.4y"`, `"basic.6y"`, `"basic.9y"` (básico), `"high.school"` (bachillerato), `"illiterate"` (analfabeto), `"professional.course"` (curso profesional), `"university.degree"` (título universitario), `"unknown"` (desconocido). |
| 5 | `default` | Mora | Categórico | ¿Tiene crédito en mora?: `"no"`, `"yes"`, `"unknown"`. |
| 6 | `housing` | Vivienda | Categórico | ¿Tiene préstamo para vivienda?: `"no"`, `"yes"`, `"unknown"`. |
| 7 | `loan` | Préstamo | Categórico | ¿Tiene préstamo personal?: `"no"`, `"yes"`, `"unknown"`. |

### B. Relacionados con el Último Contacto de la Campaña Actual

| # | Atributo (CSV) | Nombre en Español | Tipo de Dato | Valores Permitidos / Descripción |
|---|---|---|---|---|
| 8 | `contact` | Contacto | Categórico | Tipo de comunicación de contacto: `"cellular"` (celular), `"telephone"` (teléfono). |
| 9 | `month` | Mes | Categórico | Mes del año del último contacto: `"jan"`, `"feb"`, `"mar"`, ..., `"nov"`, `"dec"`. |
| 10 | `day_of_week` | Día de la semana | Categórico | Día de la semana del último contacto: `"mon"`, `"tue"`, `"wed"`, `"thu"`, `"fri"`. |
| 11 | `duration` | Duración | Numérico | Duración del último contacto en segundos. <br><br>**Nota importante:** Afecta en gran medida la salida (si `duración = 0` entonces `y = "no"`). Se recomienda descartar este atributo para modelos predictivos realistas, ya que su valor real solo se conoce después de finalizada la llamada. |

### C. Otros Atributos de la Campaña

| # | Atributo (CSV) | Nombre en Español | Tipo de Dato | Valores Permitidos / Descripción |
|---|---|---|---|---|
| 12 | `campaign` | Campaña | Numérico | Número de contactos realizados durante esta campaña y para este cliente (incluye el último contacto). |
| 13 | `pdays` | Días transcurridos | Numérico | Número de días transcurridos desde que el cliente fue contactado por última vez en una campaña anterior (`999` significa que el cliente no fue contactado previamente). |
| 14 | `previous` | Contactos anteriores | Numérico | Número de contactos realizados antes de esta campaña y para este cliente. |
| 15 | `poutcome` | Resultado previo | Categórico | Resultado de la campaña de marketing anterior: `"failure"` (fracaso), `"nonexistent"` (inexistente), `"success"` (éxito). |

### D. Indicadores de Contexto Social y Económico

| # | Atributo (CSV) | Nombre en Español | Tipo de Dato | Valores Permitidos / Descripción |
|---|---|---|---|---|
| 16 | `emp.var.rate` | Tasa de var. empleo | Numérico | Tasa de variación del empleo (indicador trimestral). |
| 17 | `cons.price.idx` | IPC | Numérico | Índice de precios al consumidor (indicador mensual). |
| 18 | `cons.conf.idx` | Confianza del cons. | Numérico | Índice de confianza del consumidor (indicador mensual). |
| 19 | `euribor3m` | Euribor 3 meses | Numérico | Tasa Euribor a 3 meses (indicador diario). |
| 20 | `nr.employed` | Nro. de empleados | Numérico | Número de empleados en el mercado (indicador trimestral). |

### E. Variable de Salida (Objetivo Deseado)

| # | Atributo (CSV) | Nombre en Español | Tipo de Dato | Valores Permitidos / Descripción |
|---|---|---|---|---|
| 21 | `y` | Suscrito | Binario | ¿El cliente ha suscrito un depósito a plazo?: `"yes"`, `"no"`. |

---

## 4. Notas y Consideraciones Adicionales

* **Valores Faltantes:** Varios atributos categóricos presentan valores faltantes codificados bajo la etiqueta `"unknown"`. Estos valores pueden tratarse como una categoría adicional o resolverse mediante técnicas de imputación o eliminación de registros.
* **Carga de Datos en Python (Pandas):** El delimitador del archivo es el punto y coma (`;`). Para importarlo correctamente en un script de Python o Jupyter Notebook se puede utilizar:
  ```python
  import pandas as pd

  # Cargar el dataset completo
  df = pd.read_csv('bank-additional-full.csv', sep=';')
  ```
