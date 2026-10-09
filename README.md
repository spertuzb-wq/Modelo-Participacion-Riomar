# Modelo predictivo basado en agentes para la participación electoral — Localidad Riomar (Barranquilla)

Código y datos del trabajo de grado **"Diseño y evaluación de un modelo predictivo basado en agentes inteligentes para la estimación de la participación electoral en la Localidad Riomar de Barranquilla, con énfasis en cinco barrios focales"**.

- Autores: Ing. Sara Pertuz Bolaños, Ing. Maciel Rodelo Álvarez
- Tutor: Ing. Ronald Suárez · Cotutor: Ing. Javier Carpintero
- Maestría en Ingeniería y Estrategia — Institución Universitaria de Barranquilla (IUB), 2026

## Contenido

```
notebooks/
  prep_datos_riomar.ipynb            # 1. Preparación: resultados mesa a mesa, DIVIPOLE, CNPV 2018, MGN 2018
  modelo_participacion_riomar.ipynb  # 2. Modelo: OE1 (caracterización), OE2 (ML + ABM + SIG), OE3 (evaluación 2023)
data/
  00_Fuentes/                        # Fuentes oficiales (ver "Fuentes pesadas")
  01_Cartografia_GIS/                # Manzanas de estudio y coordenadas de puestos
  02_Datos_Sociodemograficos_DANE/   # Variables CNPV 2018 por manzana y composición de inscritos por puesto
  03_Datos_Electorales_Registraduria/# Mesas 2019-2023 y cruce de puestos
  04_Resultados/                     # Figuras, resultados_tesis.xlsx y resumen_resultados.json
requirements.txt
```

## Cómo reproducir

### Google Colab (recomendado)
1. Copie la carpeta `data/` a `MyDrive/TesisRiomar/` en Google Drive.
2. Descargue las fuentes pesadas (abajo) en `MyDrive/TesisRiomar/00_Fuentes/`.
3. Abra `prep_datos_riomar.ipynb` en Colab, monte Drive y ejecute todo. Regenera las carpetas 01–03.
4. Abra `modelo_participacion_riomar.ipynb` y ejecute todo. Regenera `04_Resultados/`.

### Local
```bash
pip install -r requirements.txt
```
Cambie la variable `BASE` al inicio de cada cuaderno por la ruta local de `data/`.

Si solo quiere reproducir el modelo, puede omitir el paso 3: las carpetas 01–03 ya vienen procesadas.

## Fuentes pesadas (no incluidas por tamaño)

| Archivo | Fuente |
|---|---|
| `08_Atlantico.zip` (≈123 MB) | DANE — Microdatos CNPV 2018, Atlántico. Catálogo ANDA: https://microdatos.dane.gov.co |
| `MGN_URB_MANZANA2018geopackage.zip` (≈291 MB) | DANE — Marco Geoestadístico Nacional 2018, manzanas urbanas: https://geoportal.dane.gov.co |

Las demás fuentes (resultados mesa a mesa 2019 y 2023 y DIVIPOLE, Registraduría Nacional del Estado Civil) están en `data/00_Fuentes/`.

## Reproducibilidad
- Semillas fijas: réplicas del modelo de agentes con semilla `42 + r` (r = 0…99).
- Entrenamiento con Alcaldía 2019; evaluación fuera de muestra con Alcaldía 2023.
- Probado con Python 3.12–3.13.

## Uso de los datos
Se usan solo datos públicos, agregados y anonimizados (Ley 1581 de 2012). El modelo no identifica ni perfila votantes individuales y no debe usarse para segmentación de campañas.

## Licencia
Código: MIT. Datos: según los términos de uso del DANE y la Registraduría.
