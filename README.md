# Notebooks de evidencia — TFG Crypto Trading Bot

Repositorio dedicado a la evidencia en Jupyter del Trabajo de Fin de Grado sobre un bot de trading cuantitativo en criptomonedas.

- **Contenido de este repo:** 37 notebooks organizados por pilares metodológicos (ingesta, features, modelado, paper trading, SHAP).
- **Uso previsto:** consulta de resultados y figuras para la memoria del TFG; no sustituye al entrenamiento ni al despliegue operativo.

## Mapa por pilares

| Pilar | Carpeta | Tema |
| --- | --- | --- |
| 0 | `notebooks/00_infraestructura/` | Smoke tests y evidencia de plataforma |
| 1 | `notebooks/01_ingesta/` | Ingesta multifuente (OHLCV, on-chain, sentimiento, etc.) |
| 2 | `notebooks/02_features/` | EDA, etiquetado y metodología de selección |
| 3 | `notebooks/03_dataset_supervisado/` | Dataset de modelado y aceptación pre-modelo |
| 4 | `notebooks/04_preexperimento/` | FFD y screening de variables por fuente |
| 5 | `notebooks/05_modelado_predictivo/` | Exp1, Exp1.5, Exp2 y carriles de riesgo |
| 6 | `notebooks/06_paper_trading/` | Promoción, sanidad, live/paper y retrospectiva post-freeze |
| 7 | `notebooks/07_explicabilidad/` | SHAP post hoc por par promocionado |

Detalle de cada notebook, convenciones de nombres y orden de lectura: **[`notebooks/README.md`](notebooks/README.md)**.

## Licencia y datos

Los notebooks pueden referenciar rutas o artefactos del repositorio principal. Las salidas visibles en las celdas están pensadas para lectura autónoma sin acceso a datos privados ni credenciales.
