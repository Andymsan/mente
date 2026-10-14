# Mi mente

Mi tablero de autoconocimiento: personas, rutina, dieta, ciclos de emociones, diario, cómo pienso y recordatorios.

- Entra con el mismo correo y contraseña de **Mi dinero** (Firebase).
- Los datos se guardan en Firestore bajo `mente/{mi id}` y se sincronizan entre celular y computadora.
- El contenido personal de la página está **cifrado** con mi contraseña: el código público no muestra nombres ni historias.

## Reglas de Firestore

Dentro de `match /databases/{database}/documents { ... }` debe estar:

```
match /mente/{uid}/{doc=**} {
  allow read, write: if request.auth != null && request.auth.uid == uid;
}
```

## Actualizar o cambiar la contraseña

Si cambio mi contraseña de Firebase, vuelvo a correr `python cifrar.py` (en la carpeta privada, fuera de este repo) y subo el nuevo `index.html`.
