## 4. Implementación y Despliegue

<h3 id="IBMWatson"></h3>

### I. IBM Watson Assistant

<p>Watson Assistant es un servicio de IBM Cloud basado en la inteligencia artificial, el cual
permite crear, entrenar e implementar interacciones conversacionales en cualquier
aplicación, dispositivo o canal. Busca una respuesta de una base de conocimiento,
cuándo pedir aclaraciones y cuándo transferir usuarios a un agente humano con base a
un entrenamiento. Watson Assistant se puede implementar en cualquier entorno en la
nube o local, lo que significa que la IA más inteligente finalmente está disponible en
cualquier lugar donde la necesite.</p>

<h4 id="funcionamiento"><b>A. Funcionamiento</b></h4>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/FuncionamientoWatson.png" alt="Funcionamiento Watson Assistant" align="center" width="700px">
<p id="imagen2" style="text-align:center;font-size:0.8rem"><i>Imagen 2 Funcionamiento Watson Assistant</i></p>

<ol>
    <li>El cliente/usuario interactúa desde WhatsApp con el asistente por medio del punto de integración con NodeJS, el cual está integrado con 360 Dialog para acceder al canal de comunicación WhatsApp y una base de datos MongoDB.</li>
    <li>Nuestro asistente recibe los datos de entrada que proporciona nuestro usuario y los dirige a la sección correspondiente (dialog skill).</li>
    <li>La sección correspondiente interpreta los datos y luego los conecta a los diálogos de respuestas correspondientes.</li>
    <li>Existe una posibilidad en la cual no se tenga una respuesta para algún interrogante, y para este tipo casos, se dirigen dichas preguntas a un área comúnmente llamada “search skill”, la cual encuentra respuestas relevantes con base a la configuración y conocimiento que le hayamos aportado a nuestro bot.</li>
</ol>

<h4 id="crearasistente"><b>B. Crear un Asistente Watson Assistant</b></h4>

<p>El servicio se crea desde la consola de IBM Cloud buscando el servicio en el catálogo, el plan Lite permite un uso gratuito con algunas limitaciones en el servicio, al crear el servicio se debe crear un skill el cual contendrá los componentes de Intenciones, Entidades y Diálogo.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/Catalogo.png" alt="Cátalogo de IBM - Watson Assistant" align="center" width="700px">
<p id="imagen3" style="text-align:center;font-size:0.8rem"><i>Imagen 3 Cátalogo de IBM - Watson Assistant</i></p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/CrearServicioWatson.png" alt="Crear Servicio de Watson Assistant" align="center" width="700px">
<p id="imagen4" style="text-align:center;font-size:0.8rem"><i>Imagen 4 Crear Servicio de Watson Assistant</i></p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/PaginaPrincipalWatson.png" alt="Página Principal de Watson Assistant" align="center" width="700px">
<p id="imagen5" style="text-align:center;font-size:0.8rem"><i>Imagen 5 Página Principal de Watson Assistant</i></p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/CrearAsistenteWatson.png" alt="Crear Asistente en Watson Assistant" align="center" width="700px">
<p id="imagen6" style="text-align:center;font-size:0.8rem"><i>Imagen 6 Crear Asistente en Watson Assistant</i></p>

<p>Se puede crear el Dialog Skill con base a un ejemplo que se ofrece o subir un archivo .json con un Dialog Skill ya configurado.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/CrearDialogo.png" alt="Crear Dialogo en Watson Assistant" align="center" width="700px">
<p id="imagen7" style="text-align:center;font-size:0.8rem"><i>Imagen 7 Crear Dialogo en Watson Assistant</i></p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/PaginaAsistenteChatbot.png" alt="Página Principal Asistente Chatbot ECCI" align="center" width="700px">
<p id="imagen8" style="text-align:center;font-size:0.8rem"><i>Imagen 8 Página Principal Asistente Chatbot ECCI</i></p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/AsistenteUECCIWatson.png" alt="Asistente UECCI en Watson Assistant" align="center" width="700px">
<p id="imagen9" style="text-align:center;font-size:0.8rem"><i>Imagen 9 Asistente UECCI en Watson Assistant</i></p>

<h4 id="intenciones"><b>C. Intenciones</b></h4>

