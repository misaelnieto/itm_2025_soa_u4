# 1. Introducción
## ¿Qué es BPEL?
Este es un lenguaje estándar del sector de IT que sirve para implementar un servicio que requiere de diferentes componentes que requieren ser orquestados. Se relaciona con las especificaciones WSDL y el esquema XML.

Este modelo de proceso está influenciado por el modelo de servicios WSDL. La definición de un **proceso de negocio** WS-BPEL sigue el modelo de separación de WSDL entre:

- Contenido abstracto de los mensajes utilizados por el proceso de negocio.
- Información de despliegue (mensajes y tipo de puerto vs. enlace e información de dirección).

```mermaid
---
title: Ejemplo de BPEL
---
flowchart TB
	recepcion(Recepción)
	paso1(Paso 1)
	paso2(Paso 3)
	paso3(Paso 3)
	paso4(Paso 4)
	paso5(Paso 5)
	paso6(Paso 6)
	paso7(Paso 7)
	paso8(Paso 8)
	respuesta(Respuesta)

	recepcion --> paso1
	paso1 --> paso2
	paso1 --> paso4
	paso2 --> paso3
	paso4 --> paso5
	paso3 --> paso6
	paso5 --> paso6
	paso6 --> paso7
	paso6 --> paso8
	paso7 --> respuesta
	paso8 --> respuesta
``` 
## Historia
El Lenguaje de Ejecución de Procesos de Negocio para Servicios Web (BPEL4WS) se concibió inicialmente en julio de 2002 con la publicación de la especificación BPEL4WS 1.0, un esfuerzo conjunto de IBM, Microsoft y BEA, inspirado en variaciones previas como el Lenguaje de Flujo de Servicios Web (WSFL) de IBM y la especificación XLANG de Microsoft.

La versión 1.1, con contribuciones de SAP y Siebel, se publicó menos de un año después, en mayo de 2003. Posteriormente, la especificación se presentó a un comité técnico de OASIS para que pudiera convertirse en un estándar oficial y abierto.

El Comité Técnico WS-BPEL de OASIS estuvo activo desde abril de 2003 hasta mayo de 2007, copresidido por Diane Jordan de IBM y John Evdemon de Microsoft. En abril de 2007, WS-BPEL versión 2.0 fue aprobado como Estándar OASIS. Más de 37 organizaciones colaboraron en el desarrollo de WS-BPEL, incluyendo representantes de Active Endpoints, Adobe Systems, BEA Systems, Booz Allen Hamilton, EDS, HP, Hitachi, IBM, IONA, Microsoft, NEC, Nortel, Oracle, Red Hat, Rogue Wave, SAP, Sun Microsystems, TIBCO, webMethods y otros miembros de OASIS.

# 2. Análisis técnico de BPEL
A continuación se detallará más a fondo las características de este estándar.

## Características principales
BPEL tiene ciertas características que se tienen que tomar en cuenta para implementarlo.
### Actividades Estructuradas
Hay diferentes actividades estructuradas para definir el flujo de un proceso, tales como:

- Sequence: Para la ejecución secuencial de actividades.
- Flow: Para la ejecución paralela de actividades.
- If/Else: Para ejecución condicional de las actividades.
- While/RepeatUntil: Para ejecución iterativa.
- Switch: Para ejecución de múltiples ramas.

### Interacción entre servicios
También tiene mecanismos para la interacción entre servicios con actividades como `<invoke>`, `<receive>` y `<reply>` para manejar mensajes de entrada y salida.

### Manejo de datos
Para el manejo de datos se cuenta con `<assign>` para copiar datos entre variables además de soporte para Xpath para manipular XML.

### Manejo de excepciones
BPEL provee de mecanismos para excepciones muy robustos. Por ejemplo el bloque `<catch>` y `<catchall>` por si ocurren errores durante la ejecución, así como `<compensation>` para deshacer actividades completas en caso de errores posteriores.

### Comunicación asíncrona
Hay soporte para patrones de comunicación asíncrona para no bloquear el proceso y gestionar operaciones de larga duración.

