# Aviso y Política de Privacidad de Veylora (Privacy Policy)

*Última actualización: [PENDIENTE: Fecha de entrada en vigor al momento de la publicación definitiva]*

El presente Aviso de Privacidad se formula con fundamento en la **Ley Federal de Protección de Datos Personales en Posesión de los Particulares (LFPDPPP)** de los Estados Unidos Mexicanos, expedida mediante decreto publicado en el Diario Oficial de la Federación (DOF) el **20 de marzo de 2025** (en vigor a partir del 21 de marzo de 2025), bajo la vigilancia y supervisión de la **Secretaría Anticorrupción y Buen Gobierno** como autoridad reguladora federal en materia de datos personales en el sector privado.

---

## 1. Identidad y Domicilio del Responsable del Tratamiento

1. **Nombre del Proyecto:** Veylora.
2. **Distinción entre Nombre Público e Identidad Legal:** **Veylora** es la denominación pública y técnica de la aplicación para Discord. La persona física o moral responsable del tratamiento y resguardo de los datos personales recabados a través del Bot es **[PENDIENTE: Nombre completo o Razón Social del Responsable en términos de la LFPDPPP]** (en adelante, "el Responsable"), con residencia operativa en los Estados Unidos Mexicanos (México).
3. **Domicilio del Responsable:** **[PENDIENTE: Domicilio legal en México para oír y recibir notificaciones en términos de la LFPDPPP]**.
4. **Correo Electrónico de Privacidad y Atención de Derechos ARCO:** **iankarimvr@gmail.com**.
5. **Canal de Soporte Técnico Previsto:** Repositorio público oficial de GitHub, el cual se encuentra actualmente en fase de preparación previa al despliegue: **[PENDIENTE: URL definitiva del repositorio público de GitHub una vez publicado]**.

---

## 2. Principio Rector: Datos que Veylora NO Recopila

A fin de brindar certeza a los usuarios de la plataforma Discord respecto al respeto de su privacidad:

1. **NO se graba, escucha, transcribe ni almacena audio de voz entrante:** Veylora se une a los canales de voz de Discord de forma estrictamente pasiva respecto a la captura de sonido. El Bot se conecta únicamente para **transmitir audio saliente** (reproducción de música en formato digital Opus a través de los servidores de voz de Discord). El Bot **no escucha, no captura, no almacena ni analiza el sonido de los micrófonos de los miembros conectados en el canal de voz**.
2. **NO se leen mensajes generales de los canales de texto:** El código fuente de Veylora **mantiene deshabilitado el intent privilegiado de contenido de mensajes** (`Message Content Intent` ausente en su configuración de Discord Gateway). El software no tiene acceso técnico al flujo de conversación general de los canales; únicamente recibe las cargas útiles (*payloads*) estructuradas que los servidores de Discord le remiten cuando un usuario invoca de forma deliberada un comando de aplicación (comando slash como `/play`, `/queue`, `/settings`) o pulsa un botón interactivo del reproductor.
3. **NO se recopilan datos personales sensibles:** Veylora no solicita ni trata contraseñas de cuentas de Discord, direcciones de correo electrónico personales de los miembros de los servidores, números de teléfono, direcciones IP de los usuarios de Discord, datos biométricos ni información financiera o bancaria.

---

## 3. Datos que Veylora Recopila y Procesa Realmente

La auditoría técnica del código fuente confirma que Veylora procesa exclusivamente los siguientes datos técnicos, organizados conforme a su nivel de persistencia:

### A. Datos Almacenados de Forma Persistente en Base de Datos Local (SQLite `data/veylora.db`)

El software almacena en el archivo local de base de datos cuatro conjuntos de registros:

1. **Tabla de Configuraciones por Servidor (`guild_settings`):**
   - **`guild_id` (INTEGER, Clave Primaria):** Identificador numérico público (*Snowflake ID*) asignado por Discord a cada servidor.
   - **`default_volume` (INTEGER):** Nivel de volumen predeterminado al reproducir música (por defecto 80%).
   - **`max_queue_size` (INTEGER):** Límite máximo de pistas permitidas en la lista de espera (por defecto 500).
   - **`music_channel_id` (INTEGER, Opcional):** Identificador numérico del canal de texto designado para comandos musicales.
   - **`dj_role_id` (INTEGER, Opcional):** Identificador numérico del rol autorizado para controles restringidos de música.
   - **`language` (TEXT):** Código de idioma configurado para las respuestas del bot (por defecto `'es'`).
   - **`updated_at` (TIMESTAMP):** Marca de tiempo de la última modificación de los ajustes.

