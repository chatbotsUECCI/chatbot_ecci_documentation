# <h1 style="font-family:'Open Sans', sans-serif">Documentación Técnica Chatbot Universidad ECCI</h1>

<h3 id=indice></h3>

#### Índice

<p style="margin-left:1.2rem;"><b>Documentación Técnica Chatbot Universidad ECCI</b></p>

<ol style="margin-left:1rem;">
<li><a href="#introduccion">Introducción</a></li>
<li><a href="#consideracion">Consideraciones y Requerimientos Previos</a></li>
    <ol type="I">
        <li><a href="#cuentasUsuario">Cuentas de Usuario y Plataformas</a></li>
        <li><a href="#validacionCuentas">Validación de Cuentas</a></li>
    </ol>
<li><a href="#descripcionArquitectonica">Descripción Arquitectónica</a></li>
<li><a href="#implementacion">Implementación y Despliegue</a></li>
<ol type="I">
        <li><a href="#IBMWatson">IBM Watson Assistant</a></li>
        <ol type="a">        
            <li><a href="#funcionamiento">Funcionamiento</a></li>
            <li><a href="#crearasistente">Crear un Asistente Watson Assistant</a></li>
            <li><a href="#intenciones">Intenciones</a></li>
            <li><a href="#entidades">Entidades</a></li>
            <li><a href="#dialogo">Diálogo</a></li>
        </ol>
        <li><a href="#IBMObject">IBM Object Storage</a></li>
        <li><a href="#360dialog">360 Dialog</a></li>
        <li><a href="#meta">Meta Business Platform</a></li>
        <li><a href="#plataformameta">Plataforma de Administración de Meta para Whatsapp</a></li>
        <li><a href="#mongodb">MongoDB</a></li>
        <ol type="a">
            <li><a href="#ingresoplataforma">Ingreso a la Plataforma</a></li>
            <li><a href="#conectividad">Conectividad con NodeJS</a></li>
            <li><a href="#buscardatos">Buscar, Insertar, Actualizar y Eliminar Registros</a></li>
        </ol>
        <li><a href="#nodejs">NodeJS Backend (API)</a></li>
        <ol type="a">
            <li><a href="#clonandorepositorio">Clonando el Repositorio</a></li>
            <li><a href="#instalandodependencias">Instalando Dependencias</a></li>
            <li><a href="#ejecutarproyecto">Ejecutar el Proyecto en Desarrollo</a></li>
            <li><a href="#subiendoproyecto">Subiendo el Proyecto a Producción</a></li>
            <li><a href="#EstructuraArchivos">Estructura de Archivos del Proyecto</a></li>
            <li><a href="#ServiciosAPI">Servicios API Rest</a></li>
        </ol>
        <li><a href="#reactjs">ReactJS Frontend (Métricas)</a></li>
        <ol type="a">
            <li><a href="#clonandorepositoriofront">Clonando el Repositorio</a></li>
            <li><a href="#instalandodependeciasfront">Instalando Dependencias</a></li>
            <li><a href="#ejecutarproyectofront">Ejecutar el Proyecto en Desarrollo</a></li>
            <li><a href="#compilandoproyectofront">Compilando el Proyecto en Desarrollo</a></li>
            <li><a href="#estructuraarchivosfront">Estructura de Archivos del Proyecto</a></li>
        </ol>
        <li><a href="#ibmcloudfonundry">IBM Cloud Foundry</a></li>
    </ol>
    <li><a href="#balance">Balance de Operación Chatbot</a></li>
    <ol type="I">
        <li><a href="#dificultades">Posibles Dificultades</a></li>
        <ol type ="a">
            <li><a href="#CurvaAprendizaje">Curva de Aprendizaje de Tecnologías</a></li>
            <li><a href="#IBMCloud">IBM Cloud Lite</a></li>
        </ol>
        <li><a href="#recomendaciones">Recomendaciones</a></li>
    </ol>
</ol> 

---
<h3 id="indiceImagenes"></h3>

### Índice de Imágenes

<ol style="list-style:none">
    <li><a href="#imagen1">Imagen 1 Arquitectura Chatbot</a></li>
    <li><a href="imagen2">Imagen 2 Funcionamiento Watson Assistant</a></li>
    <li><a href="#imagen3">Imagen 3 Cátalogo de IBM - Watson Assistant</a></li>
    <li><a href="#imagen4">Imagen 4 Crear Servicio de Watson Assistant</a></li>
    <li><a href="#imagen5">Imagen 5 Página Principal de Watson Assistant</a></li>
    <li><a href="#imagen6">Imagen 6 Crear Asistente en Watson Assistant</a></li>
    <li><a href="#imagen7">Imagen 7 Crear Dialogo en Watson Assistant</a></li>
    <li><a href="#imagen8">Imagen 8 Página Principal Asistente Chatbot ECCI</a></li>
    <li><a href="#imagen9">Imagen 9 Asistente UECCI en Watson Assistant</a></li>
    <li><a href="#imagen10">Imagen 10 Intenciones Chat UECCI</a></li>
    <li><a href="#imagen11">Imagen 11 Ejemplo de Intención: Aspirante</a></li>
    <li><a href="#imagen12">Imagen 12 Entidades Chat UECCI</a></li>
    <li><a href="#imagen13">Imagen 13 Diálogo Chat UECCI</a></li>
    <li><a href="#imagen14">Imagen 14 Nodo Menú en Diálogo Chat UECCI</a></li>
    <li><a href="#imagen15">Imagen 15 Cloud Object Storage</a></li>
    <li><a href="#imagen16">Imagen 16 Creación de Servicio Object Storage</a></li>
    <li><a href="#imagen17">Imagen 17 Configuración IBM Cloud Object Storage</a></li>
    <li><a href="#imagen18">Imagen 18 Listado de Archivos en Cloud Object Storage</a></li>
    <li><a href="#imagen19">Imagen 19 Políticas de Acceso en Cloud Object Storage</a></li>
    <li><a href="#imagen20">Imagen 20 Detalle de Archivo en Cloud Object Storage</a></li>
    <li><a href="#imagen21">Imagen 21 Página Principal de 360 Dialog</a></li>
    <li><a href="#imagen22">Imagen 22 Dashboard de 360 Dialog</a></li>
    <li><a href="#imagen23">Imagen 23 Sección de Whatsapp en 360 Dialog</a></li>
    <li><a href="#imagen24">Imagen 24 Sección de Métricas en 360 Dialog</a></li>
    <li><a href="#imagen25">Imagen 25 Sección de Métricas y Facturación en 360 Dialog</a></li>
    <li><a href="#imagen26">Imagen 26 Sección de Perfil en 360 Dialog</a></li>
    <li><a href="#imagen27">Imagen 27 Plataforma de Desarrolladores</a></li>
    <li><a href="#imagen28">Imagen 28 Seleccionar Tipo de Aplicación</a></li>
    <li><a href="#imagen29">Imagen 29 Visualización Servicios de Meta</a></li>
    <li><a href="#imagen30">Imagen 30 Configuración Weebhook para Peticiones de Facebook</a></li>
    <li><a href="#imagen31">Imagen 31 Configuración Weebhook para Peticiones de Whatsapp</a></li>
    <li><a href="#imagen32">Imagen 32 Conexión Cuenta Whatsapp desde Plataforma Empresarial de Facebook</a></li>
    <li><a href="#imagen33">Imagen 33 Plataforma de Administración de Meta</a></li>
    <li><a href="#imagen34">Imagen 34 Sección de los Números de Teléfono</a></li>
    <li><a href="#imagen35">Imagen 35 Sección de Métricas Específicas y Detalles a Nivel de Cobertura</a></li>
    <li><a href="#imagen36">Imagen 36 Plantillas de Mensajes</a></li>
    <li><a href="#imagen37">Imagen 37 Detalles de las Plantillas de Mensajes</a></li>
    <li><a href="#imagen38">Imagen 38 Creación de Cuenta en MongoDB</a></li>
    <li><a href="#imagen39">Imagen 39 Inicio de Sesión MongoDB</a></li>
    <li><a href="#imagen40">Imagen 40 Configuración de Clúster en MongoDB</a></li>
    <li><a href="#imagen41">Imagen 41 Información de Clúster en MongoDB</a></li>
    <li><a href="#imagen42">Imagen 42 Conexión a Base de Datos MongoDB</a></li>
    <li><a href="#imagen43">Imagen 43 Información de Usuarios en MongoDB</a></li>
    <li><a href="#imagen44">Imagen 44 Crear Base de Datos MongoDB</a></li>
    <li><a href="#imagen45">Imagen 45 Lista de Colecciones en MongoDB</a></li>
    <li><a href="#imagen46">Imagen 46 Conexión a MongoDB en NodeJS</a></li>
    <li><a href="#imagen47">Imagen 47 Estructura de Archivos Backend</a></li>
    <li><a href="#imagen48">Imagen 48 Servicio de Conexión Whatsapp</a></li>
    <li><a href="#imagen49">Imagen 49 Guardar Sesión de Conversación</a></li>
    <li><a href="#imagen50">Imagen 50 Envío de Mensajes a 360 Dialog</a></li>
    <li><a href="#imagen51">Imagen 51 Direccionamiento de Conversación Según la Sección</a></li>
    <li><a href="#imagen52">Imagen 52 Conectar con Agente</a></li>
    <li><a href="#imagen53">Imagen 53 Guardar Mensajes no Comprendidos</a></li>
    <li><a href="#imagen54">Imagen 54 Servicio de Conexión de Whatsapp con 360 Dialog</a></li>
    <li><a href="#imagen55">Imagen 55 Recepción de Mensajes de Whatsapp desde 360 Dialog</a></li>
    <li><a href="#imagen56">Imagen 56 Servicio de conexión Whatsapp Sandbox - 360 Dialog - Webhook</a></li>
    <li><a href="#imagen57">Imagen 57 Servicio de conexión Whatsapp Sandbox - 360 Dialog - Weebhook Número de Producción</a></li>
    <li><a href="#imagen58">Imagen 58 Servicio de Conexión Telegram</a></li>
    <li><a href="#imagen59">Imagen 59 Ejemplo de Endpoint de Consulta de Métricas</a></li>
    <li><a href="#imagen60">Imagen 60 Conexión Middleware con Frontend</a></li>
    <li><a href="#imagen61">Imagen 61 Página Principal Frontend</a></li>
    <li><a href="#imagen62">Imagen 62 Estructura de Archivos Frontend</a></li>
    <li><a href="#imagen63">Imagen 63 Creación de Servicio de Cloud Foundry 1</a></li>
    <li><a href="#imagen64">Imagen 64 Creación de Servicio de Cloud Foundry 2</a></li>
    <li><a href="#imagen65">Imagen 65 Descripción de Despliegue de Cloud Foundry en IBM Cloud</a></li>
    <li><a href="#imagen66">Imagen 66 Descripción de Instancia de Cloud Foundry en Ejecución</a></li>
    <li><a href="#imagen67">Imagen 67 Archivo de Configuración de Despliegue en Cloud Foundry</a></li>
</ol>

---
<h4 id="introduccion"></h4>

#### 1. Introducción 

<p style="margin-left:1.2rem">La presente documentación tiene como objetivo explicar detalladamente la arquitectura
técnica del proyecto Chatbot para la Universidad ECCI, su implementación técnica y
descripción tecnológica.</p>

