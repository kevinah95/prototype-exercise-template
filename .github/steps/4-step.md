## Step 4: Inicializa Koin en cada plataforma

Ya tienes tus módulos de Koin listos. Ahora debes inicializar Koin en el punto de entrada de cada plataforma para que la inyección de dependencias funcione correctamente.

### 📖 Theory: ¿Por qué inicializar Koin en cada plataforma?

<!--
> [!TIP]
> Inicializar Koin en el punto de entrada de cada plataforma asegura que todas las dependencias estén disponibles desde el inicio de la aplicación.
-->

En proyectos multiplataforma, cada plataforma (Android, iOS) tiene su propio ciclo de vida y punto de entrada. Por eso, la inicialización de Koin debe hacerse en cada uno de ellos.

### ⌨️ Activity: Inicializa Koin en Android e iOS

1. **Android:**
   - Abre `KMPKoin/composeApp/src/androidMain/kotlin/io/github/kevinah95/MainApplication.kt`.
   - Llama a `initKoin()` en el método `onCreate` de tu clase `Application`:
     ```kotlin
     class MainApplication : Application() {
         override fun onCreate() {
             super.onCreate()
             initKoin()
         }
     }
     ```
   - No olvides registrar tu clase `MainApplication` en el `AndroidManifest.xml`:
     ```xml
     <application
         android:name=".MainApplication"
         ... >
         <!-- otras configuraciones -->
     </application>
     ```
2. **iOS:**
   - Abre `KMPKoin/composeApp/src/iosMain/kotlin/io/github/kevinah95/MainViewController.kt`.
   - Modifica la función para inicializar Koin usando `initKoin()` dentro del controlador:
     ```kotlin
     import io.github.kevinah95.di.initKoin
     
     fun MainViewController() = ComposeUIViewController(configure = { initKoin() }) { App() }
     ```
   - Así aseguras que Koin se inicializa correctamente al arrancar la app en iOS.
3. Verifica que la app arranca sin errores y que puedes inyectar dependencias en ambas plataformas.

<details>
<summary>Having trouble? 🤷</summary><br/>

- Si tienes problemas en Android, revisa que tu clase `Application` esté registrada en el `AndroidManifest.xml`.
- Si tienes problemas en iOS, revisa la integración entre Swift y Kotlin Multiplatform.
- Consulta la [documentación oficial de Koin](https://insert-koin.io/docs/setup/v4) para más detalles sobre inicialización multiplataforma.

</details>
