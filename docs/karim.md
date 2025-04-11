# BPEL


## Definición de BPEL
</br>

### ¿Qué es BPEL y cuál es su propósito en la orquestación de servicios web?

BPEL también conocido como Business Process Execution Language es un lenguaje que esta definido en XML y esta diseñado para orquestar procesos de manera automática.

Cuando decimos "Orquestar" nos referimos a que BPEL actua como el director de una orquesta de servicios web. Basicamente coordina cómo y cuando deben ejecutarse varios servicios que forman parte de un proceso de negocio.

### ¿Cómo se relaciona con la arquitectura orientada a servicios (SOA)?

Primero que nada repasamos que es la arquitectura orientada a servicios SOA. La arquitectura SOA es un metodo de desarrollo de software que utiliza componentes de software llamados servicios. Estos servicios se usan para hacer aplicaciones o software completos. Es decir, un programa esta compuesto por mas de un servicio. Recordemos que entre servicios se tiene una comunicacion mediante diferentes plataformas y lenguajes. 

BPEL se relaciona directamente con SOA porque actua como una herramienta para implementar la logica de negocio que coordina varios servicios web dentro de esa arquitectura. Es decir, BPEL controla como interactuan varios servicios web.

BPEL proporciona una forma sencilla y directa de componer varios servicios web en nuevos servicios compuestos denominados procesos de negocio.

<hr/>
<br></br>
<br></br>
<hr/>

## Evolución Histórica
</br>

### Antecedentes de BPEL

BPEL  representa la convergencia de dos lenguajes XML pioneros, el lenguaje WSFL y XLANG. Cada uno con su propio enfoque, y BPEL combina esos enfoques. BPEL fue desarrollado en 2001 por IBM y Microsoft.

### Evolución de BPEL

En el transcurso del tiempo, otros equipos han contribuido al proyecto Business Process Execution Language. Por ejemplo, en 2007 OASIS publico la WS-BPEL 2.0, esto introdujo mejoras como el manejo mas avanzado de errores, mejor soporte para actividades concurrentes entre otras ventajas. En aquel entonces, se consolido como el lenguaje estándar de orquestación en entornos SOA.

<hr/>
<br></br>
<br></br>
<hr/>

## Impacto Inicial
</br>

### Auge de BPEL en la década de 2000

Desde el 2002, la mayoria de los proveedores se han unido, lo que ha dado lugar a diversas modificaciones y mejoras, y a la adopcion de la version 1.1 en marzo del 2003. BPEL se puede utilizar dentro de empresas y entre empresas. Por ejemplo, dentro de una misma empresa, la funcion de BPEL seria estandarizar la integracion de aplicaciones y extenderlas a sistemas previamente aislados. Mientras que entre empresas, BPEL facilitará y hara más efectiva la integracion.

BPEL tuvo un gran impacto en la primer decada del siglo XXI. En aquel entonces se requeria un lenguaje sencillo que diera una descripcion de como deben integrarse los procesos de negocio. Bueno, BPEL convirtio eso en realidad, ademas de que no solo se encarga de definir como deben integrarse los procesos, sino que tambien es ejecutable. BPEL fue el rpimer lenguaje en definir procesos abstractos y ejecutables.

### Principales plataformas que lo implementaron

Algunas de las plataformas empresariales que implementaron BPEL fueron:

1- Oracle SOA Suite
Una de las implementaciones mas completas. OSS usa Oracle BPEL Process Manager para odelar y ejecutar procesos BPEL.

2- IBM WebSphere Process Server
Parte del ecosistema de IBM para integración y SOA, soporta BPEL y otras tecnologías como BPMN.

3- SAP NetWeaver Process Orchestration
Esta plataforma al igual que las anteriores, incluye soporte para orquestación de procesos BPEL.

### Principales herramientas que lo implementaron.

Por otro lado, de entre las principales herramientas que implementaron BPEL, tenemos las siguientes:

1- Apache ODE
Es uno de los motores BPEL open source más conocidos y soporta BPEL 2.0

2- ActiveBPEL
Es un proyecto que se utiliza en entornos academicos, sin embargo, lo que nos interesa es que soporta BPEL 1.1. Sin embargo, actualmente ya no se mantiene activa.

3- NetBeans
En algunas versiones antiguas, había soporte parcial con plugins para BPEL.

4- Oracle JDeveloper
Este IDE tiene implemento herramientas visuales para diseñar, desplegar y monitorear procesos BPEL.

<hr/>
<br></br>
<br></br>
<hr/>

## Características Principales de BPEL
</br>

### Uso de la Orquestación

Una de las características principales las encontramos en su definición. Un lenguaje hecho para <b>orquestar</b> procesos de manera automática. Los servicios web se pueden componener de dos maneras: orquestación y coreografía. Primero hablemos de la orquestacion.

