# Control de Concentración — Semilíquidos (MFO Advisors)

Dashboard estático de una sola página (`index.html`), sin build, sin backend, sin base de
datos. Los números están embebidos como JSON dentro del propio archivo HTML.

Diseño con la identidad visual de mfo.cl: fondo oscuro (#1B2025), acento verde (#7BC143),
tipografía Oswald para títulos y Barlow para texto — los mismos colores que ya vienen en el
tema "MFO" del Excel.

---

## Publicar en GitHub Pages — paso a paso desde cero

**Empieza con un repositorio nuevo y vacío.** Si ya tenías uno con problemas, créalo de nuevo
con otro nombre simple (sin tildes ni caracteres raros), por ejemplo `dashboard-semiliquidos`.

### 1. Crear el repositorio
1. En GitHub, click en **"+" (arriba a la derecha) → New repository**.
2. Nombre: algo simple, ej. `dashboard-semiliquidos` (evita tildes/ñ en el nombre del repo).
3. Puede quedar **Private** — no importa para Pages, mientras tengas cuenta gratuita y
   sea un repo personal (no de organización). Si tienes plan gratuito de **organización**,
   ahí sí Pages requiere que el repo sea público.
4. **No marques** "Add a README" (para evitar conflictos). Click **Create repository**.

### 2. Subir el archivo
1. En la página del repo recién creado, vas a ver un botón **"uploading an existing file"**.
2. Arrastra **solo el `index.html`** de este mensaje (el README es opcional, puedes subirlo
   también, no afecta).
3. Abajo, click **Commit changes**.
4. Verifica en la pestaña **Code** que el archivo `index.html` quedó ahí, en la raíz
   (no dentro de ninguna carpeta).

### 3. Activar GitHub Pages
1. Ve a **Settings → Pages** (menú de la izquierda).
2. En **Source**, deja **"Deploy from a branch"**.
3. En **Branch**, selecciona **`main`** y la carpeta **`/ (root)`**.
4. Click **Save**.
5. **Espera 1–2 minutos** y refresca la página (F5). Debería aparecer un recuadro verde:
   > ✅ Your site is live at `https://tu-usuario.github.io/dashboard-semiliquidos/`

### 4. Abrir el link
- Ábrelo en una **ventana de incógnito** la primera vez, para evitar que el navegador
  muestre una versión cacheada de otra página.
- La URL sigue siempre este patrón — cámbiala según tu usuario y el nombre real del repo:
  ```
  https://TU-USUARIO.github.io/NOMBRE-DEL-REPO/
  ```

**No necesitas configurar "Custom domain"** — eso es solo si quisieras un dominio propio
tipo `dashboard.mfo.cl`. Déjalo vacío.

---

## Cómo actualizar los datos más adelante

Todo el contenido numérico vive en una sola línea del archivo:

```js
const DATA = { ... };
```

Cuando tengas una versión nueva del Excel, pásamela y te devuelvo el `index.html` con los
datos frescos ya inyectados — listo para volver a subir y reemplazar el archivo en el repo
(GitHub Pages se actualiza solo, no hay que tocar Settings de nuevo).

## Qué muestra cada sección

- **Resumen general**: Total en alternativos (ALTI), total en semilíquidos, y el % que
  representan los semilíquidos dentro de los alternativos.
- **Composición y desviación**: monto y % de cada asset class sobre el total semilíquido,
  y un comparador "objetivo vs. actual promedio" (PE 60% / PD 30% / RE 10%) — calculado
  solo entre los alias que efectivamente tienen exposición semilíquida.
- **Exposición por fondo**: para cada uno de los 6 fondos evergreen (REIF, TPF, GPA, BCRED,
  OCIC, KPEC) — exposición total, clientes con posición, cuántos superan el objetivo de
  concentración (3% del patrimonio), y quién tiene la mayor concentración individual.
