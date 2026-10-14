# LifeOS 2028 — CRM personal

Aplicación web en español para organizar calendario, ventas, tutorías de contabilidad, investigación, KPI, hábitos y cierre diario.

## Para usarla desde mañana

**Esta versión funciona sin configurar una base de datos:** guarda actividades, hábitos, KPI, el formulario del cierre y los cierres guardados en el almacenamiento local del navegador (`localStorage`). Usa siempre el mismo navegador y dispositivo. Si borras los datos del navegador, cambias de dispositivo o usas otro navegador, esos datos locales no aparecerán allí. En Configuración puedes descargar una copia de seguridad JSON.

La versión local no equivale todavía a un CRM en la nube multi-dispositivo. Para sincronización y acceso desde varios dispositivos, configura Supabase siguiendo el apartado correspondiente.

## Publicar con GitHub + Netlify (paso a paso)

Necesitas una cuenta gratuita en [GitHub](https://github.com/) y una en [Netlify](https://www.netlify.com/).

### A. Crear el repositorio en GitHub
1. Descarga y descomprime el ZIP del proyecto en tu computadora. Debes ver `package.json`, `index.html`, `src/` y `supabase/`.
2. Entra en GitHub y pulsa **+ → New repository**.
3. Nombre sugerido: `lifeos-2028-crm`.
4. Selecciona **Private** para que el código no sea público. Pulsa **Create repository**.
5. Para subir los archivos, la opción más simple es instalar **GitHub Desktop** desde [desktop.github.com](https://desktop.github.com/), iniciar sesión, y elegir **File → Add local repository** si ya has inicializado Git; si no, en GitHub Desktop elige **File → New repository**, ubica la carpeta del proyecto, y crea el repositorio local.
6. En GitHub Desktop, revisa los archivos, escribe `Primera versión funcional de LifeOS 2028` en Summary y pulsa **Commit to main**.
7. Pulsa **Publish repository**. Selecciona el repositorio `lifeos-2028-crm` y mantén activado **Keep this code private**. Pulsa **Publish repository**.

> Alternativa sin GitHub Desktop: dentro del repositorio nuevo, usa **Add file → Upload files** y arrastra los archivos y carpetas del proyecto al navegador. Si GitHub no acepta carpetas anidadas en tu navegador, usa GitHub Desktop.

### B. Publicar la web en Netlify
1. Entra en [Netlify](https://app.netlify.com/) e inicia sesión.
2. Pulsa **Add new site → Import an existing project**.
3. Elige **GitHub** y autoriza a Netlify a acceder al repositorio `lifeos-2028-crm`.
4. Configura estos valores:
   - **Branch to deploy:** `main`
   - **Build command:** `npm run build`
   - **Publish directory:** `dist`
5. Pulsa **Deploy** / **Deploy site**.
6. Espera a que el despliegue termine. Netlify te dará una dirección parecida a `https://nombre-aleatorio.netlify.app`. Abre ese enlace en tu computadora y teléfono para probarlo.
7. Guarda el enlace en favoritos. Cada vez que publiques cambios nuevos en la rama `main` de GitHub, Netlify volverá a construir y publicar la web automáticamente.

### C. Prueba antes de usarla
1. Abre la dirección de Netlify.
2. En **Calendario**, crea una actividad de prueba para mañana con hora, área y prioridad.
3. Ve a **Trabajo CRM** y prueba las opciones desplegables de ventas, tutorías, investigación, pendientes y plan de mañana.
4. Pulsa **Guardar cierre del día**.
5. Recarga la página. Las actividades y el cierre deben seguir visibles en ese mismo navegador.
6. En **Configuración**, descarga una copia de seguridad y guárdala en un lugar seguro.
7. Borra las actividades de prueba y registra los datos reales.

## Qué está activo y qué no

### Funciones disponibles en el modo local
- Dashboard y navegación entre módulos.
- Actividades y calendario, con categorías, prioridades, estado y búsqueda.
- Formulario guiado del cierre laboral con opciones para ventas, tutorías, investigación y planificación.
- Guardado local de actividades, hábitos, KPI, revisión y cierres del día.
- Vista previa y copia del cierre completo.
- Descarga de copia de seguridad JSON.
- Exportación del calendario como archivo `.ics` para importarlo manualmente a Google Calendar.
- Generación de un prompt de estudio a partir del texto que pegues.

### Requiere configuración e implementación adicional
- Sincronización automática bidireccional con Google Calendar.
- Envío automático de recordatorios mediante Gmail.
- IA conectada a una API y carga/extracción automática de PDF/DOCX.
- Base de datos en la nube, sincronización entre dispositivos, colaboración y roles.

No introduzcas datos confidenciales de clientes, estudiantes o investigación en un sitio compartido o dispositivo público. El modo local almacena datos en el navegador y no ofrece sincronización ni copias de seguridad automáticas.

## Opcional: configurar Supabase
1. Crea un proyecto en [Supabase](https://supabase.com/).
2. En SQL Editor ejecuta el contenido de `supabase/schema.sql`.
3. Copia la URL del proyecto y la clave pública `anon`/publishable a un archivo `.env` local usando los nombres `VITE_SUPABASE_URL` y `VITE_SUPABASE_ANON_KEY`.
4. En Netlify, abre **Site configuration → Environment variables** y añade las mismas dos variables. Luego vuelve a desplegar.
5. Configura URL de autenticación y proveedor Google solo si realmente vas a activar inicio de sesión.

Nunca coloques una clave `service_role`, contraseña, client secret ni clave privada en el frontend o en variables que empiecen por `VITE_`.