2. **Tabla de Listas de Reproducción Guardadas (`saved_playlists`):**
   - **`id` (INTEGER, Clave Primaria Autoincremental):** Identificador interno único de la lista.
   - **`name` (TEXT):** Nombre que el usuario asignó libremente a su lista de reproducción.
   - **`owner_id` (INTEGER, Indexado):** Identificador numérico público de Discord (*User Snowflake ID*) del usuario propietario de la lista.
   - **`guild_id` (INTEGER, Opcional):** Identificador del servidor donde se registró la lista por primera vez.
   - **`created_at` (TIMESTAMP):** Marca de tiempo de registro de la lista.

3. **Tabla de Pistas de Listas de Reproducción (`saved_playlist_tracks`):**
   - **`id` (INTEGER, Clave Primaria Autoincremental):** Identificador interno único de la pista.
   - **`playlist_id` (INTEGER, Clave Foránea vinculada a `saved_playlists` con borrado en cascada `ON DELETE CASCADE`):** Asociación a la lista madre.
   - **`title` (TEXT) y `author` (TEXT):** Título de la pista y nombre del artista o canal de origen.
   - **`uri` (TEXT):** Enlace web de origen de la canción.
   - **`duration_ms` (INTEGER):** Duración de la pista en milisegundos.
   - **`source` (TEXT):** Tipo de fuente técnica (ej. `youtube`, `spotify`, `soundcloud`, `direct_url`, `attachment`).
   - **`position` (INTEGER):** Posición ordinal de la pista en la lista.

4. **Tabla de Historial de Reproducción (`playback_history`):**
   - **`id` (INTEGER, Clave Primaria Autoincremental):** Identificador interno del registro.
   - **`guild_id` (INTEGER, Indexado):** Identificador del servidor donde se reprodujo la canción.
   - **`title` (TEXT) y `author` (TEXT):** Título y autor de la pista reproducida.
   - **`uri` (TEXT):** Enlace web de origen de la pista.
   - **`requester_id` (INTEGER):** Identificador numérico público de Discord (*User Snowflake ID*) del miembro que solicitó la reproducción.
   - **`duration_ms` (INTEGER):** Duración en milisegundos.
   - **`played_at` (TIMESTAMP):** Marca de tiempo en la que comenzó a sonar la pista.

### B. Datos Procesados Temporalmente en Memoria Volátil (RAM)

Durante la reproducción activa, Veylora mantiene temporalmente en la memoria de la sesión:
- **`requester_id`:** Identificador numérico de Discord del solicitante.
- **`requester_name`:** Nombre público visible o apodo del solicitante en el servidor.
- **`requester_avatar`:** URL pública del avatar del usuario en Discord (empleada exclusivamente para ilustrar el mensaje interactivo *Now Playing* en el chat).
- **`source_type` y `original_query`:** Cadena de texto de búsqueda o enlace introducido por el usuario.
- **`thumbnail_override`:** Enlace a la miniatura visual de la pista.  
*Destrucción de datos en RAM:* Estos elementos son estrictamente volátiles; no se escriben en disco y se destruyen de forma automática e inmediata al concluir la reproducción de la pista, al vaciarse la cola o al reiniciarse el proceso del Bot.

### C. Registros Técnicos de Diagnóstico (Logs en Disco)

1. **Registro de la Aplicación (`logs/veylora.log`):** Almacena eventos de ejecución, marcas de tiempo, módulo, nivel de severidad y mensajes técnicos que pueden contener identificadores de servidor, consultas de búsqueda y trazas de error. Este archivo cuenta con un filtro de seguridad en código (`SensitiveDataFilter`) que ofusca automáticamente tokens de Discord, contraseñas, secretos y cabeceras de autorización `Bearer`.
2. **Registro del Servidor de Audio (`logs/lavalink.log`):** Registra eventos de decodificación y estado de la pasarela de voz de Lavalink, con una política de rotación automática (*rolling policy*) de 50 MB por archivo y un historial máximo de 7 archivos.