## Fortalezas y debilidades
Las ventajas de BPEL son las siguientes:
- Estandarización: Este es un estándar hecho por un conglomerado de diferentes compañías lider en el área de servicios web como IBM y Microsoft por ejemplo.
- Manejo de estados: En el estándar está integrado el manejo del estado de procesos de negocio. Esto permite el uso de variables para almacenarlas a largo plazo.
- Integración de aplicaciones empresariales: Tiene una manera muy opinionada de gestionar los servicios, por lo que permite hacer aplicaciones mejor integradas bajo una empresa.
- Integración entre diferentes empresas: Permite una integración más sencilla y efectiva con socios comerciales, al definir de manera clara las interacciones entre sus sistemas.

Sus debilidades son:
- Curva de aprendizaje: Por su estructura tan rígida hay que aprender muchos conceptos y estructuras.
- Díficil de desarrollar inicialmente: Requiere de un gran trabajo para simplemente levantar los servicios correspondientes.
- Díficil de depurar: Por ser distribuido y asíncrono los procesos pueden dificultar la identificación y resolución de errores.

## Comparación con otros estándares
<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-cly1{text-align:left;vertical-align:middle}
.tg .tg-0lax{text-align:left;vertical-align:top}
</style>
<table class="tg"><thead>
  <tr>
    <th class="tg-0lax"></th>
    <th class="tg-cly1">BPEL</th>
    <th class="tg-cly1">BPMN</th>
    <th class="tg-cly1">Microsoft Azure Integration Services</th>
    <th class="tg-cly1">FBP</th>
  </tr></thead>
<tbody>
  <tr>
    <td class="tg-cly1">Enfoque</td>
    <td class="tg-cly1">Lenguaje ejecutable basado en XML, diseñado para definir y orquestar procesos de negocio mediante la interacción con servicios web.</td>
    <td class="tg-cly1">Notación gráfica para modelar procesos de negocio</td>
    <td class="tg-cly1">Es un conjunto de servicios en la nube que ofrece Microsoft Azure para integrar aplicaciones, datos y procesos. No es un único lenguaje, sino un conjunto de herramientas.</td>
    <td class="tg-cly1">Las aplicaciones se construyen conectando componentes que realizan tareas específicas, entre los cuales los datos fluyen como flujos de paquetes estructurados.</td>
  </tr>
  <tr>
    <td class="tg-cly1">Ejecutable</td>
    <td class="tg-0lax">Requiere un <br>motor de ejecución BPEL para interpretar y ejecutar los procesos definidos en XML.</td>
    <td class="tg-cly1">Si, pero no es su enfoque. Es más para modelar.</td>
    <td class="tg-cly1">Nativo de la nube y sin servidor .</td>
    <td class="tg-cly1">Generalmente asincróno y concurrente.</td>
  </tr>
  <tr>
    <td class="tg-cly1">Facilidad de uso</td>
    <td class="tg-cly1">Alta curva de aprendizaje</td>
    <td class="tg-0lax">Dificultad de aprendizaje moderada.</td>
    <td class="tg-cly1">Fácil de aprender. Requiere menos código.</td>
    <td class="tg-cly1">Fácil de aprender. Los flujos de trabajo son intuituvo</td>
  </tr>
</tbody></table>

# Estado actual y tendencias
WS-BPEL 2.0 sigue siendo la versión actual y estable del estándar. No se han realizado revisiones importantes a la especificación principal desde 2007.

## Declive del estándar
Debido a que no ha habido actualizaciones mayores al estándar desde 2007 que fue cuando se lanzó este estándar, los desarrolladores más nuevos no lo han usado.

Uno de los problemas que evita que se haga más popular es su complejidad. Tiene demasiados conceptos que se deben tener en cuenta para levantar un servicio simple. Sumado a que depende del estándar XML que se le conoce por su verbosidad, esto hace que el estándar solo sea usado por empresas que lo adoptaron cuando no había nada mejor. Su dependencia a los servicios SOAP no ayudó a su adopción.