<p>Las intenciones en Watson Assistant se activan a través de un concepto conocido como confianza. Watson Assistant no solo crea un modelo para devolver cuál es la intención correcta. De hecho, crea un modelo diferente para cada intento. Cuando un usuario hace una pregunta, esa expresión se envía a cada modelo de intención. Cada uno de esos modelos de intención devuelve una puntuación de confianza, que indica qué tan "seguro" es el modelo de que la expresión se ajusta a esa intención. Cuando verifica si # < intent > se cumple la condición, eso esencialmente solo agrega esas puntuaciones y verifica si la intención de puntuación más alta es la que está verificando. Para capturar múltiples intenciones de un solo enunciado de usuario, vamos a seguir 3 pasos.</p>

<ol>
    <li>Definir un umbral de confianza: definiremos una variable constante para ajustar la sensibilidad para capturar múltiples intenciones. Establecer esto muy bajo podría llevar a capturar demasiados intentos. A la inversa, establecerlo demasiado alto podría resultar en que no se capturen las intenciones en la expresión del usuario.</li>
    <li>Capturar intenciones que superen el umbral de confianza: en este paso, veremos cómo puede capturar las intenciones utilizando el umbral definido previamente y luego guardarlas para usarlas más adelante.</li>
    <li>Iterar a través de la lista de intenciones: utilizando algunos trucos de diálogo, veremos cómo podemos construir un bucle en Watson Assistant para iterar a través de cada una de las intenciones capturadas previamente una por una.</li>
</ol>

<p>Primero, necesitamos definir una intención para agregar una tarea, agregando una serie de ejemplos de cómo las personas podrían agregar una tarea.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/Intenciones.png" alt="Intenciones Chat UECCI" align="center" width="700px">
<p id="imagen10" style="text-align:center;font-size:0.8rem"><i>Imagen 10 Intenciones Chat UECCI</i></p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/EjemploIntencion.png" alt="Ejemplo de Intención: Aspirante" align="center" width="700px">
<p id="imagen11" style="text-align:center;font-size:0.8rem"><i>Imagen 11 Ejemplo de Intención: Aspirante</i></p>

<h4 id="entidades"><b>D. Entidades</b></h4>

<p>Una entidad representa un término o un objeto que da contexto a una acción. Las entidades representan información en la entrada de usuario que es relevante para la finalidad de la intención. Los nombres de las entidades van precedidos del símbolo @entidad. Una entidad puede tener varios valores, y a cada uno de estos valores se le configura sinónimos, los cuales son las diferentes maneras en que puede ser mencionado ese valor de la entidad.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/Entidades.png" alt="Entidades Chat UECCI" align="center" width="700px">
<p id="imagen12" style="text-align:center;font-size:0.8rem"><i>Imagen 12 Entidades Chat UECCI</i></p>

<h4 id="dialogo"><b>E. Diálogo</b></h4>

<p>La estructura de diálogo está basada en nodos, es decir tiene forma de árbol. Cuando un mensaje es analizado por Watson Assistant, dicho mensaje recorre cada uno de estos nodos en el orden en el que han sido definidos, para encontrar una intención y una entidad que tengan relación con dicho mensaje. Cada nodo del diálogo contiene, como mínimo, una condición; y puede contener una respuesta o textos o varios nodos hijos que de igual forma deben contener una condición y una respuesta. El servicio procesa el diálogo desde el primer nodo en el árbol hasta el último. A medida que recorre por el árbol, si el servicio encuentra una condición que se cumple, activa dicho nodo. Luego se mueve por el nodo que ha sido activado para comparar la entrada del usuario con las condiciones de los nodos hijos, desde el primer nodo hijo hasta el último.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/Dialogo.png" alt="Diálogo Chat UECCI" align="center" width="700px">
<p id="imagen13" style="text-align:center;font-size:0.8rem"><i>Imagen 13 Diálogo Chat UECCI</i></p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/Nodo.png" alt="Nodo Menú en Diálogo Chat UECCI" align="center" width="700px">
<p id="imagen14" style="text-align:center;font-size:0.8rem"><i>Imagen 14 Nodo Menú en Diálogo Chat UECCI</i></p>

<p style="margin-left: 3rem"><b>Nota: </b>Mensaje no comprendido (anything else) Este nodo se implementó como un respaldo si Watson Assistant no comprende el mensaje, y se le solicita al usuario que repita la pregunta de otra manera.</p>

