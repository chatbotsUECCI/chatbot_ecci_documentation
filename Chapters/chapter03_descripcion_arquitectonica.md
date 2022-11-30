#### 3. Descripción Arquitectónica

<div>
<p style="text-align:center"><image
src="./Img/ArquitecturaChatbotECCI.png" alt="Descripción Arquitectónica Chatbot para la Universidad ECCI" align="center" width="700px">
<p id="imagen1" style="text-align:center;font-size:0.8rem"><i>Imagen 1 Arquitectura Chatbot</i></p>
</div>

<p>En la Imagen 1 se observa la arquitectura de software del producto, la cual está basada en el servicio conversacional de IBM Watson, el cual permite crear flujos conversacionales inteligentes a través de la identificación de intenciones. A su vez, los demás componentes de la arquitectura están desplegados en algunos servicios de la nube de IBM, como IBM Object Storage para el almacenamiento de archivos estáticos o IBM Cloud Foundry para el despliegue de máquinas virtuales con entornos NodeJS</p>

<p>La persistencia de datos del proyecto está soportada sobre el servicio en la nube de MongoDB Atlas; el cual permite crear y administrar bases de datos no relacionales en la nube, con planes de servicio bajo demanda, brindando flexibilidad, disponibilidad y seguridad a los datos del proyecto</p>

<p>La arquitectura cuenta con un componente backend desarrollado en NodeJS, que permite la comunicación entre las demás partes del sistema y gestiona el almacenamiento de datos y la consulta de los mismos. Así como también una interfaz web que permite consultar, visualizar y analizar la información disponible y actualizada del uso del chatbot por los usuarios.</p>

<p>La conexión con el chatbot está disponible para los usuarios de Whatsapp a través de 360 Dialog, el cual es un proveedor de comunicaciones en la nube que cuenta con el servicio de mensajería de para Whatsapp, permitiendo la comunicación y administración de la cuenta y el canal de whatsapp, así como algunas características adicionales como soporte técnico, aprobación de plantillas para envíos masivos, gestión de números y cuentas de whatsapp, entre otros. De la misma forma, la arquitectura cuenta con soporte para la conexión de usuarios con asesores humanos, quienes pueden comunicarse con los usuarios a través del chatbot mediante Whatsapp o Telegram, así como retomar un usuario inactivo.</p>