<p style="margin-left:1.2rem">Para ello se enumeran las cuentas de usuario necesarias para el despliegue de
plataformas, se realizará una breve descripción arquitectónica del proyecto, y
posteriormente se detallará el proceso de implementación de cada uno de los
componentes de la arquitectura vista, así como el despliegue de los componentes
necesarios. Por último, se relatan algunas posibles dificultades comunes y
recomendaciones futuras para la extensibilidad del proyecto.</p>

<h4 id="consideracion"></h4>

#### 2. Consideraciones y Requerimientos Previos

<h5 id="cuentasUsuario"></h5>

##### <h5 style="font-size: 18.2px; margin-left:1.2rem">I. Cuentas de Usuario y Plataformas</h5>
<p style="margin-left:2rem">La infraestructura del proyecto requiere que se cuente con algunas cuentas de usuario en diversas plataformas que apoyan el funcionamiento y despliegue de la arquitectura en la nube.</p>

<p style="margin-left:2rem">Para algunas de estas cuentas es necesario realizar un proceso de verificación y
validación de identidad y legalidad de la organización, para efectos de la activación de
una cuenta de WhatsApp con un número telefónico.</p>

<p style="margin-left:2rem">A continuación, se listan las plataformas en las cuáles es necesario tener una cuenta
de usuario creada para poder realizar correctamente el levantamiento del proyecto:</p>

<p style="margin-left:2.8rem"><b>a. IBM Cloud: </b> Es la plataforma de servicios alojados en la nube de IBM.</p>

<p style="margin-left:2.8rem">Dispone de múltiples servicios en la nube que pueden ser configurados y utilizados
bajo demanda, además de brindar la posibilidad de trabajar con Watson, la Inteligencia
Artificial de IBM, para facilitar el desarrollo de servicios a través de esta herramienta.</p>

<p style="margin-left:2.8rem">Esta plataforma se usa para la construcción del componente conversacional del proyecto, así como para disponer de un servicio de almacenamiento para los recursos estáticos de la herramienta, por último, se utiliza un servicio de IBM Cloud para el despliegue de los componentes Backend y Frontend del proyecto.</p> 

> https://www.ibm.com/es-es/cloud

<p style="margin-left:2.8rem"><b>b. Bussines Facebook Manager:</b> Es la plataforma de administración comercial de Facebook.</p>

<p style="margin-left:2.8rem">Permite la configuración, creación, administración y verificación de múltiples servicios brindados por Facebook para empresas y organizaciones comerciales. Para la
integración del proyecto con la plataforma de Whatsapp, es necesario pasar por el proceso de creación y verificación de un negocio en esta plataforma, para esto se debe disponer en lo posible de los documentos legales que validan la identidad del negocio u organización a registrar con Facebook.</p>

> https://business.facebook.com/

<p style="margin-left:2.8rem"><b>c. 360 Dialog: </b> Es el proveedor de servicios de mensajería para Whatsapp</p>

<p style="margin-left:2.8rem">Debido al modelo de negocio de Whatsapp, éste brinda un servicio de conectividad externa que solo es establecido con organizaciones que garanticen unos
requerimientos mínimos para asegurar la conectividad, estabilidad y seguridad de los
datos que envía Whatsapp, es por esto que externamente Whatsapp solo permite
conexiones desde empresas que se dedican al establecimiento de comunicaciones y
se orientan a brindar servicios de comunicaciones de calidad para otras empresas.</p>

<p style="margin-left:2.8rem">Este es el caso de 360 Dialog, un proveedor de múltiples servicios de comunicación, entre ellos, la conectividad con Whatsapp para mensajería instantánea. Existen múltiples proveedores con diversos modelos de negocio, 360 Dialog es uno de los más flexibles en
cuanto al servicio que ofrece.</p>

> https://www.360dialog.com

<p style="margin-left:2.8rem"><b>d. MongoDB Cloud: </b> MongoDB Cloud es un servicio de almacenamiento en la nube para bases de datos no relacionales MongoDB.</p>

<p style="margin-left:2.8rem">MongoDB es un gestor de bases de datos no relacionales (Nosql) que ofrece velocidad, dinamismo, fácil integración, y más. Puede ser implementado en múltiples formas, para efectos de este proyecto se hace uso de la plataforma Cloud de MongoDB para levantar y desplegar de manera fácil y sencilla las bases de datos del proyecto en un entorno Cloud.</p>

> https://www.mongodb.com/cloud

<h5 id="validacionCuentas"></h5>

##### <h5 style="font-size: 18.2px; margin-left: 1.2rem">II. Validación de Cuentas</h5>
<p style="margin-left:2rem">Adicionalmente a la creación de cuentas detallada en la sección anterior, es necesario realizar un proceso adicional de verificación de identidad y legalidad de la organización que se quiere registrar con Facebook Business.</p>

<p style="margin-left:2rem">Facebook es muy riguroso en su habilitación de servicios comerciales, y es por esto que solicita que cualquier organización que requiera utilizar algunos de sus servicios principales de manera comercial deba estar debidamente registrada como organización o empresa comercial, y debe presentar documentos de soporte legal que certifiquen:</p>

<p style="margin-left: 2.5rem">a. Nombre Legal de la Organización</p>

<p style="margin-left: 2.5rem">b. Dirección Física de la Organización</p>

<p style="margin-left: 2rem">Con este proceso Facebook valida la identidad de la organización que quiere usar sus
servicios, para mantener seguros a sus usuarios de las entidades con las que trabaja;
así mismo, con 360 Dialog es necesario realizar un proceso de solicitud de conexión con
Facebook para poder usar Whatsapp a través de 360 Dialog, que se debe realizar con el
perfil de Facebook Business verificado correctamente, desde el siguiente enlace:</p>


> https://www.360dialog.com/es/whatsapp-business-api

<p style="margin-left:2rem">Por último, dependiendo del método con el que se realice la habilitación del número telefónico para la creación de la cuenta de Whatsapp, debe realizarse una verificación de identidad similar a la solicitada por Facebook Business. Esto es, en el caso de optar por la compra de un número telefónico desde el catálogo de números disponibles en la consola de 360 Dialog, debe realizarse este proceso adicional de verificación con 360 Dialog.</p>

<h4 id="descripcionArquitectonica"></h4>

#### 3. Descripción Arquitectónica

<div>
<p style="text-align:center"><image
src="./Img/ArquitecturaChatbotECCI.png" alt="Descripción Arquitectónica Chatbot para la Universidad ECCI" align="center" width="700px">
<p id="imagen1" style="text-align:center;font-size:0.8rem"><i>Imagen 1 Arquitectura Chatbot</i></p>
</div>

<p style="margin-left:1.2rem">En la Imagen 1 se observa la arquitectura de software del producto, la cual está basada en el servicio conversacional de IBM Watson, el cual permite crear flujos conversacionales inteligentes a través de la identificación de intenciones. A su vez, los demás componentes de la arquitectura están desplegados en algunos servicios de la nube de IBM, como IBM Object Storage para el almacenamiento de archivos estáticos o IBM Cloud Foundry para el despliegue de máquinas virtuales con entornos NodeJS</p>

<p style="margin-left:1.2rem">La persistencia de datos del proyecto está soportada sobre el servicio en la nube de MongoDB Atlas; el cual permite crear y administrar bases de datos no relacionales en la nube, con planes de servicio bajo demanda, brindando flexibilidad, disponibilidad y seguridad a los datos del proyecto</p>

<p style="margin-left:1.2rem">La arquitectura cuenta con un componente backend desarrollado en NodeJS, que permite la comunicación entre las demás partes del sistema y gestiona el almacenamiento de datos y la consulta de los mismos. Así como también una interfaz web que permite consultar, visualizar y analizar la información disponible y actualizada del uso del chatbot por los usuarios.</p>

<p style="margin-left:1.2rem">La conexión con el chatbot está disponible para los usuarios de Whatsapp a través de 360 Dialog, el cual es un proveedor de comunicaciones en la nube que cuenta con el servicio de mensajería de para Whatsapp, permitiendo la comunicación y administración de la cuenta y el canal de whatsapp, así como algunas características adicionales como soporte técnico, aprobación de plantillas para envíos masivos, gestión de números y cuentas de whatsapp, entre otros. De la misma forma, la arquitectura cuenta con soporte para la conexión de usuarios con asesores humanos, quienes pueden comunicarse con los usuarios a través del chatbot mediante Whatsapp o Telegram, así como retomar un usuario inactivo.</p>

<h4 id="implementacion"></h4>

#### 4. Implementación y Despliegue

<h5 id="IBMWatson"></h5>

##### <h5 style="font-size: 18.2px; margin-left:1.2rem">I. IBM Watson Assistant</h5>

<p style="margin-left:2rem">Watson Assistant es un servicio de IBM Cloud basado en la inteligencia artificial, el cual
permite crear, entrenar e implementar interacciones conversacionales en cualquier
aplicación, dispositivo o canal. Busca una respuesta de una base de conocimiento,
cuándo pedir aclaraciones y cuándo transferir usuarios a un agente humano con base a
un entrenamiento. Watson Assistant se puede implementar en cualquier entorno en la
nube o local, lo que significa que la IA más inteligente finalmente está disponible en
cualquier lugar donde la necesite.</p>

<h5 id="funcionamiento"></h5>

##### <h5 style="font-size: 17.2px; margin-left:2rem">a. Funcionamiento</h5>

<div style="margin-left:2.5rem">
<p style="text-align:center"><image
src="./Img/FuncionamientoWatson.png" alt="Funcionamiento Watson Assistant" align="center" width="700px">
<p id="imagen2" style="text-align:center;font-size:0.8rem"><i>Imagen 2 Funcionamiento Watson Assistant</i></p>
</div>

<ol style="margin-left:2.8rem">
    <li>El cliente/usuario interactúa desde WhatsApp con el asistente por medio del punto de integración con NodeJS, el cual está integrado con 360 Dialog para acceder al canal de comunicación WhatsApp y una base de datos MongoDB.</li>
    <li>Nuestro asistente recibe los datos de entrada que proporciona nuestro usuario y los dirige a la sección correspondiente (dialog skill).</li>
    <li>La sección correspondiente interpreta los datos y luego los conecta a los diálogos de respuestas correspondientes.</li>
    <li>Existe una posibilidad en la cual no se tenga una respuesta para algún interrogante, y para este tipo casos, se dirigen dichas preguntas a un área comúnmente llamada “search skill”, la cual encuentra respuestas relevantes con base a la configuración y conocimiento que le hayamos aportado a nuestro bot.</li>
</ol>

<h5 id="crearasistente"></h5>

##### <h5 style="font-size: 17.2px; margin-left:2rem">b. Crear un Asistente Watson Assistant</h5>

<p style="margin-left:3rem">El servicio se crea desde la consola de IBM Cloud buscando el servicio en el catálogo, el plan Lite permite un uso gratuito con algunas limitaciones en el servicio, al crear el servicio se debe crear un skill el cual contendrá los componentes de Intenciones, Entidades y Diálogo.</p>

<div style="margin-left:3rem">
<p style="text-align:center"><image
src="./Img/Catalogo.png" alt="Cátalogo de IBM - Watson Assistant" align="center" width="700px">
<p id="imagen3" style="text-align:center;font-size:0.8rem"><i>Imagen 3 Cátalogo de IBM - Watson Assistant</i></p>
</div>

