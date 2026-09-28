# Fuentes y cobertura de variables: muestreo_real.csv

Humedales: La Vaca Norte, La Vaca Sur, El Burro y Techo (localidad de Kennedy, Bogotá).
El archivo tiene 58 filas y todas caen dentro del polígono de estudio.

## 1. Fuentes usadas (id de la columna `fuente`)

| id | Título | Entidad / autores | Año | URL |
|---|---|---|---|---|
| PMA_VACA_2009 | Plan de Manejo Ambiental del Humedal de La Vaca (185 p.) | EAAB-ESP / Pontificia Universidad Javeriana (ajustes SDA) | ago. 2008, ajustes oct. 2009 (muestreos de 2006) | https://www.acueducto.com.co/wps/wcm/connect/EAB2/38b76aad-2e50-4e68-b556-ecf40b3689b0/PMA_VACA.pdf?MOD=AJPERES (es el mismo archivo que https://www.metrodebogota.gov.co/sites/default/files/5.2.2.4%20PMA%20VACA.pdf) |
| PMA_VACA_2023 | PMA Reserva Distrital de Humedal La Vaca, versión final 2023 (Cap. I Descripción, Cap. II Evaluación). Adoptado por la Res. SDA 02925 de 2023 | Secretaría Distrital de Ambiente (SDA) | 2023 (monitoreo del 28 y 29 de nov. de 2022) | https://oab.ambientebogota.gov.co/descargar/15004/ (zip). Ficha: https://oab.ambientebogota.gov.co/?post_type=dlm_download&p=15004 |
| UCMC_2019 | Diagnóstico bacteriológico de la calidad del agua en la zona norte del Humedal La Vaca, Bogotá D.C., en dos épocas climáticas (trabajo de grado) | Arévalo, Argoty y Copete, Universidad Colegio Mayor de Cundinamarca | 2019 (muestreos de mayo y sep. de 2018) | https://repositorio.universidadmayor.edu.co/server/api/core/bitstreams/9c572dae-e83b-415e-beff-783ba25be65d/content |
| PMA_BURRO_2008 | Plan de Manejo Ambiental del Humedal Burro | EAAB-ESP / Universidad Nacional (IDEA) | oct. 2008 (muestreo de jul. de 2006) | https://www.acueducto.com.co/wps/wcm/connect/EAB2/ba0c591d-8306-4662-8712-4a90c9f0b612/PMA_Burro.pdf?MOD=AJPERES |
| PMA_BURRO_2023 | PMA Reserva Distrital de Humedal El Burro, versión final 2023. Adoptado por la Res. SDA 02927 de 2023 | SDA | 2023 (monitoreo del 30 de nov. y 1 de dic. de 2022) | https://oab.ambientebogota.gov.co/descargar/15021/ (zip). Ficha: https://oab.ambientebogota.gov.co/?post_type=dlm_download&p=15021 |
| PMA_TECHO_2009 | Formulación del Plan de Manejo Ambiental del Humedal de Techo (Plan_Accion_Techo.pdf, 202 p.) | Pontificia Universidad Javeriana (IDEADE) / EAAB / SDA | mar. 2007, ajustes jul. 2009 (muestreo de 2006) | https://www.acueducto.com.co/wps/wcm/connect/EAB2/d449eaf9-00c9-4824-b795-147a16a2e028/Plan_Accion_Techo.pdf?MOD=AJPERES |
| PMA_TECHO_2023 | PMA Reserva Distrital de Humedal de Techo, versión final 2023. Es el PMA actualizado que adopta la Res. SDA 2924 de 2023 | SDA | 2023 | https://oab.ambientebogota.gov.co/descargar/15047/ (zip). Ficha: https://oab.ambientebogota.gov.co/?post_type=dlm_download&p=15047 |

