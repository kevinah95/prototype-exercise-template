# Step 1: Agrega las dependencias de Koin usando Version Catalog

Ahora que conoces la estructura del proyecto, el siguiente paso es agregar Koin para la inyección de dependencias utilizando el Version Catalog (`libs.versions.toml`) y el BOM de Koin (Bill of Materials) versión 4.

### 📖 Theory: ¿Por qué usar Version Catalog y BOM?

<!--
> [!TIP]
> El Version Catalog centraliza y simplifica la gestión de versiones de dependencias. El BOM de Koin asegura que todas las dependencias de Koin sean compatibles entre sí.
-->

En proyectos modernos, es recomendable definir las versiones y módulos de dependencias en `libs.versions.toml` para mantener el proyecto organizado y fácil de actualizar.

### ⌨️ Activity: Añade Koin a tu proyecto con Version Catalog

1. Abre el archivo `gradle/libs.versions.toml` y asegúrate de tener las siguientes líneas:
   ```toml
   [versions]
   koin-bom = "4.1.0"
   # ...otras versiones

   [libraries]
   koin-bom = { module = "io.insert-koin:koin-bom", version.ref = "koin-bom" }
   koin-core = { module = "io.insert-koin:koin-core" }
   koin-compose = { module = "io.insert-koin:koin-compose" }
   # ...otras dependencias de Koin si las necesitas
   ```
2. En los archivos `build.gradle.kts` de los módulos `shared` y `composeApp`, agrega las dependencias de Koin usando el catalog:
   ```kotlin
   // En la sección dependencies
   implementation(platform(libs.koin.bom))
   implementation(libs.koin.core)
   // Para Compose Multiplatform (si aplica)
   implementation(libs.koin.compose)
   ```
3. Sincroniza el proyecto para descargar las dependencias.
4. (Opcional) Si usas iOS, asegúrate de que el código compartido exponga la inicialización de Koin para esa plataforma.

<details>
<summary>Having trouble? 🤷</summary><br/>

- Si tienes errores de sincronización, revisa que la versión de Koin sea compatible con tu versión de Kotlin.
- Consulta la [documentación oficial de Koin](https://insert-koin.io/docs/setup/v4) para más detalles sobre integración multiplataforma y uso de BOM.

</details>