<div style="margin-left:3rem">
<p style="text-align:center"><image
src="./Img/CrearServicioWatson.png" alt="Crear Servicio de Watson Assistant" align="center" width="700px">
<p id="imagen4" style="text-align:center;font-size:0.8rem"><i>Imagen 4 Crear Servicio de Watson Assistant</i></p>
</div>
 
<div style="margin-left:3rem">
<p style="text-align:center"><image
src="./Img/PaginaPrincipalWatson.png" alt="Página Principal de Watson Assistant" align="center" width="700px">
<p id="imagen5" style="text-align:center;font-size:0.8rem"><i>Imagen 5 Página Principal de Watson Assistant</i></p>
</div>

<div style="margin-left:3rem">
<p style="text-align:center"><image
src="./Img/CrearAsistenteWatson.png" alt="Crear Asistente en Watson Assistant" align="center" width="700px">
<p id="imagen6" style="text-align:center;font-size:0.8rem"><i>Imagen 6 Crear Asistente en Watson Assistant</i></p>
</div>

<p style="margin-left: 3rem">Se puede crear el Dialog Skill con base a un ejemplo que se ofrece o subir un archivo .json con un Dialog Skill ya configurado.</p>

<div style="margin-left:3rem">
<p style="text-align:center"><image
src="./Img/CrearDialogo.png" alt="Crear Dialogo en Watson Assistant" align="center" width="700px">
<p id="imagen7" style="text-align:center;font-size:0.8rem"><i>Imagen 7 Crear Dialogo en Watson Assistant</i></p>
</div>

<div style="margin-left:3rem">
<p style="text-align:center"><image
src="./Img/PaginaAsistenteChatbot.png" alt="Página Principal Asistente Chatbot ECCI" align="center" width="700px">
<p id="imagen8" style="text-align:center;font-size:0.8rem"><i>Imagen 8 Página Principal Asistente Chatbot ECCI</i></p>
</div>

<div style="margin-left:3rem">
<p style="text-align:center"><image
src="./Img/AsistenteUECCIWatson.png" alt="Asistente UECCI en Watson Assistant" align="center" width="700px">
<p id="imagen9" style="text-align:center;font-size:0.8rem"><i>Imagen 9 Asistente UECCI en Watson Assistant</i></p>
</div>

<h5 id="intenciones"></h5>

##### <h5 style="font-size: 17.2px; margin-left:2rem">c. Intenciones</h5>

<p style="margin-left: 3rem">Las intenciones en Watson Assistant se activan a través de un concepto conocido como confianza. Watson Assistant no solo crea un modelo para devolver cuál es la intención correcta. De hecho, crea un modelo diferente para cada intento. Cuando un usuario hace una pregunta, esa expresión se envía a cada modelo de intención. Cada uno de esos modelos de intención devuelve una puntuación de confianza, que indica qué tan "seguro" es el modelo de que la expresión se ajusta a esa intención. Cuando verifica si # < intent > se cumple la condición, eso esencialmente solo agrega esas puntuaciones y verifica si la intención de puntuación más alta es la que está verificando. Para capturar múltiples intenciones de un solo enunciado de usuario, vamos a seguir 3 pasos.</p>

<ol style="margin-left:3.2rem">
    <li>Definir un umbral de confianza: definiremos una variable constante para ajustar la sensibilidad para capturar múltiples intenciones. Establecer esto muy bajo podría llevar a capturar demasiados intentos. A la inversa, establecerlo demasiado alto podría resultar en que no se capturen las intenciones en la expresión del usuario.</li>
    <li>Capturar intenciones que superen el umbral de confianza: en este paso, veremos cómo puede capturar las intenciones utilizando el umbral definido previamente y luego guardarlas para usarlas más adelante.</li>
    <li>Iterar a través de la lista de intenciones: utilizando algunos trucos de diálogo, veremos cómo podemos construir un bucle en Watson Assistant para iterar a través de cada una de las intenciones capturadas previamente una por una.</li>
</ol>

<p style="margin-left: 3rem">Primero, necesitamos definir una intención para agregar una tarea, agregando una serie de ejemplos de cómo las personas podrían agregar una tarea.</p>

<div style="margin-left:3rem">
<p style="text-align:center"><image
src="./Img/Intenciones.png" alt="Intenciones Chat UECCI" align="center" width="700px">
<p id="imagen10" style="text-align:center;font-size:0.8rem"><i>Imagen 10 Intenciones Chat UECCI</i></p>
</div>

<div style="margin-left:3rem">
<p style="text-align:center"><image
src="./Img/EjemploIntencion.png" alt="Ejemplo de Intención: Aspirante" align="center" width="700px">
<p id="imagen11" style="text-align:center;font-size:0.8rem"><i>Imagen 11 Ejemplo de Intención: Aspirante</i></p>
</div>

<h5 id="entidades"></h5>

##### <h5 style="font-size: 17.2px; margin-left:2rem">d. Entidades</h5>

<p style="margin-left: 3rem">Una entidad representa un término o un objeto que da contexto a una acción. Las entidades representan información en la entrada de usuario que es relevante para la finalidad de la intención. Los nombres de las entidades van precedidos del símbolo @entidad. Una entidad puede tener varios valores, y a cada uno de estos valores se le configura sinónimos, los cuales son las diferentes maneras en que puede ser mencionado ese valor de la entidad.</p>

<div style="margin-left:3rem">
<p style="text-align:center"><image
src="./Img/Entidades.png" alt="Entidades Chat UECCI" align="center" width="700px">
<p id="imagen12" style="text-align:center;font-size:0.8rem"><i>Imagen 12 Entidades Chat UECCI</i></p>
</div>

<h5 id="dialogo"></h5>

##### <h5 style="font-size: 17.2px; margin-left:2rem">e. Diálogo</h5>

<p style="margin-left: 3rem">La estructura de diálogo está basada en nodos, es decir tiene forma de árbol. Cuando un mensaje es analizado por Watson Assistant, dicho mensaje recorre cada uno de estos nodos en el orden en el que han sido definidos, para encontrar una intención y una entidad que tengan relación con dicho mensaje. Cada nodo del diálogo contiene, como mínimo, una condición; y puede contener una respuesta o textos o varios nodos hijos que de igual forma deben contener una condición y una respuesta. El servicio procesa el diálogo desde el primer nodo en el árbol hasta el último. A medida que recorre por el árbol, si el servicio encuentra una condición que se cumple, activa dicho nodo. Luego se mueve por el nodo que ha sido activado para comparar la entrada del usuario con las condiciones de los nodos hijos, desde el primer nodo hijo hasta el último.</p>

<div style="margin-left:3rem">
<p style="text-align:center"><image
src="./Img/Dialogo.png" alt="Diálogo Chat UECCI" align="center" width="700px">
<p id="imagen13" style="text-align:center;font-size:0.8rem"><i>Imagen 13 Diálogo Chat UECCI</i></p>
</div>

<div style="margin-left:3rem">
<p style="text-align:center"><image
src="./Img/Nodo.png" alt="Nodo Menú en Diálogo Chat UECCI" align="center" width="700px">
<p id="imagen14" style="text-align:center;font-size:0.8rem"><i>Imagen 14 Nodo Menú en Diálogo Chat UECCI</i></p>
</div>

<p style="margin-left: 3rem"><b>Nota: </b>Mensaje no comprendido (anything else) Este nodo se implementó como un respaldo si Watson Assistant no comprende el mensaje, y se le solicita al usuario que repita la pregunta de otra manera.</p>

<h5 id="IBMObject"></h5>

##### <h5 style="font-size: 18.2px; margin-left:1.2rem">II. IBM Object Storage</h5>

<p style="margin-left:2rem">El componente de Object Storage es un servicio de almacenamiento en la nube que permite subir archivos estáticos para ser accedidos desde internet de forma rápida y segura. Es parte de la suite de servicios de IBM, y está disponible desde el plan Lite.</p>

> https://www.ibm.com/co-es/cloud/object-storage

<div style="margin-left:3rem">
<p style="text-align:center"><image
src="./Img/CloudObject.png" alt="Cloud Object Storage" align="center" width="700px">
<p id="imagen15" style="text-align:center;font-size:0.8rem"><i>Imagen 15 Cloud Object Storage</i></p>
</div>

<p style="margin-left:2rem">El servicio se crea desde la consola de IBM Cloud, el plan Lite permite un uso gratuito con algunas limitaciones en el servicio, se debe definir igualmente un nombre para el servicio Object Storage que se está creando.</p>

<div style="margin-left:3rem">
<p style="text-align:center"><image
src="./Img/CreacionObject.png" alt="Creación de Servicio Object Storage" align="center" width="700px">
<p id="imagen16" style="text-align:center;font-size:0.8rem"><i>Imagen 16 Creación de Servicio Object Storage</i></p>
</div>

<p style="margin-left:2rem">Luego de haber creado el servicio, debe crearse un bucket o depósito, donde se almacenarán los archivos en el servicio. Adicionalmente, se deben definir las opciones de resiliencia y ubicación y tipo de almacenamiento para el depósito que se creará, como se ve en la Imagen 17.</p>

<div style="margin-left:3rem">
<p style="text-align:center"><image
src="./Img/ConfiguracionIBMObject.png" alt="Configuración IBM Cloud Object Storage" align="center" width="700px">
<p id="imagen17" style="text-align:center;font-size:0.8rem"><i>Imagen 17 Configuración IBM Cloud Object Storage</i></p>
</div>

<b style="margin-left:2rem">Importante:</b>

<ul style="margin-left:2rem">
    <li>La separación de archivos dentro de un servicio de almacenamiento de objetos no estructurados se realiza mediante buckets o depósitos.</li>
    <li>El nombre del depósito debe cumplir con unas reglas básicas detalladas en la imagen, entre ellas, debe ser único en todo el ecosistema de IBM Cloud Object Storage. Esto es, no puede haber dos buckets con el mismo nombre en todos los servidores de IBM, ni siquiera en cuentas distintas, debe ser único.</li>
</ul>

<p style="margin-left:2rem">Luego de crear el depósito podemos visualizarlo desde la interfaz web de IBM Cloud, y desde allí interactuar con él para subir y eliminar archivos, así como modificar las configuraciones del depósito y del servicio para su conectividad.</p>

<div style="margin-left:3rem">
<p style="text-align:center"><image
src="./Img/ListadoArchivosObject.png" alt="Listado de Archivos en Cloud Object Storage" align="center" width="700px">
<p id="imagen18" style="text-align:center;font-size:0.8rem"><i>Imagen 18 Listado de Archivos en Cloud Object Storage</i></p>
</div>

<p style="margin-left:2rem">Para este caso en particular es necesario que el depósito tenga acceso público, para que cualquier persona pueda acceder a los recursos alojados en él desde su chat de Whatsapp sin necesidad de autenticación. Para realizar esto, se debe crear una política de acceso público desde las políticas de acceso del depósito, como se ve en la siguiente Imagen 19.</p>

<div style="margin-left:3rem">
<p style="text-align:center"><image
src="./Img/PoliticasAcceso.png" alt="Políticas de Acceso en Cloud Object Storage" align="center" width="700px">
<p id="imagen19" style="text-align:center;font-size:0.8rem"><i>Imagen 19 Políticas de Acceso en Cloud Object Storage</i></p>
</div>

<p style="margin-left:2rem">Por último, los archivos subidos al bucket podrán visualizarse de la siguiente forma:</p>