Lo que hizo que BPEL sea prácticamente obsoleto hoy en día fue la aparición de las API REST. Estas permiten una mayor flexibilidad sin todo lo innecesario de SOAP. Son más ligeras, fáciles de consumir y más alineadas con la arquitectura de la Web. BPEL fue diseñado para SOAP específicamente por lo que es necesario agregar extensiones a éste para que pueda trabajar con REST.

El cambio gradual que hubo con los servicios de alojamiento en la nube y sus herramientas altamente integradas a estas plataformas asentaron más a BPEL como una tecnología anticuada. Algunos ejemplos son Microsoft Azure Integration Services y toda la suite de AWS que funcionan bien para orquestar variedad de servicios.

## Tecnologías de remplazo
Como se mencionó anteriomente, las plataformas de alojamiento en la nube ya cuentan con interfaces gráficas para gestionar servicios.

**Microsoft Azure Integration Services**

Azure Web Services es un servicio de Microsoft de alojamiento en la nube con herramientas integradas para el manejo de aplicaciones. Fue lanzado el 27 de Octubre de 2008. El dashboard de Azure Web Services es bastante completo y permite la orquestación de diferentes servicios en una sola interfaz.

![Dashboard de Azure Integration Services](https://k21academy.com/wp-content/uploads/2020/05/0RihIO-cmQl-wXfEw-1024x576.png)

**Amazon Cloud Formation**

Amazon Web Services se lanzó en 2006 aprovechando que esta empresa ya había formado su infraestructura para su tienda. Incluye una utilidad para modelar y organizar recursos de las aplicaciones.

![Dashboard de AWS Cloud Formation](https://d2908q01vomqb2.cloudfront.net/972a67c48192728a34979d9a35164c1295401b71/2019/06/06/5-parent-only.png)

## El papel de BPMN
El estándar BPMN es una notación gráfica estandarizada que permite el modelado de procesos de negocio, en un formato de flujo de trabajo y es actualmente mantenida por el _Object Management Group_ (OMG) desde el 2005.

Si bien en un momento BPEL surgió como un estándar para la orquestación de servicios web y la automatización de procesos, las mejores capacidades de BPMN han llevado a que sí esté ocupando un lugar central y disminuyendo la prominencia del lenguaje BPEL.

BPMN se concibió principalmente como una notación gráfica diseñada para facilitar la comunicación y la colaboración entre los analistas de negocios y los equipos técnicos durante la fase de diseño y análisis de los procesos. Su fortaleza radicaba en su capacidad para representar visualmente los flujos de trabajo de una manera intuitiva y comprensible para una audiencia diversa. Por otro lado, BPEL surgió como un lenguaje de implementación y ejecución, particularmente dentro de SOA, donde la orquestación de servicios web era un componente clave. Su naturaleza basada en XML lo hacía más adecuado para los desarrolladores y la infraestructura de TI.

Sin embargo, el panorama de la gestión de procesos comenzó a transformarse con la llegada de BPMN 2.0. Esta revisión crucial introdujo un formato XML ejecutable, un avance significativo que permitió que los modelos BPMN no solo sirvieran como diagramas de diseño, sino que también pudieran ser interpretados y ejecutados directamente por motores de BPMN.

Las limitaciones inherentes de BPEL también contribuyeron a este cambio de paradigma. Su complejidad sintáctica, al ser un lenguaje basado en XML, lo hacía menos accesible para los usuarios de negocio. Además no era un lenguaje visual, por lo que era difícil la comunicación entre desarrolladores y stakeholders.

En contraste, BPMN por su naturaleza gráfica permitía cerrar la brecha entre los ejecutivos y TI.

## Casos de uso actuales
Aunque BPEL es una herramienta depreciada, una de las áreas más importantes donde BPEL persiste es en el mantenimiento y la ampliación de los entornos SOA existentes. Para las grandes empresas que han desarrollado aplicaciones críticas en BPEL una migración completa a BPMN es percibida como abrumadora y económicamente no viable. Estas organizaciones suelen contar con una base de código sustancial de procesos BPEL que aún funcionan y aportan valor al negocio.

# Conclusiones y perspectivas futuras
BPEL es un estándar que, aunque fundamental en la consolidación de la orquestación de servicios web bajo la arquitectura SOA, se ha visto en declive su popularidad con el tiempo. Al principio fue un lenguaje ejecutable basado en XML y ofreció una manera estructurada de integrar servicios, impulsado por la adopción de estándares como WSDL y XML. Sin embargo, las propias características que definieron a BPEL, como su rigidez estructural, su dependencia al estándar XML que es muy verboso y su enfoque en SOAP se convirtieron en obstáculos para su longevidad.

## Estado del arte
WS-BPEL 2.0 sigue siendo la versión actual y estable del estándar. Desde el 2007, no se han realizado revisiones importantes de la especificación principal. Esto indica que el estándar es estable, pero se encuentra estancado.

Los desarrolladores más nuevos son menos propensos a usar BPEL debido a la falta de actualizaciones recientes, dependencia de SOAP y la aparición de alternativas más intuitivas y flexibles como REST.

## Perspectivas futuras
Ya que se establece que BPEL fue un estándar importante para la orquestación de servicios, ha sido reemplazado por tecnologías y enfoques más nuevos. Los motoresque a continuación se verán abordan directamente la necesidad de orquestación de procesos utilizando BPMN 2.0. Por ejemplo:

- jBPM: Una Suite de Gestión de Procesos de Negocio (BPMS) de código abierto en Java que ejecuta de forma nativa las definiciones de procesos BPMN.

![jBPM GUI](https://www.jbpm.org/landingPage/03_ProcessModeler_Big.png)

- Camunda: Una plataforma integral para la automatización de flujos de trabajo y decisiones, construida en torno a los estándares BPMN y DMN (Modelo y Notación de Decisiones).

![Camunda GUI](https://camunda.com/wp-content/uploads/camunda/blog-images/cockpit-dashboard.png)

- Flowable: Un motor BPMN 2.0 ligero y fácil de usar para desarrolladores, derivado de Activiti, con un fuerte enfoque en implementaciones nativas de la nube.

![Flowable GUI](https://images.g2crowd.com/uploads/attachment/file/1264589/FAB-26-Capterra-Screenshots-V1-3.png)

También las diferentes funciones de BPEL se han remplazado por cosas herramientas como Kong, Tyk y Apigee para orquestar llamadas a API.

Hoy en día los sistemas se basan cada vez más en arquitecturas basadas en eventos, donde los servicios reaccionan a los eventos en lugar de seguir una orquestación rígida definida en un lenguaje como BPEL. Esto promueve la disociación y la resiliencia.

# Referencias
- carolgeyer (2007) **History of BPEL** https://web.archive.org/web/20241006111330/https://bpel.xml.org/history _Archivado el 6 de Octubre 2024_.
- IBM (2024) **BPEL Process** https://web.archive.org/web/20240508013541/https://www.ibm.com/docs/es/bpm/8.6.0?topic=types-bpel-process _Archivado el 8 de Mayo 2024_
- Andrews, T., Curbera, F. (May 5, 2003) **Business Process Execution Language for Web Services.** https://web.archive.org/web/20221006100523/https://download.boulder.ibm.com/ibmdl/pub/software/dw/specs/ws-bpel/ws-bpel.pdf _Archivado el 6 de Octubre 2022_
- AWS (2025) **¿Qué es AWS CloudFormation?** https://web.archive.org/web/20250316144217/https://docs.aws.amazon.com/es_es/AWSCloudFormation/latest/UserGuide/Welcome.html _Archivado el 16 de Marzo 2025_
- White, Stephen. (Abril 22, 2004) **Process Modeling Notations and Workflow Patterns** https://web.archive.org/web/20090206175640/http://bpmn.org/Documents/Notations%20and%20Workflow%20Patterns.pdf _Archivado el 23 de Abril 2024_