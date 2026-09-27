# GALI para iPhone — entrega de compilación

Este paquete conserva las mecánicas, sprites y música del proyecto aprobado. Incluye una ruta para compilar en macOS/Xcode y un flujo GitHub Actions para verificar la compilación del simulador. **No contiene un IPA firmado**: la firma para un iPhone físico requiere Xcode, cuenta Apple y un perfil de aprovisionamiento válido.

## A. Ejecutar en un iPhone conectado a una Mac
1. Instala Xcode (versión compatible con Capacitor 7), Node.js 22 y CocoaPods si Xcode lo solicita.
2. Abre Terminal en la carpeta `GALI-mobile` y ejecuta:
   ```sh
   npm install
   npm test
   npm run release:check
   npm run build
   npx cap add ios
   npx cap sync ios
   npx cap open ios
   ```
3. En Xcode selecciona el proyecto **App**, objetivo **App**, pestaña **Signing & Capabilities**. Selecciona tu **Team** de Apple y, si fuera necesario, cambia `Bundle Identifier` por uno único de tu propiedad.
4. Conecta el iPhone, habilita Developer Mode si se solicita, selecciona tu iPhone como destino y pulsa ▶ Run.
5. Para distribuir pruebas por TestFlight se requiere el programa Apple Developer, configurar firma/distribución y subir el archivo desde Xcode Organizer (Product > Archive > Distribute App).

## B. Verificar compilación sin Mac local
1. Crea un repositorio privado de GitHub con los archivos del ZIP (incluye la carpeta `.github`).
2. Ve a Actions > **GALI iOS unsigned build validation** > Run workflow.
3. Al terminar, descarga el artefacto **GALI-ios-simulator**. Es una aplicación para **simulador**, no instalable directamente en un iPhone físico.

## Limitaciones actuales
- La compilación iOS no se ha ejecutado aquí: este entorno no es macOS y no tiene Xcode ni credenciales de Apple.
- Los sprites son imágenes 2D con apariencia tridimensional derivadas de la referencia aprobada, no modelos 3D reales.
- Prueba sonido, controles multitáctiles, pausas, notch y rendimiento en un iPhone real antes de distribuir.
- No se ha alterado la melodía ni las mecánicas de la versión aprobada.