<div style="margin-left:3rem">
<p style="text-align:center"><image
src="./Img/DetalleCloud.png" alt="Detalle de Archivo en Cloud Object Storage" align="center" width="700px">
<p id="imagen20" style="text-align:center;font-size:0.8rem"><i>Imagen 20 Detalle de Archivo en Cloud Object Storage</i></p>
</div>

<p style="margin-left:2rem">Y contarán con un URL público de objeto, el cual es la URL pública para acceder a ese objeto almacenado en la nube de IBM.</p>

<h5 id="360dialog"></h5>

##### <h5 style="font-size: 18.2px; margin-left:1.2rem">III. 360 Dialog</h5>

<p style="margin-left:2rem">360 Dialog es una plataforma de mensajería instantánea que brinda un API de conexión con Whatsapp, la cuál permite una conexión simplificada y acorde a las referencias de la documentación del API de Whatsapp, así como una actualización de versiones del API de Whatsapp sin demora. La plataforma principal de 360 Dialog se encuentra alojada en <a href="https://www.360dialog.com">https://www.360dialog.com</a>.</p>

<p style="margin-left:2rem">El menú de la plataforma permite visualizar la página principal de la consola, un listado de cuentas de whatsapp activas, métricas de uso y facturación, conexión de integraciones y soporte. Adicionalmente en la sección de perfil hay otras opciones disponibles como configuración de la cuenta y la organización o opciones de facturación y cierre de sesión.</p>

<div>
    <p style="text-align:center"><image
        src="./Img/PaginaPrincipal360Dialog.png" alt="Página Principal 360 Dialog" align="center" width="300px">
    <p id="imagen21" style="text-align:center;font-size:0.8rem"><i>Imagen 21 Página Principal de 360 Dialog</i></p>
</div>

<p style="margin-left:2rem">El Dashboard muestra un resumen del estado de las cuentas de Whatsapp activas en la plataforma, así como una sección de ayuda y documentación de apoyo.</p>

<div>
    <p style="text-align:center"><image
        src="./Img/Dashboard360Dialog.png" alt="Dashboard de 360 Dialog" align="center" width="500px">
    <p id="imagen22" style="text-align:center;font-size:0.8rem"><i>Imagen 22 Dashboard de 360 Dialog</i></p>
</div>

<p style="margin-left:2rem">La sección de cuentas de Whatsapp permite la gestión y administración de las cuentas de Whatsapp enlazadas con 360 Dialog, la generación de API Keys para la conexión vía API con la plataforma y la gestión de plantillas de mensajes.</p>

<div>
    <p style="text-align:center"><image
        src="./Img/SeccionWhatsapp360Dialog.png" alt="Sección de Whatsapp en 360 Dialog" align="center" width="500px">
    <p id="imagen23" style="text-align:center;font-size:0.8rem"><i>Imagen 23 Sección de Whatsapp en 360 Dialog</i></p>
</div>

<p style="margin-left:2rem">Por su parte, en la sección de métricas y facturación se puede visualizar un resumen del balance y saldo de los números de Whatsapp. A la fecha de esta documentación, 360 Dialog cuenta con un modelo de facturación basado en saldos prepagados con auto renovación para disponibilidad automática, en la página también se puede visualizar un resumen general de uso del servicio de mensajería y una subsección con las opciones de auto renovación.</p>

<div>
    <p style="text-align:center"><image
        src="./Img/SeccionMetricas360Dialog.png" alt="Sección de Métricas en 360 Dialog" align="center" width="500px">
    <p id="imagen24" style="text-align:center;font-size:0.8rem"><i>Imagen 24 Sección de Métricas en 360 Dialog</i></p>
</div>

<div>
    <p style="text-align:center"><image
        src="./Img/SeccionMetricasFacturacion360Dialog.png" alt="Sección de Métricas en 360 Dialog" align="center" width="500px">
    <p id="imagen25" style="text-align:center;font-size:0.8rem"><i>Imagen 25 Sección de Métricas y Facturación en 360 Dialog</i></p>
</div>

<p style="margin-left:2rem">Por último, en la sección del perfil, en las opciones de facturación se puede encontrar el detalle de los datos de facturación y el historial de cobros realizados por la plataforma.</p>

<div>
    <p style="text-align:center"><image
        src="./Img/SeccionPerfil360Dialog.png" alt="Sección de Perfil en 360 Dialog" align="center" width="500px">
    <p id="imagen26" style="text-align:center;font-size:0.8rem"><i>Imagen 26 Sección de Perfil en 360 Dialog</i></p>
</div>

<p style="margin-left:2rem">A diferencia de otros proveedores, 360 Dialog no cobra tarifas por mensajería, solo maneja un cobro mensual por el alojamiento y conexión de cada número o cuenta de Whatsapp vinculada a la plataforma. A la fecha de esta documentación, el costo por cada número activo en la plataforma es de 49 EUR mensuales. Los costos de mensajería son directamente los dispuestos por Meta para el API empresarial de Whatsapp. Para mayor información acerca de los precios de cada servicio: </p>

> https://www.360dialog.com/whatsapp-business-api#pricing 
> https://business.whatsapp.com/products/platform-pricing 


<h5 id="meta"></h5>

##### <h5 style="font-size: 18.2px; margin-left:1.2rem">IV. Meta Business Platform</h5>

<p style="margin-left:2rem">A mediados del 2022, Meta abrió la posibilidad para que las empresas puedan conectarse directamente a su API de servicios de Whatsapp, lo que permite la integración directa sin intermediarios para el uso de cuentas empresariales a través del API de Meta para Whatsapp. </p>

<p style="margin-left:2rem">La página principal del servicio está disponible en:</p>

> https://business.whatsapp.com/products/business-platform


