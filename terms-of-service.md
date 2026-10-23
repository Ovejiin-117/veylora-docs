# Condiciones del Servicio de Veylora (Terms of Service)

*Última actualización: [PENDIENTE: Fecha de entrada en vigor al momento de la publicación definitiva]*

---

## 1. Identificación y Descripción del Servicio

1. **Nombre del Proyecto:** Veylora.
2. **Distinción entre Nombre Público e Identidad Legal del Responsable:** El nombre público y marca funcional del bot de Discord es **Veylora**. La operación, administración y mantenimiento técnico del software están a cargo de **[PENDIENTE: Nombre completo o Razón Social del Titular/Desarrollador responsable]** (en adelante, "el Operador"), con país de referencia en los Estados Unidos Mexicanos (México).
3. **Domicilio del Responsable:** **[PENDIENTE: Domicilio o sede del responsable para efectos legales en México]**.
4. **Canal Oficial de Contacto:** Para consultas generales, soporte técnico o notificaciones de cualquier índole, el correo oficial es: **iankarimvr@gmail.com**.
5. **Canal de Soporte Previsto:** El canal público de soporte y seguimiento de incidencias será el repositorio público de GitHub del proyecto, el cual se encuentra en fase de preparación previa: **[PENDIENTE: URL definitiva del repositorio público de GitHub una vez publicado]**. No existen otros canales no verificados.
6. **Naturaleza del Software y Ausencia de Licencias Directas de Catálogo:**
   - Veylora es una aplicación de software modular diseñada para ejecutarse dentro del entorno de la plataforma Discord. Su función técnica consiste en conectar un reproductor de audio a canales de voz de Discord para gestionar colas de reproducción y transmitir audio saliente en formato digital bajo la petición expresa de los usuarios del servidor.
   - **Veylora no es una plataforma de distribución de contenidos, no comercializa música, no almacena archivos de audio protegidos en servidores propios con fines de radiodifusión ni posee licencias directas de catálogo discográfico o de ejecución pública.** La resolución y reproducción de pistas depende exclusivamente de la disponibilidad, legalidad y términos técnicos de las plataformas externas de origen desde las que se solicitan los flujos de audio.

---

## 2. Aceptación y Requisitos de Uso

