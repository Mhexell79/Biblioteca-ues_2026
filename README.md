# Sistema de Biblioteca UES

Aplicación de escritorio Java Swing con persistencia en MongoDB. Estructura Maven importable directamente desde Apache NetBeans 21.

## Requisitos

- JDK 21
- Apache NetBeans 21 con soporte Maven
- MongoDB local o MongoDB Atlas

## Abrir y ejecutar

1. En NetBeans, selecciona **File → Open Project** y abre la carpeta que contiene `pom.xml`.
2. Configura `MONGODB_URI` y `MONGODB_DATABASE` en las variables de entorno del sistema. Por defecto usa `mongodb://localhost:27017` y la base `biblioteca_ues`.
3. Ejecuta `com.biblioteca.app.Main` desde NetBeans (o `mvn compile exec:java`).

La aplicación se conecta a MongoDB al iniciar. Si la colección de usuarios está vacía, crea la cuenta inicial únicamente cuando configures `BIBLIOTECA_ADMIN_PASSWORD`: correo `admin@ues.edu.sv`, contraseña el valor de esa variable y tipo `Docente`. El programa carga tres materiales de ejemplo si la colección de materiales está vacía. Cambia la contraseña inicial después del primer ingreso (actualmente se cambia directamente en MongoDB; la interfaz todavía no incluye esa opción).

## Colecciones

- `usuarios`: identidad, correo y hash de contraseña.
- `materiales`: libros y revistas, con disponibilidad.
- `prestamos`: historial y estado activo.

## Subir a GitHub

Desde una terminal en la carpeta del proyecto:

```bash
git init
git add .
git commit -m "Inicializa sistema de biblioteca UES"
git branch -M main
git remote add origin https://github.com/TU-USUARIO/biblioteca-ues.git
git push -u origin main
```

No subas URI con credenciales, contraseñas ni archivos `.env`. El archivo `.gitignore` excluye `.env` y los archivos generados.