En la orquestación, un proceso central toma el control de los servicios web involucrados y coordina la ejecucion de las diferentes operaciones en ellos. En la orquestación, los servicios web involucrados desconocen que participan en una composicion y que forman parte de un proceso superior. En lo personal, a mi me gusta mas la orquestación, porque permite mas flexibilidad, por ejemplo, piensa en una botella que sirve solo para beber soda, pero no sirve para beber nada mas, posteriormente tienes ganas de beber cafe, asi que compras un envase que solo permite contener cafe, pero luego quieres tomar jugo, en vez de tener que comprar un vaso para cada bebida, compra un solo vaso que sirve para almacenar cualquier clase de liquido, independientemente de su temperatura, su espesor o su contenido. Sucede lo mismo con los servicios web. Cuando tu creas un servicio web para "Inicio de sesión de usuarios", "Creacion de cuentas" y "Autenticación de los mismos" es decir, un servicio de "LogIn", lo haces para que cualquier aplicacion lo pueda aplicar de manera sencilla, para que otras empresas tambien puedan usar dicho servicio, todo esto esta relacionado con lo que aprendimos en la unidad 1 de la materia. La orquestación permite crear servicios sin tener que preocuparte si dicho servicio es compatible o no con otros servicios, es decir, si podra pertenecer a un todo. En la orquestación los servicios no necesitan saber siquiera sí pertenecen a un composición y que forman parte de un proceso de negocio superior.

Ahora hablemos de la coreografía. La coreografía no depende de un coordinador central. Cada servicio web involucrado sabe exactamente cuando ejecutar sus operaciones y con quien interactuar. La coreografía es un esfuerzo colaborativo centrado en el intercambio de mensajes. A diferencia de la orquestación, aquí todos los participantes deben conocer el proceso de negocio.

Otras de las caracteristicas principales de BPEL es que los procesos son la unidad principal en BPEL. Un proceso define como se orquestan varios servicios web para cumplir un objetivo de negocio.

### Actividades

Las actividades son los bloques de construcción de un proceso. Se dividen en:

Actividades basicas:

-receive: recibe un mensaje de un socio externo
-reply: envía una respuesta
-invoke: llama a un servicio web externo
-assign: asigna o copia valores entre variables
-wait: pause el proceso por un tiempo
-thorwL lanza una excepción.

Actividades estructuradas:

-sequence: ejecuta actividades en orden
-flow: permite ejecutar actividades en paralelo
-while: repite mientras se cumple una condición
-if/switch: flujo condicional
-pick: espera varios eventos posibles y reacciona al primero que ocurra.


### Variables

En un archivo BPEL hay una sección que es para definir las variables, son usadas para almacenar mensajes o datos temporales. Cada variable tiene un tipo.

<b>
&lt;variables&gt;
   </br>
  &nbsp;&nbsp;&nbsp;&nbsp;  &lt;variable name="orden" messageType="tns:OrdenMensaje"/&gt;
   </br>
&lt;/variables&gt;
</b>

### Socios

Representan los servicios web externos con los que el proceso interactúa. Cada socio tiene un rol: proveedor o solicitante.

<b>
&lt;partnerLinks&gt;
</br>
   &nbsp;&nbsp;&nbsp;&nbsp; &lt;partnerLink name="cliente" partnerLinkType="tns:clienteLT" myRole="procesador"/&gt;
</br>
&lt;/partnerLinks&gt;
</b>

### Definición de flujos de trabajo complejos

Precisamente se hace uso de lo que mencionamos anteriormente para la definicion de flujos de trabajo complejos. Por ejemplo:

-Secuencia de pasos: Puedes ordenar exactamente qué hacer, cuándo y con qué datos.

-Condiciones y ciclos: Podemos hacernos valer de los if, while y switch para hacer decisiones o repetir pasos en el proceso.

-Paralelismo: Gracias a actividades estructuradas como flow, uno puede ejecutar múltiples tareas al mismo tiempo.

-Manejo de errores y eventos: Uno puede capturar excepciones, esperar eventos o definir acciones compensatorias.

<hr/>
<br></br>
<br></br>
<hr/>


## Fortalezas y Debilidades
</br>

### Ventajas

Algunas de las ventajas de BPEL son las siguientes:

1- Orquestacion clara y centralizada: Permite definir un flujo completo de un proceso desde un solo punto, coordinando multiples servicios web.

2- Reutilización de servicios: Puedes utilizar servicios web existentes (incluso desarrollados por otras empresas) sin modificarlos.

3- Separación de lógica y servicios: La logica del proceso esta separa de los servicios individuales facilitando mantenimiento y cambios.

4- Soporte para lógica: Soporta condiciones, ciclos, paralelismo, manejo de errores y compensaciones.

### Desventajas

