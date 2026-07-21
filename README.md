# Neverita - JUN2026

Visor de fotos y vídeos en forma de carrusel, con las métricas de Meta Ads de cada creatividad.

## Cómo añadir contenido nuevo

1. Copia tu foto o vídeo dentro de la carpeta `media/`.
2. Abre `index.html`, busca la lista `CONTENIDO` (cerca de la línea 220) y añade un bloque, por ejemplo:
   ```js
   {
     type: "image", src: "media/mi-foto.jpg", nota: "Campaña verano",
     metricas: { impresiones: "12.400", alcance: "9.800", frecuencia: "1,27", clics: "310", ctr: "2,5%", gasto: "145,00 €", resultados: "42", costeResultado: "3,45 €", valorResultados: "890,00 €" }
   },
   ```
   Usa `"video"` en vez de `"image"` si es un vídeo (mp4).
3. Guarda el archivo. Ya está.

Puedes borrar `sample1.svg`, `sample2.svg` y `sample3.mp4` (son solo ejemplos) y quitar sus líneas de `CONTENIDO`.

## De dónde saco las métricas (exportar desde Meta Ads Manager)

1. Entra en **Meta Ads Manager** → selecciona la campaña `Neverita - JUN2026`.
2. Cambia el desglose al nivel **Anuncio** (así ves cada creatividad por separado, no la campaña agregada).
3. En "Columnas", elige **Personalizar columnas** y añade: Impresiones, Alcance, Frecuencia, Clics en el enlace, CTR, Importe gastado, Resultados, Costo por resultados, Valor de conversión (o "Valor de resultados").
4. Botón **Exportar** → **Exportar tabla como .csv**.
5. Abre el CSV con Excel o Google Sheets. Cada fila es un anuncio (una creatividad).
6. Copia los valores de cada fila y pégalos en su bloque `metricas` correspondiente dentro de `index.html`, tal como aparecen (con símbolo de € o %, no hace falta limpiarlos).

No hay forma de conectar esto en directo con Meta (GitHub Pages es una web estática, sin servidor), así que hay que repetir este export/pegado cada vez que quieras actualizar los números.

## Cómo subirlo a GitHub (primera vez)

1. Crea un repositorio nuevo en GitHub (botón **+ → New repository**). Ponle un nombre, ej. `creatividades`.
2. En tu ordenador, abre una terminal dentro de esta carpeta y ejecuta:
   ```bash
   git init
   git add .
   git commit -m "Primera versión"
   git branch -M main
   git remote add origin https://github.com/TU-USUARIO/creatividades.git
   git push -u origin main
   ```
3. En GitHub, entra al repositorio → **Settings → Pages**.
4. En "Branch", elige `main` y la carpeta `/ (root)` → **Save**.
5. Espera 1-2 minutos. Tu web quedará publicada en:
   `https://TU-USUARIO.github.io/creatividades/`

## Cómo actualizarla después

Cada vez que añadas o cambies contenido:
```bash
git add .
git commit -m "Nuevas creatividades"
git push
```
La web se actualiza sola en un par de minutos.
