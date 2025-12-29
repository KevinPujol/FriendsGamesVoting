# Guía de Configuración de Firebase para Friends Games Voting

Esta guía te ayudará a crear el proyecto en Firebase y obtener las credenciales necesarias para que la aplicación funcione.

## Paso 1: Crear Proyecto en Firebase Console
1. Ve a [Firebase Console](https://console.firebase.google.com/).
2. Haz clic en **"Agregar proyecto"** (o "Create a project").
3. Ponle un nombre, por ejemplo: `FriendsGamesVoting`.
4. Desactiva Google Analytics (no es necesario para esto) y finaliza la creación.

## Paso 2: Crear la App Web
1. En la pantalla principal de tu nuevo proyecto, verás iconos circulares bajo "¿Empezar por añadir Firebase a tu app?". Haz clic en el icono de **Web** (el símbolo `</>`).
2. Ponle un apodo a la app (ej: `VotingApp`).
3. No es necesario marcar "Firebase Hosting" por ahora (usaremos GitHub Pages).
4. Haz clic en **"Registrar app"**.
5. Aparecerá un bloque de código con `firebaseConfig`. **Copia este objeto**, lo necesitarás más adelante. Se ve así:
   ```javascript
   const firebaseConfig = {
     apiKey: "...",
     authDomain: "...",
     databaseURL: "...",
     projectId: "...",
     storageBucket: "...",
     messagingSenderId: "...",
     appId: "..."
   };
   ```

## Paso 3: Configurar Realtime Database
1. En el menú izquierdo, ve a **Compilación (Build)** -> **Realtime Database**.
2. Haz clic en **"Crear base de datos"**.
3. Selecciona la ubicación (Estados Unidos o Bélgica suelen estar bien).
4. En "Reglas de seguridad", selecciona **"Comenzar en modo de prueba"** (Start in test mode). *Esto permitirá escribir datos sin autenticación compleja inicialmente.*
5. Haz clic en **Habilitar**.

## Paso 4: Ajustar Reglas de Seguridad (Importante)
Como no estamos usando un sistema de Login con contraseña (solo seleccionamos nombre), para evitar que cualquiera borre todo, vamos a poner unas reglas básicas que permitan leer y escribir, pero validando un poco la estructura.

1. En la pestaña **Reglas** de Realtime Database, borra lo que hay y pega esto:

```json
{
  "rules": {
    ".read": true,
    "votes": {
      "$player_id": {
        // Solo permite escribir si eres un usuario válido (opcional, por ahora dejamos abierto)
        ".write": true
      }
    }
  }
}
```
*Nota: Para máxima seguridad en producción deberíamos usar Firebase Auth Anónimo o Email, pero para este uso entre amigos, el modo test o estas reglas sencillas suelen bastar.*

## Paso 5: Conectar con tu Código
1. Abre el archivo `VotingApp/app.js` en tu ordenador.
2. Busca las líneas donde dice `const firebaseConfig = { ... }`.
3. Reemplaza todo ese bloque con el que copiaste en el **Paso 2**. IMPORTANTE: Asegúrate de que `databaseURL` esté presente (a veces no sale en el snippet inicial y tienes que copiarlo de la configuración general).

## Paso 6: Despliegue
Guarda los cambios, haz commit y push a GitHub. Activa GitHub Pages y ¡listo!