<p style="margin-left:2rem"><b>NOTA:</b> Para el uso del servicio es necesario contar con una cuenta empresarial de Facebook (<a href="https://business.facebook.com">https://business.facebook.com</a>) correctamente verificada, así como una cuenta enlazada con la plataforma de desarrolladores de Facebook (<a href="https://developers.facebook.com">https://developers.facebook.com</a>). </p>

<p style="margin-left:2rem">En la plataforma de desarrolladores se debe crear una aplicación de tipo empresarial para habilitar el servicio de Whatsapp, como se muestra en la imágen.</p>

<div>
    <p style="text-align:center"><image
        src="./Img/InformacionBasica.png" alt="Plataforma de Desarrolladores" align="center" width="500px">
    <p id="imagen27" style="text-align:center;font-size:0.8rem"><i>Imagen 27 Plataforma de Desarrolladores</i></p>
</div>

<p style="margin-left:2rem">A continuación, se debe indicar un nombre para la aplicación, un correo de contacto y una cuenta empresarial para conectar la aplicación.</p>

<div>
    <p style="text-align:center"><image
        src="./Img/PlataformaDesarrolladores.png" alt="Seleccionar Tipo de Aplicación" align="center" width="500px">
    <p id="imagen28" style="text-align:center;font-size:0.8rem"><i>Imagen 28 Seleccionar Tipo de Aplicación</i></p>
</div>

<h5 id="mongodb"></h5>

<p style="margin-left:2rem">Una vez creada la aplicación es posible visualizar una lista de productos o servicios disponibles en Meta para la aplicación, para conectar el servicio de Whatsapp o Messenger deben configurarse los correspondientes servicios.</p>

<div>
    <p style="text-align:center"><image
        src="./Img/VisualizacionServiciosMeta.png" alt="Visualización Servicios de Meta" align="center" width="500px">
    <p id="imagen29" style="text-align:center;font-size:0.8rem"><i>Imagen 29 Visualización Servicios de Meta</i></p>
</div>

<p style="margin-left:2rem">Cada servicio se configura a través de Webhooks, por lo que al activar alguno de ellos se añadirá automáticamente el servicio de Webhooks también.</p>

<p style="margin-left:2rem">Una vez configurados los servicios, se mostrarán las secciones correspondientes en el menú lateral de la plataforma, para configurar el servicio de messenger debe configurarse la conexión con una página de Facebook, la cuenta de desarrollo de la aplicación debe contar con los permisos necesarios de administración en la página a conectar para que el proceso sea exitoso.</p>

<p style="margin-left:2rem">Por su parte, se debe configurar un Webhook para escuchar las peticiones del API de Facebook para messenger, así como los eventos a ser escuchados por el webhook. Otras opciones o características no son usadas actualmente.</p>

<div>
    <p style="text-align:center"><image
        src="./Img/ConfiguracionWeebhook.png" alt="Configuración Weebhook para Peticiones de Facebook" align="center" width="500px">
    <p id="imagen30" style="text-align:center;font-size:0.8rem"><i>Imagen 30 Configuración Weebhook para Peticiones de Facebook</i></p>
</div>

<p style="margin-left:2rem">Para el servicio de Whatsapp también debe configurarse un webhook para conectar el servicio API de Whatsapp.</p>

<div>
    <p style="text-align:center"><image
        src="./Img/ConexionWeebhookWhatsapp.png" alt="Configuración Weebhook para Peticiones de Whatsapp" align="center" width="500px">
    <p id="imagen31" style="text-align:center;font-size:0.8rem"><i>Imagen 31 Configuración Weebhook para Peticiones de Whatsapp</i></p>
</div>

<p style="margin-left:2rem">Para poder usar el servicio es necesario conectar una cuenta de Whatsapp Business. Desde la plataforma empresarial de facebook, en la sección de cuentas de Whatsapp se puede realizar la gestión y administración de cuentas de Whatsapp conectadas a una cuenta empresarial.</p>

<div>
    <p style="text-align:center"><image
        src="./Img/AdministracionServiciosWhatsapp.png" alt="Conexión Cuenta Whatsapp desde Plataforma Empresarial de Facebook" align="center" width="500px">
    <p id="imagen32" style="text-align:center;font-size:0.8rem"><i>Imagen 32 Conexión Cuenta Whatsapp desde Plataforma Empresarial de Facebook</i></p>
</div>

<p style="margin-left:2rem">La opción de “Administración de Whatsapp” permite ingresar a la plataforma de administración de Whatsapp de Meta. La cual es la plataforma principal de gestión del servicio de Whatsapp de Meta.</p>

<h5 id="plataformameta"></h5>

##### <h5 style="font-size: 18.2px; margin-left:1.2rem">V. Plataforma de Administración de Meta para Whatsapp </h5>

<p style="margin-left:2rem">La plataforma de administración de Meta para Whatsapp brinda una gestión centralizada del servicio de mensajería Whatsapp desde Meta, en ella se pueden visualizar un listado resumen de las cuentas de Whatsapp activas asociadas a una cuenta empresarial específica, así como un conjunto de opciones específicas para cada cuenta empresarial vinculada, como métricas, gestión de plantillas de mensajes, números de teléfono asociados a la cuenta de Whatsapp y catálogo de productos.</p>

<div>
    <p style="text-align:center"><image
        src="./Img/PlataformaAdministracionMeta.png" alt="Plataforma de Administración de Meta" align="center" width="500px">
    <p id="imagen33" style="text-align:center;font-size:0.8rem"><i>Imagen 33 Plataforma de Administración de Meta</i></p>
</div>

<p style="margin-left:2rem">Como se muestra en la imágen anterior(#), la sección de Descripción muestra un resumen del uso de las cuentas de Whatsapp activas, así como un resumen de costos aproximados y conversaciones.</p>

<p style="margin-left:2rem">La sección de números de teléfono muestra el listado de números de teléfono asociados con una cuenta específica, permite gestionar y configurar los números de teléfono y perfiles asociados a cada uno en Whatsapp.</p>

<div>
    <p style="text-align:center"><image
        src="./Img/SeccionNumerosTelefono.png" alt="Sección de los Números de Teléfono" align="center" width="500px">
    <p id="imagen34" style="text-align:center;font-size:0.8rem"><i>Imagen 34 Sección de los Números de Teléfono</i></p>
</div>

<p style="margin-left:2rem">Dentro de la configuración de cada número se pueden encontrar opciones adicionales como métricas específicas y detalles del nivel de cobertura y calidad del número, configurar el perfil de Whatsapp, la verificación en dos pasos y enlaces de mensajes.</p>

<div>
    <p style="text-align:center"><image
        src="./Img/MetricasNumerosTelefono.png" alt="Sección de Métricas Específicas y Detalles a Nivel de Cobertura" align="center" width="500px">
    <p id="imagen35" style="text-align:center;font-size:0.8rem"><i>Imagen 35 Sección de Métricas Específicas y Detalles a Nivel de Cobertura</i></p>
</div>

<p style="margin-left:2rem">Por su parte, la sección de plantillas de mensajes del menú lateral permite una administración directa de las plantillas de mensajes y su solicitud de aprobación directamente con Meta, muestra un listado de las plantillas creadas y su estado, así como los idiomas de cada plantilla.</p>

<div>
    <p style="text-align:center"><image
        src="./Img/PlantillasMensajes.png" alt="Plantillas de Mensajes" align="center" width="500px">
    <p id="imagen36" style="text-align:center;font-size:0.8rem"><i>Imagen 36 Plantillas de Mensajes.</i></p>
</div>

<p style="margin-left:2rem">El detalle de cada plantilla muestra los detalles de la plantilla como el texto, encabezado o botones si los hay, y una previsualización de la plantilla resultante en Whatsapp.</p>

<div>
    <p style="text-align:center"><image
        src="./Img/DetallesPlantilla.png" alt="Detalles de las Plantillas de Mensajes" align="center" width="500px">
    <p id="imagen37" style="text-align:center;font-size:0.8rem"><i>Imagen 37 Detalles de las Plantillas de Mensajes.</i></p>
</div>

<h5 id="mongodb"></h5>

##### <h5 style="font-size: 18.2px; margin-left:1.2rem">VI. MongoDB</h5>

<p style="margin-left:2rem">MongoDB es una base de datos orientada a documentos. Esto quiere decir que en lugar de guardar los datos en registros, guarda los datos en documentos. Estos documentos son almacenados en BSON, que es una representación binaria de JSON. Una de las diferencias más importantes con respecto a las bases de datos relacionales, es que no es necesario seguir un esquema. Los documentos de una misma colección - concepto similar a una tabla de una base de datos relacional, con la diferencia que pueden tener esquemas diferentes.</p>

<ol style="margin-left:2rem" type="a">
    <b><li id="ingresoplataforma">Ingreso a la plataforma</li></b>
    <p>Para crear una base de datos MongoDB se accede al link <a href="https://account.mongodb.com/account/login">https://account.mongodb.com/account/login</a> con una cuenta ya creada.</p>
    <div>
        <p style="text-align:center"><image
        src="./Img/CreacionCuentaMongo.png" alt="Creación de Cuenta en MongoDB" align="center" width="500px">
        <p id="imagen38" style="text-align:center;font-size:0.8rem"><i>Imagen 38 Creación de Cuenta en MongoDB</i></p>
    </div>
    <p>Ingresa con usuario y contraseña.</p>
    <div>
        <p style="text-align:center"><image
        src="./Img/InicioSesionMongo.png" alt="Inicio de Sesión MongoDB" align="center" width="600px">
        <p id="imagen39" style="text-align:center;font-size:0.8rem"><i>Imagen 39 Inicio de Sesión MongoDB</i></p>
    </div>
    <p>Una vez dentro, se crea un cluster. Actualmente se usa el gratuito, el cual proporciona creación de base de datos con un límite de 512MB.</p>
    <div>
        <p style="text-align:center"><image
        src="./Img/ConfiguracionClusterMongo.png" alt="Configuración de Clúster en MongoDB" align="center" width="700px">
        <p id="imagen40" style="text-align:center;font-size:0.8rem"><i>Imagen 40 Configuración de Clúster en MongoDB</i></p>
    </div>
    <div>
        <p style="text-align:center"><image
        src="./Img/InformacionClusterMongo.png" alt="Información de Clúster en MongoDB" align="center" width="700px">
        <p id="imagen41" style="text-align:center;font-size:0.8rem"><i>Imagen 41 Información de Clúster en MongoDB</i></p>
    </div>
    <p>Es posible ver la información de conectividad con NodeJS, donde se puede copiar y pegar en el servidor de NodeJS.</p>
    <div>
        <p style="text-align:center"><image
        src="./Img/ConexionBaseMongo.png" alt="Conexión a Base de Datos MongoDB" align="center" width="700px">
        <p id="imagen42" style="text-align:center;font-size:0.8rem"><i>Imagen 42 Conexión a Base de Datos MongoDB</i></p>
    </div>
    <p>También se requiere un usuario y contraseña, para administrar los usuarios de las bases de datos, se debe ir a Database Access.</p>
    <div>
        <p style="text-align:center"><image
        src="./Img/InformacionUsuariosMongo.png" alt="Información de Usuarios en MongoDB" align="center" width="700px">
        <p id="imagen43" style="text-align:center;font-size:0.8rem"><i>Imagen 43 Información de Usuarios en MongoDB</i></p>
    </div>
    <p>Es posible crear la base de datos con el nombre que se requiera.</p>
    <div>
        <p style="text-align:center"><image
        src="./Img/CrearBaseMongo.png" alt="Crear Base de Datos en MongoDB" align="center" width="700px">
        <p id="imagen44" style="text-align:center;font-size:0.8rem"><i>Imagen 44 Crear Base de Datos MongoDB</i></p>
    </div>
    <p>y sus respectivas colecciones:</p>
    <div>
        <p style="text-align:center"><image
        src="./Img/ListaColeccionesMongo.png" alt="Lista de Colecciones en MongoDB" align="center" width="700px">
        <p id="imagen45" style="text-align:center;font-size:0.8rem"><i>Imagen 45 Lista de Colecciones en MongoDB</i></p>
    </div>
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
    <b><li id="conectividad">Conectividad con NodeJS</li></b>
    <p>NodeJS es una tecnología backend basada en JavaScript, para conectarse a la base de datos se usa un archivo server.js. Previo a esto debe instalarse la librería correspondiente mediante el gestor de paquetes para poder ser importada en el archivo, como se ve a continuación en la Imagen 33.</p>
    <div>
        <p style="text-align:center"><image
        src="./Img/ConexionMongoyNode.png" alt="Conexión a MongoDB en NodeJS" align="center" width="700px">
        <p id="imagen46" style="text-align:center;font-size:0.8rem"><i>Imagen 46 Conexión a MongoDB en NodeJS</i></p>
    </div>
    <b><li id="buscardatos">Búscar, Insertar, Actualizar y Eliminar Registros</li></b>
    <ol>
        <li>Buscar Datos</li>
        <p>Para buscar documentos en nuestra base de datos, utilizaremos el comando find. La sintaxis es la que se muestra a continuación, el primer parámetro es el nombre de la colección y el último se refiere a los atributos a buscar en ella en formato JSON.</p>
        <i><p>dbmongo.collection("collection").find({ key: "value" })</p></i>
        <li>Insertar Datos</li>
        <p>Insertar documentos es muy sencillo. Como parámetro recibe el objeto JSON que se quiere insertar con la función insertOne o insertMany, junto con una función callback que se ejecuta cuando finaliza la inserción.</p>
        <i>dbmongo.collection("collection").insertOne({ key: “value” }, function (err, r) {
        <p style="margin-left:1rem">if (err) {</p>
        <p style="margin-left:2rem">res.send({ success: false });</p>
        <p style="margin-left:1rem">} else {</p>
        <p style="margin-left:2rem">console.log("record created")</p>
        <p style="margin-left:1rem">}</p>
        <p>});</p></i>
        <li>Eliminación de Datos</li>
        <p>Para eliminar datos de una colección, se utiliza el comando deleteOne, recibe como parámetro la consulta para filtrar los registros de la colección y elimina la primera coincidencia. También es posible usar el comando deleteMany, si no especificamos ninguna consulta, se eliminarán todos los datos de la colección.</p>
        <i><p>dbmongo.collection("collection").deleteOne({ key: “value” })</p></i>
        <li>Actualización de Datos</li>
        <p>Para actualizar datos, se usa el comando findOneAndUpdate. Este comando, recibe tres parámetros: el primero con la consulta para filtrar los documentos a modificar, el segundo con los elementos que se modificarán, y el tercero opcionalmente permite definir el comportamiento de retorno de la consulta, en el ejemplo permite definir que el elemento retornado sea el documento con los datos actualizados recientemente</p>
        <i><p>dbmongo.collection("collection").findOneAndUpdate({ "chat_id": from }, {</p>
        <p style="margin-left:1rem">$set: { "status": context?.status }</p>
        <p>})}, { returnDocument: “after” })</p>
        </i>
    </ol>
</ol>
<h5 id="nodejs"></h5>

##### <h5 style="font-size: 18.2px; margin-left:1.2rem">V. NodeJS Backend (API)</h5>

<p style="margin-left:2rem">Node.js es un entorno de ejecución de JavaScript que permite el desarrollo de aplicaciones JavaScript en el lado del servidor. Este entorno de ejecución en tiempo real incluye todo lo que se necesita para ejecutar un programa escrito en JavaScript.</p>

<p style="margin-left:2rem">Node.js utiliza un modelo de entrada y salida sin bloqueo controlado por eventos que lo hace ligero y eficiente (entrada se refiere a solicitudes y salida a respuestas).</p>

<p style="margin-left:2rem">El proyecto de NodeJS del backend está desarrollado sobre la versión 16 LTS de Node.JS. Utilizando algunas dependencias principales como express para el manejo de solicitudes HTTP, o cloudant de IBM Cloud para la conexión con Watson Assistant. Así como también las librerías de conexión de MongoDB y 360 Dialog para JavaScript, entre otras.</p>

<p style="margin-left:2rem">A continuación, se muestran los pasos para poder descargar, ejecutar y compilar el proyecto:</p>

