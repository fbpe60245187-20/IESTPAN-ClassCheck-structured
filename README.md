# ClassCheck

Sistema web de gestión académica con PHP y MySQL. Este repositorio conserva el producto ClassCheck y organiza sus archivos con una estructura de proyecto sencilla: documentación en `docs/` y aplicación en `src/`.

## Estructura

```text
.
├── README.md
├── design/                         # Recursos y decisiones de diseño
├── docs/
│   └── class_Check_final_impresion_arreglada.xlsx
└── src/
    ├── administrador/              # Gestión administrativa
    ├── alumno/                     # Vistas del alumno
    ├── assets/                     # CSS y JavaScript
    ├── config/                     # Conexión y seguridad
    ├── database/                   # Esquema SQL
    ├── docente/                    # Vistas del docente
    ├── includes/                   # Componentes comunes
    └── *.php                       # Entrada, login y registro
```

## Requisitos e instalación local

- XAMPP para macOS, Windows o Linux con Apache, PHP y MySQL/MariaDB.
- PHP 8.1 o superior recomendado y PDO MySQL habilitado.

1. Coloca la carpeta del proyecto en el directorio web de XAMPP.
2. Enciende Apache y MySQL.
3. Importa `src/database/classcheck.sql` en phpMyAdmin. El esquema crea la base `classcheck`, sus tablas y las carreras iniciales.
4. Configura las credenciales locales en `src/config/conexion.php`.
5. Abre `src/crear_administrador.php` mediante el servidor web y crea el primer administrador con una contraseña de al menos 14 caracteres.
6. Después de crear el administrador, elimina `crear_administrador.php` del servidor web.
7. Abre la ruta web de `src/` e inicia sesión.

> Si Apache sirve la carpeta raíz del repositorio directamente, usa `src/` como raíz del sitio o ajusta la configuración del virtual host para que apunte a esa carpeta.

## Alcance actual

Incluye autenticación basada en el rol guardado en MySQL, creación inicial segura del administrador, registro de alumnos y solicitudes de cuentas docentes, paneles por rol, gestión básica de usuarios, carreras, unidades y horarios, plazos, solicitudes de reapertura y auditoría.

No es aún una implementación académica completa para producción: los formularios y flujos detallados para registrar asistencia y calificaciones requieren completarse y probarse con las reglas oficiales del instituto. La edición y eliminación de horarios también necesitan un flujo POST completo.

## Seguridad

- No publiques credenciales reales. `src/config/conexion.php` contiene valores locales de ejemplo; utiliza secretos de entorno o una configuración local no versionada para producción.
- Configura HTTPS, límites de intentos de acceso, respaldos y gestión segura de secretos antes de desplegar.
- No uses datos personales reales hasta completar las funciones pendientes y realizar pruebas.
- El esquema SQL elimina las tablas de `classcheck` al importarse: úsalo solo en una base nueva o respalda los datos antes.

Consulta el libro de requisitos y planificación en `docs/class_Check_final_impresion_arreglada.xlsx`.