1- Complejidad del lenguaje: Aunque a principios del siglo XXI era a mejor opción, la realidad es que es dificil de aprender si lo comparamos con nuevas tecnologias.

2- Curva de aprendizaje alta: Para poder entender BPEL, se requiere conocimiento de WSDL, XML, SOAP y conceptos de SOA.

3- Bajo rendimiento en procesos pesados: En procesos muy grandes o con muchas invocaciones, el rendimiento puede verse afectado.

<hr/>
<br></br>
<br></br>
<hr/>

## Comparación con otros estandares
</br>

### BPMN

Es un modelado y la notacion de procesos de negocio, es una notacion grafica precisa para documentar procesos de negocio, sin embargo, BPMN se usa principalmente solo como un lenguaje de modelado. BPMN esta disenada para ayudar a las organizaciones a:

- Coordine las estrategias de externalizacion de procesos de negocio.
- Facilite el analisis y la mejora de las operaciones.
- Alcanzar acuerdos más rápidos sobre los procesos.

### WS-CDL

A diferencia de BPEL, es un lenguaje de descripcion "coreográfica" de servicios web, sin embargo, tiene en comun que tambien es un lenguaje basado en XML. 

WS-CDL describe colaboraciones entre pares de participantes definiendo, desde un punto de vista global, su comportamiento. Aqui se busca que el intercambio de mensajes ordenados den como resultado el logro de un objetivo común.

### XPDL

XPDL viene de sus siglas en ingles XML Process Definition Language. Es un formato estándar de intercambio usado para guardar diagramas BPMN en XML.

### Service Mesh

Tambien conocido como malla de servicios en nuestro idioma, es una capa de software que gestiona toda la comunicacion entre los servicios de las aplicaciones. Esta capa se compone de microservicios en contenedores. Una malla de servicios es independiente del código de los servicios. Lo que lo diferencia de BPEL es que la orquestación y control de tráfico se hace a nivel de red entre microservicios. Esto quiere decir que la gestion no se hace en código, sino en la infraestructura de la red. De igual forma al usar la orquestación, significa que los servicios son independientes uno de otros, es decir que no se necesita tener conocimiento de que pertenecen a un entorno mas grande.

<hr/>
<br></br>
<br></br>
<hr/>

## Declive relativo
</br>

### Perdida de BPEL

Precisamente el surgimiento de nuevas tecnologías como Service Mesh ha generado que la gente ya no quiera usar BPEL. Para empezar, recordemos que BPEL en realidad no es sencillo de aprender, y que no ofrece muchas ventajas con respecto a otros estandares. Razon por la que BPEL ha ido perdiendo terreno a lo largo del tiempo y esto tiene a seguir así. 

<hr/>
<br></br>
<br></br>
<hr/>

## Tecnologías de Reemplazo
</br>

### Plataformas de Low-Code

Las plataformas de low-code son entornos de desarrollo que permiten crear aplicaciones de software con poco cóidog o sin necesidad de escribir mucho código, gracias a una interfaz visual y herramientas de arrastrar y soltar. Algunas de las caracterisiticas principales son las siguientes:

- Interfaz visual: Permiten crear aplicaciones mediante interfaces graficas, tipo visual studio.

- Automatizacion: Integran flujos de trabajo automatizados, reglas de negocio y tareas repetitivas sin necesidad de escribir código complejo.

- Integración de servicios: Facilitan la integración con otras plataformas y servicios, como bases de datos.

<hr/>
<br></br>
<br></br>
<hr/>

## El papel de BPMN
</br>

Como mencionamos antes, BPMN es el estandar moderno para la modelación de procesos de negocio, y con motores de ejecución como Camunda y Zeebe, se ha convertido en la opcion mas popular para la orquestación de procesos.

De entre las ventajas encontramos las siguientes:
- Modelado grafico intuitivo.
- Ejecución de procesos.
- Configuración flexible.

El papel de BPMN en la orquestación de procesos de negocio es clave, ya que proporciona un lenguaje estándar y gráfico para modelar, representar y ejecutar procesos de negocio. Este estándar es ampliamente utilizado en organizaciones que buscan automatizar y optimizar sus procesos de negocio mediante la orquestación de servicios y la integración de diferentes sistemas.

<hr/>
<br></br>
<br></br>
<hr/>

## Casos de uso actuales
</br>

### Donde se sigue utilzando BPEL

1- Integracion de sistemas empresariales: BPEL sigue siendo una opcion valida para empresas que necesitan orquestar y coordinar multiples servicios web, especialmente cuando se trata de integrar sistemas complejos como ERP, CRM y otros sistemas empresariales legados.

2- Soluciones de software empresarila tradicional: Las empresas que han adoptado plataformas como Oracle SOA Suite o IBM WebSphere pueden seguir utilizando BPEL para la automatizacion de procesos de negocio en entornos complejos y multinivel.