<ol style="margin-left:2rem" type="a">
    <b><li id="clonandorepositorio">Clonando el Repositorio</li></b>
    <p><i>git clone git@github.com:chatbotsONU-UECCI/chatbot_ECCI.git</i></p>
    <b><li id="instalandodependencias">Instalando Dependencias</li></b>
    <p><i>cd chatbotECCI/</i>></p>
    <p style="margin-top:-18px"><i>yarn install</i></p>
    <b><li id="ejecutarproyecto">Ejecutar el Proyecto en Desarrollo</li></b>
    <p><i>yarn start</i></p>
    <p><b>Nota: </b>Este comando crea un servidor de desarrollo que estará escuchando peticiones y ejecutando acciones según las peticiones recibidas. Este servidor se ejecuta por defecto en http://localhost/3000</p>
    <b><li id="subiendoproyecto">Subiendo el Proyecto a Producción</li></b>
    <p><i>ibmcloud cf push</i></p>
    <p><b>Nota: </b>El backend del proyecto no necesita ser compilado antes de ser subido al servicio de Cloud Foundry, sin embargo, el Frontend si debe ser compilado en la ruta chatbotECCI/front/build/ para poder ser direccionado por el backend, quien se encarga de habilitar las rutas disponibles de la plataforma web.</p>
    <p>Este comando sólo puede ser ejecutado después de registrarse en la interfaz de línea de comandos de ibm cloud. En las siguientes secciones se detalla más acerca del servicio de cloud foundry y la instalación del CLI de ibm cloud.</p>
    <b><li id="EstructuraArchivos">Estructura de Archivos del Proyecto</li></b>
    <div>
        <p style="text-align:center"><image
        src="./Img/EstructuradeArchivos.png" alt="Estructura de Archivos Backend" align="center" width="200px">
        <p id="imagen47" style="text-align:center;font-size:0.8rem"><i>Imagen 47 Estructura de Archivos Backend</i></p>
    </div>
    <p>En la imagen 34 se puede apreciar la estructura de archivos para el componente Backend, la cual se compone principalmente de:</p>
    <ul type="square">
        <li><b>bubble_chat/</b> Directorio del componente frontend del proyecto.</li>
        <li><b>documentation/</b> Directorio donde se encuentra la documentación técnica del proyecto.</li>
        <li><b>front/</b> Directorio del componente frontend del proyecto.</li>
        <li><b>kubernets/</b> Contiene el archivo .yaml de despliegue del proyecto, viene del proyecto plantilla de ibm, no es necesario modificarlo.</li>
        <li><b>node_modules/</b> Directorio donde se almacenan las librerías y dependencias de nodeJS necesarias para la ejecución del proyecto.</li>
        <li><b>views/</b> Carpeta para vistas, debido a que esta parte del proyecto es un backend puro, no es necesario modificarla.</li>
        <li><b>Dockerfile</b> Archivo Dockerfile que define la creación del contenedor que se desplegará en Cloud Foundry.</li>
        <li><b>manifest.yml</b> Archivo .yml que define las configuraciones de despliegue del servicio de Cloud Foundry en la nube de IBM.</li>
        <li><b>package.json</b> Define las características del proyecto nodeJS, como sus dependencias y versiones utilizadas.</li>
        <li><b>server.js</b> Archivo principal del proyecto, en él se encuentra el código fuente del backend para ser desplegado.</li>
    </ul><br>
    <p><b>Nota: </b>El resto de documentos no mencionados anteriormente no hacen parte del core del proyecto, sino que vienen desde la plantilla de IBM Cloud para aplicaciones node en Cloud Foundry, y no es necesario modificarlos.</p>
    <b><li id="ServiciosAPI">Servicios API Rest</li></b>
    <p>Dentro del backend actualmente se tienen implementados los siguientes servicios API Rest:</p>
    <ul type="square">
        <li>Servicio recepción mensajes 360 Dialog. “/inbound”</li><br>
        <div>
        <p style="text-align:center"><image
        src="./Img/ServicioConexionWhatsapp.png" alt="Servicio de Conexión Whatsapp" align="center" width="700px">
        <p id="imagen48" style="text-align:center;font-size:0.8rem"><i>Imagen 48 Servicio de Conexión Whatsapp</i></p>
        </div>
    <p>Este servicio es llamado por 360 Dialog al momento de recibir un mensaje por parte de un usuario. La información obtenida es el número del usuario, a que número va dirigido y el cuerpo del mensaje de tipo texto.</p>
    <p>Al recibir un mensaje se verifica dentro de la base de datos que exista una sesión vigente del número del usuario si no existe una sesión se le envía a Watson Assistant con la utilización de la siguiente función del API de Watson Assistant:</p>
    <i><p>assistant.createSession({ </p>
    <p style="margin-left:1.5rem">assistantId: 'xxxx-xxx-xxx-xxx'</p>
    <p>}).then(res => {</p>
    <p style="margin-left:1.5rem">console.log(JSON.stringify(res, null, 2)); </p>
    <p>}).catch(err => {</p>
    <p style="margin-left:1.5rem">console.log(err);</p>
    <p>});</p>
    </i>
    <p>La cual responde con un número de sesión que se almacenará en la colección “sessions” de la base de datos MongoDB para manejar las sesiones de los usuarios.</p>
    <div>
        <p style="text-align:center"><image
        src="./Img/GuardarSesionConversacion.png" alt="Guardar Sesión de Conversación" align="center" width="700px">
        <p id="imagen49" style="text-align:center;font-size:0.8rem"><i>Imagen 49 Guardar Sesión de Conversación</i></p>
    </div>
    <p>Cuando ya existe una sesión del usuario con Watson Assistant envía el mensaje recibido de 360 Dialog a Watson Assistant con la siguiente función:</p>
    <i>
    <p>assistant.message({ </p>
    <p style="margin-left:1.5rem">assistantId: '{assistant_id}',</p>
    <p style="margin-left:1.5rem">sessionId: '{session_id}',</p>
    <p style="margin-left:1.5rem">input: {</p>
    <p style="margin-left:3rem">message_type': 'text',</p>
    <p style="margin-left: 3rem">'text': 'Hello'</p>
    <p style="margin-left:1.5rem">}</p>
    <p>}).then(res => {</p>
    <p style="margin-left:1.5rem">console.log(JSON.stringify(res.result, null, 2)); </p>
    <p>}).catch(err => { </p>
    <p style="margin-left: 1.5rem">console.log(err);</p>
    <p>});</p></i>
    <div>
        <p style="text-align:center"><image
        src="./Img/EnvioMensajes360Dialog.png" alt="Envío de Mensajes a 360 Dialog" align="center" width="700px">
        <p id="imagen50" style="text-align:center;font-size:0.8rem"><i>Imagen 50 Envío de Mensajes a 360 Dialog</i></p>
    </div>
    <p>Dentro del servicio API Rest “/inbound” se valida a qué pregunta está respondiendo el usuario, o si se encuentra dentro de alguna categoría del menú dependiendo del contexto de la conversación y la sección que se encuentra en la colección “sessions”.</p>
    <div>
        <p style="text-align:center"><image
        src="./Img/DireccionamientoConversacion.png" alt="Direccionamiento de Conversación Según la Sección" align="center" width="700px">
        <p id="imagen51" style="text-align:center;font-size:0.8rem"><i>Imagen 51 Direccionamiento de Conversación Según la Sección.</i></p>
    </div>
    <p>Además, se valida si el usuario accede a una conversación con un agente, se consultan los agentes disponibles y se establece la conexión con el primer agente disponible encontrado, al cual el bot le notifica y le pregunta si desea o no atender al usuario. Si acepta se actualizarán los datos de las sesiones y el agente podrá escribirle al usuario para atender su consulta, si no, el bot buscará otro agente disponible y liberará al agente que rechazó atender al usuario. El detalle de este comportamiento se encuentra dentro de la función “connectToAgent” mostrada en la Imagen 39.</p>
    <div>
        <p style="text-align:center"><image
        src="./Img/ConectarAgente.png" alt="Conectar con Agente" align="center" width="700px">
        <p id="imagen52" style="text-align:center;font-size:0.8rem"><i>Imagen 52 Conectar con Agente.</i></p>
    </div>
    <p>Si el bot no comprende el mensaje, el api no devolverá ninguna intención o entidad, en este caso se guardará en la base de datos en la colección “othersmessages” el mensaje del usuario.</p>
    <div>
        <p style="text-align:center"><image
        src="./Img/GuardarMensajesNoComprendidos.png" alt="Guardar Mensajes no Comprendidos" align="center" width="700px">
        <p id="imagen53" style="text-align:center;font-size:0.8rem"><i>Imagen 53 Guardar Mensajes no Comprendidos.</i></p>
    </div>
    <p>Cuando un usuario que ya tiene una sesión creada interactúa nuevamente con el bot se actualiza la fecha para mantener la sesión activa.</p>
    <li>Servicio para la Recepción de Mensajes Whatsapp desde 360 Dialog.</li><br>
    <div>
        <p style="text-align:center"><image
        src="./Img/ServicioConexionWhatsappy360.png" alt="Servicio de Conexión de Whatsapp con 360 Dialog" align="center" width="700px">
        <p id="imagen54" style="text-align:center;font-size:0.8rem"><i>Imagen 54 Servicio de Conexión de Whatsapp con 360 Dialog</i></p>
    </div>
    <p>Este servicio escucha las peticiones realizadas desde el API de Whatsapp cuando un bot configurado con la url del endpoint recibe un mensaje, gestiona la comunicación del chatbot a través de la plataforma de Whatsapp desde la API de 360 Dialog.</p>
    <P>Este endpoint gestiona toda la lógica de recepción de mensajes y pre procesado de multimedia para enviar el mensaje recibido desde 360 Dialog al flujo de conversación de watson assistant.</P>
    <li>Servicio para la Recepción de Mensajes Whatsapp Sandbox desde 360 Dialog</li><br>
    <div>
        <p style="text-align:center"><image
        src="./Img/RecepcionMensajesWhatsapp.png" alt="Recepción de Mensajes de Whatsapp desde 360 Dialog" align="center" width="700px">
        <p id="imagen55" style="text-align:center;font-size:0.8rem"><i>Imagen 55 Recepción de Mensajes de Whatsapp desde 360 Dialog</i></p>
    </div>
    <p>Este servicio escucha las peticiones realizadas desde el API de Whatsapp para el número sandbox de 360 Dialog, gestiona la comunicación del chatbot a través de la plataforma de Whatsapp desde la API de 360 Dialog. Es necesario verificar un token individual para cada usuario del sandbox habilitado.</p>
    <p>Este endpoint gestiona toda la lógica de recepción de mensajes y preprocesado de multimedia para enviar el mensaje recibido desde el sandbox de 360 Dialog al flujo de conversación de watson assistant.</p>
    <li>Servicios para la Configuración y Consulta del Webhook del Sandbox de 360 Dialog</li><br>
    <div>
        <p style="text-align:center"><image
        src="./Img/Weebhook360Dialog.png" alt="Servicio de conexión Whatsapp Sandbox - 360 Dialog - Webhook" align="center" width="700px">
        <p id="imagen56" style="text-align:center;font-size:0.8rem"><i>Imagen 56 Servicio de conexión Whatsapp Sandbox - 360 Dialog - Webhook</i></p>
    </div>
    <p>Estos servicios permiten la consulta y actualización de la url del webhook del sandbox de 360 Dialog.</p>
    <li>Servicios para la Configuración y Consulta del Webhook del Número de Producción de 360 Dialog</li><br>
    <div>
        <p style="text-align:center"><image
        src="./Img/WeebhookProduccion360.png" alt="Servicio de conexión Whatsapp Sandbox - 360 Dialog" align="center" width="700px">
        <p id="imagen57" style="text-align:center;font-size:0.8rem"><i>Imagen 57 Servicio de conexión Whatsapp Sandbox - 360 Dialog - Weebhook Número de Producción</i></p>
    </div>   
    <p>Estos servicios permiten la consulta y actualización de la url del webhook del número de producción de 360 Dialog.</p>
    <li>Servicio para la Recepción de Mensajes Telegram</li><br>
    <p>Este servicio escucha las peticiones realizadas desde el API de Whatsapp para el número sandbox de 360 Dialog, gestiona la comunicación del chatbot a través de la plataforma de Whatsapp desde la API de 360 Dialog. Es necesario verificar un token individual para cada usuario del sandbox habilitado.</p>
    <p>Este endpoint gestiona toda la lógica de recepción de mensajes y preprocesado de multimedia para enviar el mensaje recibido desde el sandbox de 360 Dialog al flujo de conversación de watson assistant.</p>
    <div>
        <p style="text-align:center"><image
        src="./Img/ServicioConexionTelegram.png" alt="Servicio de Conexión Telegram" align="center" width="700px">
        <p id="imagen58" style="text-align:center;font-size:0.8rem"><i>Imagen 58 Servicio de Conexión Telegram.</i></p>
    </div>
    <p>Este servicio escucha las peticiones realizadas desde el API de Telegram cuando un bot configurado con la url del endpoint recibe un mensaje, gestiona la comunicación del chatbot a través de la plataforma de Telegram. Actualmente está orientado exclusivamente al rol de agentes y tiene un comportamiento similar al de los agentes en whatsapp, con las particularidades requeridas por la plataforma de Telegram para la interacción de mensajes.</p>
    <li>Consulta de información para métricas Frontend</li>
    <p>El backend también gestiona las consultas realizadas por la interfaz web que permite conocer estadísticas e información importante acerca de los datos almacenados por el chatbot. Estas consultas son realizadas con base en un periodo de fechas determinado, el cual es recibido por el backend en formato JSON, como se ve en la Imagen 42.</p>
    <div>
        <p style="text-align:center"><image
        src="./Img/EndpointConsultaMetricas.png" alt="Ejemplo de Endpoint de Consulta de Métricas" align="center" width="700px">
        <p id="imagen59" style="text-align:center;font-size:0.8rem"><i>Imagen 59 Ejemplo de Endpoint de Consulta de Métricas.</i></p>
    </div>
    <p>El endpoint recibe un objeto json con los campos necesarios para la consulta, con ellos el backend realiza la consulta específica para cada petición, la procesa y retorna la respuesta en formato JSON. Así como el ejemplo mostrado, se pueden encontrar los siguientes endpoints de consulta para la interfaz de métricas desde el backend:</p>
    <ol>
