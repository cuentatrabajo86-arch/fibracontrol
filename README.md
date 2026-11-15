# FibraControl 2.0

App web móvil (PWA) para técnicos FTTH: clientes, instalaciones, inventario de equipos e informes. HTML + CSS + JavaScript, sin servidor ni servicios de pago.

## Tres cosas distintas
- **A. Código en GitHub:** estos archivos. Subirlos no sube ningún dato de clientes.
- **B. App publicada:** la misma app abierta desde una dirección web (GitHub Pages).
- **C. Datos:** clientes e instalaciones se guardan **solo en el navegador de cada teléfono** (IndexedDB). No hay sincronización entre teléfonos ni nube. Para pasar datos: *Datos → Descargar respaldo* y *Restaurar respaldo*.

## Estructura
```
index.html            App completa (estilos y código)
manifest.webmanifest  Datos de instalación PWA
sw.js                 Service worker (uso sin conexión)
icons/                icon-192.png, icon-512.png
.gitignore            Evita subir respaldos, CSV, fotos y secretos
README.md             Esta guía
```

## Funciones (parte 1 de 2.0)
Todo lo de 1.0 (clientes, importación por imagen/texto, instalaciones, búsqueda, informes CSV/imprimible, respaldo) más: inventario de equipos con ID único (EQ-0001), serial y MAC sin duplicados, estados y historial por equipo; las instalaciones con serial crean o actualizan el equipo; historial de instalaciones en la ficha del cliente; informes por día, semana, mes o todo.

**Pendiente (parte 2):** control de materiales, escáner OCR de documentos de identidad, gráficos interactivos, exportación del inventario. El OCR siempre necesitará Internet la primera vez.

## Subir a GitHub desde Android
1. Descarga el ZIP y extráelo con *Files de Google* (mantén pulsado → Extraer).
2. En Chrome abre github.com, crea una cuenta gratuita y activa ⋮ → *Sitio para computadora*.
3. **+ → New repository**: nombre `fibracontrol`, *Public*, **Create**.
4. **uploading an existing file**: elige `index.html`, `sw.js`, `manifest.webmanifest`, `README.md` y `.gitignore` (si el selector no muestra `.gitignore`, créalo con *Add file → Create new file* y pega su contenido). **Commit changes**.
5. Carpeta de iconos: *Add file → Create new file*, escribe `icons/.gitkeep` y confirma. Entra en `icons`, *Add file → Upload files* y sube los dos PNG.
6. El `.gitignore` **no protege** las subidas desde el navegador: no subas respaldos, CSV ni fotos.

## Publicar con GitHub Pages
*Settings → Pages → Deploy from a branch → `main` / `(root)` → Save.* En 1–3 minutos estará en `https://TU-USUARIO.github.io/fibracontrol/` (HTTPS incluido). Las rutas son relativas, así que funcionan en subdirectorio.

## Instalar en el teléfono
Abre esa dirección en Chrome → ⋮ → *Instalar aplicación* (o *Añadir a pantalla de inicio*).

## Actualizar
1. En GitHub abre `index.html` → ✏️ o *Add file → Upload files* con el nuevo archivo del mismo nombre.
2. Abre `sw.js`, cambia `fibracontrol-v2.0.0` por `v2.0.1` y confirma.
3. En el teléfono abre la app dos veces (la primera descarga, la segunda ya usa la nueva).

**Datos al actualizar:** se conservan mientras la dirección web no cambie. Si cambias el usuario o el nombre del repositorio, la dirección cambia y los datos locales no se verán: descarga un respaldo antes.

**Datos de 1.0:** en la versión anterior usa *Datos → Descargar respaldo*; en 2.0 usa *Restaurar respaldo*.

## Privacidad
No incluyas datos reales en el repositorio. Los datos de demostración son ficticios y se cargan desde *Datos → Cargar datos de demostración*. La app no envía información a servidores propios; el único acceso externo es la descarga del motor OCR y la fuente tipográfica.

## Verificación pendiente
Comprueba en tu teléfono, ya publicada: que se pueda instalar, que abra sin conexión tras la segunda visita, que los datos persistan al cerrar y que los respaldos se restauren.
