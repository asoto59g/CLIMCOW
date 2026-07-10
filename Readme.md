## **DESCRIPCIÓN PROYECTO CLIMCOW** 

Este proyecto implementa una aplicación modular en **Google Earth Engine Code Editor** diseñada para realizar análisis integrales de fincas o áreas de estudio, combinando datos agroclimáticos, hídricos y ganaderos. Su objetivo principal es actuar como una herramienta de apoyo en la toma de decisiones mediante la generación de indicadores clave y mapas de diagnóstico. 

Visor geografico del proyecto:  https://api-project-732156244341.projects.earthengine.app/view/climcow

A continuación, se presenta un resumen de las capas generadas, manteniendo las escalas: 

## 1. Pronóstico Meteorológico (ECMWF) 

Este módulo proyecta condiciones a corto plazo (7 y 15 días) para alertar sobre posibles riesgos: 

- **Temperatura (°C):** < 10 (Baja), 10 - 25 (Moderada), 25 - 32 (Cálida), > 32 ( **Estrés térmico potencial** ) . 

- **Precipitación Pronosticada (mm):** 0 - 5 (Baja), 5 - 20 (Ligera), 20 - 50 (Moderada), > 50 (Alta) . 

- **Humedad Relativa (%):** < 40 (Aire seco), 40 - 70 (Moderada), > 70 (Alta). 

- **Viento (m/s):** < 2 (Bajo), 2 - 5 (Moderado), > 5 (Fuerte). 

## 2. Precipitación Observada (CHIRPS / IMERG) 

Analiza la lluvia acumulada y su comportamiento histórico: 

- **Lluvia Acumulada (mm):** 0 - 10 (Muy baja), 10 - 50 (Baja), 50 - 150 (Moderada), > 150 (Alta). 

- **Anomalía de Lluvia:** Valores < 0 indican menos lluvia de lo normal; > 0 indican exceso frente al promedio histórico. 

- **SPI (Índice de Precipitación Estandarizado):** < -2.0 (Sequía extrema), -2.0 a -1.0 (Sequía severa/moderada), -1.0 a 1.0 (Normal), > 1.0 (Húmedo). 

## 3. Variables de Suelo (OpenLandMap / SoilGrids) 

Evalúa las propiedades físicas y químicas del terreno: 

- **Arcilla/Arena (%):** Define la textura; por ejemplo, > 35% de arcilla indica suelos arcillosos y > 70% de arena indica suelos arenosos. 

- **Materia Orgánica (%):** < 2 (Baja), 2 - 5 (Media), > 5 (Alta). 

- **pH:** < 5.5 (Ácido), 5.5 - 7.5 (Adecuado para pasturas), > 7.5 (Alcalino). 

- **Agua Disponible (mm):** < 50 (Baja reserva), 50 - 120 (Reserva media), > 120 (Buena reserva). 

## 4. Topografía y Relieve (Copernicus DEM) 

- **Pendiente (Grados):** 0 - 5 (Plano), 5 - 15 (Ondulado), 15 - 30 (Inclinado), > 30 (Muy pendiente). 

- **TWI (Índice de Humedad Topográfica):** Valores altos señalan zonas donde tiende a acumularse la humedad. 

## 5. Análisis Satelital (Sentinel-1 y Sentinel-2) 

- **Humedad S1 (Radar):** 0 - 0.3 (Baja), 0.3 - 0.6 (Media), 0.6 - 1.0 (Alta humedad superficial). 

- **NDVI (Vigor Vegetal):** < 0.2 (Suelo desnudo), 0.2 - 0.35 (Pobre), 0.35 - 0.55 (Medio), > 0.55 ( **Vegetación vigorosa** ). 

- **NDMI (Humedad Vegetal):** < 0 (Vegetación seca), 0 - 0.3 (Media), > 0.3 (Alta humedad foliar). 

- **LAI (Índice de Área Foliar):** < 1 (Bajo), 1 - 3 (Medio), > 3 (Alto). 

## 6. Balance Hídrico y Riesgos 

Calcula el estado del agua integrando suelo, clima y satélite: 

- **Déficit Hídrico (mm):** 0 - 20 (Bajo), 20 - 60 (Moderado), > 60 (Alto). 

- **Exceso Hídrico (mm):** 20 - 60 (Riesgo de saturación), > 60 ( **Alto riesgo de barro/encharcamiento** ). 

- **Humedad Relativa del Suelo:** 0 - 0.3 (Seco), 0.3 - 0.6 (Medio), > 0.6 (Húmedo). 

## 7. Indicadores Ganaderos y Semáforo 

Es el resumen operativo para el ganadero: 

- **Biomasa (kg MS/ha):** < 1000 (Baja), 1000 - 3000 (Media), > 3000 (Alta). 

- **Riesgo de Sequía / Barro:** 0 - 0.3 (Bajo), 0.3 - 0.7 (Medio), > 0.7 (Alto). 

- **Carga Animal Sugerida (UGG/ha):** < 0.5 (Baja), 0.5 - 1.5 (Media), > 1.5 (Alta). 

- **Índice THI (Calor):** < 72 (Confort), 72 - 78 (Alerta), > 78 ( **Estrés calórico** ). 

- **Semáforo Ganadero: Verde** (Condición favorable), **Amarillo** 

   - (Precaución/Monitorear), **Rojo** ( **Condición crítica** por bajo NDVI, alto déficit o estrés térmico). 

**Nota importante:** Los indicadores de biomasa y carga animal son orientativos y deben calibrarse con mediciones de campo reales y registros locales. 

Si el repo siguiente es instalado en https://code.earthengine.google.com/, en la pestaña "Inspector" puede cliclear sobre su finca cualquier punto y obtener la información igual qa los datos de la pestaña de "Promedios" de la localización.

Acceso al repositorio de GEE:  https://code.earthengine.google.com/?accept_repo=users/oasotob/Proyecto_Ganadero

<img width="1364" height="529" alt="image" src="https://github.com/user-attachments/assets/017077e9-94c4-4153-8b2c-c9da9b08beeb" />

