# Política de privacidad — Latent

**Última actualización:** 30 de junio de 2026  
**App:** Latent (`com.juanmartos.LatentApp`)  
**Responsable:** Juan Martos

Esta política describe cómo **Latent** trata la información cuando usas la aplicación en iPhone o iPad. Latent es una app de notas y gestión de conocimiento personal **local-first**: el diseño prioriza que tus datos permanezcan bajo tu control.

---

## Resumen

| Pregunta | Respuesta |
|----------|-----------|
| ¿Vendemos tus datos? | **No** |
| ¿Usamos publicidad o tracking? | **No** |
| ¿Tus notas se envían a servidores de IA de terceros? | **No** — la IA de chat corre con **Apple Intelligence** en el dispositivo |
| ¿Hay analítica de terceros (Firebase, etc.)? | **No** |
| ¿Puedes usar la app sin iCloud? | **Sí** — las notas pueden permanecer solo en el dispositivo |

---

## 1. Qué datos trata la app

Latent procesa únicamente la información que **tú creas o importas**:

- **Notas:** título, contenido, enlaces entre notas (`@menciones`), fechas de creación y modificación.
- **Fragmentos indexados:** divisiones internas de tus notas usadas para búsqueda semántica (derivadas de tu contenido).
- **Embeddings vectoriales:** representaciones numéricas generadas **en el dispositivo** a partir de tus textos, para búsqueda y grafo.
- **Mensajes de chat:** preguntas y respuestas de la sesión actual, almacenados **solo en el dispositivo** (no se sincronizan con iCloud).
- **PDFs importados:** el texto extraído se convierte en una nota; el archivo original no se sube a servidios propios.
- **Preferencias de la app:** tema (claro/oscuro/sistema) y ajustes del editor, guardados localmente.

Latent **no** solicita crear una cuenta propia. No recopilamos nombre, email ni identificadores de marketing.

---

## 2. Dónde se almacenan los datos

### En tu dispositivo

La mayor parte de los datos vive en el almacenamiento local del iPhone/iPad, cifrado en reposo (ver sección 4).

### iCloud (opcional)

Si inicias sesión en **iCloud** en el dispositivo, las **notas y sus fragmentos indexados** pueden sincronizarse con tu **contenedor privado de CloudKit** (`iCloud.com.juanmartos.LatentApp`), gestionado por Apple.

- El **historial de chat no se sincroniza** con iCloud.
- La sincronización depende de la configuración de iCloud del usuario y de los servicios de Apple.
- Los datos en iCloud están asociados a **tu Apple ID**, no a una cuenta de Latent.

Latent no opera servidores propios para almacenar el contenido de tus notas.

---

## 3. Cómo se usa la inteligencia artificial

### Búsqueda semántica y grafo

Los embeddings y la búsqueda híbrida (texto + vectores) se ejecutan **íntegramente en el dispositivo** mediante CoreML y el Neural Engine. Ningún contenido de tus notas se envía a servidores externos para indexar o buscar.

### Chat con Apple Intelligence

Para responder preguntas sobre tus notas, Latent:

1. Recupera fragmentos relevantes **localmente** de tu biblioteca.
2. Envía ese contexto al modelo **Apple Intelligence** (`Foundation Models`) **on-device**.

Latent **no** utiliza APIs de chat en la nube de terceros (OpenAI, Anthropic, etc.) para el contenido del usuario.

El uso de Apple Intelligence está sujeto a la [política de privacidad de Apple](https://www.apple.com/legal/privacy/).

---

## 4. Seguridad

- **Cifrado en reposo:** títulos y contenidos de notas, fragmentos y mensajes de chat se protegen con **ChaCha20-Poly1305** antes de persistirse.
- **Claves:** las claves de cifrado se guardan en el **Keychain** del dispositivo (con soporte de sincronización vía iCloud Keychain para descifrar en tus dispositivos Apple).
- **Sin tracking:** la app declara que **no realiza tracking** ni vincula datos con terceros con fines publicitarios (ver `PrivacyInfo.xcprivacy` incluido en la app).

---

## 5. Datos que no recopilamos

Latent **no** recopila ni comparte:

- Datos de localización GPS
- Contactos, fotos o micrófono (salvo lo que el sistema permita al importar un PDF que tú elijas)
- Identificadores publicitarios (IDFA) ni perfiles de uso para anuncios
- Estadísticas de uso con terceros (Google Analytics, Mixpanel, etc.)
- Contenido de tus notas con el desarrollador

---

## 6. APIs del sistema declaradas

Latent accede a **UserDefaults** únicamente para guardar preferencias de interfaz (por ejemplo, tema claro/oscuro), conforme a las razones declaradas en el manifiesto de privacidad de Apple (categoría CA92.1 — preferencias del usuario en la app).

---

## 7. Conservación y eliminación

- **Notas:** permanecen hasta que las elimines en la app. Al borrar una nota, se eliminan también sus fragmentos e índices asociados en el dispositivo (y en iCloud, si la sincronización está activa).
- **Chat:** cada vez que abres la app comienza una sesión nueva; los mensajes anteriores de sesiones pasadas no se conservan de forma persistente entre arranques.
- **Desinstalación:** al eliminar Latent del dispositivo se borran los datos locales. Los datos en iCloud pueden persistir en tu cuenta hasta que los elimines o desactives la sincronización; consulta [soporte de Apple sobre iCloud](https://support.apple.com/icloud).

---

## 8. Menores

Latent no está dirigida a menores de 13 años. No recopilamos datos de menores de forma consciente.

---

## 9. Tus derechos

Como tus datos están bajo tu control:

- Puedes **acceder, editar y exportar** tu contenido desde la propia app (notas, PDFs importados).
- Puedes **dejar de sincronizar** desactivando iCloud o cerrando sesión en el dispositivo.
- Puedes **eliminar** tus datos borrando notas o desinstalando la app.

Para usuarios en el Espacio Económico Europeo, puedes ejercer derechos de protección de datos contactándonos (sección 11). Latent actúa como responsable del tratamiento de las preferencias de la app; el contenido sincronizado en iCloud se rige también por las condiciones de Apple como encargado de infraestructura.

---

## 10. Cambios en esta política

Publicaremos cualquier cambio en esta página del repositorio público:

**https://github.com/juanmmm21/Latent/blob/main/privacy.md**

La fecha de «Última actualización» reflejará la versión vigente. Los cambios sustanciales pueden comunicarse mediante una actualización de la app o una nota en el repositorio.

---

## 11. Contacto

Para preguntas sobre privacidad o soporte:

- **Incidencias (GitHub):** [github.com/juanmmm21/Latent/issues](https://github.com/juanmmm21/Latent/issues)
- **Repositorio del producto:** [github.com/juanmmm21/Latent](https://github.com/juanmmm21/Latent)

---

## 12. Declaración en App Store Connect

En el cuestionario de privacidad de App Store Connect, Latent se configura coherente con esta política:

- **Datos vinculados al usuario:** contenido generado por el usuario (notas), almacenado on-device y opcionalmente en el iCloud privado del usuario.
- **Tracking:** no.
- **Datos usados con fines de tracking:** ninguno.

---

<p align="center"><sub>© 2026 Juan Martos · Latent</sub></p>
