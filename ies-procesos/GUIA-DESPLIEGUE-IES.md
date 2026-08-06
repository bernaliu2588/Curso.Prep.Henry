# Guía de despliegue — App IES Procesos Contables

Documento de referencia para poner la aplicación en línea.
Tiempo estimado: 30 a 40 minutos.

---

## Resumen de usuarios

| Nombre | Correo | Rol en la app | Qué puede hacer |
|---|---|---|---|
| Cristian Bernal | contabilidad@iesonline.com.co | Administrador | Todo: marcar cualquier tarea, crear, editar, eliminar y gestionar usuarios |
| Isnardi Sanches | tesoreria@iesonline.com.co | Miembro | Marcar sus propias tareas y crear tareas nuevas |
| Luis Santiago Amador | auxiliar.contable2@iesonline.com.co | Miembro | Marcar sus propias tareas y crear tareas nuevas |
| Edgar Metaute | gerencia@iesonline.com.co | Solo lectura | Ver todo el progreso y crear tareas nuevas |
| Ingrithh Giraldo | administrador@solucionesies.co | Solo lectura | Ver todo el progreso y crear tareas nuevas |

**Beatriz** no tiene cuenta. Sus tareas aparecen en el sistema y las marca Cristian.

---

## PASO 1 — Crear el proyecto en Firebase

1. Entrar a **console.firebase.google.com** e iniciar sesión con una cuenta de Google.
2. Clic en **Agregar proyecto**.
3. Nombre del proyecto: `ies-contabilidad`. Continuar.
4. Google Analytics: puede **desactivarlo**, no se necesita. Crear proyecto.
5. Cuando termine de cargar, en la pantalla principal buscar el ícono **`</>`** (Web) y hacer clic.
6. Sobrenombre de la app: `ies-web`. Clic en **Registrar app**.
7. Firebase muestra un bloque de código con los datos de conexión. **Copiarlo completo.** Se ve así:

```javascript
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "ies-contabilidad.firebaseapp.com",
  projectId: "ies-contabilidad",
  storageBucket: "ies-contabilidad.appspot.com",
  messagingSenderId: "123456789012",
  appId: "1:123456789012:web:abc123..."
};
```

---

## PASO 2 — Pegar la configuración en el archivo

1. Abrir `ies-app.html` con el **Bloc de notas** (clic derecho → Abrir con → Bloc de notas).
2. Buscar cerca del inicio estas líneas:

```javascript
const FB_CFG = {
  apiKey:            "PEGAR_API_KEY",
  authDomain:        "PEGAR_PROJECT_ID.firebaseapp.com",
  projectId:         "PEGAR_PROJECT_ID",
  storageBucket:     "PEGAR_PROJECT_ID.appspot.com",
  messagingSenderId: "PEGAR_SENDER_ID",
  appId:             "PEGAR_APP_ID"
};
```

3. Reemplazar cada valor entre comillas por el que dio Firebase.
4. **Guardar** el archivo (Ctrl + G o Archivo → Guardar).

> Importante: no borrar las comillas ni las comas. Solo cambiar el texto de adentro.

---

## PASO 3 — Activar el inicio de sesión

1. En el menú izquierdo de Firebase: **Authentication** → botón **Comenzar**.
2. Pestaña **Sign-in method** → elegir **Correo electrónico/contraseña**.
3. Activar el primer interruptor (dejar desactivado el de "vínculo por correo"). **Guardar**.
4. Ir a la pestaña **Users** → botón **Agregar usuario**.
5. Crear las cinco cuentas, una por una:

| Correo | Contraseña |
|---|---|
| contabilidad@iesonline.com.co | (defina una) |
| tesoreria@iesonline.com.co | (defina una) |
| auxiliar.contable2@iesonline.com.co | (defina una) |
| gerencia@iesonline.com.co | (defina una) |
| administrador@solucionesies.co | (defina una) |

> Firebase exige mínimo 6 caracteres. Anote las contraseñas para repartirlas después.

---

## PASO 4 — Crear la base de datos

1. Menú izquierdo: **Firestore Database** → **Crear base de datos**.
2. Elegir **Iniciar en modo de producción**. Siguiente.
3. Ubicación: **us-east1** (o la más cercana). **Habilitar**.

---

## PASO 5 — Reglas de seguridad

