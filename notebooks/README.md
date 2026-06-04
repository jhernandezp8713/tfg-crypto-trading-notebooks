# Estructura de evidencia en notebooks

Esta carpeta agrupa la evidencia técnica del TFG por **pilares metodológicos**, en orden cronológico aproximado del pipeline.

## Mapa de carpetas

```text
notebooks/
├── 00_infraestructura/
├── 01_ingesta/
│   ├── ohlcv/
│   ├── microestructura/
│   ├── derivados/
│   ├── onchain/
│   ├── wikipedia/
│   ├── reddit/
│   ├── google_trends/
│   ├── guardian/
│   └── nytimes/
├── 02_features/
├── 03_dataset_supervisado/
├── 04_preexperimento/
├── 05_modelado_predictivo/
├── 06_paper_trading/
└── 07_explicabilidad/
```

## Pilares y notebooks

### `00_infraestructura` — plataforma y entorno

| Notebook | Propósito |
| --- | --- |
| `01_smoke_test_infraestructura.ipynb` | Salud mínima del stack (BD, Timescale, MLflow, volúmenes) desde JupyterLab. |
| `02_evidencia_infraestructura.ipynb` | Evidencia ampliada de infraestructura local-first y rutas del proyecto. |
| `03_smoke_api_externa.ipynb` | Smoke HTTPS opcional contra APIs externas (p. ej. ping público de Binance), opt-in. |

### `01_ingesta` — linaje multifuente

| Subcarpeta | Notebook | Fuente |
| --- | --- | --- |
| `ohlcv/` | `01_arquitectura_ingesta_datos_OHLCV.ipynb` | Diseño y arquitectura de ingesta OHLCV. |
| `ohlcv/` | `02_evidencia_ingesta_ohlcv.ipynb` | Evidencia de calidad y cobertura OHLCV. |
| `microestructura/` | `01_evidencia_ingesta_microestructura.ipynb` | Libro de órdenes, trades y métricas de microestructura. |
| `derivados/` | `01_evidencia_ingesta_derivados.ipynb` | Futuros, funding, open interest. |
| `onchain/` | `01_evidencia_ingesta_onchain.ipynb` | Métricas on-chain agregadas. |
| `wikipedia/` | `01_evidencia_ingesta_wikipedia.ipynb` | Pageviews de Wikipedia. |
| `reddit/` | `01_evidencia_ingesta_reddit.ipynb` | Sentimiento Reddit (PullPush / Arctic Shift + FinBERT). |
| `google_trends/` | `01_evidencia_ingesta_google_trends.ipynb` | Google Trends (buckets 4h). |
| `guardian/` | `01_evidencia_ingesta_guardian.ipynb` | Sentimiento Guardian (Content API + FinBERT). |
| `nytimes/` | `01_evidencia_ingesta_nytimes.ipynb` | Sentimiento NYTimes (Archive / Article Search + FinBERT). |

### `02_features` — ingeniería, targets y selección

| Notebook | Propósito |
| --- | --- |
| `01_eda_features_intermedias.ipynb` | EDA sobre features intermedias: distribuciones, missing, correlación, extremos. |
| `02_evaluacion_etiquetado_targets.ipynb` | Comparación metodológica de etiquetado (`fixed_horizon`, `triple_barrier`, `trend_scanning`). |
| `03_metodologia_seleccion_features.ipynb` | Protocolo de selección en dos capas (prefiltro estructural + selección intra-fold). |

### `03_dataset_supervisado` — materialización pre-modelo

| Notebook | Propósito |
| --- | --- |
| `01_evidencia_dataset_modelado.ipynb` | Dataset supervisado en `data/03_processed/` y gate de aceptación pre-modelado. |

### `04_preexperimento` — universo de entrada (FFD + screening)

| Notebook | Propósito |
| --- | --- |
| `01_evaluacion_fracdiff.ipynb` | Screening de diferenciación fraccionaria (FFD) por símbolo y variable. |
| `02_resultados_screening_columnas_por_fuente.ipynb` | Screening de columnas candidatas por fuente de datos. |
| `03_presentacion_screening_variables_y_ffd_por_fuente.ipynb` | Presentación consolidada del screening y política FFD por fuente. |

