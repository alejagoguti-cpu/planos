# Planos hídricos · Kennedy

21 planos temáticos de calidad y cantidad de agua (incluido uno de residuos plásticos) para los humedales **La Vaca**, **El Burro** y **Techo** (localidad de Kennedy, Bogotá), dentro del perímetro `data/perimetro_kennedy_polygon2.kml`. Cada plano tiene su propia rampa de color y se descarga como PNG en 8K: completo con hoja y convenciones (7680 × 5120 px) o «solo plano», sin nada más y con fondo transparente fuera del perímetro (7680 × 7680 px); también en ZIP con los 21 o todos juntos en un ZIP.

Abre `index.html` en el navegador (o publícalo con GitHub Pages: *Settings → Pages → Deploy from branch → main*).

## Datos

| Archivo | Contenido |
|---|---|
| `data/muestreo_real.csv` | Valores por punto de muestreo con su fuente (`fuente`, `referencia`). Celda vacía = la fuente no reporta esa variable. |
| `data/humedales.geojson` | Límites de los humedales, OpenStreetMap (© colaboradores de OpenStreetMap, ODbL). |
| `data/perimetro_kennedy_polygon2.kml` | Perímetro de estudio. |
| `data.js` | Los tres anteriores empaquetados para que la página funcione sin servidor. |

**Copernicus Sentinel-2:** la página calcula en vivo la mediana por banda (B2, B3, B4, B5, B6, B8, B11, B12) de escenas Sentinel-2 L2A (Earth Search / AWS, máscara de nubes SCL, 10 m) y los 21 planos pueden mostrar un índice espectral propio (selector «Fuente», o «Fuente en los 21 planos»). El MNDWI del plano 16 mide agua; los demás (FDI, NDCI, NDTI, Stumpf, SI, NDBI, AWEI, BSI, NDVI, SAVI, NDMI, MSI, GNDVI y relaciones de bandas) son indicadores relativos sin calibrar, no mediciones de la variable. Contiene datos Copernicus Sentinel modificados.

El periodo de muestreo (desde/hasta) filtra los datos de campo por fecha, como el parámetro datetime del notebook; el periodo de Sentinel-2 se elige aparte. No se necesita backend ni claves de API: todo usa servicios públicos (Earth Search, AWS S3, Esri/OSM).

También puedes cargar tu propio CSV (mismas columnas) o cambiar el perímetro (KML/GeoJSON) desde la página.

## Planos

1 pH · 2 Eutrofización (DBO5+DQO+N+P) · 3 Oxígeno disuelto · 4 Fósforo total · 5 NTK / NH₄ · 6 DQO · 7 DBO5 · 8 Relación DBO/DQO · 9 Turbiedad · 10 SST · 11 Conductividad · 12 Grasas y aceites · 13 Coliformes fecales · 14 Coliformes totales · 15 Profundidad de lámina · 16 Área inundada · 17 Nivel freático · 18 Conexiones erradas · 19 Caudal de entrada · 20 Carga contaminante (concentración × caudal) · 21 Residuos plásticos y sólidos

**Plano 21, residuos plásticos.** Con Sentinel-2 usa el *Floating Debris Index* (Biermann et al. 2020, *Sci. Rep.* 10:5364): FDI = B8 − [B6 + (B11 − B6) × (832,8 − 664,6)/(1613,7 − 664,6) × 10], solo dentro de los humedales. Resalta acumulaciones flotantes densas (≥30 % del píxel); el buchón y la vegetación acuática también lo elevan, así que es indicativo, no una concentración de plástico. En campo solo hay un dato real: 732 t de residuos sólidos extraídos por la EAAB del humedal La Vaca desde 2020 (Bogotá.gov.co, 20-mar-2025). Ninguna fuente separa el plástico ni reporta microplásticos en La Vaca, El Burro o Techo; ver `data/FUENTES.md`.

Métodos: superficies IDW (o Thiessen) sobre todo el perímetro, en clases por cuantiles con isolíneas, sin difuminado; índices Sentinel-2 píxel a píxel a 10 m. Marco con coordenadas geográficas (grados, minutos y segundos), norte y escala gráfica. Textura: brillo real de Sentinel-2 a 10 m como sombreado (no altera valores). Todas las convenciones se pueden prender o apagar.

## NDVI

`ndvi.html`: serie de NDVI Sentinel-2 con máscara SCL, máximo semanal, interpolación y filtro Savitzky-Golay (misma lógica del notebook de PySTAC).