En Firestore Database, pestaña **Reglas**. Borrar todo lo que haya y pegar esto:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {

    function signedIn(){ return request.auth != null; }
    function isAdmin(){
      return signedIn() && request.auth.token.email == 'contabilidad@iesonline.com.co';
    }

    // Roles de usuario: todos leen, solo el administrador modifica
    match /config/roles {
      allow read:  if signedIn();
      allow write: if isAdmin();
    }

    // Progreso del mes: todos leen y marcan tareas
    match /progress/{mes} {
      allow read, write: if signedIn();
    }

    // Tareas adicionales: todos crean, SOLO el administrador edita o elimina
    match /extraTasks/{id} {
      allow read:           if signedIn();
      allow create:         if signedIn();
      allow update, delete: if isAdmin();
    }
  }
}
```

Clic en **Publicar**.

> Estas reglas hacen que la restriccion de "solo Cristian edita o borra" se cumpla en el servidor, no solo en los botones de la pantalla.
>
> Si algun dia cambia el correo del administrador, hay que actualizar esa linea **y tambien** la constante `ADMIN_EMAIL` dentro de `ies-app.html`.

---

## PASO 6 — Publicar en internet

1. Entrar a **app.netlify.com** y crear una cuenta gratis (puede usar Google).
2. En el panel principal aparece una zona punteada que dice *"Drag and drop your site folder here"*.
3. **Arrastrar el archivo `ies-app.html`** hasta esa zona.
4. Netlify publica el sitio y da una direccion tipo `https://nombre-aleatorio.netlify.app`.
5. Para dejarla mas presentable: **Site configuration -> Change site name** -> escribir `ies-contabilidad`.

La direccion final queda: `https://ies-contabilidad.netlify.app`

Esa es la que se comparte con el equipo.

---

## PASO 7 — Configuracion inicial (automatica)

Este paso lo hace la aplicacion sola. Solo hay que entrar una vez:

1. Abrir la direccion en el navegador.
2. Iniciar sesion con **contabilidad@iesonline.com.co**.
3. Aparece la pantalla **Configuracion inicial** con los cinco usuarios del equipo listados.
4. Clic en **Crear configuracion del equipo**.

Listo. La app crea sola el documento `config/roles` en Firestore con estos accesos:

| Nombre | Correo | Rol |
|---|---|---|
| Cristian Bernal | contabilidad@iesonline.com.co | Administrador |
| Isnardi Sanches | tesoreria@iesonline.com.co | Miembro |
| Luis Santiago Amador | auxiliar.contable2@iesonline.com.co | Miembro |
| Edgar Metaute | gerencia@iesonline.com.co | Solo lectura |
| Ingrithh Giraldo | administrador@solucionesies.co | Solo lectura |

> Esta pantalla solo la puede ejecutar el administrador. Si otra persona entra primero, la app le dice que espere a que Cristian haga la configuracion.
>
> Despues de este paso, para agregar o quitar personas se usa **ADM -> Usuarios** dentro de la app. Ya no hay que volver a tocar Firestore.

---

## PASO 8 — Verificacion

1. Con la sesion de Cristian abierta, confirmar que aparece el boton **ADM** arriba a la derecha.
2. Entrar a **ADM -> Usuarios** y ver las cinco personas con su rol.
3. Marcar una tarea cualquiera.
4. Abrir la misma direccion en el celular, entrar con otra cuenta y confirmar que la tarea aparece marcada. Eso comprueba la sincronizacion en vivo.

---

## Si algo falla

| Síntoma | Causa más probable |
|---|---|
| "Tu cuenta no ha sido habilitada" | El correo en Authentication no coincide con el de la lista del PASO 7. Corregirlo desde ADM -> Usuarios |
| Pantalla en blanco | La configuración de Firebase quedó mal pegada en el PASO 2 |
| "Correo o contraseña incorrectos" | La cuenta no se creó en Authentication, o la contraseña es otra |
| No aparece el boton ADM | Entro con un correo distinto al del administrador |
| No sale la pantalla de configuracion inicial | Ya se creo antes. Se gestiona desde ADM -> Usuarios |
| Las tareas no se sincronizan | Las reglas del PASO 5 no se publicaron |

---

## Actualizaciones futuras

Para cambiar algo de la aplicación: editar `ies-app.html` y volver a arrastrarlo a Netlify en **Deploys → Drag and drop**. La dirección se mantiene igual.

Los datos (progreso y tareas adicionales) viven en Firebase, no en el archivo, así que no se pierden al actualizar.
