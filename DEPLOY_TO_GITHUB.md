# Cómo subir tu proyecto a GitHub y publicarlo

Sigue estos pasos para subir tu carpeta `Friends Games` a GitHub y hacer que la web sea accesible para todos.

## 1. Crear un Repositorio en GitHub
1. Entra en [GitHub.com](https://github.com/) e inicia sesión.
2. Haz clic en el botón **+** (arriba a la derecha) y selecciona **"New repository"**.
3. Nombre del repositorio: `FriendsGamesVoting` (o el que prefieras).
4. Asegúrate de que esté marcado como **Public**.
5. No marques ninguna casilla de "Initialize this repository with...".
6. Haz clic en **Create repository**.

## 2. Preparar tu carpeta local
Abre la terminal en tu mac y ve a la carpeta de tu proyecto (copia y pega estos comandos uno a uno):

```bash
cd "/Users/kevinpujolgutierrez/Documents/Friends Games"
```

Inicia git si no lo has hecho:
```bash
git init
```

Añade todos los archivos:
```bash
git add .
```

Guarda los cambios (commit):
```bash
git commit -m "Primera version de la app de votacion"
```

## 3. Subir el código (Push)
Ahora conecta tu carpeta con el repositorio que creaste en el paso 1. GitHub te habrá dado unos comandos, serán parecidos a estos (¡pero usa los tuyos!):

```bash
# Cambia "TU_USUARIO" por tu nombre de usuario de GitHub
git remote add origin https://github.com/TU_USUARIO/FriendsGamesVoting.git

git branch -M main

git push -u origin main
```

## 4. Activar la web (GitHub Pages)
Una vez subido el código:
1. En tu repositorio de GitHub, ve a la pestaña **Settings** (Configuración).
2. En el menú de la izquierda, busca y haz clic en **Pages**.
3. En la sección **Build and deployment**:
   - **Source**: Déjalo en "Deploy from a branch".
   - **Branch**: Selecciona `main` y la carpeta `/VotingApp` (¡Importante! Porque tu web está dentro de esa subcarpeta, no en la raíz). 
   *Nota: Si GitHub no te deja seleccionar la subcarpeta `/VotingApp`, tendrás que seleccionar `/ (root)` y tu web estará disponible en `tudominio.github.io/FriendsGamesVoting/VotingApp/`.*
4. Haz clic en **Save**.

Espera unos minutos y refresca la página. Verás un enlace en la parte superior (ej: `https://kevin.github.io/FriendsGamesVoting/`). ¡Esa es tu web pública!

---
**Nota sobre la URL:**
Si tuviste que desplegar desde `root`, asegúrate de compartir el enlace terminado en `/VotingApp/index.html` con tus amigos para que vayan directo a la app.
