## Step 1: Configura tu entorno y explora el proyecto

¡Bienvenido! En este tutorial aprenderás a integrar Koin para la inyección de dependencias y a gestionar usuarios en un proyecto Kotlin Multiplatform (KMP) usando como base el proyecto KMPKoin.

### 📖 Theory: ¿Qué es Kotlin Multiplatform y por qué usar Koin?

<!--
> [!NOTE]
> Kotlin Multiplatform te permite compartir lógica de negocio entre Android, iOS y otras plataformas, manteniendo UIs nativas.
-->

Koin es un framework ligero de inyección de dependencias para Kotlin. Facilita la gestión de dependencias y la escalabilidad de tu código, especialmente en proyectos multiplataforma.

### ⌨️ Activity: Prepara tu entorno y explora la estructura

1. Clona el repositorio base de KMPKoin o descarga el código inicial.
2. Abre el proyecto en tu IDE favorito (IntelliJ IDEA o Android Studio recomendado).
3. Explora la estructura del proyecto, identificando los módulos principales: `shared`, `composeApp`, `iosApp`.
4. Revisa los archivos `build.gradle.kts` y la carpeta `shared/src/commonMain/kotlin` para familiarizarte con la organización del código.

<details>
<summary>Having trouble? 🤷</summary><br/>

- Si tienes problemas para abrir el proyecto, asegúrate de tener instalada la última versión de IntelliJ IDEA o Android Studio y el plugin de Kotlin Multiplatform.
- Si el proyecto no compila, ejecuta `./gradlew clean build` desde la terminal para forzar una reconstrucción.

</details>
