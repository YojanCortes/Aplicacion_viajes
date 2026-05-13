# Aplicacion_viajes — Repositorio de Actualizaciones

Este repositorio es el servidor de actualizaciones remotas para la app **App Buses**.

## ¿Cómo funciona?

1. La app Flutter consulta el archivo `version.json` de este repositorio (rama `main`).
2. Si la versión remota es mayor que la instalada, muestra la pantalla de actualización.
3. El usuario descarga e instala el nuevo APK directamente desde la app.

---

## Flujo de trabajo para publicar una nueva versión

### 1. Compilar el APK
En el proyecto Flutter (`app-_viajes`), ejecuta:
```bash
flutter build apk --release
```
El archivo se genera en: `build/app/outputs/flutter-apk/app-release.apk`

### 2. Subir el APK a GitHub Releases
1. Ve a este repositorio en GitHub.
2. Haz clic en **"Releases"** → **"Create a new release"**.
3. En **Tag version** escribe la nueva versión (ej: `v1.0.1`).
4. Adjunta el archivo `app-release.apk`.
5. Publica el Release.

### 3. Actualizar `version.json`
Edita el archivo `version.json` con la nueva versión y la URL del APK:
```json
{
  "version": "1.0.1",
  "apk_url": "https://github.com/YojanCortes/Aplicacion_viajes/releases/download/v1.0.1/app-release.apk",
  "notas": "Descripción breve de los cambios en esta versión."
}
```

### 4. Hacer commit y push
```bash
git add version.json
git commit -m "release: v1.0.1"
git push origin main
```

¡Listo! La próxima vez que los choferes abran la app y presionen **"Buscar actualización"**, recibirán la nueva versión automáticamente.

---

## Estructura del repositorio

```
Aplicacion_viajes/
├── version.json       ← Controla qué versión está disponible
└── README.md
```

> **Nota:** Los archivos APK se alojan en GitHub **Releases**, no directamente en el repositorio, para evitar que el repo se vuelva muy pesado.
