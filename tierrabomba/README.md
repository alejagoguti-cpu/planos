# Planos hídricos · Tierra Bomba

22 planos temáticos de calidad y cantidad de agua (incluido uno de residuos plásticos y uno de presión económica) para la **isla de Tierra Bomba** (Cartagena de Indias, Bolívar) y sus aguas costeras: Bocachica, Caño del Oro, Punta Arena, el poblado de Tierra Bomba, la bahía interna y la costa abierta, más las lagunas, la ciénaga y el manglar de la isla. Es la misma herramienta de los [planos de Kennedy](../), adaptada a un medio marino-costero.

Se abre en `index.html` (en GitHub Pages: `https://alejagoguti-cpu.github.io/planos/tierrabomba/`). No necesita servidor propio ni claves.

## Datos

| Archivo | Contenido |
|---|---|
| `data/muestreo_real.csv` | 245 filas, 10 ubicaciones, 1996–2025. Red REDCAM / ICAM del INVEMAR: microdatos `datos_icam` (1996–2019), cuadros de salida ICAM 2021–2025 e informes técnicos REDCAM 2022, 2023 y 2025. Cada fila trae `fuente` y `referencia` (hoja, tabla o página). Celda vacía = la fuente no reporta esa variable. |
| `data/FUENTES.md` | Fuentes usadas y revisadas, coordenadas, convenciones, cobertura por variable y sector, advertencias y geometría. |
| `data/fuentes.json` | Lista de fuentes que muestra la página. |
| `data/perimetro_tierrabomba.kml` | Perímetro de estudio (isla y aguas costeras). |
| `data/tierra.geojson` | Tierra firme a partir de la línea de costa de OpenStreetMap (isla, Bocagrande–Castillogrande, Manzanillo e islotes). |
| `data/cuerpos_agua.geojson` | Lagunas, ciénaga y manglar de la isla (OpenStreetMap, ODbL). |
| `data/presion_economica.geojson` | Turismo, comercio, canteras e industria en la isla (OpenStreetMap). |
| `data.js` | Todo lo anterior empaquetado para que la página funcione sin servidor. |

**Qué tiene datos de campo:** pH, oxígeno disuelto, SST, DBO5 y coliformes termotolerantes (NMP/100 mL) en todos los sectores menos Punta Arena; coliformes totales solo en F. Emisario (2025); microplásticos en arena (ítems/m²) en Punta Arena y Castillogrande.

**Qué queda «sin dato»:** fósforo total, NTK, amonio, DQO, turbiedad, conductividad, grasas y aceites, profundidad, nivel freático, vertimientos y caudales. La REDCAM mide ortofosfatos, nitratos, hidrocarburos (HPDD), COT y clorofila a. Esos valores están en la columna `referencia` y no se mezclan con las variables de los planos. Ninguna fuente pública trae mediciones en las lagunas internas de la isla.

**Copernicus Sentinel-2:** igual que en Kennedy, la página calcula en vivo la mediana por banda de escenas Sentinel-2 L2A (Earth Search / AWS, máscara SCL, 10 m) y cada plano puede mostrar un índice espectral. En el plano 21, el FDI (Biermann et al. 2020) se calcula solo sobre agua: el mar fuera de tierra firme con MNDWI > 0 y las lagunas y el manglar. Sedimentos, sargazo y vegetación también lo elevan. Contiene datos Copernicus Sentinel modificados.

**Recorte al agua:** con la convención «Solo agua» (activa por defecto), las superficies IDW o Thiessen solo se pintan sobre el mar, la bahía y los cuerpos de agua de la isla, no sobre tierra firme.

## Planos

1 pH · 2 Eutrofización (DBO5+DQO+N+P) · 3 Oxígeno disuelto · 4 Fósforo total · 5 NTK / NH₄ · 6 DQO · 7 DBO5 · 8 Relación DBO/DQO · 9 Turbiedad · 10 SST · 11 Conductividad · 12 Grasas y aceites · 13 Coliformes fecales (termotolerantes) · 14 Coliformes totales · 15 Profundidad de lámina · 16 Área inundada · 17 Nivel freático · 18 Vertimientos · 19 Caudal de entrada · 20 Carga contaminante · 21 Residuos plásticos y sólidos · 22 Presión económica

`ndvi.html`: serie de NDVI Sentinel-2 con filtro Savitzky-Golay; trae la isla como zona de estudio predeterminada.
