# SAI - Sistema de Alerta de Incendios

Proyecto web para Visual Studio Code + GitHub Pages.

## Qué hace

- Muestra un mapa Leaflet.
- Consulta NASA FIRMS mediante su API de área.
- Usa datos VIIRS en tiempo casi real.
- Clasifica las detecciones por FRP (Fire Radiative Power) y por concentración de puntos cercanos.
- Detecciones bajas: punto discreto.
- Detecciones moderadas/altas: fuego animado.
- Detecciones críticas: fuego grande + humo animado.
- Al hacer clic en un incendio muestra FRP, coordenadas, fecha, hora, confianza y satélite.
- La MAP_KEY se guarda en `localStorage` del navegador y no se escribe en el repositorio.

## 1. Obtener MAP_KEY

Solicítala gratis en:

https://firms.modaps.eosdis.nasa.gov/api/map_key/

Después de recibirla por correo, abre la página del proyecto y pégala en el campo MAP_KEY.

## 2. Probar en VS Code

No abras `index.html` directamente con `file://` si el navegador bloquea alguna solicitud.

La forma recomendada es usar una extensión como **Live Server** en VS Code:

1. Instala "Live Server".
2. Abre esta carpeta en VS Code.
3. Clic derecho en `index.html`.
4. Selecciona "Open with Live Server".

## 3. Publicar en GitHub

Crea un repositorio público llamado:

`fire`

Tu URL será:

`https://darwincalderon.github.io/fire/`

Desde la terminal de VS Code:

```bash
git init
git add .
git commit -m "SAI - Sistema de Alerta de Incendios"
git branch -M main
git remote add origin https://github.com/darwincalderon/fire.git
git push -u origin main
```

Después en GitHub:

Settings → Pages → Build and deployment → Source: GitHub Actions

El repositorio incluye un workflow en `.github/workflows/pages.yml` para publicar el sitio.

## 4. Sobre los incendios "grandes"

FIRMS proporciona FRP (Fire Radiative Power), que se usa aquí como indicador de intensidad radiativa. Los umbrales del proyecto son una clasificación visual heurística; no significan que NASA FIRMS esté diciendo directamente el tamaño físico del incendio.

Los umbrales iniciales son:

- < 20 MW: baja
- 20–49.99 MW: moderada
- 50–99.99 MW: alta
- >= 100 MW: crítica

Además, si hay suficientes detecciones próximas entre sí, la zona puede subir a crítica para que se vea como una concentración de actividad.

## 5. Nota sobre la MAP_KEY

GitHub Pages es alojamiento estático. Cualquier clave que se incluya directamente en JavaScript sería visible para los visitantes.

Por eso este proyecto NO contiene tu MAP_KEY. La clave se introduce en el navegador y se guarda únicamente en `localStorage`.

Para un proyecto académico esto es práctico, pero para un sistema de producción convendría colocar la consulta FIRMS detrás de un backend/proxy y mantener la clave fuera del navegador.

## Fuentes

NASA FIRMS API:
https://firms.modaps.eosdis.nasa.gov/api/

NASA FIRMS Area API:
https://firms.modaps.eosdis.nasa.gov/api/area/

GitHub Pages:
https://docs.github.com/en/pages
