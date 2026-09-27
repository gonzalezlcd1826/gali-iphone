# GALI en iPhone sin Mac — instalación web (PWA)

Esta entrega **no es un IPA** y todavía no se ha probado en un iPhone físico. Conserva el código, las imágenes y la música del proyecto anterior. El flujo de GitHub Pages permite alojarlo con HTTPS y añadirlo a la pantalla de inicio del iPhone.

## Desde Windows

1. En GitHub, crea un repositorio nuevo **público** llamado `gali-iphone`. No subas contraseñas ni certificados. GitHub Pages gratis es más sencillo en un repositorio público.
2. Descomprime este ZIP. Abre la carpeta `GALI-mobile` y sube **su contenido** a la raíz del repositorio, incluyendo la carpeta oculta `.github` (no subas `node_modules`). Si GitHub no permite subir la carpeta oculta desde el navegador, usa GitHub Desktop para publicar toda la carpeta.
3. En el repositorio, entra en **Settings → Pages → Build and deployment → Source → GitHub Actions**.
4. Abre **Actions → GALI iPhone web install → Run workflow**. También se inicia automáticamente al subir a la rama `main`.
5. Espera a que termine en verde y abre la dirección que aparece en la sección de despliegue (habitualmente `https://TU_USUARIO.github.io/gali-iphone/`). Si falla, revisa los mensajes de Actions y compártelos para corregirlos.
6. En tu **iPhone**, abre esa dirección con **Safari**, toca **Compartir → Añadir a pantalla de inicio → Añadir**. Abre el icono GALI y pulsa **JUGAR CON MÚSICA**. La música necesita esa interacción inicial por las restricciones de audio de iOS.
7. Para probar el modo sin conexión, abre el juego una vez con internet y espera unos segundos; después prueba con modo avión. La primera visita necesita conexión.

## Para obtener una app nativa de iPhone después

El proyecto también incluye `.github/workflows/ios-unsigned.yml`, que compila en macOS alojado por GitHub, pero su resultado es **solo para simulador**, no para instalar en tu iPhone.

Para un IPA instalable mediante TestFlight necesitas una cuenta activa de Apple Developer, certificados y perfiles de firma, así como un proceso de compilación macOS alojado que use tus credenciales de forma segura. **No compartas contraseñas ni claves privadas en este chat.** Cuando quieras pasar a TestFlight, podremos preparar el flujo firmado y las instrucciones para configurar los secretos del repositorio.
