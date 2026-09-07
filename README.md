# LoginGit

## Pasos para conectarse a GitHub desde la terminal

### 1. Abrir la terminal

Abre la aplicación **Terminal** en tu computadora.

### 2. Configurar el usuario de Git

Configura el nombre que aparecerá en tus commits:

```bash
git config --global user.name "TuNombreDeUsuario"
```

Configura el correo electrónico:

```bash
git config --global user.email "tuemail@ejemplo.com"
```

Para comprobar la configuración:

```bash
git config --global -l
```

### 3. Conectar el proyecto con GitHub

Primero, asegúrate de estar dentro de la carpeta de tu proyecto.

Si `origin` ya existe, utiliza:

```bash
git remote set-url origin https://github.com/TuUsuario/TuRepositorio.git
```

Si `origin` todavía no existe, utiliza:

```bash
git remote add origin https://github.com/TuUsuario/TuRepositorio.git
```

Para comprobar la conexión:

```bash
git remote -v
```

### 4. Preparar los archivos

Agrega todos los archivos del proyecto:

```bash
git add .
```

### 5. Crear un commit

Guarda los cambios en un commit:

```bash
git commit -m "Primer commit"
```

### 6. Configurar la rama principal

Cambia el nombre de la rama a `main`:

```bash
git branch -M main
```

### 7. Subir el proyecto a GitHub

Ejecuta:

```bash
git push -u origin main
```

La opción `-u` conecta la rama local `main` con la rama `main` del repositorio remoto.

## Autenticación con GitHub

Si Git solicita:

```text
Username for 'https://github.com':
```

Introduce tu usuario de GitHub:

```text
TuNombreDeUsuario
```

Si solicita:

```text
Password for 'https://github.com':
```

GitHub **no acepta la contraseña normal** para operaciones Git mediante HTTPS.

Debes utilizar un **Personal Access Token (PAT)**.

> Al pegar el token en la terminal no aparecerán caracteres. Esto es normal. Pega el token y presiona `Enter`.

## Si aparece "Invalid username or token"

Si aparece un error como:

```text
remote: Invalid username or token.
fatal: Authentication failed
```

puedes eliminar las credenciales de GitHub guardadas en macOS:

```bash
printf "protocol=https\nhost=github.com\n\n" | git credential-osxkeychain erase
```

Después vuelve a intentar:

```bash
git push -u origin main
```

Git debería solicitar nuevamente las credenciales.

## Cerrar sesión de GitHub

Para eliminar las credenciales de GitHub guardadas en macOS:

```bash
printf "protocol=https\nhost=github.com\n\n" | git credential-osxkeychain erase
```

Esto **no elimina** tu nombre ni tu correo configurados en Git.

Si también quieres eliminar tu identidad global de Git:

```bash
git config --global --unset user.name
git config --global --unset user.email
```

Para comprobar la configuración restante:

```bash
git config --global -l
```
