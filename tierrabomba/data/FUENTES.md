# Fuentes y método: planos hídricos de la Isla de Tierra Bomba (Cartagena de Indias)

Archivos de datos: `muestreo_real.csv` (245 filas, 10 puntos de muestreo, datos de 1996 a 2025) y `fuentes.json` (un objeto `{id, corto, titulo, url}` por cada id que aparece en la columna `fuente`).

Todos los valores numéricos se copiaron de una tabla digital (xlsx) o del texto de un informe oficial. No hay valores estimados, interpolados ni leídos de gráficas. Si la fuente no trae el número, la celda queda vacía.

Recuadro de trabajo: lat 10.295–10.395, lon −75.610 a −75.525. Comprende la isla y sus aguas inmediatas. Se descartaron las estaciones REDCAM que caen fuera de ese recuadro:
- Al norte: Playas de Bocagrande C13003048 (10.4054) y Boya 41 C13003038 (10.4006).
- Al este, en la costa de Mamonal: Astillero Naval C13003033 (−75.5222), Roja F. Corelca C13003034 (−75.5186), B. Canal del Dique C13003031 (−75.5242) y Álcalis (−75.5078).
- Más lejos: Manzanillo del Mar, Marbella, Crespo, Las Quintas y Punta Canoa.

---

## 1. Fuentes

### 1.1 Fuentes usadas (aportan filas)