<h3 id="IBMObject"><b>II. IBM Object Storage</b></h3>

<p>El componente de Object Storage es un servicio de almacenamiento en la nube que permite subir archivos estáticos para ser accedidos desde internet de forma rápida y segura. Es parte de la suite de servicios de IBM, y está disponible desde el plan Lite.</p>

<a href="https://www.ibm.com/co-es/cloud/object-storage">https://www.ibm.com/co-es/cloud/object-storage</a>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/CloudObject.png" alt="Cloud Object Storage" align="center" width="700px">
<p id="imagen15" style="text-align:center;font-size:0.8rem"><i>Imagen 15 Cloud Object Storage</i></p>

<p>El servicio se crea desde la consola de IBM Cloud, el plan Lite permite un uso gratuito con algunas limitaciones en el servicio, se debe definir igualmente un nombre para el servicio Object Storage que se está creando.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/CreacionObject.png" alt="Creación de Servicio Object Storage" align="center" width="700px">
<p id="imagen16" style="text-align:center;font-size:0.8rem"><i>Imagen 16 Creación de Servicio Object Storage</i></p>

<p>Luego de haber creado el servicio, debe crearse un bucket o depósito, donde se almacenarán los archivos en el servicio. Adicionalmente, se deben definir las opciones de resiliencia y ubicación y tipo de almacenamiento para el depósito que se creará, como se ve en la Imagen 17.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/ConfiguracionIBMObject.png" alt="Configuración IBM Cloud Object Storage" align="center" width="700px">
<p id="imagen17" style="text-align:center;font-size:0.8rem"><i>Imagen 17 Configuración IBM Cloud Object Storage</i></p>

<b>Importante:</b>

<ul>
    <li>La separación de archivos dentro de un servicio de almacenamiento de objetos no estructurados se realiza mediante buckets o depósitos.</li>
    <li>El nombre del depósito debe cumplir con unas reglas básicas detalladas en la imagen, entre ellas, debe ser único en todo el ecosistema de IBM Cloud Object Storage. Esto es, no puede haber dos buckets con el mismo nombre en todos los servidores de IBM, ni siquiera en cuentas distintas, debe ser único.</li>
</ul>

<p>Luego de crear el depósito podemos visualizarlo desde la interfaz web de IBM Cloud, y desde allí interactuar con él para subir y eliminar archivos, así como modificar las configuraciones del depósito y del servicio para su conectividad.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/ListadoArchivosObject.png" alt="Listado de Archivos en Cloud Object Storage" align="center" width="700px">
<p id="imagen18" style="text-align:center;font-size:0.8rem"><i>Imagen 18 Listado de Archivos en Cloud Object Storage</i></p>

<p>Para este caso en particular es necesario que el depósito tenga acceso público, para que cualquier persona pueda acceder a los recursos alojados en él desde su chat de Whatsapp sin necesidad de autenticación. Para realizar esto, se debe crear una política de acceso público desde las políticas de acceso del depósito, como se ve en la siguiente Imagen 19.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/PoliticasAcceso.png" alt="Políticas de Acceso en Cloud Object Storage" align="center" width="700px">
<p id="imagen19" style="text-align:center;font-size:0.8rem"><i>Imagen 19 Políticas de Acceso en Cloud Object Storage</i></p>

<p style="margin-left:2rem">Por último, los archivos subidos al bucket podrán visualizarse de la siguiente forma:</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/DetalleCloud.png" alt="Detalle de Archivo en Cloud Object Storage" align="center" width="700px">
<p id="imagen20" style="text-align:center;font-size:0.8rem"><i>Imagen 20 Detalle de Archivo en Cloud Object Storage</i></p>

<p>Y contarán con un URL público de objeto, el cual es la URL pública para acceder a ese objeto almacenado en la nube de IBM.</p>


<h3 id="360dialog"><b>III. 360 Dialog</b></h3>

<p>360 Dialog es una plataforma de mensajería instantánea que brinda un API de conexión con Whatsapp, la cuál permite una conexión simplificada y acorde a las referencias de la documentación del API de Whatsapp, así como una actualización de versiones del API de Whatsapp sin demora. La plataforma principal de 360 Dialog se encuentra alojada en <a href="https://www.360dialog.com">https://www.360dialog.com</a>.</p>