---

## 4. Finalidades del Tratamiento de los Datos

El tratamiento de los datos personales atiende a las siguientes finalidades:

### Finalidades Primarias (Necesarias para la Prestación del Servicio)
1. **Transmisión de Audio y Control de Sesión:** Conectar el reproductor al canal de voz, decodificar el flujo de audio y ejecutar instrucciones de pausa, reanudación, salto, orden de cola y volumen.
2. **Personalización del Servidor:** Guardar y aplicar en `guild_settings` los parámetros fijados por los administradores (volumen inicial, capacidad de cola, rol de DJ y canal de texto exclusivo).
3. **Persistencia de Listas de Reproducción:** Permitir a los usuarios almacenar colecciones personales de canciones mediante `/playlist save` y recargarlas en cualquier servidor donde Veylora esté presente mediante `/playlist load`.
4. **Identificación Visual del Solicitante:** Mostrar el apodo y avatar del usuario que pidió la pista en el mensaje informativo del chat mientras se reproduce.
5. **Diagnóstico Técnico y Seguridad:** Registrar eventos en el historial y en los archivos de log para identificar fallos de red, depurar errores de reproducción y prevenir abusos contra el sistema.

### Finalidades Secundarias
**Veylora no tiene finalidades secundarias.** No se realiza prospección comercial, elaboración de perfiles mercadotécnicos ni publicidad. **No se venden, no se alquilan, no se transfieren ni se ceden datos a anunciantes, plataformas publicitarias, intermediarios (*data brokers*) ni empresas de entrenamiento de modelos de inteligencia artificial.**

---

## 5. Infraestructura y Transferencias Técnicas de Datos

### 5.1 Aclaración Técnica sobre el Servidor Lavalink
**Lavalink v4 es un software autoalojado:** Se ejecuta localmente dentro de la misma infraestructura privada y red de contenedores Docker del Operador (`veylora-lavalink`). **No es un servicio operado por un tercero ni una plataforma externa.** Toda comunicación entre Veylora y Lavalink ocurre dentro del entorno privado del anfitrión y no constituye una transferencia de datos.

### 5.2 Destinatarios y Servicios Externos Involucrados
Para operar técnicamente, Veylora interactúa con las siguientes plataformas externas:

| Plataforma Externa | Función Operativa | Datos Técnicos Transmitidos | Datos que NUNCA se Transmiten |
| :--- | :--- | :--- | :--- |
| **Discord Inc.** | Pasarela Gateway, comandos slash y protocolo WebRTC/UDP. | Snowflake IDs de usuario, canal y servidor; opciones del comando; paquetes de audio salientes Opus. | Audio de micrófonos de los usuarios; mensajes de chat ajenos a comandos. |
| **YouTube / Google LLC** | Búsqueda y extracción de flujos de audio bajo demanda mediante Lavalink. | Dirección IP pública del anfitrión de Lavalink; términos de búsqueda; ID de video; credencial OAuth del bot si está configurada. | Identificador de usuario de Discord; ID del servidor de Discord; apodo del usuario. |
| **Spotify AB** | Consulta de metadatos públicos de pistas, álbumes y playlists. | Identificador del track/álbum/playlist; IP pública del anfitrión; credenciales de API del bot (si están configuradas). | Cuentas privadas de Spotify de los usuarios; IDs de Discord. |
| **SoundCloud Global Limited** | Búsqueda y streaming web alternativo (*fallback*). | Términos de búsqueda textual; IP pública del anfitrión; cabecera User-Agent técnica estándar. | Identidad o Snowflake ID del usuario de Discord. |
| **LRCLIB (`lrclib.net`)** | Consulta de letras musicales abiertas para `/lyrics`. | Título de la pista y nombre del artista para coincidencia textual en base de datos comunitaria. | Cualquier identificador de usuario o servidor de Discord. |
| **Servidor Remote Cipher (`cipher.kikkia.dev`)** | Descifrado técnico de firmas web de reproductores JavaScript de YouTube. | Cadenas técnicas de código web de YouTube para cálculo de firmas. | Ningún dato de usuario, servidor o canal de Discord. |

