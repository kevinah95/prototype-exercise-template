## Step 3: Configura los módulos de Koin

Ahora que tienes tus modelos y repositorios, es momento de configurar los módulos de Koin para que puedas inyectar estas dependencias en tu aplicación.

### 📖 Theory: ¿Qué es un módulo de Koin?

<!--
> [!IMPORTANT]
> Un módulo de Koin es una colección de definiciones de dependencias. Permite declarar cómo se crean y comparten las instancias de tus clases.
-->

Los módulos de Koin te permiten definir qué objetos estarán disponibles para inyección y su ciclo de vida (singleton, factory, etc.).

### ⌨️ Activity: Crea y registra tus módulos de Koin

1. En `KMPKoin/shared/src/commonMain/kotlin/io/github/kevinah95/di/`, crea un archivo `AppModule.kt` con el siguiente contenido:
   ```kotlin
   package io.github.kevinah95.di

   import io.github.kevinah95.data.UserRepository
   import org.koin.dsl.module

   val appModule = module {
       single { UserRepository() }
   }
   ```
2. (Opcional) Si tienes más dependencias, agrégalas en este módulo o crea módulos adicionales.
3. En la misma carpeta, crea `KoinApp.kt` para inicializar Koin:
   ```kotlin
   package io.github.kevinah95.di

   import org.koin.core.context.startKoin

   fun initKoin() = startKoin {
       modules(appModule)
   }
   ```

<details>
<summary>Having trouble? 🤷</summary><br/>

- Si tienes errores de importación, revisa que los paquetes y rutas sean correctos.
- Consulta la [documentación oficial de Koin](https://insert-koin.io/docs/reference/koin-core/modules/) para más ejemplos de módulos.

</details>