<p>El menú de la plataforma permite visualizar la página principal de la consola, un listado de cuentas de whatsapp activas, métricas de uso y facturación, conexión de integraciones y soporte. Adicionalmente en la sección de perfil hay otras opciones disponibles como configuración de la cuenta y la organización o opciones de facturación y cierre de sesión.</p>

<p style="text-align:center"><image 
src="/chatbot_ecci_documentation/Img/PaginaPrincipal360Dialog.png" alt="Página Principal 360 Dialog" align="center" width="300px">
<p id="imagen21" style="text-align:center;font-size:0.8rem"><i>Imagen 21 Página Principal de 360 Dialog</i></p>

<p>El Dashboard muestra un resumen del estado de las cuentas de Whatsapp activas en la plataforma, así como una sección de ayuda y documentación de apoyo.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/Dashboard360Dialog.png" alt="Dashboard de 360 Dialog" align="center" width="500px">
<p id="imagen22" style="text-align:center;font-size:0.8rem"><i>Imagen 22 Dashboard de 360 Dialog</i></p>

<p>La sección de cuentas de Whatsapp permite la gestión y administración de las cuentas de Whatsapp enlazadas con 360 Dialog, la generación de API Keys para la conexión vía API con la plataforma y la gestión de plantillas de mensajes.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/SeccionWhatsapp360Dialog.png" alt="Sección de Whatsapp en 360 Dialog" align="center" width="500px">
<p id="imagen23" style="text-align:center;font-size:0.8rem"><i>Imagen 23 Sección de Whatsapp en 360 Dialog</i></p>

<p>Por su parte, en la sección de métricas y facturación se puede visualizar un resumen del balance y saldo de los números de Whatsapp. A la fecha de esta documentación, 360 Dialog cuenta con un modelo de facturación basado en saldos prepagados con auto renovación para disponibilidad automática, en la página también se puede visualizar un resumen general de uso del servicio de mensajería y una subsección con las opciones de auto renovación.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/SeccionMetricas360Dialog.png" alt="Sección de Métricas en 360 Dialog" align="center" width="500px">
<p id="imagen24" style="text-align:center;font-size:0.8rem"><i>Imagen 24 Sección de Métricas en 360 Dialog</i></p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/SeccionMetricasFacturacion360Dialog.png" alt="Sección de Métricas en 360 Dialog" align="center" width="500px">
<p id="imagen25" style="text-align:center;font-size:0.8rem"><i>Imagen 25 Sección de Métricas y Facturación en 360 Dialog</i></p>

<p>Por último, en la sección del perfil, en las opciones de facturación se puede encontrar el detalle de los datos de facturación y el historial de cobros realizados por la plataforma.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/SeccionPerfil360Dialog.png" alt="Sección de Perfil en 360 Dialog" align="center" width="500px">
<p id="imagen26" style="text-align:center;font-size:0.8rem"><i>Imagen 26 Sección de Perfil en 360 Dialog</i></p>

<p>A diferencia de otros proveedores, 360 Dialog no cobra tarifas por mensajería, solo maneja un cobro mensual por el alojamiento y conexión de cada número o cuenta de Whatsapp vinculada a la plataforma. A la fecha de esta documentación, el costo por cada número activo en la plataforma es de 49 EUR mensuales. Los costos de mensajería son directamente los dispuestos por Meta para el API empresarial de Whatsapp. Para mayor información acerca de los precios de cada servicio: </p>

<a href="https://www.360dialog.com/whatsapp-business-api#pricing">https://www.360dialog.com/whatsapp-business-api#pricing</a>
<a href="https://business.whatsapp.com/products/platform-pricing">https://business.whatsapp.com/products/platform-pricing</a>

<h3 id="meta"><b>IV. Meta Business Platform</b></h3>

<p>A mediados del 2022, Meta abrió la posibilidad para que las empresas puedan conectarse directamente a su API de servicios de Whatsapp, lo que permite la integración directa sin intermediarios para el uso de cuentas empresariales a través del API de Meta para Whatsapp. </p>

<p>La página principal del servicio está disponible en:</p>

<a href="https://business.whatsapp.com/products/business-platform">https://business.whatsapp.com/products/business-platform</a>