---

## 6. Mecanismos Reales de Conservación y Eliminación de Datos

En estricta correspondencia con el código fuente implementado:

1. **Listas de Reproducción Guardadas (`saved_playlists` y `saved_playlist_tracks`):**
   - Se conservan de manera permanente en la base de datos SQLite mientras el propio usuario no las elimine mediante el comando `/playlist delete nombre:<nombre>` o solicite su cancelación manual al Responsable.
2. **Configuraciones de Servidor (`guild_settings`):**
   - Se mantienen activas de forma indefinida mientras no sean sobreescritas mediante `/settings`.
   - *Nota técnica sobre la expulsión del bot:* Si Veylora es expulsado o retirado de un servidor de Discord, la fila de `guild_settings` **permanece almacenada** en la base de datos local para preservar los ajustes en caso de reinvitación futura, a menos que el Administrador solicite su purga manual al Responsable.
3. **Historial de Reproducción (`playback_history`):**
   - **El historial se conserva actualmente sin purga automática.** Las canciones reproducidas y el identificador del solicitante (`requester_id`) se acumulan indefinidamente en la base de datos local SQLite. El código actual no contiene rutinas programadas de depuración periódica ni borrado por antigüedad, por lo que los registros persisten hasta que el Responsable ejecute un mantenimiento manual o atienda una solicitud formal de cancelación de datos.
4. **Registros Técnicos (Logs):**
   - El archivo `veylora.log` se almacena de forma continua en el volumen de datos del bot hasta su depuración por el administrador del sistema. El archivo `lavalink.log` rota a los 50 MB con un límite de 7 archivos históricos.

---

## 7. Ejercicio de Derechos ARCO y Revocación del Consentimiento

Conforme a la **Ley Federal de Protección de Datos Personales en Posesión de los Particulares (publicada en el DOF el 20 de marzo de 2025)**, el titular de los datos personales (o su representante legal) goza de los derechos de **Acceso, Rectificación, Cancelación y Oposición (Derechos ARCO)**, así como del derecho a revocar su consentimiento:

### 7.1 Mecanismo de Autoservicio
- **Supresión de Listas Personales:** Todo usuario puede eliminar de forma autónoma, inmediata e irreversible cualquiera de sus listas guardadas mediante el comando `/playlist delete nombre:<nombre>`. Esta acción ejecuta un borrado en cascada en la base de datos (`ON DELETE CASCADE`), eliminando tanto el registro de la lista como todas sus pistas asociadas.

### 7.2 Eliminación General de Datos y Solicitudes ARCO
- **Aclaración indispensable:** El usuario no dispone de un comando automatizado para borrar la totalidad de sus datos del sistema. **La eliminación general de datos personales (listas de reproducción y purga/desvinculación de su `requester_id` en el historial de reproducción) requiere de una solicitud formal y de la intervención manual del Responsable en la base de datos SQLite.**

### 7.3 Procedimiento y Requisitos para el Ejercicio de Derechos ARCO
Para ejercer cualquiera de los derechos ARCO o revocar el consentimiento:

1. **Medio de Contacto:** Enviar un correo electrónico a la cuenta oficial: **iankarimvr@gmail.com**, indicando en el asunto "Solicitud de Derechos ARCO — Veylora".
2. **Requisitos de la Solicitud (Proporcionales y No Excesivos):**
   En estricto apego al principio de proporcionalidad y minimización de datos, **no se exigirá la entrega de documentos oficiales de identidad (como credenciales de elector, pasaportes o identificaciones gubernamentales) por defecto**. La solicitud deberá contener:
   - Nombre o seudónimo del titular y dirección de correo electrónico a la que se comunicará la respuesta a su solicitud (la cual será respondida desde `iankarimvr@gmail.com`).
   - Identificador numérico público de Discord (*Snowflake ID* de usuario o de servidor, según corresponda).
   - Mecanismo razonable de acreditación de control: Para evitar solicitudes fraudulentas sobre cuentas ajenas, el Responsable verificará únicamente lo estrictamente necesario para constatar el control legítimo de la cuenta de Discord correspondiente (por ejemplo, solicitando la confirmación de un código aleatorio enviado por mensaje directo en Discord o mediante una instrucción emitida desde la propia cuenta dentro del servidor de soporte).
   - Descripción clara y precisa de los datos personales respecto de los cuales se busca ejercer alguno de los derechos ARCO (por ejemplo: "solicito la cancelación de todos los registros de canciones asociados a mi User ID en el historial de reproducción").
   - Manifestación expresa del derecho que se ejerce (Acceso, Rectificación, Cancelación u Oposición).

