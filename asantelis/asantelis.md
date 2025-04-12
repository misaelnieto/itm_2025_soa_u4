# Reporte BPEL (Business Process Execution Language)

## 1. Introducción y Contexto Histórico

### ¿Qué es BPEL?

Business Process Execution Language (BPEL), también conocido como WS-BPEL, es un lenguaje de programación basado en XML diseñado específicamente para definir procesos de negocio que se ejecutan sobre servicios web. Su propósito principal es la **orquestación**, es decir, la coordinación de múltiples servicios independientes para trabajar como un único flujo empresarial automatizado.

![BPEL](https://dzone.com/storage/rc-covers/15962-thumb.png)

**Características clave:**
- **Interoperabilidad**: Diseñado para trabajar con estándares WS-* (SOAP, WSDL, etc.)
- **Estado persistente**: Mantiene el estado del proceso durante ejecuciones largas
- **Transaccional**: Soporta compensaciones para manejo de errores complejos
- **Escalable**: Permite ejecución distribuida en entornos empresariales

### Origen y Evolución Histórica

BPEL surge de la necesidad de formalizar la interacción entre servicios web dentro de arquitecturas SOA (Service-Oriented Architecture). Fue desarrollado inicialmente por IBM y Microsoft a partir de sus lenguajes predecesores: **WSFL** (Web Services Flow Language) y **XLANG**, respectivamente.

**Detalles históricos:**
- **2001**: IBM publica WSFL como lenguaje para flujos de trabajo basados en servicios web
- **2001**: Microsoft desarrolla XLANG para orquestación en BizTalk Server
- **2002**: Ambas empresas fusionan sus enfoques creando BPEL4WS 1.0
- **2003**: Siebel Systems, BEA y SAP se unen al esfuerzo de estandarización
- **2004-2006**: OASIS trabaja en la versión 2.0 con mejoras significativas
- **2008**: Aparecen las primeras implementaciones open-source (Apache ODE)

**Principales contribuidores:**
- Frank Leymann (IBM)
- Dieter Roller (IBM)
- Satish Thatte (Microsoft)
- Steve Winkler (SAP)

### Rol dentro de la Arquitectura SOA

BPEL actúa como el "cerebro" dentro de una SOA, orquestando el orden, condiciones y lógica de negocio entre diversos servicios definidos mediante WSDL.

**Comparación con otros enfoques:**
- **Orquestación vs Coreografía**:
  - Orquestación (BPEL): Control centralizado, un proceso coordina a los participantes
  - Coreografía (WS-CDL): Control descentralizado, cada servicio conoce su rol

**Componentes SOA donde opera BPEL:**
1. **Service Bus (ESB)**: Conexión con servicios distribuidos
2. **Registry/Repository**: Descubrimiento de servicios
3. **Monitorización**: Seguimiento de instancias de procesos
4. **Security Gateway**: Manejo de políticas de seguridad

### Casos de Uso Iniciales

**Sectores con mayor adopción temprana:**

1. **Sector Financiero:**
   - Procesamiento de transacciones interbancarias
   - Automatización de aprobación de créditos
   - Conciliación de cuentas corporativas

2. **Telecomunicaciones:**
   - Provisión de servicios triple play (voz, datos, TV)
   - Gestión de portabilidad numérica
   - Activación/desactivación de servicios premium

3. **Manufactura:**
   - Coordinación de cadenas de suministro globales
   - Gestión de pedidos just-in-time
   - Integración con sistemas ERP y CRM

4. **Gobierno:**
   - Procesos de contratación pública
   - Tramitación electrónica de documentos
   - Sistemas de interoperabilidad entre organismos

---

## 2. Fundamentos Técnicos de BPEL

### Componentes Principales 

**1. Actividades básicas:**
- `invoke`: 
  - Soporte para patrones síncronos y asíncronos
  - Manejo de timeouts y reintentos configurables
- `receive`:
  - Puede ser bloqueante o no bloqueante
  - Soporta creación de nuevas instancias de proceso
- `assign`:
  - Transformación XPath/XSLT entre variables
  - Copia parcial o total de estructuras de datos
- `faultHandlers`:
  - Jerarquía de excepciones personalizables
  - Propagación de fallos entre scopes

**2. Nuevas estructuras avanzadas:**
- `eventHandlers`: Manejo de eventos asíncronos durante la ejecución
- `compensationHandler`: 
  - Lógica para deshacer transacciones completas
  - Invocación explícita mediante `compensate`
- `terminationHandler`: Manejo de cancelaciones abruptas

**3. Manejo de datos:**
- Tipos de variables complejas (XML Schema)
- Validación de mensajes contra esquemas XSD
- Conversión entre formatos (SOAP/JSON)

**4. Patrones de correlación:**
- Basados en campos de mensaje
- Usando identificadores de conversación
- Mediante tokens de contexto

### Modelo de Ejecución (Profundizado)

**Arquitectura típica de un motor BPEL:**
1. **Parser**: Transforma el XML BPEL a objetos ejecutables
2. **Scheduler**: Gestiona el plan de ejecución de actividades
3. **Persistence Layer**: Almacena el estado del proceso
4. **Message Broker**: Maneja la comunicación con servicios externos
5. **Recovery Manager**: Gestiona fallos y recuperaciones

**Características de ejecución:**
- **Long-running transactions**: Procesos que pueden durar días o meses
- **Checkpointing**: Puntos de guardado automático del estado
- **Versioning**: Soporte para múltiples versiones del mismo proceso

**Estados del ciclo de vida:**
1. Created
2. Ready
3. Active
4. Suspended
5. Completed
6. Terminated
7. Compensating
8. Faulted

---

## 3. Comparativa con BPMN y otras Tecnologías

### BPMN vs BPEL

| Aspecto               | BPMN 2.0                          | WS-BPEL                          |
|-----------------------|-----------------------------------|----------------------------------|
| Nivel de abstracción  | Alto (negocio)                    | Bajo (implementación)            |
| Soporte gráfico       | Completo (BPMN DI)                | Limitado (requiere herramientas) |
| Manejo de excepciones | Básico                            | Avanzado (compensaciones)        |
| Subprocesos           | Colapsables/reusables             | Inline/scopes                    |
| Tooling               | Herramientas visuales             | Editores XML/IDEs                |
| Rendimiento           | Depende de implementación         | Optimizado para ejecución        |
| Aprendizaje           | Más accesible                     | Curva pronunciada                |

### BPMN
![bpmn](https://media.licdn.com/dms/image/v2/C4D12AQEUGsxDLS5FtQ/article-cover_image-shrink_720_1280/article-cover_image-shrink_720_1280/0/1594159642155?e=2147483647&v=beta&t=Wr0uFvhg9mpL38iwOIS_lQBYQrB3H-SAFPCr9bcdnBw)

### Otras Alternativas Modernas

**1. Camunda BPM:**

![bpmn](https://camunda.com/wp-content/uploads/camunda/blog-images/trigger-bpmnerror-escalation-usertask.png)

- Ventajas:
  - Modelado visual con ejecución directa
  - Soporte para DMN (Decision Model)
  - Integración con Spring Boot
- Limitaciones:
  - Menor soporte para transacciones largas
  - Menos adecuado para integraciones SOAP

**2. Zeebe:**

![bpmn](https://unsupported.docs.camunda.io/8.1/assets/images/zeebe-architecture-67c608106ddc1c9eaa686a5a268887f9.png)

- Arquitectura basada en eventos
- Protocolo gRPC para alta performance
- Escalabilidad horizontal nativa

**3. Temporal:**
- Patrón "Workflow as Code"
- Soporte para múltiples lenguajes (Go, Java, Python)
- Historial completo de ejecución

**4. Apache Airflow:**
- Orientado a flujos de datos
- Programación en Python
- Gran ecosistema de operadores

**Cuadro comparativo de rendimiento:**
| Tecnología | TPS* | Latencia | Recursos | Complejidad |
|------------|------|----------|----------|-------------|
| BPEL       | 100-500 | Alta   | Altos    | Alta        |
| Camunda    | 500-2K | Media  | Medios   | Media       |
| Zeebe      | 10K+  | Baja    | Bajos    | Baja-Media  |
| Temporal   | 5K+   | Muy baja| Medios   | Media       |
*Transacciones por segundo en configuración estándar

---

## 4. Estado Actual de BPEL

### Causas del Declive

**Factores técnicos:**
1. **Complejidad XML**:
   - Difícil mantenimiento a escala
   - Problemas de versionamiento
   - Limitada expresividad para lógica compleja

2. **Rigidez arquitectónica**:
   - Acoplamiento fuerte a SOAP/WS-*
   - Pobre soporte para REST/JSON
   - Dificultad para integración con microservicios

**Factores de mercado:**
- Crecimiento de alternativas low-code
- Cambio hacia arquitecturas event-driven
- Mayor adopción de BPMN ejecutable

**Estadísticas de adopción (2024):**
- 15% de empresas Fortune 500 aún usan BPEL
- 72% reducción en nuevos proyectos desde 2015
- 3% crecimiento anual en mantenimiento de legacy

### Adopción Actual 

**Industrias con uso activo:**
1. **Banca:**
   - Procesos de clearing interbancario
   - Cumplimiento de regulaciones (Basel III)
   - Reportes automatizados a supervisores

2. **Seguros:**
   - Procesamiento de siniestros complejos
   - Subscripción de pólizas corporativas
   - Detección de fraudes

3. **Aerolíneas:**
   - Sistemas de reservas legacy
   - Coordinación entre GDS (Global Distribution Systems)
   - Facturación interaerolínea

**Motores BPEL aún soportados:**
- Oracle BPEL Process Manager
- IBM Integration Bus
- Apache ODE (versión community)
- Software AG webMethods

---

## 5. Futuro y Tendencias

### Hiperautomatización

**Evolución tecnológica:**
1. **BPEL 3.0 (Propuesta no estandarizada):**
   - Soporte para JSON/REST
   - Sintaxis simplificada
   - Integración con eventos

2. **Patrones híbridos:**
   - BPEL para core business processes
   - Microservicios para lógica específica
   - Event-driven para integraciones

3. **BPEL como servicio:**
   - Implementaciones cloud-native
   - Escalado elástico
   - Modelo pay-per-execution

### Convergencia con APIs y Arquitecturas Event-Driven

![bpmn](https://media.licdn.com/dms/image/v2/D4D12AQG8DHKu0HuKPw/article-cover_image-shrink_720_1280/article-cover_image-shrink_720_1280/0/1694658185382?e=2147483647&v=beta&t=ejLFMykhBWoyo2pIJVnU9Jza5VknjNWbFcS-aKA1q_A)

**Patrones emergentes:**
- **BPEL + API Gateway**:
  - Exposición de procesos como APIs REST
  - Transformación SOAP-REST en edge

- **Event Sourcing**:
  - Persistencia del estado como secuencia de eventos
  - Reconstrucción de estados históricos

- **Sagas Pattern**:
  - Transacciones distribuidas sin bloqueos
  - Compensaciones basadas en eventos

**Tecnologías complementarias:**
1. **Service Mesh**:
   - Istio/Linkerd para gestión de comunicaciones
   - Políticas de resiliencia aplicadas a invocaciones BPEL

2. **Serverless**:
   - Ejecución de actividades como funciones
   - Escalado automático de tareas intensivas

1. **Blockchain**:
   - Registro inmutable de ejecuciones
   - Smart contracts como servicios orquestados

---

# Ejemplo Completo de Proceso BPEL

```xml
<process name="LoanApprovalProcess" 
         xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"
         targetNamespace="http://example.com/loan-approval">
    
    <!-- Partner Links -->
    <partnerLinks>
        <partnerLink name="customer" 
                   partnerLinkType="lns:loanPartnerLinkType"
                   myRole="loanApprover"/>
        <partnerLink name="assessor"
                   partnerLinkType="lns:assessorLinkType"
                   partnerRole="assessorService"/>
        <partnerLink name="approver"
                   partnerLinkType="lns:approverLinkType"
                   partnerRole="approverService"/>
    </partnerLinks>

    <!-- Variables -->
    <variables>
        <variable name="loanApplication" 
                 messageType="lns:loanApplicationMessage"/>
        <variable name="riskAssessment"
                 messageType="lns:riskAssessmentMessage"/>
        <variable name="approvalDecision"
                 messageType="lns:approvalMessage"/>
    </variables>

    <!-- Main Process -->
    <sequence>
        <!-- Receive initial request -->
        <receive partnerLink="customer"
                operation="requestLoan"
                variable="loanApplication"
                createInstance="yes"/>
        
        <!-- Parallel assessment -->
        <flow>
            <!-- Get risk assessment -->
            <invoke partnerLink="assessor"
                   operation="checkRisk"
                   inputVariable="loanApplication"
                   outputVariable="riskAssessment"/>
            
            <!-- Get credit history -->
            <invoke partnerLink="assessor"
                   operation="checkCredit"
                   inputVariable="loanApplication"
                   outputVariable="creditHistory"/>
        </flow>

        <!-- Make decision -->
        <if>
            <condition>
                $riskAssessment/riskFactor < 0.3 
                and $creditHistory/score > 650
            </condition>
            <sequence>
                <assign>
                    <copy>
                        <from expression="'approved'"/>
                        <to variable="approvalDecision" part="status"/>
                    </copy>
                </assign>
                <invoke partnerLink="approver"
                       operation="approveLoan"
                       inputVariable="approvalDecision"/>
            </sequence>
            <else>
                <assign>
                    <copy>
                        <from expression="'rejected'"/>
                        <to variable="approvalDecision" part="status"/>
                    </copy>
                </assign>
            </else>
        </if>

        <!-- Send response -->
        <reply partnerLink="customer"
              operation="requestLoan"
              variable="approvalDecision"/>
    </sequence>

    <!-- Fault Handling -->
    <faultHandlers>
        <catch faultName="lns:assessmentFailed">
            <reply partnerLink="customer"
                  operation="requestLoan"
                  variable="faultResponse"/>
        </catch>
    </faultHandlers>
</process>
```

### C. Glosario de Términos BPEL

- **Activity**: Unidad básica de trabajo en un proceso BPEL (invoke, receive, etc.)
- **Assign**: Operación para copiar datos entre variables del proceso
- **Compensation Handler**: Mecanismo para revertir transacciones completadas
- **Correlation Set**: Conjunto de propiedades que identifican una instancia de proceso
- **Dead-Path Elimination (DPE)**: Eliminación de rutas no activas en flujos paralelos
- **Endpoint Reference (EPR)**: Dirección física de un servicio web asociado
- **Fault Handler**: Bloque que captura y maneja excepciones durante la ejecución
- **Link**: Conexión entre actividades dentro de un flujo paralelo
- **Partner Link**: Definición de la relación entre el proceso y un servicio externo
- **Process Instance**: Ejecución única de una definición de proceso BPEL
- **Scope**: Contenedor que agrupa actividades con manejadores comunes
- **Variable**: Contenedor de datos usado para almacenar mensajes y estados
- **WS-Coordination**: Protocolo para manejar transacciones distribuidas
- **WS-Transaction**: Estándar para transacciones atómicas en servicios web
- **XPath**: Lenguaje usado para acceder y manipular datos en variables BPEL

---

## Referencias


- Fu, X., Bultan, T., & Su, J. (2004, May). Analysis of interacting BPEL web services. In Proceedings of the 13th international conference on World Wide Web (pp. 621-630).
- Ouyang, C., Dumas, M., Ter Hofstede, A. H., & Van der Aalst, W. M. (2006, September). From BPMN process models to BPEL web services. In 2006 IEEE International Conference on Web Services (ICWS'06) (pp. 285-292). IEEE.
- Pautasso, C. (2009). RESTful Web service composition with BPEL for REST. Data & Knowledge Engineering, 68(9), 851-866.
- Louridas, P. (2008). Orchestrating web services with bpel. IEEE software, 25(2), 85-87.
- Nitzsche, J., Van Lessen, T., Karastoyanova, D., & Leymann, F. (2007). Bpel for semantic web services (bpel4sws). In On the Move to Meaningful Internet Systems 2007: OTM 2007 Workshops: OTM Confederated International Workshops and Posters, AWeSOMe, CAMS, OTM Academy Doctoral Consortium, MONET, OnToContent, ORM, PerSys, PPN, RDDS, SSWS, and SWWS 2007, Vilamoura, Portugal, November 25-30, 2007, Proceedings, Part I (pp. 179-188). Springer Berlin Heidelberg.
- Pautasso, C. (2008, September). Bpel for rest. In International Conference on Business Process Management (pp. 278-293). Berlin, Heidelberg: Springer Berlin Heidelberg.
- Bazán, P. (2007). BPEL: una propuesta para el uso de Web Services. In XIII Congreso Argentino de Ciencias de la Computación.
- IBM Business Process Manager. (s. f.-b). https://www.ibm.com/docs/es/bpm/8.6.0?topic=types-bpel-process