| id (columna `fuente`) | Título | Entidad / autores | Año | URL |
|---|---|---|---|---|
| INVEMAR_datos_icam_1996-2019 | `datos_icam` (xlsx, hoja `icam`). Microdatos REDCAM por estación y muestreo, con lat/lon, OD, pH, NO3, PO4, SST, DBO, HDD, CTE, CLA y metales | INVEMAR, Programa Calidad Ambiental Marina (hub de datos abiertos ICAM) | archivo guardado en 2019; datos de 1993 a 2019 (en el recuadro, de 1996 a 2019) | https://www.arcgis.com/sharing/rest/content/items/4a2f87c9367b42edab08dce471f7a5c2/data (hub: https://icam-invemar.opendata.arcgis.com/) |
| INVEMAR_ICAM_cuadros_2021 … _2025 | "Cuadros de salidas o resultados ICAM" de 2021, 2022, 2023, 2024 y 2025 (xlsx). Una hoja por variable con el valor medido por estación | INVEMAR, Operación Estadística ICAM | 2021–2026 (muestreos de 2021 a 2025) | 2021: …/items/52c931ae9a63466dac0a4e7b359da8c1/data · 2022: …/21f9dfcdcf75421db4a3328fe01c6894/data · 2023: …/3453b499f97c43c7b0c7dae3c5ef8b0b/data · 2024: …/2eaa4314340348a3a096e834c2297c4b/data · 2025: …/37eec98e5c534c68884812486a0d99d0/data (prefijo https://www.arcgis.com/sharing/rest/content/items/) |
| REDCAM_2022 | Informe Técnico REDCAM 2022: Diagnóstico y evaluación de la calidad de las aguas marinas y costeras del Caribe y Pacífico colombianos (capítulo Bolívar, microplásticos p. 126) | INVEMAR y CAR costeras (Serie de Publicaciones Periódicas No. 4) | 2023 | https://www.invemar.org.co/documents/37438/102725/Informe+REDCAM+2022.pdf/9ea74f54-64bb-cd70-4896-4faeddec18e6 |
| REDCAM_2023 | Informe Técnico REDCAM 2023 (Bolívar, microplásticos p. 97) | INVEMAR | 2024 | https://www.invemar.org.co/documents/37438/102725/Informe+REDCAM+2023.pdf/eb6ac529-3faf-b59e-2439-a10768dd0691 |
| REDCAM_2025 | Informe Técnico REDCAM 2025 (Bolívar: coliformes p. 109; basura marina y microplásticos pp. 114–115) | INVEMAR | 2026 | https://www.invemar.org.co/documents/37438/102725/Informe+t%C3%A9cnico+REDCAM+2025.pdf/8cc93f01-73af-10dd-5aff-05d5444e37b1 |

Fuentes de apoyo. No aportan valores, pero sí coordenadas y unidades:
- **Capa de estaciones REDCAM** `estacion_icam_2018`: código, nombre, etiqueta, lat/lon y tipo de agua. INVEMAR. https://services7.arcgis.com/GKny40YX8LUCGYz6/arcgis/rest/services/estacion_icam_2018/FeatureServer/0 (también la capa `icam_estaciones`).
- **Documento Metodológico del ICAM** (INVEMAR, código ME-CAM-1). Da las unidades: OD, SST, DBO y COT en mg/L; CTE en NMP/100 mL; NO3, PO4, HPDD y CLA en µg/L. https://www.arcgis.com/sharing/rest/content/items/4d3b0649671d420ab333a549e268094c/data
- **OpenStreetMap / Nominatim**: coordenadas de poblados y playas, solo para los puntos marcados "aproximada".

### 1.2 Fuentes revisadas que no aportaron filas

| Fuente | Por qué no aporta |
|---|---|
| Boletines estadísticos ICAM 2020–2026 (PDF, INVEMAR) | Las tablas por estación traen solo los **subíndices** del ICAM (0–100), no concentraciones. Por ejemplo, la Tabla 12 de 2024 (P. Tierra Bomba ICAM 74,5) y la Tabla 12 de 2026 (P. Tierra Bomba ICAM 85,9). Los subíndices no son valores medidos y no se usan. |
| Capa `icam` (FeatureServer) y "Indicador serie histórica ICAM" | Traen subíndices y categorías, no concentraciones. |
| `Calidad_Playas_Microbiologico.xlsx` (hub ICAM) | En el recuadro solo está Playas de Bocagrande (2006–2018), con columnas `TOTAL` (log) y `ANTI_LOG`. El archivo no dice qué indicador es (CTE, CTT o enterococos) ni si es media geométrica. Se descartó por ambiguo. |
| Informe Técnico REDCAM 2024 (INVEMAR, 2025). https://www.invemar.org.co/documents/37438/102725/Informe+REDCAM+2024.pdf/4a343207-ed7c-715a-6a9e-e9ea76b2e1d4 | El único valor en texto de una estación cercana es el de B. Canal del Dique (CTE 16.000 y CTT 41.000 NMP/100 mL, abril de 2024, pp. 71–72), y esa estación quedó fuera del recuadro. El resto de las estaciones de la isla solo aparece en gráficas. |
| Informe Técnico REDCAM 2021 (análisis histórico 2001–2021) | En Bolívar solo hay gráficas y rangos departamentales; no da valores por estación de la isla. |
| Informes REDCAM 2024 y 2025: pH, OD, nutrientes, SST y CTE de las estaciones antiguas (Roja Bocachica, Verde F. Caño Loro, Escollera, Tierra Bomba, Verde Polvorín…) | Esos valores solo aparecen en gráficas (Figuras 10-2, 10-5 y 11-5). Solo se tomaron los números escritos en el texto. |
| Gómez-Cuartas & López-Suárez (2020). Bol. Cient. CIOH 39(1):41-52. DOI 10.26640/22159045.2020.499 | Da coordenadas de 26 estaciones (Tabla 1); E8–E12, E16 y E18–E26 caen en el recuadro, en el norte de la bahía. Pero los coliformes totales, E. coli y Enterococcus por estación solo están en las Figuras 2–4. El texto da promedios y rangos mensuales de toda la bahía. Un valor puntual de E12 (1122 NMP/100 mL de Enterococcus, mayo de 2019) contradice el máximo del mismo párrafo (1112), así que no se usó. |
| Tous et al. (2007). Bol. Cient. CIOH 25:120-134 (10 estaciones, bahía) | Resultados en gráficas y contornos. No hay tabla por estación cerca de la isla. |
| Quintana & Santa (2013). Bol. Cient. CIOH 31:29-48 (NSFWQI, época seca) | Estaciones de la bahía (Emisario, Bosque, etc.); no hay tabla con estaciones de la isla. |
| Tuchkovenko & Rondón, Bol. Cient. CIOH (contaminación bacteriana en la bahía) | Sin estaciones en la isla. |
| Bol. Cient. CIOH 28 (2010) | Es sobre el Golfo de Morrosquillo (no aplica). |
| Romero-Murillo et al. (2023). Toxics 11:631 (revisión sobre la Bahía de Cartagena) | Revisión bibliográfica; no da datos primarios por punto de la isla. |
| Acosta-Coley et al. (2019). Mar. Pollut. Bull. 139 y 146 (microplásticos en Cartagena) | El resumen no da valores por playa de Tierra Bomba y el texto completo es de pago. |
| Artículo de la Revista Universidad EAFIT sobre Tierra Bomba y Bocachica | Según los resultados de búsqueda no trae valores por estación; no se pudo verificar. |
| Copias de informes REDCAM 2010–2019 en crautonoma.gov.co y PDFs de cecoldodigital.dimar.mil.co | El servidor respondió 502 desde esta sesión. Los informes 2001–2021 están en invemar.org.co; no se revisaron porque los microdatos de 1996–2019 ya los cubren. |
| Tesis doctoral de Garcés-Ordóñez (Univ. de Barcelona, 2025) | El enlace devolvió 404. |
| Sentencia T-012/2019, notas de El Universal sobre el acueducto y alcantarillado de Bocachica y Tierrabomba, y MinVivienda/SINAS | Solo traen cifras de inversión o de cobertura del servicio, sin mediciones georreferenciadas de agua dulce, pozos o vertimientos. El informe SINAS (sinas.minvivienda.gov.co) no se descargó. |
| El Universal (21-09-2024): limpieza que recogió 522 kg en Tierrabomba | Es una nota periodística sobre una jornada de limpieza, no un muestreo. No se usa. |

---

## 2. Coordenadas

- **`coord_tipo = documento`**. Hay dos casos:
  - Las filas 1996–2019 traen lat/lon en el propio archivo `datos_icam` (columnas `lat` y `lon`).
  - Las filas de informes y cuadros de estaciones con código REDCAM toman las coordenadas de la capa `estacion_icam_2018`.
  - Para "F. Emisario" (cuadros 2021–2025), la asociación con el código C13003037 se hizo **por etiqueta** (`label_st`) de la capa. Se indica en `ubicacion_desc`. "P. Bocagrande" quedó fuera del recuadro.
- **`coord_tipo = aproximada`**. Son tres puntos sin coordenadas en la fuente, ubicados con Nominatim (OSM):
  - **P. Tierra Bomba** (ICAM 2021–2025) → nodo del poblado Tierra Bomba (10.38022, −75.57532). INVEMAR la clasifica como agua estuarina. Es **otra estación** que "Tierra Bomba" C13003040 (agua marina, costa occidental).
    En el CSV final la coordenada se desplazó 80 m al punto más cercano de la línea de costa OSM (10.38090, −75.57509), porque la muestra es de agua de playa y el nodo del poblado cae en tierra.
  - **Playa Punta Arena** (microplásticos) → nodo del poblado Punta Arena (10.36518, −75.54960).
  - **Playa / P. Castillogrande** → objeto OSM "Playa Castillo Grande" (10.39316, −75.55952). La muestra de agua (P. Castillogrande) se desplazó 20 m a la línea de costa (10.39298, −75.55957); los microplásticos (arena) conservan la coordenada de la playa.
- **Centros poblados (OSM/Nominatim)**:

| Lugar | lat | lon |
|---|---|---|
| Tierra Bomba | 10.38022 | −75.57532 |
| Punta Arena | 10.36518 | −75.54960 |
| Caño del Oro | 10.34287 | −75.54526 |
| Bocachica | 10.32364 | −75.58107 |

- **Asignación de sector (`humedal`)**:

| Sector | Estaciones |
|---|---|
| Mar abierto | Tierra Bomba C13003040 |
| Bocachica | Roja Bocachica C13003049 |
| Caño del Oro | Verde F. Caño Loro C13003032 (nota: "Caño Loro" es Caño del Oro) |
| Punta Arena | Playa Punta Arena |
| Tierra Bomba (norte) | P. Tierra Bomba y Escollera submarina C13003036 (boca de Bocagrande) |
| Bahía interna | Verde Polvorín C13003035, F. Emisario C13003037, P. Castillogrande y Playa Castillo Grande (continente, frente a la punta norte de la isla) |

---

## 3. Convenciones de valores

- **Unidades**:
  - OD, SST, DBO5 y COT: mg/L.
  - `coliformes_fecales` = **coliformes termotolerantes (CTE), NMP/100 mL**.
  - `coliformes_totales` = CTT, NMP/100 mL.
  - pH: unidades de pH.
- **Variables que van en `referencia`** (no tienen columna propia):
  - Ortofosfatos (P-PO4), nitratos (N-NO3), HPDD y clorofila a, todos en µg/L, y COT en mg/L.
  - No se pusieron en `p_total`, `ntk` ni `grasas_aceites`.
  - En los microdatos 1996–2019 las columnas `no3` y `po4` están vacías para todas las estaciones del recuadro.
- **Valores censurados**:
  - "<LCM" se escribe con el límite que da la nota de cada hoja: PO4 <2, NO3 <2.1, HPDD <0.075 µg/L, DBO <4.23 mg/L, COT <0.5 mg/L, CLA <0.07 µg/L.
  - En las hojas CTE, la nota dice que el valor 1,8 es el LCM, así que se escribe "<1.8".
  - En el texto de REDCAM 2025, CTE "<LCM (1 NMP/100 mL)" se escribe "<1".
  - "NM" (no medido) y "NC" quedan vacíos.
- **Fecha**: AAAA-MM del muestreo, según el campo `ano`/`mes` o el mes de la hoja. Para los microplásticos de 2025 se escribe solo "2025", porque el texto fecha la basura marina (31-03-2025) pero no los microplásticos.
- **Duplicados**: la base 1996–2019 trae a veces 2 registros de la misma estación en el mismo mes (5 casos dentro del recuadro). Se conservaron todos sin promediar, con la marca "registro n de m" en `referencia`.
- **Otras notas**:
  - Todas las muestras REDCAM son superficiales (`profundidad` = "S" en la fuente), así que la columna `profundidad` queda vacía.
  - Algunos registros antiguos traen DBO = 0 o CLA = 0. Se copiaron tal cual; es probable que signifiquen "por debajo del límite de detección".
  - Los metales (Pb, Cd, Cr) de `datos_icam` no se incluyeron porque el archivo no documenta sus unidades.
- **Fila con dos fuentes**: la fila F. Emisario de 2025-04 lleva `fuente` = INVEMAR_ICAM_cuadros_2025, pero su valor de `coliformes_totales` (24.000 NMP/100 mL) viene del Informe REDCAM 2025, p. 109. Así lo dice su `referencia`.
- **Excluido por inconsistencia**: la hoja PO4 de 2025 tiene dos columnas "Valor" que no concuerdan entre sí (por ejemplo, P. Tierra Bomba 192 y 2,33). Se dejó fuera y se anotó en `referencia`.

---

## 4. Cobertura por variable y sector

Cada celda indica el número de filas con dato y el rango de años.

| variable | Tierra Bomba (norte) | Punta Arena | Caño del Oro | Bocachica | Bahía interna | Mar abierto |
|---|---|---|---|---|---|---|
| ph | 47 (1997–2025) | sin dato | 34 (2001–2019) | 32 (2001–2019) | 82 (1996–2025) | 35 (2001–2019) |
| od | 48 (1997–2025) | sin dato | 31 (2001–2019) | 29 (2001–2019) | 77 (1996–2025) | 33 (2001–2019) |
| p_total | sin dato | sin dato | sin dato | sin dato | sin dato | sin dato |
| ntk | sin dato | sin dato | sin dato | sin dato | sin dato | sin dato |
| nh4 | sin dato | sin dato | sin dato | sin dato | sin dato | sin dato |
| dqo | sin dato | sin dato | sin dato | sin dato | sin dato | sin dato |
| dbo5 | 32 (1997–2014) | sin dato | 23 (2001–2014) | 20 (2001–2014) | 60 (1996–2023) | 21 (2001–2014) |
| turbiedad | sin dato | sin dato | sin dato | sin dato | sin dato | sin dato |
| sst | 43 (1997–2025) | sin dato | 32 (2001–2019) | 31 (2001–2019) | 79 (1996–2025) | 34 (2001–2019) |
| conductividad | sin dato | sin dato | sin dato | sin dato | sin dato | sin dato |
| grasas_aceites | sin dato | sin dato | sin dato | sin dato | sin dato | sin dato |
| coliformes_fecales (CTE) | 32 (1997–2025) | sin dato | 30 (2001–2019) | 29 (2001–2019) | 60 (2001–2025) | 21 (2001–2025) |
| coliformes_totales | sin dato | sin dato | sin dato | sin dato | 2 (2025) | sin dato |
| profundidad | sin dato | sin dato | sin dato | sin dato | sin dato | sin dato |
| area_inundada | sin dato | sin dato | sin dato | sin dato | sin dato | sin dato |
| nivel_freatico | sin dato | sin dato | sin dato | sin dato | sin dato | sin dato |
| conexiones | sin dato | sin dato | sin dato | sin dato | sin dato | sin dato |
| caudal | sin dato | sin dato | sin dato | sin dato | sin dato | sin dato |
| residuos_solidos (microplásticos, ítems/m²) | sin dato | 3 (2022–2025) | sin dato | sin dato | 2 (2022–2025) | sin dato |

En `referencia` hay además estos datos:
- HPDD en 38 filas.
- Clorofila a en 66 filas.
- Ortofosfatos, nitratos y COT de 2021–2025 en P. Tierra Bomba, F. Emisario y P. Castillogrande.

**Faltantes explícitos**:
- No hay P total, NTK, amonio, DQO, turbiedad, conductividad ni salinidad por estación, ni grasas y aceites. REDCAM mide salinidad, amonio y nitritos, pero en los informes solo aparecen en gráficas o diagramas de caja.
- No hay datos de agua dulce de la isla (pozos, nivel freático, acueducto, caudales de vertimiento).
- No hay datos de ciénagas, lagunas ni manglares internos de la isla: no se encontró ninguna fuente con valores.
- Las estaciones antiguas (Bocachica, Caño del Oro, Escollera, Tierra Bomba C13003040) se siguen muestreando en 2024–2025, pero sus valores solo están en gráficas. La excepción es CTE <1 en Tierra Bomba en marzo de 2025.

---

## 5. Residuos plásticos y sólidos

- **Dato usado en `residuos_solidos`**: abundancia de **microplásticos en arena de playa, en ítems/m²**, según el texto de los Informes Técnicos REDCAM. Se eligió esta variable porque es la única con valor numérico para una playa de la isla (Punta Arena) en varios años:

| Playa | Fecha | Microplásticos (ítems/m²) | Fuente |
|---|---|---|---|
| Punta Arena | 2022-04 | 748 | REDCAM 2022, p. 126 |
| Punta Arena | 2023-04 | 128,8 | REDCAM 2023, p. 97 |
| Punta Arena | 2025 | 22,4 | REDCAM 2025, p. 115 |
| Castillogrande | 2022-04 | 246,4 | REDCAM 2022, p. 126 |
| Castillogrande | 2025 | 22,4 | REDCAM 2025, p. 115 |

  - El valor de 2024 de ambas playas solo aparece en gráficas.
  - Bocagrande tiene datos en esos informes, pero su valor individual no está en el texto.
- **Basura marina (macro)**:
  - Castillogrande, 31-03-2025: 0 ítems/m² ("no se registró presencia"). Está anotado en `referencia`.
  - Punta Arena, 2025: el valor solo está en la Figura 11-8. El texto da el rango departamental de 0 a 0,22 ítems/m², con el máximo en Crespo.
- **Composición** (porcentajes en `referencia`):
  - Punta Arena 2022: 52,3% gránulos (pellets, de origen primario).
  - Punta Arena 2023: 48,4% fragmentos.
  - Punta Arena 2025: 14,29% filamentos y 57,14% fragmentos.
- **Literatura académica**: Acosta-Coley et al. (2019) y Garcés-Ordóñez et al. (2020) estudian microplásticos en Cartagena, pero no se obtuvo ningún valor por playa de Tierra Bomba con texto verificable.

---

## Advertencias

1. **Dos estaciones distintas con "Tierra Bomba" en el nombre**:
   - "Tierra Bomba" C13003040 (2001–2019 y 2025): costa occidental, agua marina, coordenadas documentadas.
   - "P. Tierra Bomba" (2021–2025): playa, agua estuarina, coordenadas aproximadas.
2. **F. Emisario** (bahía interna, ~2,5 km al NE de Punta Arena) es la estación del recuadro con más carga microbiológica en 2025: CTT de 24.000 NMP/100 mL en abril y 61.000 en septiembre.
3. **Calidad de los registros de 1996–1997**: tienen valores de pH atípicos (9,9–10,0) y duplicados en el mismo mes. Se copiaron tal cual.
4. **Asociación por etiqueta**: las estaciones de los cuadros ICAM 2021–2025 se ligaron a las coordenadas del catálogo de 2018 por la etiqueta. Si INVEMAR reubicó alguna estación después de 2018, la coordenada podría no ser exacta.
5. **Ámbito del CSV**: solo contiene datos de agua marina y costera. No se halló ninguna medición pública y georreferenciada de agua dulce o subterránea dentro de la isla.

## 6. Geometría y capas del visor

- **Perímetro de estudio** (`perimetro_tierrabomba.kml`): rectángulo de lon −75,608 a −75,526 y lat 10,306 a 10,399. Abarca la isla, sus aguas costeras y las diez ubicaciones del CSV.
- **Tierra firme** (`tierra.geojson`): polígonos armados con las líneas `natural=coastline` de OpenStreetMap (consulta del 15 de noviembre de 2026), cerrados contra el perímetro. Son la isla (19,8 km²; relación OSM 11226348), la punta de Bocagrande–Castillogrande, la isla de Manzanillo y los islotes, entre ellos Draga y Abanico. Con la convención «Solo agua», las superficies interpoladas se muestran solo sobre el mar, la bahía y los cuerpos de agua de la isla.
- **Cuerpos de agua** (`cuerpos_agua.geojson`): los polígonos `natural=water`, `natural=wetland` y la «Reserva de Manglar» (*Rhizophora mangle*) de OSM que están dentro de la isla y miden al menos 0,1 ha. Se excluyeron dos charcas de 0,1 ha y una laguna en la cantera. OSM no les da nombre, así que se agruparon por cercanía con nombres descriptivos: Lagunas de Punta Arena (29,2 ha), Lagunas de Caño del Oro (9,0 ha), Ciénaga del centro (5,2 ha) y Manglar de Punta Icacos (44,9 ha). No son topónimos oficiales.
- **Presión económica** (`presion_economica.geojson`): elementos OSM dentro de la isla etiquetados como turismo (hoteles, hostales, fuertes de Bocachica), ocio (`beach_resort`), comercio, restaurantes o bares, canteras (`landuse=quarry`) e industria. Los nodos (puntos) se convirtieron en círculos de 15 m de radio. La clasificación alta/media/baja usa el NDBI de Sentinel-2 más la etiqueta semántica, igual que en Kennedy. Es un proxy, no una delimitación catastral. Muchos *beach clubs* de Punta Arena no están mapeados en OSM.
- **Poblados**: nodos OSM `place=*` de Tierra Bomba, Punta Arena, Caño del Oro y Bocachica.