### 7.4 Plazos Legales Estrictos conforme a la LFPDPPP (2025)
De conformidad con los artículos aplicables de la ley:

1. **Plazo para Comunicar la Determinación:** El Responsable comunicará al titular, en un plazo máximo de **veinte días hábiles** contados desde la fecha en que se recibió la solicitud, la determinación adoptada.
2. **Plazo para Hacer Efectiva la Solicitud Procedente:** Si la solicitud resulta procedente, se hará efectiva dentro de los **quince días hábiles** siguientes a la fecha en que se comunique la determinación adoptada al titular.
3. **Ampliación Legal de Plazos:** Los plazos anteriores podrán ser ampliados por una sola vez y por un periodo igual (es decir, hasta veinte días hábiles adicionales para comunicar la determinación y hasta quince días hábiles adicionales para su ejecución técnica), siempre y cuando las circunstancias del caso lo justifiquen fehacientemente (por ejemplo, ante volúmenes complejos de registros técnicos o requerimientos especiales de verificación), notificándose dicha prórroga y sus motivos al titular dentro del plazo original.

### 7.5 Autoridad Reguladora y Medios de Defensa
Si el titular considera que su derecho a la protección de datos personales ha sido lesionado por alguna conducta del Responsable, o si no recibe respuesta dentro de los plazos legales, podrá interponer el procedimiento correspondiente ante la **Secretaría Anticorrupción y Buen Gobierno** del Gobierno de México (autoridad federal facultada para supervisar la observancia de la LFPDPPP conforme al decreto publicado el 20 de marzo de 2025).

---

## 8. Medidas de Seguridad Técnicas y Organizativas

1. **Aislamiento en Contenedores:** Veylora opera dentro de entornos aislados mediante Docker Compose con permisos de acceso restringidos.
2. **Protección Anti-SSRF:** La capa de seguridad de red en [src/audio/seguridad.py](file:///c:/Users/oveji/OneDrive/Desktop/Veylora-DiscordBot/src/audio/seguridad.py) verifica y resuelve los nombres de dominio antes de cursar peticiones HTTP, bloqueando de manera sistemática interfaces de loopback, rangos de IP privadas, endpoints de metadatos en la nube y esquemas no permitidos (`file://`, `ftp://`).
3. **Filtro de Datos Sensibles en Registros:** Se implementa un filtro automático que enmascara credenciales, tokens y contraseñas antes de su escritura en disco.
4. **Resguardo de Credenciales:** Las variables críticas y tokens de acceso residen exclusivamente en variables de entorno locales (`.env`), excluidas del control de versiones mediante reglas estrictas en `.gitignore`.

---

## 9. Modificaciones al Aviso de Privacidad

El Responsable se reserva el derecho de actualizar el presente Aviso de Privacidad para adecuarlo a modificaciones en la legislación mexicana, nuevas directrices de la Secretaría Anticorrupción y Buen Gobierno, o cambios funcionales en Veylora. Cualquier cambio sustancial se reflejará con una nueva fecha de actualización al inicio de este documento y se notificará en el repositorio público oficial.

---

## 10. Canales de Contacto

Para cualquier duda, aclaración o solicitud relacionada con este Aviso de Privacidad y el tratamiento de sus datos personales:

- **Proyecto:** Veylora.
- **Responsable del Tratamiento:** [PENDIENTE: Nombre completo o Razón Social del Responsable]
- **Domicilio:** [PENDIENTE: Domicilio legal en los Estados Unidos Mexicanos]
- **Correo Electrónico de Contacto y Privacidad:** **iankarimvr@gmail.com**
- **Canal de Soporte Previsto:** [PENDIENTE: URL definitiva del repositorio público de GitHub una vez publicado]