<li><b>/getsede:</b> Endpoint de consultas por cada sede disponible.</li>
<li><b>/getcatsmenu:</b> Endpoint de consultas por cada categoría del menú principal.</li>
<li><b>/getsolution:</b> Endpoint de respuestas a la pregunta de satisfacción.</li>
<li><b>/getservicequalification:</b> Endpoint de respuestas a la encuesta de calificación del servicio.</li>
<li><b>/getsenttemplates:</b> Endpoint de consulta de los mensajes plantilla enviados desde la plataforma.</li>
<li><b>/getgeneral:</b> Endpoint para el total de mensajes registrados por día.</li>
<li><b>/getmessagesbyhour:</b> Endpoint para consultar el número de mensajes por hora en un mismo día.</li>
<li><b>/getothermessages:</b> Endpoint de mensajes no comprendidos por el chatbot.</li>
<li><b>/getvisits:</b> Endpoint que retorna el número de usuarios del chatbot por día.</li>
<li><b>/getchatsbyagent:</b> Endpoint para la consulta de mensajes atendidos por cada agente.</li>
<li><b>/gettransfered:</b> Endpoint que retorna el total de chats transferidos a agentes.</li>
<li><b>/getbotvsagents:</b> Endpoint para el total de chats atendidos por el bot versus el total de chats atendidos por agentes.</li>
<li><b>/getchatsbyprogram:</b> Endpoint para el total de consultas realizadas por cada programa académico.</li>
<li><b>/getrequestsbysection:</b> Endpoint de consultas por cada subsección dentro de una categoría principal.</li>
<li><b>/getresponsetimeagents:</b> Endpoint que retorna los tiempos de respuesta promedio de cada agente.</li>
<li><b>/requestreport:</b> Endpoint para la generación de reportes descargables en formato .csv</li>
<li><b>/requesttemplates:</b> Endpoint para la consulta de plantillas disponibles para su envío masivo desde la plataforma web.</li>
<li><b>/savetemplate:</b> Endpoint que permite el registro de nuevas plantillas de mensajes para envíos masivos.</li>
<li><b>/sendtemplates:</b> Endpoint para el envío de mensajes plantilla a números de Whatsapp.</li>
<li><b>/statuscallback:</b> Endpoint que recibe el estado de los mensajes plantilla enviados mediante la plataforma web para su posterior consulta.</li>
<li><b>/getcallback:</b> Endpoint que retorna los estados de los mensajes plantilla enviados a la plataforma web como retroalimentación del envío masivo.</li>
<li><b>/statuscallbackretake:</b> Endpoint que recibe el estado de un intento de retoma de usuario por parte de un agente para su posterior consulta.</li>
<li><b>/getcallbackretake:</b> Endpoint que retorna el estado de los mensajes enviados para la retoma de un usuario por parte de un agente como retroalimentación para éste.</li>
<li><b>/requestusers:</b> Endpoint para la consulta de información de los usuarios en la plataforma web.</li>
<li><b>/getuserbyid:</b> Endpoint que permite la consulta detallada de la información de un usuario.</li>
<li><b>/saveuser:</b> Endpoint para la actualización de datos de un usuario.</li>
<li><b>/deleteuser:</b> Endpoint para la eliminación de un usuario del sistema.</li>
<li><b>/deleteusers:</b> Endpoint para la eliminación masiva de usuarios del sistema.</li>
<li><b>/updateUserProfile:</b> Permite la actualización de datos de un usuario.</li>
<li><b>/createticket:</b> Endpoint que permite crear nuevos tickets en la plataforma.</li>
<li><b>/requesttickets:</b> Endpoint que realiza la consulta de información de tickets en la aplicación.</li>
<li><b>/updateticketstatus:</b> Endpoint para la actualización del estado de un ticket.</li>
<li><b>/updatetickettags:</b> Endpoint para la actualización de las etiquetas de un ticket.</li>
<li><b>/updateticketsede:</b> Endpoint para la actualización de la sede de un ticket.</li>
<li><b>/updateticketagent:</b> Endpoint para la actualización del agente asignado a un ticket.</li>
<li><b>/getticket:</b> Permite la consulta de un ticket basado en su id.</li>
<li><b>/getagent:</b> Permite la consulta de un agente basado en su id.</li>
<li><b>/getagents:</b> Endpoint para la consulta de agentes disponibles en la plataforma web.</li>
<li><b>/setagentstatus:</b> Endpoint que permite configurar el estado de un agente en la plataforma.</li>
<li><b>/updatepasswordagent:</b> Endpoint que permite el cambio de clave de un usuario en la plataforma web.</li>
<li><b>/saveagent:</b> Endpoint para la inserción o actualización de un agente chatbot.</li>
<li><b>/deteleagent:</b> Endpoint que permite la eliminación de un agente chatbot del sistema.</li>
<li><b>/deleteagents:</b> Endpoint que gestiona la eliminación masiva de agentes.</li>
<li><b>/getcompetences:</b> Endpoint para la consulta de áreas de competencias o programas académicos disponibles para asignar a agentes.</li>
<li><b>/savecompetence:</b> Endpoint para la creación de nuevas áreas de competencia o programas académicos para agentes.</li>
<li><b>/deletecompetence:</b> Endpoint para la eliminación única de competencias.</li>
<li><b>/deletecompetences:</b> Endpoint que permite la eliminación masiva de competencias.</li>
<li><b>/gettags:</b> Endpoint para la consulta de etiquetas para los tickets.</li>
<li><b>/savetag:</b> Endpoint para la creación de nuevas etiquetas de tickets</li>
<li><b>/deletetag:</b> Endpoint para la eliminación de etiquetas.</li>
<li><b>/deletetags:</b> Endpoint para la eliminación masiva de etiquetas</li>
<li><b>/getmessages:</b> Endpoint para la consulta de mensajes asociados a un ticket.</li>
    </ol><br>
    <p>Por último, el backend utiliza express como middleware para habilitar las rutas correspondientes a la plataforma web Frontend, apuntando al directorio build generado por la compilación del componente Frontend del proyecto, explicado en la siguiente sección. A continuación, se muestra el fragmento de código que habilita esta característica en la Imagen 43.</p>
    <div>
        <p style="text-align:center"><image
        src="./Img/ConexionMiddlewareFrontend.png" alt="Conexión Middleware con Frontend" align="center" width="700px">
        <p id="imagen60" style="text-align:center;font-size:0.8rem"><i>Imagen 60 Conexión Middleware con Frontend.</i></p>
    </div>
    </ul>
</ol>
<h5 id="reactjs"></h5>

##### <h5 style="font-size: 18.2px; margin-left:1.2rem">VI. ReactJS Frontend (Métricas)</h5>

<p style="margin-left:2rem">El componente Frontend del proyecto permite el levantamiento de una plataforma web para la visualización de métricas estadísticas básicas acerca de la usabilidad del Chatbot por los usuarios, identificar de mejor manera la población que hace uso de la herramienta, qué categorías son las más visitadas, entre otras. Así como el registro de los mensajes que no son comprendidos por el bot mes a mes.</p>
<p style="margin-left:2rem">A continuación, se muestran los pasos para poder descargar, ejecutar y compilar el proyecto:</p>
<ol style="margin-left:2rem" type="a">
<b><li id="clonandorepositoriofront">Clonando el Repositorio</li></b>
<i><p>git clone git@github.com:chatbotsONU-UECCI/chatbotECCI.git</p></i>
<b><li id="instalandodependeciasfront">Instalando Dependencias</li></b>
<i><p>cd chatbotECCI/front/</p></i>
<p><b>Nota:</b> Debe ubicarse en la ubicación del "front" del proyecto para ejecutar este componente.</p>
<i><p>yarn install</p></i>
<b><li id="ejecutarproyectofront">Ejecutar el Proyecto en Desarrollo</li></b>
<i><p>yarn start</p></i>
<p><b>Nota: </b>Este comando crea un servidor de desarrollo para visualizar la plataforma web, este servidor se ejecuta por defecto en http://localhost/3000</p>
<div>
    <p style="text-align:center"><image
    src="./Img/PaginaPrincipalFront.png" alt="Página Principal Frontend" align="center" width="700px">
    <p id="imagen61" style="text-align:center;font-size:0.8rem"><i>Imagen 61 Página Principal Frontend.</i></p>
</div>
<b><li id="compilandoproyectofront">Compilando el Proyecto para Producción</li></b>
<i><p>yarn run build</p></i>
<p><b>Nota: </b>ste comando crea un nuevo directorio llamado "build" que es usado por el Backend para ser desplegado en las rutas correspondientes.</p>
<b><li id="estructuraarchivosfront">Estructura de Archivos del Proyecto</li></b>
<div>
    <p style="text-align:center"><image
    src="./Img/EstructuraArchivosFrontend.png" alt="Estructura de Archivos Frontend" align="center" width="200px">
    <p id="imagen62" style="text-align:center;font-size:0.8rem"><i>Imagen 62 Estructura de Archivos Frontend.</i></p>
