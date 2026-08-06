# IES · Seguimiento de Procesos Contables

Aplicación web para el seguimiento del ciclo contable mensual del equipo IES.

## Archivos

| Archivo | Qué es |
|---|---|
| `index.html` | **La aplicación.** Requiere configurar Firebase antes de publicarla. |
| `demo.html` | Versión de demostración. Funciona sin Firebase; guarda todo en el navegador y no comparte el progreso. |
| `GUIA-DESPLIEGUE-IES.md` | Guía paso a paso para ponerla en línea. |
| `Manual-Procesos-Equipo-IES.docx` | Manual de procesos por persona, puntos de cruce y cronograma. |
| `Calendario-Procesos-IES-2026.xlsx` | Calendario de los 12 meses, una hoja por mes. |

## Cómo publicarla

Resumen — el detalle está en `GUIA-DESPLIEGUE-IES.md`:

1. Crear un proyecto en **console.firebase.google.com**.
2. Pegar el bloque `firebaseConfig` dentro de `index.html`, donde dice `PEGAR_API_KEY`.
3. Activar **Authentication → Correo electrónico/contraseña**.
4. Crear la base de datos **Firestore**.
5. Publicar las reglas de seguridad que están en la guía.
6. Arrastrar `index.html` a **app.netlify.com** para obtener la dirección pública.
7. Entrar por primera vez con el correo del administrador y pulsar *Crear configuración del equipo*.

## Acceso del equipo

Cada persona crea su propia contraseña la primera vez: escribe su correo de trabajo,
inventa una clave de 6 caracteres o más y pulsa **Primera vez — crear mi contraseña**.
Solo funciona con los correos de la lista autorizada que está dentro de `index.html`
(constante `SEED_ROLES`).

| Persona | Rol en la app |
|---|---|
| Cristian Bernal | Administrador — marca cualquier tarea, edita y elimina, gestiona usuarios |
| Isnardi Sanches | Miembro — marca sus tareas y registra tareas nuevas |
| Luis Santiago Amador | Miembro — marca sus tareas y registra tareas nuevas |
| Edgar Metaute | Solo lectura — ve el progreso y registra tareas nuevas |
| Ingrithh Giraldo | Solo lectura — ve el progreso y registra tareas nuevas |

Beatriz no tiene cuenta. Sus tareas están en el sistema y las marca el administrador.

## Qué hace la aplicación

- Tablero por persona con las tareas del mes, su estado y el detalle de cada una.
- Registro de **tareas adicionales** con responsable, tipo, detalle, fecha de solicitud,
  inicio y fin estimados y tiempo estimado. Todos pueden crear; solo el administrador
  puede editar o eliminar.
- Calendario mensual con las tareas por día y vista del año completo.
- Progreso del equipo sincronizado en tiempo real entre todos los usuarios.
- Panel de administración para gestionar los accesos.