### Fuentes revisadas que no aportaron filas
- **Artículo de la Revista Tecnura / Tecnogestión de la UD** (https://revistas.udistrital.edu.co/index.php/tecges/article/download/4330/6336): trata del **humedal Jaboque** (Engativá), no de los humedales de Kennedy. No se usó.
- **Datos Abiertos Bogotá (CKAN)**: el conjunto "Estación de Calidad del Agua. Bogotá D.C." (SDA) solo tiene ubicaciones de la Red de Calidad Hídrica, sin resultados de laboratorio. Dentro del polígono solo aparecen 3 estaciones del río Fucha (FU-VC, FU-ZFRANCA, FU-ALAMEDA) y ninguna está en los humedales. Ninguna búsqueda en CKAN arrojó datos de calidad de agua de humedales. Ese conjunto sirvió para comprobar la conversión de coordenadas: sus coordenadas planas y sus lat/lon coinciden con proj4 a menos de 1e-6°.
- **PMA de Techo 2023, Cap. I (Figuras 15 a 22)**: trae los resultados SDA/CAR de 2019-2021 de TEC-Entr, TEC-Pnor y TEC-Mpte (OD, DBO5, DQO, fósforo total, NTK, coliformes totales, temperatura y pH), pero **solo en gráficos de barras sin etiquetas numéricas**. Leer valores de las barras sería estimar, así que no se incluyeron. Las coordenadas de esos puntos sí están en la Tabla 21 del Cap. I (p. 99), en grados, minutos y segundos (TEC-Mpte 4°38'54.54"N 74°8'34.94"W, entre otros). Para conseguir los números habría que pedir el informe SDA (2021a) o el SDA (2022a) del PMAE, o el Anexo A3, que no se publicó.
- **Anexos A3 "Calidad_agua" de los PMA 2023**: no están en el portal del OAB. Los zip "4_Layers" solo traen archivos .lyr de simbología, sin datos.
- **Orarbo** (orarbo.gov.co): el certificado SSL falló y la página de Techo redirige a otro sitio. Los documentos que enlaza son los mismos de EAAB y SDA listados arriba.

## 2. Coordenadas
- Las coordenadas de los documentos están en el plano cartesiano **MAGNA-SIRGAS Ciudad de Bogotá (EPSG:6247)**: origen 4°40'49.75"N, 74°08'47.73"W, FE 92334.879, FN 109320.965, k = 1.000399787532524. Se pasaron a WGS84 con proj4.
- `coord_tipo=documento` se usa para las coordenadas numéricas del documento: La Vaca 2006 (Tabla 27 del PMA de 2009) y los puntos UCMC 2018 (Tabla 3, ya en grados decimales).
- `coord_tipo=aproximada` agrupa dos casos:
  (a) Puntos **digitalizados de los mapas de muestreo con grilla MAGNA Bogotá**: PMA 2023 Figura 40 (La Vaca) y Figura 44 (El Burro), y PMA Techo 2009 Figura 41. El error estimado es de unos 10 m. Hay dos comprobaciones independientes: UCMC P1 (4.62753, -74.15928) queda a unos 15 m de VAC-ArrBiof, y las estaciones de Techo 2006 quedan junto a TEC-Mpte 2019.
  (b) Puntos ubicados **por su descripción** sobre el polígono del humedal: El Burro 2006 (la Figura 82 no numera los 5 puntos, incertidumbre de 50 a 100 m), el alcantarillado de la Calle 42G Sur, las filas por sector y las entregas pluviales.
- Techo 2006: la Figura 41 muestra 6 puntos y la tabla tiene 4 estaciones. Se supone que las estaciones 1 a 4 corresponden a los puntos numerados 1 a 4 de la figura.

## 3. Convenciones de los valores
- Se conservan los valores censurados tal como vienen en el documento, como texto: `<0.28`, `<1`, `<0.900`, `>5700`.
- En los PMA de 2009 los coliformes se reportan en **UFC/100 ml** y en UCMC_2019 también en UFC/100 ml. En el PMA_BURRO_2008 y en los PMA de 2023 se reportan en NMP/100 mL. Los valores no se convirtieron. La unidad de cada fila está en `referencia`.
- `coliformes_fecales` de los PMA 2023 son los "coliformes termotolerantes". Los valores de *E. coli* no se pusieron en `coliformes_fecales`. Los de El Burro 2006 se anotaron en `referencia`, y los de 2022 están en las Tablas 23 y 24.
- `nh4`: la columna recoge el "Nitrógeno amoniacal" en mg/L (y NH3-N en 2022), y en El Burro 2006 el "Amonio".
- `caudal`: **ningún documento trae caudales de entrada medidos**. Las filas de caudal son caudales pico de diseño modelados para Tr = 3 años. Los valores de Tr = 10 y Tr = 25 están en `referencia`. Úselos solo como magnitud relativa entre entregas.
- Techo 2006: la Tabla 15 tiene invertidas las filas de coliformes (fecales mayores que totales, lo que es imposible). Se usó la asignación de la Tabla 16 del mismo documento.
- El Burro 2006: en el PDF las celdas de coliformes y E. coli se parten en dos líneas (por ejemplo "379000" / "0"). Se leyeron como el número completo, 3 790 000.

## 4. Cobertura por variable

| Variable | La Vaca Norte | La Vaca Sur | El Burro | Techo |
|---|---|---|---|---|
| ph | 2006 (2 pts), 2022 (3 pts) | 2006, 2022 | 2006 (5), 2022 (4) | 2006 (4) |
| od | 2006, 2022 | 2006 (+2 alcantarillado), 2022 | 2006, 2022 | 2006 |
| p_total | 2006, 2022 | 2006 (+alc.), 2022 | 2006, 2022 | 2006 |
| ntk | 2006, 2022 | 2006 (+alc.), 2022 | 2006, 2022 | 2006 |
| nh4 | 2006, 2022 | 2006, 2022 | 2006 (amonio), 2022 | 2006 |
| dqo | 2006, 2022 | 2006 (+alc.), 2022 | 2006, 2022 | 2006 (177, 106, 146, 197) |
| dbo5 | 2006, 2022 | 2006 (+alc.), 2022 | 2006, 2022 | 2006 (DBO/DQO 0.24, 0.26, 0.27, 0.17) |
| turbiedad | 2006, 2022 | 2006, 2022 | 2006, 2022 | 2006 (13, 11, 11, 12 UNT) |
| sst | 2006, 2022 | 2006 (+alc.), 2022 | 2006, 2022 | 2006 |
| conductividad | 2006, 2022 | 2006, 2022 | 2006, 2022 | 2006 |
| grasas_aceites | 2006, 2022 | 2006 (+alc.), 2022 | 2006 (todos 0), 2022 | 2006 |
| coliformes_fecales | 2006, 2022 | 2006 (+alc.), 2022 | 2022 (en 2006 solo E. coli) | 2006 |
| coliformes_totales | 2006, 2018 (10 pts × 2 épocas), 2022 | 2006 (+alc.), 2022 | 2006, 2022 | 2006 |
| profundidad | 1.5 m máx. (zona NW, 2006) | 0.5 m (canal) | **sin dato** | T1 0.6, T2 0.3, T3 0.3 m |
| area_inundada | 1.4 ha (espejo proyectado) | **sin dato** (no hay espejo) | 0.2 ha espejo (2008) y 9.62 ha inundable TR100 modelada (2023) | 2.81 ha (espejo del balance, 2009) |
| nivel_freatico | 0.5 m | **sin dato** | **sin dato** | **sin dato puntual** (el PMA 2023 solo da el rango regional de 0.4 a 2 m) |
| conexiones | 13 identificadas (11 corregidas), 2021 | **sin dato** | 49 identificadas (35 corregidas), 2023 | 343 identificadas (270 corregidas), 2023 |
| caudal | Tubo 1 3787.5 y Tubo 2 2745.3 L/s (modelados) | 2500.2 L/s (modelado) | **sin dato en L/s** (solo balances en mm/mes y un caudal máximo de 26 m³/s para Tr = 100, sin punto de entrada) | Sur 1254 y Oriente 1737.9 L/s (modelados) |

### Faltantes o de baja calidad
- **Caudal medido**: no se encontró en ninguna fuente. Todo lo que hay es modelado.
- **Nivel freático**: solo existe un valor puntual para La Vaca (0.5 m, PMA 2009). Los PMA 2023 describen piezómetros y miras (La Vaca: mira 1 con moda de 170 cm, mira 2 de 250 cm y mira 3 de 90 cm entre 2019 y 2022; El Burro: 8 miras), pero dicen que son poco confiables. Además, las lecturas de mira son cotas de regleta y no profundidad del agua ni nivel freático, por eso no se incluyeron.
- **Profundidad en El Burro**: el PMA de 2008 no reporta la lámina de agua. Los 2.3 m que menciona corresponden al espesor del botadero.
- **Área inundada de La Vaca en 2023**: el PMA da 2.73 ha para TR100 en todo el humedal sin separar norte y sur, así que no se asignó a ningún sector.
- **Conexiones por punto**: las fuentes solo dan totales por área de aporte o por sector. No hay conteos por punto de muestreo.
- **Techo 2019-2021**: los datos de la SDA solo están en gráficos (ver la sección 1).