1. **Aceptación Obligatoria:** Al invitar a Veylora a un servidor de Discord, interactuar con sus comandos de aplicación (comandos slash como `/play`, `/queue`, `/playlist`, etc.) o interactuar con sus componentes visuales (botones y menús), el usuario (en adelante, "el Usuario") o el administrador del servidor (en adelante, "el Administrador") acepta expresamente quedar sujeto a las presentes Condiciones del Servicio (en adelante, "las Condiciones").
2. **Requisitos de Edad y Capacidad:** El Usuario declara cumplir con la edad mínima requerida por los Términos de Servicio de Discord para su territorio (al menos 13 años o la edad legal superior exigida en su país de residencia para el consentimiento telemático).
3. **Subordinación y Cumplimiento de las Normas de Discord:** El uso de Veylora está estrictamente condicionado al cumplimiento ininterrumpido de las normativas de la plataforma Discord:
   - [Términos de Servicio de Discord](https://discord.com/terms).
   - [Directrices de la Comunidad de Discord](https://discord.com/guidelines).
   - [Términos del Desarrollador de Discord](https://discord.com/developers/docs/policies-and-agreements/developer-terms-of-service).  
   Cualquier uso que contravenga las directrices de Discord se considerará un incumplimiento directo de estas Condiciones.

---

## 3. Uso Permitido y Responsabilidad del Usuario

1. **Operación Bajo Demanda de la Comunidad:** Veylora opera exclusivamente bajo demanda. El Bot no emite audio de forma autónoma ni selecciona contenidos por decisión propia. Toda pista transmitida responde a una instrucción enviada por un usuario del servidor mediante comandos de texto o botones de control.
2. **Responsabilidad sobre Términos de Búsqueda, Enlaces y Archivos:**
   - Al introducir un texto de búsqueda, proporcionar un enlace (URL) o adjuntar un archivo de audio para su reproducción, el Usuario manifiesta que ostenta los derechos, autorizaciones, facultades o excepciones legítimas pertinentes según la legislación aplicable para solicitar la reproducción de dicho material en el canal de voz correspondiente.
   - El Usuario es el único responsable civil, administrativo o técnico ante los titulares de derechos o terceros por las instrucciones y contenidos que ordene procesar al Bot.
3. **Facultades y Responsabilidad de la Administración del Servidor:**
   - Los Administradores de cada servidor son responsables de vigilar el uso que sus miembros hacen del Bot.
   - Veylora proporciona herramientas técnicas de configuración mediante el comando `/settings` para mitigar usos no deseados:
     - Asignación de canal de texto exclusivo (`canal_musica`).
     - Asignación de rol de DJ (`rol_dj`) para restringir comandos de control (salto, detención, volumen).
     - Fijación del límite máximo de canciones en cola (`limite_cola`) y volumen base (`volumen_predeterminado`).

---

## 4. Conductas y Usos Prohibidos

Queda terminantemente prohibido utilizar Veylora para:

1. **Infracción de Propiedad Intelectual:** Solicitar, emitir o retransmitir material protegido por derechos de autor o marcas registradas en contravención de las leyes aplicables o de los términos de las plataformas de origen.
2. **Ataques a la Seguridad de Red e Infraestructura:**
   - Intentar o ejecutar ataques de *Server-Side Request Forgery* (SSRF), incluyendo intentos deliberados de dirigir peticiones hacia interfaces de red local (`127.0.0.1`, `localhost`, `0.0.0.0`), rangos de direcciones IP privadas (`10.0.0.0/8`, `172.16.0.0/12`, `192.168.0.0/16`), direcciones link-local (`169.254.0.0/16`) o endpoints de metadatos en la nube (`169.254.169.254`, `metadata.google.internal`).
   - Suministrar intencionadamente URLs fraudulentas, archivos con código malicioso o cargas útiles diseñadas para desbordar búferes o interrumpir la infraestructura del Bot, del servidor Lavalink o del anfitrión.
3. **Saturación y Denegación de Servicio (DoS):**
   - Ejecutar peticiones masivas automatizadas (*spam* de comandos, llamadas concurrentes mediante scripts no autorizados) que degraden la operatividad del Bot.
   - Inundar deliberadamente las colas de reproducción para agotar los recursos del sistema.
4. **Emisiones Lesivas o Ilícitas:** Reproducir o compartir audios que contengan amenazas, discursos de odio, incitación a delitos, pornografía infantil o cualquier material que vulnere el marco legal vigente o las políticas de Discord.
5. **Elusión de Controles:** Intentar vulnerar o manipular las restricciones de seguridad implementadas en el código fuente del Bot.

---

## 5. Plataformas, Servicios y Proveedores de Terceros

1. **Interacción con Servicios Externos:** Veylora se comunica técnicamente con diversas plataformas ajenas para resolver metadatos y obtener flujos de audio:
   - **Discord Inc.:** Para la entrega de comandos mediante Gateway y la transmisión de voz mediante protocolo WebRTC/UDP.
   - **YouTube / Google LLC:** Para búsquedas y transmisión de audio mediante componentes de decodificación en el servidor Lavalink.
   - **Spotify AB:** Para la consulta de metadatos públicos de pistas, álbumes y playlists (mediante credenciales oficiales de API o metadatos abiertos oEmbed). Veylora **no reproduce audio desde los servidores de Spotify**, sino que localiza equivalencias en plataformas compatibles.
   - **SoundCloud Global Limited:** Para búsqueda y reproducción de flujos de audio web compatibles, actuando también como respaldo automático (*fallback*) cuando YouTube restringe una pista.
   - **LRCLIB (`lrclib.net`):** Para la consulta de letras musicales abiertas mediante el comando `/lyrics`.
   - **Servidores de Descifrado Remoto (*Remote Cipher*):** Herramientas auxiliares para el cálculo de firmas web de reproductores (ej. `cipher.kikkia.dev`).
2. **Términos de Terceros:** Cada uno de estos servicios está gobernado por sus propios términos de uso y políticas de privacidad, los cuales el Usuario debe respetar.
3. **Ausencia de Afiliación:** Veylora es un desarrollo independiente. **No existe afiliación, patrocinio, aval comercial ni vínculo contractual con Discord, Google, YouTube, Spotify, SoundCloud ni LRCLIB**.
4. **Disponibilidad de Contenidos Externos:** El Operador no garantiza la disponibilidad continua ni la inalterabilidad de los enlaces o flujos provistos por plataformas externas. Si una plataforma bloquea, restringe geográficamente o elimina un contenido, Veylora no podrá reproducirlo.

---

## 6. Procedimiento ante Infracciones de Derechos de Autor (Avisos de Retirada)

El Operador respeta los derechos de propiedad intelectual de creadores y titulares legítimos. Ante reportes fundados de presuntas infracciones facilitadas mediante el uso del Bot:

1. **Canal de Recepción:** Las notificaciones deben remitirse por correo electrónico a: **iankarimvr@gmail.com**.
2. **Información Mínima Requerida:**
   - Identificación de la obra protegida supuestamente infringida.
   - Identificación precisa del enlace (URL), identificador o contenido específico objeto de reclamo.
   - Datos de contacto del titular de los derechos o de su representante legal debidamente acreditado (nombre completo, correo electrónico y cargo o representación).
   - Declaración bajo protesta de decir verdad de que el uso reclamado no está autorizado por el titular, su representante o la ley.
   - Declaración de que la información contenida en la notificación es veraz y de que el firmante actúa con facultades suficientes.
3. **Acciones Técnicas:** Al verificar la validez de un aviso, el Operador podrá incorporar bloqueos en la capa de seguridad del resolvedor de Veylora para impedir la carga técnica de los enlaces o identificadores señalados.

---

## 7. Disponibilidad, Mantenimiento y Modificaciones del Servicio

1. **Prestación "Tal Cual" (*As Is*):** Veylora se suministra bajo la modalidad *"as is"* (tal cual) y *"as available"* (según disponibilidad). No se otorga garantía de funcionamiento ininterrumpido, puntual, libre de errores o exento de fallos de red.
2. **Interrupciones Técnicas:** El Servicio podrá suspenderse temporalmente por mantenimiento programado, actualizaciones de software, incidentes en la infraestructura de alojamiento, fallos en la API de Discord o medidas de mitigación antibot aplicadas por proveedores de audio externos.
3. **Modificaciones del Servicio:** El Operador se reserva el derecho de modificar, actualizar, restringir o descontinuar comandos, fuentes de audio o la totalidad del Bot en cualquier momento, sin que ello genere obligación indemnizatoria alguna.

---

## 8. Suspensión, Restricción y Terminación

1. **Facultades del Operador:** El Operador podrá restringir, suspender temporalmente o bloquear de forma definitiva el acceso a Veylora a usuarios, roles o servidores completos que incumplan estas Condiciones o incurran en conductas abusivas, mediante mecanismos de lista negra (*blacklist*) o desconexión del servidor.
2. **Terminación por el Usuario:** El Usuario o Administrador puede terminar el uso del Servicio en cualquier momento expulsando a Veylora de su servidor o dejando de invocar sus comandos.

---

## 9. Limitación Razonable de Responsabilidad

1. **Alcance de la Exclusión:** En la medida máxima permitida por la legislación aplicable en los Estados Unidos Mexicanos:
   - El Operador no será responsable por daños indirectos, incidentales, punitivos, especiales, lucro cesante, pérdida de datos, interrupción de actividades comunitarias o daños derivados del uso o de la imposibilidad de uso de Veylora.
   - El Operador no asume responsabilidad civil ni de ninguna otra índole por las acciones, audios, enlaces o archivos que los usuarios decidan transmitir en los canales de Discord mediante el uso del Bot.
2. **Respeto a Derechos Irrenunciables:** Nada en estas Condiciones pretende excluir ni limitar responsabilidades legales que, por disposición expresa e imperativa de la ley (incluyendo normativas de protección a consumidores o responsabilidades por dolo o culpa grave donde no resulte renunciable), no puedan ser legalmente excluidas.

---

## 10. Modificaciones a las Condiciones

1. El Operador podrá actualizar las presentes Condiciones para reflejar modificaciones técnicas en el software, cambios en las directrices de Discord o reformas legales aplicables.
2. Toda modificación sustancial será reflejada en este documento, actualizando la fecha de revisión en el encabezado.
3. La continuidad en el uso de Veylora tras la entrada en vigor de nuevas condiciones implica su aceptación. De no estar de acuerdo, el Usuario deberá cesar el uso del Bot y retirarlo de su servidor.

---

## 11. Legislación Aplicable y Jurisdicción

1. **País de Referencia:** Las presentes Condiciones se regirán e interpretarán de conformidad con las leyes vigentes en los **Estados Unidos Mexicanos (México)**, salvaguardando las disposiciones de orden público y derechos irrenunciables reconocidos al consumidor en su lugar de residencia.
2. **Determinación de Tribunales y Fuero Judicial:** **[PENDIENTE: Confirmación del tribunal, fuero judicial o mecanismo alternativo de resolución de controversias específico, una vez validada la procedencia legal de dicha estipulación territorial]**. Mientras dicha cláusula no sea ratificada, la competencia se determinará con arreglo a las reglas generales de competencia procesal aplicables.

---

## 12. Contacto

Para cualquier duda, solicitud o notificación relativa a estas Condiciones del Servicio:

- **Proyecto:** Veylora.
- **Responsable del Proyecto:** [PENDIENTE: Nombre completo o Razón Social del Responsable]
- **Correo Electrónico Oficial:** **iankarimvr@gmail.com**
- **Repositorio Público de Soporte:** [PENDIENTE: URL definitiva del repositorio público de GitHub una vez publicado]
