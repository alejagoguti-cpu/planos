# Planos hídricos · Kennedy

20 planos temáticos de calidad y cantidad de agua para los humedales **La Vaca**, **El Burro** y **Techo** (localidad de Kennedy, Bogotá), dentro del perímetro `data/perimetro_kennedy_polygon2.kml`. Cada plano tiene su propia rampa de color y se descarga como PNG en 8K (7680 × 5120 px) o menor o todos juntos en un ZIP.

Abre `index.html` en el navegador (o publícalo con GitHub Pages: *Settings → Pages → Deploy from branch → main*).

## Datos

| Archivo | Contenido |
|---|---|
| `data/muestreo_real.csv` | Valores por punto de muestreo con su fuente (`fuente`, `referencia`). Celda vacía = la fuente no reporta esa variable. |
| `data/humedales.geojson` | Límites de los humedales, OpenStreetMap (© colaboradores de OpenStreetMap, ODbL). |
| `data/perimetro_kennedy_polygon2.kml` | Perímetro de estudio. |
| `data.js` | Los tres anteriores empaquetados para que la página funcione sin servidor. |

**Copernicus Sentinel-2:** la página calcula en vivo una mediana de escenas Sentinel-2 L2A (Earth Search / AWS, máscara de nubes SCL, 10 m) y obtiene MNDWI (humedad y agua abierta), NDCI (clorofila, proxy de eutrofización) y NDTI (turbiedad/sedimentos, proxy). Se usan en los planos 2, 9, 10 y 16 con el selector «Fuente». Contiene datos Copernicus Sentinel modificados.

El periodo de muestreo (desde/hasta) filtra los datos de campo por fecha, como el parámetro datetime del notebook; el periodo de Sentinel-2 se elige aparte. No se necesita backend ni claves de API: todo usa servicios públicos (Earth Search, AWS S3, Esri/OSM).

También puedes cargar tu propio CSV (mismas columnas) o cambiar el perímetro (KML/GeoJSON) desde la página.

## Planos

1 pH · 2 Eutrofización (DBO5+DQO+N+P) · 3 Oxígeno disuelto · 4 Fósforo total · 5 NTK / NH₄ · 6 DQO · 7 DBO5 · 8 Relación DBO/DQO · 9 Turbiedad · 10 SST · 11 Conductividad · 12 Grasas y aceites · 13 Coliformes fecales · 14 Coliformes totales · 15 Profundidad de lámina · 16 Área inundada · 17 Nivel freático · 18 Conexiones erradas · 19 Caudal de entrada · 20 Carga contaminante (concentración × caudal)

Métodos: superficies IDW (o Thiessen) sobre todo el perímetro, en clases por cuantiles con isolíneas, sin difuminado; índices Sentinel-2 píxel a píxel a 10 m. Marco con coordenadas geográficas (grados, minutos y segundos), norte y escala gráfica.

## NDVI

`ndvi.html`: serie de NDVI Sentinel-2 con máscara SCL, máximo semanal, interpolación y filtro Savitzky-Golay (misma lógica del notebook de PySTAC).
