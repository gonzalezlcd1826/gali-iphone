# GALI — Space Arsenal · Proyecto móvil fase 2

Proyecto fuente de un juego web móvil con configuración Capacitor para Android e iOS. Incluye una copia de la **imagen de referencia visual elegida** en `www/assets/referencia-aprobada.jpeg` (no es un sprite utilizable directamente). El motor jugable usa ilustración Canvas con volumen simulado; Se han incorporado seis sprites PNG transparentes recortados de la referencia elegida. Son imágenes 2D derivadas de la referencia con apariencia 3D; los modelos 3D reales y la limpieza final de los sprites quedan pendientes. La melodía incluida es una composición electrónica tropical sintetizada, no la melodía comercial de *Lambada*.

## Requisitos
- Node.js y npm
- Para Android: Android Studio + SDK de Android
- Para iOS: macOS + Xcode + cuenta de desarrollador según destino de distribución

## Ejecutar y compilar
```bash
npm install
npm run start
npm run build
npx cap add android
npx cap add ios  # ejecutar únicamente en macOS
npm run sync
npm run android  # Android Studio
npm run ios      # Xcode, solo macOS
```

**Nota:** el directorio de salida de Vite es `dist`, usado por Capacitor. El proyecto incluye código fuente, no APK/IPA compilados ni publicación en tiendas. No se ha probado todavía en dispositivos físicos. La orientación vertical y las pantallas seguras deben confirmarse en los dispositivos de prueba.

## Funciones
- Cohete vertical y control por arrastre, botones laterales y disparo mantenido.
- Balas lentas (0,65 s), láser azul de doble impacto (1,8 s), granadas de área (8 s).
- Peluches multicolores, monedas, tres vidas, niveles, explosiones, sonido por arma.
- Música tropical electrónica original a 126 BPM, control independiente de música y efectos.

## Pendientes para lanzamiento
- Producir sprites/modelos 3D definitivos fieles a `www/assets/referencia-aprobada.jpeg`.
- Sustituir los dibujos de Canvas por los recursos finales sin cambiar las mecánicas.
- Probar rendimiento, audio y multitouch en iPhone y Android; generar iconos, splash, firma y builds.
- Revisar licencias de todos los recursos musicales y visuales antes de distribuir.

## Fase 2 — actualización de personajes
Los sprites `public/assets/plush-*.png` se cargan en el juego para sustituir los dibujos provisionales. Si no cargan, se usa el dibujo Canvas anterior como respaldo. El archivo `sprite-preview.jpg` permite revisar el resultado; los haces luminosos residuales se deberán limpiar en la versión final. No se han cambiado armas, música ni mecánicas.

## Fase 2 — preparación móvil y limpieza inicial
- Se conserva una copia de los seis recortes anteriores en `source-sprites/`.
- Se ha atenuado el haz luminoso central que sobresalía por encima de cada personaje. Es una limpieza inicial, no un modelado 3D nuevo.
- Se añadió manifiesto web para instalación de prueba desde navegador, iconos preliminares y metadatos de pantalla completa para iOS. Los iconos son provisionales y deberán revisarse antes de publicar.
- Las mecánicas, tiempos de recarga, melodía y sonidos no se han modificado.
- Para generar APK/IPA sigue siendo necesario instalar dependencias y generar proyectos nativos con Capacitor; iOS requiere macOS/Xcode.

## Fase 3 — preparación para pruebas en móviles
- Controles multitáctiles: arrastre del cohete con un dedo y disparo con otro; botones laterales con movimiento sostenido.
- Pausa automática al ocultar la app o perder foco, para evitar partidas y música activas en segundo plano.
- Márgenes seguros en pantallas con notch y navegación por gestos.
- Prueba automatizada de integridad: `npm test` verifica recursos, controles, parámetros y configuración.
- **Limitación:** son pruebas estáticas; no sustituyen la ejecución en dispositivos físicos ni confirman que existan instaladores APK/IPA.

## Fase 4 — canal de compilación para Android y validación iOS
- `.github/workflows/android-debug.yml`: al subir este proyecto a GitHub, permite lanzar una compilación de APK Android de **depuración**, descargable desde los artefactos de GitHub Actions si el flujo termina correctamente. No es un APK firmado para Play Store.
- `.github/workflows/ios-unsigned.yml`: permite compilar y verificar el proyecto para **simulador iOS** en un ejecutor macOS. No genera un IPA instalable en iPhone; eso requiere firma, certificados y perfil de aprovisionamiento de Apple.
- `npm run release:check`: valida identificador, seis PNG, tamaños de iconos, configuración y existencia de flujos de compilación. `npm test` sigue validando mecánicas y controles.
- **Importante:** los flujos se proporcionan sin ejecutar; el entorno actual no tiene las dependencias npm instaladas ni los SDK nativos necesarios para confirmar compilaciones. Antes de publicar se necesitan pruebas reales de rendimiento, audio y controles en ambos teléfonos.
