# Class - EduTrack

[Carpeta de recursos en Google Drive](https://drive.google.com/drive/folders/1PiJUpd-nDcZ7rt-phgaVotthFRTup0mC?usp=drive_link)

## 1. Datos de la auditoría

| Campo | Información |
| --- | --- |
| Equipo auditor | Dharmauy |
| Equipo auditado | Class / EduTrack |
| Fecha | 14/10/2026 |
| Ambiente autorizado | https://edutrack-uy.com/ |
| Versión / commit | Sin versionado |
| Navegador y dispositivo | Google Chrome |
| Alcance | Realizar pruebas exploratorias con usuario administrador y docente |

### Usuarios de prueba

| Perfil | Usuario | Contraseña |
| --- | --- | --- |
| Administrador | `admin` | `3I?'V/=x9m9l` |
| Docente | `jorge.marrero@estudiantes.utec.edu.uy` | `Utec2026` |

## 2. Resumen ejecutivo

**Objetivo:** Evaluar la usabilidad, las validaciones funcionales, la seguridad de acceso y la consistencia de las funcionalidades para la administración de clases y docentes.

## 3. Funcionalidades revisadas

- [ ] Inicio de sesión y cierre de sesión.
- [ ] Ingreso a datos de equipo.
- [ ] Datos académicos: cursos.
- [ ] Libreta.
- [ ] Configuraciones.
- [ ] Perfil de usuario.

## 4. Hallazgos

Las referencias «img» se conservan tal como aparecen en el documento de origen. Las imágenes no están incrustadas en este Markdown.

### 4.1. Perfil administrador

| Funcionalidad | Observación o propuesta | Evidencia |
| --- | --- | --- |
| Libreta | La tarjeta de los usuarios de la libreta es apaisada. | img 1 |
| Calificaciones | Al imprimir las calificaciones, estas no se muestran. | img 2 |
| Desplegable | Se propone convertir el desplegable en un filtro de búsqueda con autocompletado al escribir. | img 3 |
| Gráfica de barras | La gráfica de barras no se ve con claridad. | img 4 |
| Recuperación de contraseña | Aparece el texto «también puedes ingresar con», pero no se muestran opciones. | img 5 |

### 4.2. Perfil docente

| Funcionalidad | Observación o propuesta | Evidencia |
| --- | --- | --- |
| Libreta docente | El menú lateral muestra menos opciones que la libreta, que ya tiene su propio submenú. Se propone quitar los accesos rápidos del menú lateral y dejar solo «Mis libretas», para utilizar las opciones de su submenú. | img 6 |
| Navegación y perfil | Se propone destacar la funcionalidad y sección en la que se encuentra el usuario. El ícono de «Mi perfil» en el submenú corresponde a la iconografía de filtros. | img 7 |
| Mi agenda | Se plantea la consulta: ¿el usuario docente no puede crear su propia agenda? | img 8 |
| Mi agenda | Falta información como tipo de curso o materia, grupo, salón y enlace a videollamada. | img 9 |
| Pase de lista | No permite ingresar comentarios con caracteres como el espacio. | img 10 |
| Pase de lista | El usuario docente no puede visualizar reportes de actividad por clase. | Sin referencia de imagen en el documento |
| Pase de lista | No se identifica dónde realizar el check-in del propio docente. | Sin referencia de imagen en el documento |
| Accesibilidad | El recorrido con teclado solo recorre los botones; no ingresa a los bloques o tarjetas. | img 11 |

### 4.3. Perfil estudiante: creación de cuenta

| Funcionalidad | Observación o propuesta | Evidencia |
| --- | --- | --- |
| Datos personales | Se propone ordenar los bloques para mantener nombre y apellido en la misma línea. | img 12 |
| Creación de cuenta | Completar los datos no habilita el botón «Continuar» para crear la cuenta. | img 13 |
| Continuar con Google | El botón exige al usuario completar los datos. | img 15 |

## 5. Pentesting

### 5.1. Datos inválidos y fecha extrema

- **Qué probamos:** En el registro se ingresó un correo sin arroba, la cédula `123`, el celular `111111111` y una fecha de nacimiento del año 3000.
- **Qué esperábamos:** Que se indicara qué datos eran incorrectos.
- **Qué pasó:** Se mostraron mensajes de correo, cédula y celular inválidos. Para la fecha apareció «La fecha de nacimiento no puede ser futura». El botón «Crear cuenta» seguía deshabilitado.
- **Resultado:** La validación en pantalla respondió bien. No se envió el formulario.

### 5.2. Acceso a Administración con perfil docente

- **Qué probamos:** Se ingresó con la cuenta docente y se intentó abrir directamente «Usuarios», «Auditoría» y «Configuración del sistema».
- **Qué esperábamos:** Que no se permitiera acceder a esas secciones.
- **Qué pasó:** Los tres intentos devolvieron al inicio. No se mostraron las pantallas administrativas.
- **Resultado:** El control de acceso funcionó en estas tres pantallas.
- **Rutas probadas:** `/admin/users`, `/admin/audit` y `/admin/settings`.

### 5.3. Modificación de una lista cerrada

- **Qué probamos:** Se abrió la lista del 2 de octubre y se revisaron las opciones para cambiarla o guardarla.
- **Qué esperábamos:** Que, si ya había vencido el plazo, no se permitiera modificarla.
- **Qué pasó:** Las opciones de asistencia, «Todos presentes», «Copiar hora anterior» y «Guardar lista» estaban deshabilitadas.
- **Resultado:** El bloqueo de edición en pantalla funcionó. No se cambió ninguna asistencia.

## 6. Fuente

[Documento original: Class - EduTrack](https://drive.google.com/file/d/1OFRmW_HDrIbiDct4V7HGZZxgeCMjA4aqdDCVYqXpC1k)
