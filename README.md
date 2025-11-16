# HenryBootcamp-DS-PoyectoM1-InsightReach

📊 InsightReach – Proyecto Integrador (PI)
Módulo 1 – Carrera Data Science
Análisis de Datos, Limpieza, Enriquecimiento y Sistema de Recomendación
🧠 Introducción

InsightReach es una empresa de marketing digital especializada en campañas personalizadas para negocios locales. Con su expansión y crecimiento, surge la necesidad de optimizar la segmentación y mejorar la efectividad de las campañas.

Este proyecto simula el trabajo de un analista de datos en un entorno real, donde se requiere explorar, limpiar y enriquecer datos provenientes de múltiples fuentes, para luego generar insights accionables y un sistema de recomendación personalizado.

🎯 Objetivos del Proyecto

Explorar y comprender estructuras de datos provenientes de distintas fuentes.

Aplicar técnicas de limpieza y transformación de datos.

Realizar análisis exploratorios usando pandas, numpy, matplotlib y seaborn.

Conectarse a una API externa (Yelp) para enriquecer el dataset.

Implementar técnicas de web scraping.

Interpretar los insights y generar recomendaciones.

Documentar el proceso de forma clara, coherente y reproducible.

🚀 Desarrollo del Proyecto
🧩 Avance 1 – Conexión, exploración y limpieza de datos (Clientes – Boston)
✔ Exploración inicial

Carga del dataset de clientes.

Identificación de ciudades y filtrado para trabajar únicamente con Boston.

Revisión de estructura: filas, columnas, tipos de datos y primeras observaciones.

✔ Limpieza y normalización

Se detectaron problemas en columnas clave:

Variable	Problema	Solución
edad	valores inválidos (-5, 300)	imputación por mediana según estrato + gasto + género
frecuencia_visita	valores 0 o negativos	eliminación (0) y corrección (-3) con medianas por grupos
promedio_gasto_comida	valores ≤ 0	corrección mediante imputación
preferencias_alimenticias	datos faltantes	imputación con modas por grupos y fallback
teléfono / correo	nulos	se dejan vacíos para evitar sobrecargar el dataset
✔ Segmentaciones y análisis inicial

Creación de rangos etarios: 18–30, 31–45, 46–60 y 60+.

Cruce de edad con preferencias alimenticias.

Distribución de género por edad.

Estrato socioeconómico por rango etario.

Top 3 de preferencias alimenticias por edad + género.

El resultado final se exportó como df_clientes_boston.csv.

🧩 Avance 2 – Conexión con la API de Yelp y enriquecimiento de datos
✔ Conexión a Yelp

Obtención de datos usando YELP_API_KEY.

Descarga de 200 registros de restaurantes de Boston (en lotes de 50).

Consolidación en un DataFrame único: df_rest.

✔ Limpieza y tratamiento

Eliminación de columnas irrelevantes (image_url, is_closed).

Normalización del campo price → conversión a escala numérica (1–4).

Imputación de precios faltantes mediante promedios por categoría.

Validación de calidad: rating y review_count sin valores anómalos.

Dataset final exportado como df_rest_boston.csv.

🧩 Avance 3 – Análisis integrado (Clientes + Restaurantes)
✔ Análisis clientes

Incluye visualizaciones y relaciones entre:

Género y estrato socioeconómico.

Gasto en comida según estrato.

Frecuencia de visita vs. gasto promedio.

Preferencias alimenticias totales y por subgrupos.

Análisis premium, consumo de alcohol, ingresos y edad.

✔ Análisis restaurantes

Distribución de precios normalizados.

Ranking Top 10 por puntaje ponderado (rating + review_count).

Análisis de categorías (Top 15).

Procesamiento de servicios (delivery, pickup, reserva) → variables binarias.

Mapa de calor relacionando servicios, calidad y precio.

🍽️ Sistema de Recomendación de Restaurantes

Para cada cliente se calculan 3 componentes:

🔹 1. Compatibilidad económica (30%)

Función: puede_pagar()
Evalúa si un estrato socioeconómico puede afrontar un nivel de precio.

🔹 2. Compatibilidad alimentaria (50%)

Función: le_gusta_comida()
Cruza preferencias del cliente con categorías del restaurante.

🔹 3. Calidad del restaurante (20%)

Función: calcular_calidad()
Combina:

Rating (30%)

Popularidad según review_count (70%)

🔹 Función principal

recomendar_restaurantes(cliente_id, top_n=5) devuelve un ranking ordenado por score total.

El modelo fue probado y validado con múltiples clientes, demostrando consistencia en los resultados.

✅ Resultados Principales

Integración exitosa de datos heterogéneos (clientes + Yelp).

Limpieza profunda y normalización de variables críticas.

Exploración detallada de comportamientos y patrones de consumo.

Sistema de recomendación funcional basado en criterios económicos, alimentarios y de calidad.

Documentación reproducible y escalable para otras ciudades.

🔮 Futuras Líneas de Análisis
🔹 Ampliación de datos

Incorporar nuevas ciudades.

Añadir clima, eventos y tendencias gastronómicas.

🔹 Mejora del modelo de recomendación

Ajustar ponderaciones mediante métricas reales o A/B testing.

Implementar machine learning (clustering, filtrado colaborativo).

Procesamiento de menús con NLP.

🔹 Dashboard & visualización

Dashboard interactivo con filtros por cliente, estrato y precio.

Integración de mapas con ubicaciones y recomendaciones.

🔹 Automatización

Conexión continua con la API de Yelp.

Pipelines de limpieza y actualización periódica.

🗂 Archivos generados

df_clientes_boston.csv

df_rest_boston.csv

Scripts de conexión, limpieza, análisis y recomendación.
