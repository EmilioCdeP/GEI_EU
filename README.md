# 📊 Análisis y Predicción de Gases de Efecto Invernadero en Europa

[![Ver informe web](https://img.shields.io/badge/📈_Ver_informe_web-Click_aquí-2ea44f?style=for-the-badge)](https://emiliocdep.github.io/GEI_EU/)


Este proyecto realiza un análisis exploratorio, espacial y de predicción sobre la expulsión de gases de efecto invernadero (GEI) en Europa a partir de datos trimestrales.\
Incluye el modelado mediante un modelo **SARIMA** y la representación **geográfica interactiva** de las emisiones por país.

------------------------------------------------------------------------

## 📁 Contenido del repositorio

El repositorio está organizado de la siguiente forma:
```
GEI_EU/
│
├── Datos/                         
│   ├── NUTS_RG_60M_2021_3035.shp  # Cartografía de Eurostat
│
├── docs/                          # ✅ Sitio web generado (GitHub Pages)
│   ├── index.html                 # Página principal renderizada
│   ├── GCEU.html                  # Informe completo interactivo
│   ├── search.json                # Configuración de búsqueda
│   ├── site_libs/                 # Librerías JS/CSS para interactividad
│   └── ...                        # Otros archivos generados automáticamente
│
├── .gitignore                     # Exclusiones del repositorio
├── GCEU.Rmd                       # Informe completo del análisis en R Markdown
└── README.md                      # Este archivo
├── _quarto.yml                    # Configuración del sitio (Quarto Website)
├── index.qmd                      # Página principal del sitio web (Quarto)

```
------------------------------------------------------------------------

## 🧠 Metodología

1.  **Carga y limpieza de datos**
    -   Descarga de datos de Eurostat mediante la API oficial (`eurostat`).\
    -   Conversión de unidades a millones de toneladas.\
    -   Estandarización de nombres de países y códigos ISO.\
    -   Creación de series temporales trimestrales (`ts`).
2.  **Análisis exploratorio**
    -   Evolución de las emisiones por año y trimestre.\
    -   Comparación entre trimestres y análisis estacional.\
    -   Identificación de tendencias y anomalías.
3.  **Geocomputación y análisis espacial** 🌍
    -   Integración de datos de emisiones con geometrías geográficas de Europa (`sf`).\
    -   Cálculo de medias de emisiones por país.\
    -   Creación de mapas temáticos interactivos con `tmap` y `ggplot2`.\
    -   Visualización de patrones espaciales y temporales de las emisiones.
4.  **Modelado y validación estadística**
    -   Modelos ARIMA y SARIMA mediante `forecast` y `tseries`.\
    -   Validación de residuos (Ljung-Box, Shapiro-Wilk, tests de autocorrelación con `lmtest`).\
    -   Selección de modelo óptimo según AIC y BIC.
5.  **Pronóstico y visualización interactiva**
    -   Predicción de emisiones hasta 10 trimestres futuros.\
    -   Gráficos interactivos con `dygraphs`.\
    -   Tablas dinámicas con `DT` y salida formateada con `printr`.

------------------------------------------------------------------------

## 📦 Librerías utilizadas

``` r
library(DT)
library(dplyr)
library(dygraphs)
library(eurostat)
library(forecast)
library(ggplot2)
library(lmtest)
library(printr)
library(scales)
library(sf)
library(stats)
library(tidyr)
library(tmap)
library(tseries)
library(zoo)
```

------------------------------------------------------------------------

## 🧾 Resultados principales

-   El modelo **SARIMA(0,1,1)(0,1,1)[4]** fue el más adecuado para la predicción de emisiones.\
-   Los residuos del modelo presentan comportamiento de **ruido blanco**, indicando un buen ajuste.\
-   Se generaron previsiones fiables hasta el año **2027**.\
-   Los mapas evidencian diferencias significativas entre regiones del norte y sur de Europa en la evolución de las emisiones.

------------------------------------------------------------------------

## 📊 Visualización del proyecto (versión web)

Para ver el informe completo con gráficos interactivos, visita la versión web del proyecto:

👉 **https://emiliocdep.github.io/GEI_EU/**

Esta visualización incluye:
- Gráficos interactivos (dygraphs, plotly, leaflet)
- Tablas dinámicas (DT)
- Resultados del modelo SARIMA
- Mapas y análisis geoespacial
- Previsiones trimestrales de emisiones

> Nota: La vista en GitHub (github.com) muestra solo el código.  
> Para ver la versión final completa debe abrirse el enlace anterior.


## 🚀 Cómo reproducir el análisis

1.  Clona el repositorio:

    ``` bash
    git clone https://github.com/EmilioCdeP/GEI_EU.git
    ```

2.  Abre el archivo `GCEU.Rmd` en **RStudio**.

3.  Instala las librerías necesarias (si no las tienes):

    ``` r
    install.packages(c("DT", "dplyr", "dygraphs", "eurostat", "forecast", "ggplot2",
                       "lmtest", "printr", "scales", "sf", "stats", "tidyr", "tmap",
                       "tseries", "zoo"))
    ```

4.  Ejecuta las celdas o **Knit** el documento para generar el informe.

------------------------------------------------------------------------

## 🔮 Futuras líneas de investigación

Aunque este proyecto analiza las emisiones de gases de efecto invernadero agregadas para el conjunto de actividades económicas, los datos disponibles permiten avanzar hacia un estudio más detallado mediante la desagregación por sectores NACE_R2.

Entre las posibles extensiones destacan:

- **Análisis temporal por sector económico**, estudiando individualmente actividades como agricultura, manufactura, electricidad y gas, construcción, transporte, servicios, etc.
- **Comparación de patrones estacionales** entre sectores para identificar cuáles presentan mayor variabilidad trimestral o tendencias más pronunciadas.
- **Estimación de la contribución relativa de cada sector** a los cambios totales observados en las emisiones europeas.
- **Modelos SARIMA sectoriales** o **modelos multivariantes** que incorporen simultáneamente varias series económicas.
- **Evaluación del impacto de políticas específicas** sobre determinados sectores, analizando si se observan rupturas estructurales en las series.
- **Integración con análisis espacial** para comparar sectores entre países o regiones.

Estas líneas permitirían obtener una visión más completa de la dinámica de emisiones en Europa y aportar información útil para la toma de decisiones y el diseño de políticas medioambientales.

------------------------------------------------------------------------

## 🧑‍💻 Autor

-   **Nombre:** Emilio Coronado de Palma
-   **Fecha:** 2025

------------------------------------------------------------------------

## 📄 Licencia

Este proyecto se distribuye bajo la licencia **MIT**, lo que permite su libre uso, modificación y distribución, siempre citando la fuente original.
