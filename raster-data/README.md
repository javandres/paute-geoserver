# Raster data (host) → GeoServer (container)

Esta carpeta está pensada para **copiar aquí tus archivos ráster** (por ejemplo GeoTIFF `.tif/.tiff`) y que GeoServer pueda leerlos desde Docker.

## Dónde se monta en el contenedor

Con `docker-compose*.yml`, esta carpeta del host:

- `./raster-data`

se monta dentro del contenedor GeoServer en:

- `/opt/raster-data`

## Cómo crear un “almacén de datos ráster” en GeoServer (Coverage Store)

1. Copia tu archivo, por ejemplo:
   - `raster-data/mi_raster.tif`
2. Entra a la UI de GeoServer:
   - `http://localhost:8600/geoserver/web/`
3. Ve a:
   - **Data → Stores → Add new Store → GeoTIFF**
4. En **URL** (o **File**), usa una ruta del contenedor, por ejemplo:
   - `file:/opt/raster-data/mi_raster.tif`
5. Guarda y luego publica la capa (Publish).

## Notas

- Esta carpeta **no se versiona** (para evitar subir rásters pesados al repo).
- Si cambias/añades archivos, normalmente **no necesitas reiniciar** el contenedor: GeoServer leerá el archivo al crear el store.

