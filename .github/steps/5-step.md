## Step 5: Usa las dependencias inyectadas en la UI

¡Ya tienes Koin funcionando en ambas plataformas! Ahora es momento de consumir las dependencias inyectadas (por ejemplo, el UserRepository) desde la UI usando Koin y Compose Multiplatform.

### 📖 Theory: Inyección de dependencias en la UI

<!--
> [!TIP]
> Koin permite inyectar dependencias directamente en tus composables o viewmodels, facilitando la reutilización y el testeo de componentes.
-->

En Compose Multiplatform, puedes usar funciones como `get()` o `inject()` de Koin para obtener instancias de tus dependencias en los composables o viewmodels.

### ⌨️ Activity: Inyecta y usa UserRepository en la UI

1. Abre `KMPKoin/composeApp/src/commonMain/kotlin/io/github/kevinah95/App.kt`.
2. Inyecta el repositorio de usuarios usando `koinInject` y el ViewModel usando `koinViewModel` en tu composable principal:
   ```kotlin
   import org.koin.compose.koinInject
   import org.koin.compose.koinViewModel
   import io.github.kevinah95.data.UserRepository
   import io.github.kevinah95.UserViewModel

   @Composable
   fun App() {
       val userViewModel = koinViewModel<UserViewModel>()
       val greeting = userViewModel.getGreeting()
       // Usa el greeting en tu UI, por ejemplo:
       Text(text = greeting)
       // También puedes mostrar la lista de usuarios si lo deseas
   }
   ```

> [!NOTE]
> `koinInject` se utiliza para inyectar cualquier dependencia registrada en Koin, mientras que `koinViewModel` está especializado para inyectar ViewModels y maneja automáticamente su ciclo de vida en Compose.

3. Muestra la lista de usuarios en la interfaz usando Compose (por ejemplo, con un LazyColumn).
4. (Opcional) Inyecta otros viewmodels o dependencias según lo necesites, por ejemplo:
   ```kotlin
   val anotherViewModel = koinInject<AnotherViewModel>()
   ```

<details>
<summary>Having trouble? 🤷</summary><br/>

- Si tienes errores de inyección, revisa que Koin esté inicializado antes de acceder a las dependencias.
- Consulta la [documentación de Koin para Compose](https://insert-koin.io/docs/compose/compose/) para más ejemplos de integración.

</details>
