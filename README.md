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
- **Zoom con Ctrl + rueda** (Cmd en Mac), con amortiguación propia (dolly inercial) y paso
  proporcional del 8.5 % por muesca. La rueda sola **no** hace zoom: baja la página con
  normalidad, para que el visor no secuestre el scroll mientras se recorre la propuesta.
  También hay doble clic para encuadrar una pieza concreta y teclas `+` / `-` / `0`.
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
- Diseño responsive, **superficie clara** sobre el sistema de propuestas (fondo blanco,
  tinta verde-oscura, acento teal `#0f766e`, tipografías IBM Plex Sans y Mono).
  El visor 3D va sobre fondo blanco con el canvas transparente.
- **Hero inmersivo**: el visor 3D ocupa la pantalla completa y el titular editorial se
  superpone a la izquierda. El equipo arranca armado y el scroll lo va despiezando hasta
  mostrar todo el hardware por separado; al subir se rearma solo. El botón
  «Vista explosionada» sigue disponible como control manual.
- **Estructura editorial numerada** (001 equipo · 002 asignación · 003 instalación ·
  004 inversión), con titular display de hasta 84 px y aire vertical amplio.
- **Presupuesto en panel de cristal** (`backdrop-filter`) anclado abajo a la derecha,
  con cifras tabulares; en tableta y móvil pasa a tarjeta propia para no tapar el modelo.
- **Visor 3D responsive**: la cámara mide la silueta real de la escena proyectada sobre
  sus propios ejes y calcula la distancia de encuadre para cada tamaño de pantalla, con
  reencuadre automático al girar el móvil (`ResizeObserver`). Verificado de 375 px a 1440 px:
  las 11 piezas quedan dentro del cuadro y clicables en todos los tamaños.
- **Layout sobre retícula de 8px** (patrón de sistema de diseño financiero): contenedor de
  1200 px con gutter fluido, tarjetas de 24-32 px de padding, cuatro puntos de quiebre
  (1440 / 1024 / 768 / 375), controles con área táctil mínima de 44x44 px y footer navy
  como superficie de cierre.
- Accesibilidad: canvas etiquetado para lectores de pantalla, botones de solo icono con
  `aria-label`, contraste verificado ≥ 4.5:1 y respeto de `prefers-reduced-motion`
  (sin giro automático ni despiece por scroll, mostrando el equipo ya despiezado).
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