<p><b>NOTA:</b> Para el uso del servicio es necesario contar con una cuenta empresarial de Facebook (<a href="https://business.facebook.com">https://business.facebook.com</a>) correctamente verificada, así como una cuenta enlazada con la plataforma de desarrolladores de Facebook (<a href="https://developers.facebook.com">https://developers.facebook.com</a>). </p>

<p>En la plataforma de desarrolladores se debe crear una aplicación de tipo empresarial para habilitar el servicio de Whatsapp, como se muestra en la imágen.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/InformacionBasica.png" alt="Plataforma de Desarrolladores" align="center" width="500px">
<p id="imagen27" style="text-align:center;font-size:0.8rem"><i>Imagen 27 Plataforma de Desarrolladores</i></p>

<p>A continuación, se debe indicar un nombre para la aplicación, un correo de contacto y una cuenta empresarial para conectar la aplicación.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/PlataformaDesarrolladores.png" alt="Seleccionar Tipo de Aplicación" align="center" width="500px">
<p id="imagen28" style="text-align:center;font-size:0.8rem"><i>Imagen 28 Seleccionar Tipo de Aplicación</i></p>

<p>Una vez creada la aplicación es posible visualizar una lista de productos o servicios disponibles en Meta para la aplicación, para conectar el servicio de Whatsapp o Messenger deben configurarse los correspondientes servicios.</p>

<p style="text-align:center"><image
    src="/chatbot_ecci_documentation/Img/VisualizacionServiciosMeta.png" alt="Visualización Servicios de Meta" align="center" width="500px">
<p id="imagen29" style="text-align:center;font-size:0.8rem"><i>Imagen 29 Visualización Servicios de Meta</i></p>

<p>Cada servicio se configura a través de Webhooks, por lo que al activar alguno de ellos se añadirá automáticamente el servicio de Webhooks también.</p>

<p>Una vez configurados los servicios, se mostrarán las secciones correspondientes en el menú lateral de la plataforma, para configurar el servicio de messenger debe configurarse la conexión con una página de Facebook, la cuenta de desarrollo de la aplicación debe contar con los permisos necesarios de administración en la página a conectar para que el proceso sea exitoso.</p>

<p>Por su parte, se debe configurar un Webhook para escuchar las peticiones del API de Facebook para messenger, así como los eventos a ser escuchados por el webhook. Otras opciones o características no son usadas actualmente.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/ConfiguracionWeebhook.png" alt="Configuración Weebhook para Peticiones de Facebook" align="center" width="500px">
<p id="imagen30" style="text-align:center;font-size:0.8rem"><i>Imagen 30 Configuración Weebhook para Peticiones de Facebook</i></p>

<p>Para el servicio de Whatsapp también debe configurarse un webhook para conectar el servicio API de Whatsapp.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/ConexionWeebhookWhatsapp.png" alt="Configuración Weebhook para Peticiones de Whatsapp" align="center" width="500px">
<p id="imagen31" style="text-align:center;font-size:0.8rem"><i>Imagen 31 Configuración Weebhook para Peticiones de Whatsapp</i></p>

<p>Para poder usar el servicio es necesario conectar una cuenta de Whatsapp Business. Desde la plataforma empresarial de facebook, en la sección de cuentas de Whatsapp se puede realizar la gestión y administración de cuentas de Whatsapp conectadas a una cuenta empresarial.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/AdministracionServiciosWhatsapp.png" alt="Conexión Cuenta Whatsapp desde Plataforma Empresarial de Facebook" align="center" width="500px">
<p id="imagen32" style="text-align:center;font-size:0.8rem"><i>Imagen 32 Conexión Cuenta Whatsapp desde Plataforma Empresarial de Facebook</i></p>

<p>La opción de “Administración de Whatsapp” permite ingresar a la plataforma de administración de Whatsapp de Meta. La cual es la plataforma principal de gestión del servicio de Whatsapp de Meta.</p>

<h3 id="plataformameta"><b>V. Plataforma de Administración de Meta para Whatsapp </b></h3>

<p>La plataforma de administración de Meta para Whatsapp brinda una gestión centralizada del servicio de mensajería Whatsapp desde Meta, en ella se pueden visualizar un listado resumen de las cuentas de Whatsapp activas asociadas a una cuenta empresarial específica, así como un conjunto de opciones específicas para cada cuenta empresarial vinculada, como métricas, gestión de plantillas de mensajes, números de teléfono asociados a la cuenta de Whatsapp y catálogo de productos.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/PlataformaAdministracionMeta.png" alt="Plataforma de Administración de Meta" align="center" width="500px">
<p id="imagen33" style="text-align:center;font-size:0.8rem"><i>Imagen 33 Plataforma de Administración de Meta</i></p>

<p>Como se muestra en la imágen anterior(#), la sección de Descripción muestra un resumen del uso de las cuentas de Whatsapp activas, así como un resumen de costos aproximados y conversaciones.</p>

<p>La sección de números de teléfono muestra el listado de números de teléfono asociados con una cuenta específica, permite gestionar y configurar los números de teléfono y perfiles asociados a cada uno en Whatsapp.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/SeccionNumerosTelefono.png" alt="Sección de los Números de Teléfono" align="center" width="500px">
<p id="imagen34" style="text-align:center;font-size:0.8rem"><i>Imagen 34 Sección de los Números de Teléfono</i></p>

<p>Dentro de la configuración de cada número se pueden encontrar opciones adicionales como métricas específicas y detalles del nivel de cobertura y calidad del número, configurar el perfil de Whatsapp, la verificación en dos pasos y enlaces de mensajes.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/MetricasNumerosTelefono.png" alt="Sección de Métricas Específicas y Detalles a Nivel de Cobertura" align="center" width="500px">
<p id="imagen35" style="text-align:center;font-size:0.8rem"><i>Imagen 35 Sección de Métricas Específicas y Detalles a Nivel de Cobertura</i></p>

<p>Por su parte, la sección de plantillas de mensajes del menú lateral permite una administración directa de las plantillas de mensajes y su solicitud de aprobación directamente con Meta, muestra un listado de las plantillas creadas y su estado, así como los idiomas de cada plantilla.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/PlantillasMensajes.png" alt="Plantillas de Mensajes" align="center" width="500px">
<p id="imagen36" style="text-align:center;font-size:0.8rem"><i>Imagen 36 Plantillas de Mensajes.</i></p>

<p>El detalle de cada plantilla muestra los detalles de la plantilla como el texto, encabezado o botones si los hay, y una previsualización de la plantilla resultante en Whatsapp.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/DetallesPlantilla.png" alt="Detalles de las Plantillas de Mensajes" align="center" width="500px">
<p id="imagen37" style="text-align:center;font-size:0.8rem"><i>Imagen 37 Detalles de las Plantillas de Mensajes.</i></p>

<h3 id="mongodb"><b>VI. MongoDB</b></h3>

<p>MongoDB es una base de datos orientada a documentos. Esto quiere decir que en lugar de guardar los datos en registros, guarda los datos en documentos. Estos documentos son almacenados en BSON, que es una representación binaria de JSON. Una de las diferencias más importantes con respecto a las bases de datos relacionales, es que no es necesario seguir un esquema. Los documentos de una misma colección - concepto similar a una tabla de una base de datos relacional, con la diferencia que pueden tener esquemas diferentes.</p>

<h4 id="ingresoplataforma"><b>A.Ingreso a la plataforma</b></h4>

<p>Para crear una base de datos MongoDB se accede al link <a href="https://account.mongodb.com/account/login">https://account.mongodb.com/account/login</a> con una cuenta ya creada.</p>
    
<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/CreacionCuentaMongo.png" alt="Creación de Cuenta en MongoDB" align="center" width="500px">
<p id="imagen38" style="text-align:center;font-size:0.8rem"><i>Imagen 38 Creación de Cuenta en MongoDB</i></p>
    
<p>Ingresa con usuario y contraseña.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/InicioSesionMongo.png" alt="Inicio de Sesión MongoDB" align="center" width="600px">
<p id="imagen39" style="text-align:center;font-size:0.8rem"><i>Imagen 39 Inicio de Sesión MongoDB</i></p>

<p>Una vez dentro, se crea un cluster. Actualmente se usa el gratuito, el cual proporciona creación de base de datos con un límite de 512MB.</p>
    
<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/ConfiguracionClusterMongo.png" alt="Configuración de Clúster en MongoDB" align="center" width="700px">
<p id="imagen40" style="text-align:center;font-size:0.8rem"><i>Imagen 40 Configuración de Clúster en MongoDB</i></p>
    
<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/InformacionClusterMongo.png" alt="Información de Clúster en MongoDB" align="center" width="700px">
<p id="imagen41" style="text-align:center;font-size:0.8rem"><i>Imagen 41 Información de Clúster en MongoDB</i></p>
    
<p>Es posible ver la información de conectividad con NodeJS, donde se puede copiar y pegar en el servidor de NodeJS.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/ConexionBaseMongo.png" alt="Conexión a Base de Datos MongoDB" align="center" width="700px">
<p id="imagen42" style="text-align:center;font-size:0.8rem"><i>Imagen 42 Conexión a Base de Datos MongoDB</i></p>
   
<p>También se requiere un usuario y contraseña, para administrar los usuarios de las bases de datos, se debe ir a Database Access.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/InformacionUsuariosMongo.png" alt="Información de Usuarios en MongoDB" align="center" width="700px">
<p id="imagen43" style="text-align:center;font-size:0.8rem"><i>Imagen 43 Información de Usuarios en MongoDB</i></p>

<p>Es posible crear la base de datos con el nombre que se requiera.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/CrearBaseMongo.png" alt="Crear Base de Datos en MongoDB" align="center" width="700px">
<p id="imagen44" style="text-align:center;font-size:0.8rem"><i>Imagen 44 Crear Base de Datos MongoDB</i></p>

<p>y sus respectivas colecciones:</p>
    
<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/ListaColeccionesMongo.png" alt="Lista de Colecciones en MongoDB" align="center" width="700px">
<p id="imagen45" style="text-align:center;font-size:0.8rem"><i>Imagen 45 Lista de Colecciones en MongoDB</i></p>
    
<p>A continuación, se detallan las distintas colecciones disponibles en el proyecto chatbot:</p>

<ul type="disc">
    <li><b>agents:</b> Almacena la información de los agentes.</li>
    <li><b>campus:</b> Guarda las consultas realizadas por sede.</li>
    <li><b>candidates:</b> Almacena la información de los aspirantes.</li>
    <li><b>categories:</b> Registra las consultas de los usuarios cuando acceden a una categoría específica del menú principa</li>
    <li><b>chatsbyacademicprogram:</b> Guarda las consultas por programa académico.</li>
    <li><b>chatsbyagent:</b> Guarda los chats atendidos por cada agente.</li>
    <li><b>chatsbybot:</b> Guarda los chats atendidos exclusivamente por el bot.</li>
    <li><b>competences:</b> Guarda el nombre de los programas académicos que se encuentran en la universidad.</li>
    <li><b>login:</b> Guarda los datos de usuario y contraseña de acceso para interfaz web.</li>
    <li><b>messages:</b> Registra la interacción de mensajes de los usuarios con el bot.</li>
    <li><b>messagesagents:</b> Registra la interacción de mensajes de los usuarios con agentes.</li>
    <li><b>othermessages:</b> Almacena los mensajes que el bot no comprendió.</li>
    <li><b>requestsbysection:</b> Registra las consultas realizadas por sección dentro de cada categoría del menú principal.</li>
    <li><b>sandbox_dialog: </b> Almacena los registros de números de Whatsapp y API Keys de conexión al sandbox de 360 Dialog para cada número.</li>
    <li><b>satisfaction:</b> Registra las respuestas de satisfacción de los usuarios.</li>
    <li><b>sede:</b> Guarda el registro de consultas de cada número a una sede específica en el chatbot.</li>
    <li><b>senttemplates</b> Almacena el registro de mensajes plantilla enviados en campañas masivas y el estado de los mismos.</li>
    <li><b>servicequalification:</b> Registra las respuestas de calificación del servicio por parte de los usuarios.</li>
    <li><b>sessions:</b> Guarda las sesiones activas de los usuarios de Watson Assistant y el tiempo que llevan en sesión.</li>
    <li><b>sessionsagents:</b> Guarda las sesiones activas de los agentes con los usuarios.</li>
    <li><b>tags:</b> Almacena las etiquetas de aspirante nuevo u homologado.</li>
    <li><b>templatesmessages:</b> Almacena los mensajes plantillas aprobados disponibles para envío masivo desde la interfaz web.</li>
    <li><b>tickets:</b> Guarda el registro de tickets creados en el chatbot.</li>
    <li><b>unassignedTickets:</b> Guarda el registro de tickets no asignados a agentes debido a la no disponibilidad de agentes para el programa consultado al momento de la consulta.</li>
    <li><b>users:</b> Guarda la información de los usuarios.</li>
</ul>

<h4 id="conectividad"><b>B. Conectividad con NodeJS</b></h4>

<p>NodeJS es una tecnología backend basada en JavaScript, para conectarse a la base de datos se usa un archivo server.js. Previo a esto debe instalarse la librería correspondiente mediante el gestor de paquetes para poder ser importada en el archivo, como se ve a continuación en la Imagen 33.</p>

<p style="text-align:center"><image
src="/chatbot_ecci_documentation/Img/ConexionMongoyNode.png" alt="Conexión a MongoDB en NodeJS" align="center" width="700px">
<p id="imagen46" style="text-align:center;font-size:0.8rem"><i>Imagen 46 Conexión a MongoDB en NodeJS</i></p>

<h4 id="buscardatos"><b>C. Búscar, Insertar, Actualizar y Eliminar Registros</b></h4>

<ul type="disc">
    <li>Buscar Datos</li>
    <p>Para buscar documentos en nuestra base de datos, utilizaremos el comando find. La sintaxis es la que se muestra a continuación, el primer parámetro es el nombre de la colección y el último se refiere a los atributos a buscar en ella en formato JSON.</p>
    <i><p>dbmongo.collection("collection").find({ key: "value" })</p></i>
    <li>Insertar Datos</li>
    <p>Insertar documentos es muy sencillo. Como parámetro recibe el objeto JSON que se quiere insertar con la función insertOne o insertMany, junto con una función callback que se ejecuta cuando finaliza la inserción.</p>
    <pre>
        dbmongo.collection("collection").insertOne({ key: “value” }, function (err, r) {
            if (err) {
                res.send({ success: false });
            } else {
                console.log("record created")
            }
        });
    </pre>
    <li>Eliminación de Datos</li>
    <p>Para eliminar datos de una colección, se utiliza el comando deleteOne, recibe como parámetro la consulta para filtrar los registros de la colección y elimina la primera coincidencia. También es posible usar el comando deleteMany, si no especificamos ninguna consulta, se eliminarán todos los datos de la colección.</p>
    <i><p>dbmongo.collection("collection").deleteOne({ key: “value” })</p></i>
    <li>Actualización de Datos</li>
    <p>Para actualizar datos, se usa el comando findOneAndUpdate. Este comando, recibe tres parámetros: el primero con la consulta para filtrar los documentos a modificar, el segundo con los elementos que se modificarán, y el tercero opcionalmente permite definir el comportamiento de retorno de la consulta, en el ejemplo permite definir que el elemento retornado sea el documento con los datos actualizados recientemente</p>
    <i><p>dbmongo.collection("collection").findOneAndUpdate({ "chat_id": from }, {</p>
    <p style="margin-left:1rem">$set: { "status": context?.status }</p>
    <p>})}, { returnDocument: “after” })</p>
    </i>
</ul>

<h3 id="nodejs">V. NodeJS Backend (API)</h3>

<p>Node.js es un entorno de ejecución de JavaScript que permite el desarrollo de aplicaciones JavaScript en el lado del servidor. Este entorno de ejecución en tiempo real incluye todo lo que se necesita para ejecutar un programa escrito en JavaScript.</p>

<p>Node.js utiliza un modelo de entrada y salida sin bloqueo controlado por eventos que lo hace ligero y eficiente (entrada se refiere a solicitudes y salida a respuestas).</p>

<p>El proyecto de NodeJS del backend está desarrollado sobre la versión 16 LTS de Node.JS. Utilizando algunas dependencias principales como express para el manejo de solicitudes HTTP, o cloudant de IBM Cloud para la conexión con Watson Assistant. Así como también las librerías de conexión de MongoDB y 360 Dialog para JavaScript, entre otras.</p>

<p>A continuación, se muestran los pasos para poder descargar, ejecutar y compilar el proyecto:</p>

