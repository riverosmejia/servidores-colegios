# Miniservidor de IA Escolar · Configurador 3D

Página web educativa de una sola página que explica, con una representación 3D interactiva,
el armado de un **Miniservidor de IA para colegios en Colombia**: qué componente tiene el equipo,
para qué sirve cada uno y cuánto cuesta.

**Sitio publicado:** https://riverosmejia.github.io/servidores-colegios/

## Qué incluye

- **Escena 3D despiezada** (Three.js + OrbitControls) con las 11 piezas del equipo: gabinete,
  2 GPU (RTX 4060 Ti 16GB), CPU Ryzen 9 7900X, refrigeración líquida AIO 360 mm, placa base,
  2 módulos DDR5, 2 discos NVMe M.2, fuente 1000 W, 3 ventiladores, UPS y switch de red.
- **Interactividad**: hover con resaltado y tooltip (nombre, modelo, costo y justificación),
  clic para abrir la ficha técnica en un panel lateral, botón de vista explosionada/ensamblada,
  rotación automática y contador de presupuesto con desglose resaltable.
- **Secciones de scroll**: asignación de recursos por GPU, requisitos de instalación física
  (ubicación, eléctrico, térmico y red) y footer con la inversión total.

## Presupuesto

| Concepto | Monto (COP) |
| :--- | ---: |
| Suma de los 11 componentes | $16.590.000 |
| Margen de imprevistos | $50.000 |
| **Total del proyecto** | **$16.640.000** |

> Nota de transparencia: la tabla de origen declara un total de $16.640.000, mientras que
> la suma de sus 11 ítems da $16.590.000. La página muestra el total oficial y declara
> explícitamente los $50.000 de diferencia como margen de imprevistos, sin alterar
> ninguna cifra real de los componentes.

## Detalles técnicos

- Un solo archivo `index.html` autocontenido (HTML + CSS + JS embebidos), sin build.
- Three.js r160 y OrbitControls por CDN (jsdelivr) mediante `importmap`.
- Vanilla JS, sin frameworks. `Raycaster` para hover y clic sobre las piezas.
- Diseño responsive, dark mode, tipografías Space Grotesk e Inter (Google Fonts).
- Animación de despiece por interpolación lineal simple (`lerp`), sin librerías externas.
- Código comentado en español.

## Publicación

Servido con GitHub Pages desde la rama `main` (raíz del repositorio). El archivo `.nojekyll`
evita el procesamiento con Jekyll.

## Uso local

Abrir `index.html` en el navegador. Para servirlo por HTTP:

```bash
python3 -m http.server 8000
```
