# LoginGit

## pasos para conectarse a GitHub desde la terminal
1. Abrir la terminal.
2. Configurar el nombre de usuario y correo electrónico:
   ```bash
   git config --global user.name "TuNombreDeUsuario"
   git config --global user.email "tuemail@ejemplo.com"                                              

# ============================================================
# CONFIGURACIÓN DE GIT Y CONEXIÓN CON GITHUB
# ============================================================


# 1. Ver la configuración global de Git
#    Sirve para comprobar qué nombre, email y otras opciones
#    tienes configuradas.
git config --global -l


# 2. Configurar el nombre que aparecerá en tus commits
git config --global user.name "lil-doggy"


# 3. Configurar el email que aparecerá en tus commits
#    Asegúrate de que el correo sea correcto.
git config --global user.email "albino.caceres@gmail.com"


# 4. Verificar nuevamente el nombre y email configurados
git config --global -l


# ============================================================
# CONFIGURAR EL REPOSITORIO DE GITHUB
# ============================================================


# 5. APUNTAR EL PROYECTO LOCAL A TU REPOSITORIO DE GITHUB
#    Cambia la URL por la URL de tu propio repositorio.
#
#    Usa "set-url" si "origin" YA existe.
git remote set-url origin https://github.com/lil-doggy/LoginGit.git


# 6. Verificar que "origin" apunta correctamente a GitHub
git remote -v


# ============================================================
# LIMPIAR CREDENCIALES ANTERIORES DE GITHUB
# ============================================================


# 7. Eliminar las credenciales de GitHub guardadas en macOS.
#    Esto es importante si recibiste:
#
#    "Invalid username or token"
#
#    para que Git vuelva a solicitar autenticación.
printf "protocol=https\nhost=github.com\n\n" | git credential-osxkeychain erase


# ============================================================
# PREPARAR Y SUBIR EL PROYECTO
# ============================================================


# 8. Agregar todos los archivos del proyecto al área de
#    preparación (staging).
git add .


# 9. Crear un commit con los cambios preparados.
git commit -m "Primer commit"


# 10. Cambiar el nombre de la rama actual a "main".
git branch -M main


# 11. Subir la rama "main" a GitHub.
#     La opción -u conecta tu rama local "main" con
#     "origin/main".
git push -u origin main


# ============================================================
# AUTENTICACIÓN DE GITHUB
# ============================================================


# Cuando Git solicite:
#
# Username for 'https://github.com':
#
# Escribe:
# lil-doggy
#
# Cuando solicite:
#
# Password for 'https://lil-doggy@github.com':
#
# NO escribas tu contraseña normal de GitHub.
# Debes utilizar un Personal Access Token (PAT).
#
# IMPORTANTE:
# Al pegar el token en la terminal NO verás caracteres.
# Es normal. Pega el token y presiona Enter.


# ============================================================
# CERRAR SESIÓN / ELIMINAR CREDENCIALES DE GITHUB
# ============================================================


# 12. Eliminar las credenciales de GitHub guardadas en macOS.
printf "protocol=https\nhost=github.com\n\n" | git credential-osxkeychain erase


# Después de esto, el próximo "git push" debería solicitar
# nuevamente las credenciales de GitHub.


# ============================================================
# OPCIONAL: ELIMINAR TAMBIÉN EL USUARIO/EMAIL DE GIT
# ============================================================


# 13. Eliminar el nombre global de Git.
git config --global --unset user.name


# 14. Eliminar el email global de Git.
git config --global --unset user.email


# 15. Comprobar la configuración global restante.
git config --global -l
