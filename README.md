# Análisis de clientes ConnectaTel

## Objetivo
Analizar el comportamiento de los clientes de ConnectaTel (telecomunicaciones en Latinoamérica) con datos hasta 2024, para construir un perfil estadístico, detectar usos atípicos, segmentar clientes y proponer mejoras en los planes.

## Datasets
| Archivo | Contenido | Filas |
|---|---|---|
| `plans.csv` | Planes actuales (Básico y Premium): precio, mensajes, GB y minutos incluidos, costos por extra | 2 |
| `users_latam.csv` | Clientes: edad, ciudad, fecha de registro, plan, fecha de baja (churn) | 4,000 |
| `usage.csv` | Uso real: llamadas (duración) y mensajes (longitud) de enero a junio de 2024 | 40,000 |

## Etapas del análisis
1. **Carga y exploración** de los tres datasets (`shape`, `info`).
2. **Calidad de datos**: nulos, sentinels (`-999` en `age`, `?` en `city`), valores sospechosos (120 min, 1490 caracteres) y fechas imposibles (40 registros de 2026).
3. **Limpieza**: mediana para la edad, nulos para ciudad y fechas imposibles, revisión de nulos estructurales en `duration`/`length` y corrección de 28 registros inconsistentes.
4. **Estadísticas por usuario**: mensajes, llamadas y minutos por cliente (`user_profile`).
5. **Distribuciones y outliers**: histogramas por plan, boxplots y límites por IQR.
6. **Segmentación**: `grupo_uso` (Bajo / Medio / Alto) y `grupo_edad` (Joven / Adulto / Adulto Mayor).
7. **Insight ejecutivo** con hallazgos y recomendaciones.

## Hallazgos principales
- Premium (35% de los clientes) consume prácticamente lo mismo que Básico; el 99.6% de los usuarios Premium usó en seis meses menos de lo que Básico incluye en un mes (mensajes y minutos).
- La edad no explica el nivel de uso, y el churn global (11.65%) no difiere de forma significativa por plan, uso o edad.
- Limitaciones: el uso cubre solo enero–junio de 2024 y no hay datos de GB consumidos.

## Cómo ejecutar el notebook
1. Abre `S7_ConnectaTel_Resuelto.ipynb` en [Google Colab](https://colab.research.google.com/) (File → Upload notebook).
2. Sube los tres CSV al entorno de Colab (panel de archivos, carpeta `/content`).
3. En la celda de carga, cambia la ruta `'/datasets/'` por `'/content/'` (o por la carpeta donde estén los archivos).
4. Ejecuta todo con **Runtime → Run all**.

## Requisitos
Python 3 con `pandas`, `numpy`, `seaborn`, `matplotlib` y `scipy` (todas vienen preinstaladas en Colab).
