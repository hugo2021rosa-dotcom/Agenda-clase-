# Agenda de clase

App web compartida para el grupo: exámenes y trabajos ordenados por fecha, y libros con enlace digital. Todo se sincroniza en tiempo real con Firebase (Firestore).

## 1. Crear el proyecto en Firebase
1. Entra en https://console.firebase.google.com y crea un proyecto.
2. **Compilación > Firestore Database > Crear base de datos** (modo producción, cualquier región).
3. **Configuración del proyecto > Tus apps > Web (`</>`)**: registra la app y copia el objeto `firebaseConfig`.
4. Pega esos valores en `firebase-config.js`.

## 2. Reglas de Firestore (pestaña "Reglas")
Para empezar rápido (cualquiera con el enlace puede editar):

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if true;
    }
  }
}
```
Si quieres más seguridad, activa Authentication y limita `write` a `request.auth != null`.

## 3. Subir a GitHub y publicar
```
git init
git add .
git commit -m "Agenda de clase"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/agenda-clase.git
git push -u origin main
```
Luego en GitHub: **Settings > Pages > Deploy from branch > main / root**. Comparte el enlace con tus tres compañeros.

> Prueba en local con un servidor (por ejemplo `python3 -m http.server`), no abriendo el archivo directamente, porque usa módulos ES.
