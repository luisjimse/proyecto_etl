# ETL de Reservas de Hoteles

## 📚 Descripción

El objetivo de este proyecto es implementar y ejecutar un proceso de ETL (Extracción, Transformación y Carga) para procesar datos de reservas de hoteles propios y de la competencia. Este proceso permitirá en futuras fases analizar la demanda hotelera, identificar patrones de reserva y optimizar estrategias de precios y ocupación.

## 💂️ Estructura del Proyecto

```plaintext
├── data/                # Datos crudos y procesados
│   ├── raw/             # Datos originales
│   └── processed/       # Datos ya transformados y listos para análisis
├── jupyters/            # Archivos .ipynb con el código del ETL
├── src/                 # (Vacío por ahora, se incluirán scripts .py en futuros pasos)
├── README.md            # Descripción del proyecto y guía para reproducir el proceso
```

## 🛠️ Instalación y Requisitos

- **Entorno de Ejecución:**  
  - Python (se recomienda utilizar un entorno virtual con `venv`)
  - SQL

- **Librerías y Herramientas:**  
  - [Pandas](https://pandas.pydata.org/) para la manipulación y análisis de datos.
  - [Numpy](https://numpy.org/) para operaciones numéricas.
  - [psycopg2](https://www.psycopg.org/) para la conexión y operaciones con bases de datos PostgreSQL.
  - [Selenium](https://www.selenium.dev/) para la automatización del web scraping.
  - [pyarrow](https://arrow.apache.org/docs/python/) para la lectura y escritura de archivos .parquet.

- **Requisitos Adicionales:**  
  - Acceso a fuentes de datos de reservas de hoteles propios y de la competencia.

## 🔄 Proceso ETL

### Extracción

1. **Fuente de Datos Principal (.parquet):**  
   - Se inicia el proceso leyendo el archivo .parquet proporcionado, el cual contiene aproximadamente 15.000 registros.
   
2. **Web Scraping:**  
   - Se automatiza la extracción de datos de reservas de la competencia utilizando Selenium. Esto incluye información sobre disponibilidad, tarifas y tendencias de ocupación.
   
3. **API Externa:**  
   - Se integran datos de API de reservas de la Comunidad de Madrid para complementar el dataset.

### Transformación

1. **Limpieza y Formateo:**  
   - Se corrigen los formatos de datos (fechas, números, etc.) y se estandarizan los valores para asegurar la coherencia entre las diferentes fuentes.
   - Se rellenan los valores nulos utilizando dos estrategias:  
     - **Web Scraping:** Para completar datos faltantes con información de fuentes externas.
     - **Cálculo de la Media:** Cuando la información no está disponible vía scraping, se opta por imputar el valor medio.
   
2. **Integración de Fuentes:**  
   - Se combinan los datos extraídos del archivo .parquet, el web scraping y la API para formar un dataset unificado y enriquecido.

### Carga

1. **Base de Datos y SQL:**  
   - Utilizando la librería `psycopg2`, se realiza la carga de los datos procesados en una base de datos PostgreSQL. Esto facilita futuras consultas y análisis utilizando SQL.
   
2. **Validación de Carga:**  
   - Se ejecutan consultas de verificación para asegurar que los datos se han cargado correctamente y que se mantiene la integridad de la información.

## 🎯 Próximos Pasos

- **Análisis de Resultados:**  
  - Explorar y analizar los datos transformados para responder a las preguntas clave sobre patrones de reserva y ocupación.
  
- **Desarrollo de Modelos Predictivos:**  
  - Una vez realizado el análisis, se podrá desarrollar un modelo predictivo que permita anticipar la demanda hotelera en función de variables como la ubicación, temporada y tipo de hotel.
  
- **Implementación de Scripts en `src/`**  
  - Migrar los procesos actuales de los notebooks en `jupyters/` a scripts Python en `src/` para mayor modularidad y automatización.

## ✏️ Autores

- **Luis Jiménez** - [@luisjimse](https://github.com/luisjimse)
