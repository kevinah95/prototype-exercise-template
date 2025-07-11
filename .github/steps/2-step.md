# Step 2: Crea los modelos y repositorios de usuario

Ahora que tienes Koin integrado, es momento de definir la lógica de negocio creando los modelos y repositorios para la gestión de usuarios en el módulo `KMPKoin`.

### 📖 Theory: ¿Por qué separar modelos y repositorios?

<!--
> [!NOTE]
> Separar los modelos de datos y los repositorios permite una arquitectura más limpia, facilita el testing y el mantenimiento del código.
-->

Un modelo representa la estructura de los datos (por ejemplo, un usuario). Un repositorio abstrae el acceso y manipulación de esos datos, permitiendo cambiar la fuente de datos sin afectar el resto de la app.

### ⌨️ Activity: Implementa User y UserRepository

1. En `KMPKoin/shared/src/commonMain/kotlin/io/github/kevinah95/data/`, crea un archivo `User.kt` con el siguiente contenido:
   ```kotlin
   package io.github.kevinah95.data

   data class User(val id: String, val name: String, val email: String)
   ```
2. En la misma carpeta, crea `UserRepository.kt`:
   ```kotlin
   package io.github.kevinah95.data

   class UserRepository {
       private val users = mutableListOf<User>()

       fun addUser(user: User) {
           users.add(user)
       }

       fun getUsers(): List<User> = users
   }
   ```
3. (Opcional) Crea un archivo `DefaultData.kt` para poblar el repositorio con datos de ejemplo:
   ```kotlin
   package io.github.kevinah95.data

   object DefaultData {
       val sampleUsers = listOf(
           User(id = "1", name = "Alice", email = "alice@example.com"),
           User(id = "2", name = "Bob", email = "bob@example.com")
       )
   }
   ```
4. Asegúrate de que los archivos estén en el paquete correcto y que el código compile.
5. (Para el siguiente paso) Crea un archivo `UserViewModel.kt` en la misma carpeta con una implementación básica:
   ```kotlin
   package io.github.kevinah95

   import io.github.kevinah95.data.UserRepository

   class UserViewModel(private val userRepository: UserRepository) {
       fun getGreeting(): String = "Hello, ${userRepository.getUsers().firstOrNull()?.name ?: "Guest"}!"
       fun getUsers() = userRepository.getUsers()
   }
   ```

<details>
<summary>Having trouble? 🤷</summary><br/>

- Si tienes errores de compilación, revisa los nombres de los paquetes y la ubicación de los archivos.
- Puedes consultar la [documentación oficial de Kotlin Multiplatform](https://kotlinlang.org/docs/multiplatform.html) para más ejemplos de organización de código.

</details>