### Cuando usar BPEL

1- Cuando se requiere orquestacion de servicios web basados en SOAP: BPEL esta disenado principalmente para coordinar y orquestar servicios web que siguen el protocolo SOAP. Esto que quiere decir? Bueno, si tu app o software esta basados en servicios tradicionales usando SOA, BPEL puede ser una buena opcion, incluso entre las mas recomendables.

2- En sistemas empresariales monolíticos o complejos: Cuando se tiene un sistema grande con un entorno monolítico o altamente estructurado, BPEL puede ser útil para orquestar procesos y servicios en un sistema complejo.

<hr/>
<br></br>
<br></br>
<hr/>

## Resumen del estado del arte
</br>

En resumen, BPEL es un lenguaje de orquestacion que surgio en 2001 por IBM y Microsoft, posteriormente formalizado por OASIS. Dicho lenguaje fue un hit en aquella decada, ya que los archivos BPEL tambien era ejecutables, permitio por muchos años la coordinacion de procesos de negocio mediante la definicio de flujos de trabajo.

Del 2003 al 2010 BPEL fue ampliamente adoptado en entornos SOA, especialmente en organizaciones que utilizaban servicios SOAP.

Del 2010 en adelante, la aparición de tecnologías más ágiles como BPMN 2.0, microservicios y plataformas de contenedores fue desplazando a BPEL como solución principal.

En la actualidad, BPEL se considera una tecnología madura pero que lamentablemente va en decilve, aunque aun se mantiene en sistemas legados y plataformas empresariales tradicionales, ademas de que no deja de ser en mi opinion una manera de orquestacion valido.

<hr/>
<br></br>
<br></br>
<hr/>

## Perspectivas Futuras
</br>

Tendencias futuras en Orquestación y automatización

1 Microservicios y arquitecturas desacopladas
    - Se consolida el enfoque descentralizado, donde los servicios se comunican entre si mediante eventos o APIs RESTful.
    - La orquestación se reemplaza por coreografias entre microservicios o se delega a un service mesh.

2 BPMN 2.0
    - Herramientas como Camunda, Flowable y Zeebe permiten una ejecucion directa de modelos BPMN, integrando orquestación y reglas de negocio.
    - Su enfoque visual e intuitivo lo hace ideal para entornos colaborativos entre técnicos y analistas de negocio.

3 Service Mesh y Kubernetes
    - Tecnologías como Istio, Linkerd o Consul automatizan el enrutamiento, balanceo, seguridad y observabilidad entre microservicios.
    - La orquestación se realiza más en la capa de red, y menos en flujos escritos por humanos.

4 Low-code/ No-code
    - Plataforma como Mendiz, OutSystems o Appian permiten automatizar procesos empresariales sin escribir código.
    - Democratizan la automatización, acercándola a usuarios de negocio.

5- Automatización Ineligente
    - La combinacion de inteligencia artificial, automatizacion robótica de procesos (RPA) y BPMN permite crear procesos adaptativos e inteligentes.
    - Procesos se ajustan dinámicamente segun el contexto o los datos recibidos.


<hr/>
<br></br>
<br></br>
<hr/>

## Referencias
</br>

<ul>
<li>Sevillano, F. (2009b, septiembre 22). Diferencias entre BPMN, BPML´s, BPML , WS BPEL y XPDL. https://redindustria.blogspot.com/2009/09/diferencias-entre-bpmn-bpmls-bpml-ws.html</li>
</br>
<li>Web Services Choreography Description Language Version 1.0. (s. f.). https://www.w3.org/TR/ws-cdl-10/</li>
</br>
<li>Ibm. (2025, 17 febrero). Modelado y notación de procesos de negocio. IBM. https://www.ibm.com/mx-es/think/topics/bpmn</li>
</br>
<li>Juric, M. (2005, 1 abril). BPEL and Java. TheServerSide.com. https://www.theserverside.com/news/1364554/BPEL-and-Java</li>
</br>
<li>Miller, A. (s. f.). What’s BPEL? Business process execution language explained. BMC Blogs. https://www.bmc.com/blogs/bpel-business-process-execution-language/</li>
</br>
<li>A Hands-on Introduction to BPEL. (s. f.). https://www.oracle.com/technical-resources/articles/matjaz-bpel.html</li>
</br>
<li>¿Qué es AOS? - Explicación sobre la arquitectura orientada a servicios - AWS. (s. f.). Amazon Web Services, Inc. https://aws.amazon.com/es/what-is/service-oriented-architecture/</li>
</br>
<li>Oblancarte. (2014, 15 julio). Que es BPEL - Oscar Blancarte - Software Architecture. Oscar Blancarte - Software Architecture. https://www.oscarblancarteblog.com/2014/07/15/que-es-bpel/</li>
</ul>