</div>
<p>En la Imagen 45 se puede apreciar la estructura de archivos para el componente Frontend, la cual se compone principalmente de:</p>
<ul type="disc">
<li><b>build/</b> Directorio en donde se almacenan los archivos compilados del proyecto para su despliegue.</li>
<li><b>node_modules/</b> Directorio donde se almacenan las librerías y dependencias de nodeJS necesarias para la ejecución del proyecto.</li>
<li><b>public/</b> Directorio donde se encuentra el <i>index.html</i> del proyecto.</li>
<li><b>src/</b> Directorio donde se encuentra todo el código fuente del proyecto.</li>
<ul type="circle">
<li><b>assets/</b> Directorio donde se almacenan los archivos estáticos del proyecto (imágenes, estilos, fuentes, etc).</li>
<li><b>components/</b> Directorio donde se encuentran todos los componentes del proyecto.</li>
<li><b>layouts/</b> Directorio para los marcos de estructura de la página web.</li>
<li><b>variables/</b> Carpeta donde se encuentran los archivos de configuración base del proyecto.</li>
<li><b>views/</b> Directorio en donde se almacenan las distintas vistas de la página web.</li>
<li><b>index.js</b> Archivo principal del proyecto de ReactJS.</li>
<li><b>routes.js</b> rchivo donde se definen las rutas públicas de la página web.</li>
<li><b>package.json</b> Archivo de definición del proyecto, contiene la información necesaria para ejecutar el proyecto.</li>
</ul>
</ul>
</ol>
<h5 id="ibmcloudfonundry"></h5>

##### <h5 style="font-size: 18.2px; margin-left:1.2rem">VII. ReactJS Frontend (Métricas)</h5>

<p style="margin-left:2rem">IBM Cloud Foundry es un servicio perteneciente a IBM Cloud, que permite crear instancias de varias plataformas de Cloud Foundry aisladas y con recursos a petición. Instancias de la ejecución de servicio de IBM Cloud Foundry Enterprise en su cuenta de IBM Cloud. El entorno se despliega en hardware aislado (clústeres de Kubernetes). Tiene un control completo sobre el entorno, que incluye el control de accesos, la capacidad, las actualizaciones de versiones, el uso de recursos y la supervisión. Además, la integración de Cloud Foundry en IBM Cloud permite a los desarrolladores aprovechar los servicios disponibles en su cuenta de IBM Cloud.</p>
<p style="margin-left:2rem">Para poder usar el servicio de IBM® Cloud Foundry se necesita instalar CLI siguiendo las instrucciones que se encuentra en:</p>
<p style="margin-left:2rem" >
<a href="https://docs.cloudfoundry.org/cf-cli/install-go-cli.html">https://docs.cloudfoundry.org/cf-cli/install-go-cli.html</a></p>
<p style="margin-left:2rem">Para poder crear una instancia de SDK de NodeJS basada en Cloud Foundry, se debe buscar el servicio. Luego se selecciona el plan con el cual se va a trabajar, en este caso se selecciona el plan Lite que no tiene ningún costo pero que tiene como limitante un espacio de 256MB.</p>
<div>
    <p style="text-align:center"><image
    src="./Img/CreacionServicioCloud.png" alt="Creación de Servicio de Cloud Foundry 1" align="center" width="700px">
    <p id="imagen63" style="text-align:center;font-size:0.8rem"><i>Imagen 63 Creación de Servicio de Cloud Foundry 1.</i></p>
</div>
<div>
    <p style="text-align:center"><image
    src="./Img/CreacionServicioCloud2.png" alt="Creación de Servicio de Cloud Foundry 2" align="center" width="700px">
    <p id="imagen64" style="text-align:center;font-size:0.8rem"><i>Imagen 64 Creación de Servicio de Cloud Foundry 2.</i></p>
</div>
<p style="margin-left:2rem">Al crear el servicio, se redirigirá a la información de este, donde también se podrá descargar un proyecto base para que pueda ser modificado y desplegado con Cloud Foundry y se podrá administrar las rutas de acceso y el nombre.</p>
<p style="margin-left:2rem">Además de las instrucciones para loguearse desde nuestra máquina con el usuario y contraseña de nuestra cuenta. Este paso es necesario para poder subir el proyecto a la instancia creada.</p>
<div>
    <p style="text-align:center"><image
    src="./Img/DescripcionDespliegueCloud.png" alt="Descripción de Despliegue de Cloud Foundry en IBM Cloud" align="center" width="700px">
    <p id="imagen65" style="text-align:center;font-size:0.8rem"><i>Imagen 65 Descripción de Despliegue de Cloud Foundry en IBM Cloud.</i></p>
</div>
<div>
    <p style="text-align:center"><image
    src="./Img/DescripcionInstanciaCloud.png" alt="Descripción de Instancia de Cloud Foundry 
    en Ejecución" align="center" width="700px">
    <p id="imagen66" style="text-align:center;font-size:0.8rem"><i>Imagen 66 Descripción de Instancia de Cloud Foundry 
    en Ejecución.</i></p>
</div>
<p style="margin-left:2rem">Para poder subir el servicio es necesario que el proyecto tenga un archivo manifest.yml el cual contenga los datos del servicio creado.</p>
<div>
    <p style="text-align:center"><image
    src="./Img/ArchivoConfiguracionDespliegue.png" alt="Archivo de Configuración de Despliegue en Cloud Foundry" align="center" width="700px">
    <p id="imagen67" style="text-align:center;font-size:0.8rem"><i>Imagen 67 Archivo de Configuración de Despliegue en Cloud Foundry.</i></p>
</div>
<p style="margin-left:2rem">Para subir el proyecto en la instancia de NodeJS se usa el comando</p>
<p style="margin-left:2rem"><i>cf push chatbot_ecci</i></p>
<p style="margin-left:2rem">Por último, es posible visualizar los logs de la instancia de NodeJS usando el comando</p>
<p style="margin-left:2rem"><i>cf logs chatbot_ecci</i></p>

<h4 id="balance"></h4>
#### 5. Balance de Operación Chatbot

<p style="margin-left:2rem">La herramienta Chatbot se entrega en un estado completamente operativo, con los contenidos actualizados según disposición del territorio, con las cuentas activas y en regla para cada uno de los requerimientos del sistema.</p>
<p style="margin-left:2rem">De la misma forma están funcionando todos los componentes de la arquitectura a cabalidad, generando una solución interactiva, intuitiva y de fácil uso a través de Whatsapp. Y con componentes de análisis de usabilidad, registro de respuestas y visualización de las mismas mediante una plataforma web accesible desde internet en cualquier momento.</p>
<h5 id="dificultades"></h5>

##### <h5 style="font-size: 18.2px; margin-left:1.2rem">I. Posibles Dificultades</h5>

<ol style="margin-left:2rem" type="a">
    <b><li id="CurvaAprendizaje">Curva de Aprendizaje de Tecnologías</li></b>
    <p>Las principales dificultades presentadas en la administración y mantenimiento del proyecto pueden deberse especialmente a la curva de aprendizaje de las tecnologías empleadas en el mismo.</p>
    <p>Para esto se recomienda mucho el hábito de visitar la documentación oficial de las tecnologías cuando sea una duda específica, o para revisar las múltiples guías, tutoriales y narrativa documental de las herramientas. De la misma forma es muy recomendable revisar videotutoriales, mini cursos, blogs y diversos recursos disponibles en la web para poder documentarse apropiadamente y avanzar en la apropiación de las múltiples tecnologías tratadas.</p>
    <p>Actualmente el lenguaje no es una barrera significativa, en YouTube directamente se pueden encontrar diversos recursos audiovisuales en español que pueden ser muy útiles para entender o ver una explicación más detallada de algún tema técnico que no se comprenda completamente. Sin embargo, siempre que se pueda remitirse a documentación en inglés se puede acceder a un conjunto significativamente mayor de recursos, respuestas, y enlaces útiles.</p>
    <b><li id="IBMCloud">IBM Cloud Lite</li></b>
    <p>Por otra parte, una eventual dificultad que pueda presentarse es que los servicios alojados en IBM se apaguen, o en el peor de los casos se supriman, debido a un periodo prolongado de inactividad en el uso de los servicios desplegados.</p>
    <p>Para evitar estas situaciones lo que se recomienda es realizar una revisión periódica de los servicios, utilizando los servicios por lo menos para efectos de pruebas de funcionalidad, y que no se genere una interrupción en el servicio debido al no uso de la herramienta. En la sección de recomendaciones se detallará más información al respecto.</p>
    <p>De igual forma, si se genera una alta demanda de uso del servicio, es posible que llegue a exceder la capacidad de memoria de la instancia que soporta los componentes backend y frontend del sistema. Si esto llega a ocurrir quiere decir que el sistema ha tenido una acogida muy grande, y vale la pena evaluar el actualizar la cuenta de IBM Cloud a un plan de pago, para mejorar las capacidades de este y todos los servicios de IBM Cloud.</p>
    <p>Por último, en un caso extremo de eliminación de uno de los recursos de Watson Assistant u Object Storage, se deben recrear los servicios, y subir tanto los archivos estáticos de los recursos e imágenes, como el diálogo del Chatbot a Watson Assistant. Si el servicio eliminado es el de Object Storage, posiblemente se deban actualizar las urls de las imágenes en el flujo del Bot debido a que se re-subieron a un servicio nuevo.</p>
</ol>
<h5 id="recomendaciones"></h5>

##### <h5 style="font-size: 18.2px; margin-left:1.2rem">II. Recomendaciones</h5>

<p style="margin-left:2rem">A continuación, se mencionan algunas recomendaciones a tener en cuenta para la administración, mantenimiento y extensibilidad del proyecto.</p>
<p style="margin-left:2rem">En primer lugar, es importante recordar que el proyecto está pensado en un principio para generar costos mínimos en cuanto al sostenimiento del sistema, para ello, se hace uso de ciertos planes gratuitos que ofrecen algunas plataformas, para aprovechar los recursos limitados disponibles en estos planes de uso y generar un producto final económico, sustentable y extensible en sus primeras etapas de lanzamiento, según las necesidades del territorio.</p>
<p style="margin-left:2rem">Debido a esto, es posible que, a futuro, según el crecimiento y acogida de la plataforma en el territorio, pueden verse excedidos los límites de uso de los planes gratuitos, en cuyo caso debe evaluarse el ampliamiento de recursos de las plataformas, posiblemente en un plan de pago, que aunque genera un cobro, sigue siendo mínimo y bajo demanda, según el uso que se le dé al servicio del Chatbot.</p>
<p style="margin-left:2rem">Por otra parte, en particular, para la plataforma de IBM Cloud, como se explicaba anteriormente, se está haciendo uso de los servicios bajo un plan de cuenta Lite para mantener su funcionamiento de forma gratuita. IBM tiene unas condiciones especiales de inactividad las cuales deben ser tenidas en cuenta especialmente para evitar bajas en el servicio debido a inactividad prolongada de uso. Para más información sobre estas restricciones de cuenta ver: <a href="https://www.ibm.com/es-es/cloud/free">https://www.ibm.com/es-es/cloud/free</a></p>
<p style="margin-left:2rem">De igual forma, se recomienda si se extienden las funcionalidades del Chatbot, mantener backups periódicos de los archivos de los diálogos de Watson Assistant en git, así como copias de las imágenes y recursos estáticos para poder tener una herramienta de recuperación del bot en un posible caso extremo de eliminación del recurso por inactividad mayor a 30 días</p>
<p style="margin-left:2rem"><b>Nota:</b> Esto ocurre por el uso del plan Lite gratuito de IBM Cloud, si se quiere evitar este riesgo por completo se puede actualizar el plan de IBM a un plan pago, y estas restricciones no serán aplicables.</p>