### `05_modelado_predictivo` — evidencia experimental confirmatoria

Notebooks de **solo lectura** sobre bundles persistidos bajo `reports/validation/experiments/<study_id>/`. No sustituyen al pipeline oficial de entrenamiento.

| Notebook | Propósito |
| --- | --- |
| `01_evidencia_shortlist_baseline.ipynb` | Evidencia final Exp1 (*baseline shortlist*). |
| `02_evidencia_robustez_fold_shortlist_baseline.ipynb` | Robustez fold-level y solape de etiquetas (Exp1). |
| `03_evidencia_shortlist_meta_labeling.ipynb` | Evidencia Exp1.5 (*meta-labeling shortlist*). |
| `04_evidencia_robustez_fold_shortlist_meta_labeling.ipynb` | Robustez fold-level del efecto meta (Exp1.5). |
| `05_resumen_greedy_contextual.ipynb` | Exp2: *greedy contextual* de inyección de fuentes. |
| `06_resumen_carril_riesgo_greedy_contextual.ipynb` | Carril 2.5 post-Exp2: EVT/CVaR y *position sizing*. |
| `07_resumen_greedy_contextual_meta_labeling.ipynb` | *Meta-labeling contextual greedy*: síntesis narrativa y visual. |
| `08_resumen_carril_riesgo_meta_labeling_contextual.ipynb` | Carril 2.5 sobre meta-labeling contextual. |

### `06_paper_trading` — validación operativa

| Notebook | Propósito |
| --- | --- |
| `01_tabla_promocion.ipynb` | Tabla de promoción unificada y manifiesto *frozen* para paper trading. |
| `02_comprobacion_sanidad_senales.ipynb` | Sanidad del motor paper vs. predicciones offline congeladas. |
| `03_postmortem_paper_trading.ipynb` | Post-mortem de la ventana live/paper. |
| `04_retrospectiva_post_freeze.ipynb` | Retrospectiva sobre datos posteriores al freeze metodológico (2026-02-28). |

### `07_explicabilidad` — SHAP post hoc

Evidencia SHAP **post hoc** de los cinco modelos promocionados. **No reentrena**: reutiliza el último fold de cada estudio promocionado.

| Notebook | Par / arquitectura |
| --- | --- |
| `01_shap_btcusdt.ipynb` | BTCUSDT — LSTM, `core_only`. |
| `02_shap_bnbusdt.ipynb` | BNBUSDT — *residual_hybrid staged*, `core_only`. |
| `03_shap_ethusdt.ipynb` | ETHUSDT — *residual_hybrid staged*, bloque `sentiment`. |
| `04_shap_solusdt.ipynb` | SOLUSDT — *residual_hybrid staged*, bloque `derivatives_futures`. |
| `05_shap_xrpusdt.ipynb` | XRPUSDT — carril *meta-labeling*, backbone LSTM. |

## Cadena metodológica (orden de lectura sugerido)

1. Infraestructura (`00_*`) -> ingesta por fuente (`01_*`).
2. Features y targets (`02_*`) -> dataset supervisado (`03_*`).
3. Preexperimento FFD/screening (`04_*`) -> modelado predictivo (`05_*`).
4. Promoción y validación operativa (`06_*`) -> explicabilidad SHAP (`07_*`).

Dentro de `05_modelado_predictivo/`, leer primero evidencia por experimento (`01_*`–`04_*`) y después los resúmenes de carril (`05_*`–`08_*`).

## Criterio de ejecución

- Los notebooks siguen criterio **Run All secuencial**: deben funcionar tras `Kernel > Restart Kernel and Run All`.
- La mayoría son **evidencia de solo lectura**: el entrenamiento completo pertenece al pipeline oficial, no a celdas ad hoc del notebook.
- Los notebooks de resultados deben declarar el `study_id` analizado y los manifiestos o bundles en los que se apoyan.
