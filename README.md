# 📊 Análisis y Predicción de Gases de Efecto Invernadero en Europa

[![Ver informe web](https://img.shields.io/badge/📈_Ver_informe_web-Click_aquí-2ea44f?style=for-the-badge)](https://emiliocdep.github.io/GEI_EU/)


Este proyecto realiza un análisis exploratorio, espacial y de predicción sobre la expulsión de gases de efecto invernadero (GEI) en Europa a partir de datos trimestrales.\
Incluye el modelado mediante un modelo **SARIMA** y la representación **geográfica interactiva** de las emisiones por país.

------------------------------------------------------------------------

## 📁 Contenido del repositorio

GEI_EU/
│
├── GCEU.Rmd # Informe completo del análisis en R Markdown
├── index.qmd # Página principal del sitio web (Quarto)
├── _quarto.yml # Configuración del sitio (Quarto Website)
│
├── docs/ # ✅ Sitio web generado (GitHub Pages)
│ ├── index.html # Página principal renderizada
│ ├── GCEU.html # Informe completo renderizado con interactivos
│ ├── search.json # Datos de búsqueda interna del sitio
│ ├── site_libs/ # Librerías JS/CSS necesarias para gráficos interactivos
│ └── (otros archivos) # Archivos auxiliares generados automáticamente
│
├── .gitignore # Exclusiones del repositorio
└── README.md # Descripción general del proyecto

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

## 🧑‍💻 Autor

-   **Nombre:** Emilio Coronado\
-   **Fecha:** 2025

------------------------------------------------------------------------

## 📄 Licencia

Este proyecto se distribuye bajo la licencia **MIT**, lo que permite su libre uso, modificación y distribución, siempre citando la fuente original.
