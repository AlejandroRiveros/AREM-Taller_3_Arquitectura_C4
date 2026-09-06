# 📄 Informe Técnico del Taller

## 🔖 Nombre del Taller

**Taller 3 - Arquitectura Actual del Sistema con el Modelo C4**

## 👥 Integrantes del equipo

- Juan Pablo Luna Zuleta
- Alejandro Riveros
- Martín Ortega

**Equipo:** Adictos al Azúcar  
**Cliente:** Jefatura de Cultura de Innovación y Servicio — Dirección de Desarrollo Estratégico, Universidad de La Sabana

---

## 🧠 Descripción general del trabajo

El objetivo del taller es representar la arquitectura actual (**AS-IS**) que soporta la gestión del directorio de extensiones telefónicas de la Universidad de La Sabana mediante las vistas C1 (Contexto) y C2 (Contenedores) del modelo C4.

El proceso actual no está soportado por una aplicación desarrollada específicamente para este propósito. La operación se distribuye entre herramientas corporativas existentes: un directorio en Microsoft Excel, almacenamiento y compartición mediante OneDrive, coordinación manual mediante Microsoft Teams, información proveniente del Sistema de Desarrollo Humano y la Plataforma PBX institucional administrada por la Dirección de Tecnología.

El modelo se construyó a partir de la información ya levantada en la Ficha de Caracterización del Cliente, Architecture Vision, BPMN y Modelo de Información. Se mantuvo estrictamente el estado AS-IS; por esta razón, Power Automate y otras capacidades propuestas para el futuro no se modelan como elementos existentes.

---

## 🔧 Proceso de desarrollo

Se siguió la metodología de cuatro pasos indicada en la guía del Taller 3:

1. **Identificación de actores y límite del sistema:** se definieron los actores que interactúan directamente con el ecosistema actual y se estableció el sistema en alcance.
2. **Identificación de sistemas externos:** se mantuvieron fuera del límite el Sistema de Información de Desarrollo Humano y la Plataforma PBX institucional, en coherencia con el alcance definido en Architecture Vision.
3. **Descomposición en contenedores:** el C2 descompone el ecosistema actual en Microsoft Excel, Microsoft OneDrive y Microsoft Teams, cada uno con una responsabilidad diferenciada.
4. **Trazado y etiquetado de relaciones:** las relaciones se etiquetaron con la acción, información o mecanismo de interacción real, evitando inventar APIs, bases de datos o integraciones que no existen.

La herramienta utilizada fue **draw.io / diagrams.net** y se respetó la convención visual indicada por la guía del taller: actores en óvalo azul, sistema en alcance en azul oscuro, sistemas externos en gris con doble borde y contenedores en azul claro.

---

## 🧩 Análisis del modelo propuesto

### Vista C1 — Contexto

El sistema en alcance se denomina **“Ecosistema actual de gestión del directorio de extensiones”** porque actualmente no existe una aplicación única. El nombre permite representar de forma fiel el conjunto de herramientas que soportan el proceso sin presentar una solución futura como si ya estuviera implementada.

Los actores directos son:

- **Gestoras de servicio (×4):** consultan el directorio para identificar la extensión correcta y transferir llamadas.
- **Profesional de Experiencia y Servicio:** realiza la conciliación con la nómina, actualiza el directorio y coordina novedades.
- **Analista de Aprovisionamiento de Tecnología:** participa en la atención de solicitudes de aprovisionamiento, cambio o liberación de extensiones.

Los sistemas externos son:

- **Sistema de Información de Desarrollo Humano:** origina la nómina mensual que se usa como insumo para detectar novedades.
- **Plataforma PBX institucional:** contiene y gestiona técnicamente las extensiones telefónicas; su operación está fuera del alcance del proceso analizado.

No se incluyó al usuario que realiza una llamada como actor del C4 porque no interactúa directamente con el ecosistema tecnológico modelado; su interacción ocurre con la gestora y la plataforma de telefonía.

### Vista C2 — Contenedores

El C2 descompone el sistema en tres contenedores actuales:

| Contenedor | Tecnología / tipo | Responsabilidad |
|---|---|---|
| Directorio de Extensiones | Microsoft Excel / hoja de cálculo | Mantener los registros de colaborador, cargo, unidad, extensión y estado. |
| Repositorio del Directorio | Microsoft OneDrive / almacenamiento | Alojar el archivo y compartirlo con las gestoras en modo solo lectura. |
| Canal de Coordinación | Microsoft Teams / colaboración | Soportar reuniones y coordinación manual con la Dirección de Tecnología. |

La nómina llega como un archivo exportado desde Desarrollo Humano y se compara manualmente contra el directorio. Cuando existe una novedad que requiere aprovisionamiento, la Profesional coordina con Tecnología por Teams. El Analista de Aprovisionamiento ejecuta posteriormente el cambio en la PBX.

### Supuestos tomados

- No se conoce ni se infiere la arquitectura interna del Sistema de Desarrollo Humano o de la PBX.
- No se modelan servidores, APIs, bases de datos ni protocolos internos no confirmados por el cliente.
- El archivo de Excel y su repositorio se representan por separado porque cumplen responsabilidades diferentes: gestión del dato y almacenamiento/compartición.
- Teams se incluye dentro del ecosistema actual porque es una herramienta corporativa utilizada directamente como parte del flujo operativo de coordinación.
- La ausencia de sincronización automática PBX → directorio se documenta como una debilidad, no como una relación técnica inexistente.

---

## 🔁 Flujos principales identificados

1. Desarrollo Humano publica/exporta la nómina del mes vencido.
2. La Profesional de Experiencia y Servicio obtiene el archivo y lo contrasta manualmente con el directorio.
3. La Profesional actualiza los registros del directorio en Excel.
4. El archivo se almacena en OneDrive y se comparte con las gestoras.
5. Las gestoras consultan el directorio para direccionar llamadas.
6. Si una novedad requiere aprovisionamiento o liberación, la Profesional coordina con Tecnología mediante Teams.
7. Tecnología realiza el cambio en la PBX.
8. Actualmente no existe un mecanismo automático que confirme el resultado en el directorio.

---

## ⚠️ Debilidades actuales

| ID | Debilidad | Impacto arquitectónico |
|---|---|---|
| D1 | Conciliación manual entre nómina y directorio | Alto esfuerzo operativo y riesgo de error humano. |
| D2 | Directorio mantenido como archivo Excel | Dependencia de un artefacto no diseñado como fuente institucional estructurada. |
| D3 | Directorio alojado en OneDrive personal | Dependencia de una cuenta individual y gobierno limitado del dato. |
| D4 | Solicitudes de aprovisionamiento coordinadas manualmente por Teams/reuniones | Baja trazabilidad y tiempos de espera. |
| D5 | No existe confirmación automática desde Tecnología hacia el directorio | Registros pueden permanecer indefinidamente en “pendiente por aprovisionar”. |
| D6 | No existe sincronización entre PBX y directorio | El estado técnico real puede diferir del dato consultado por las gestoras. |
| D7 | La nómina se entrega mes vencido | Existe un desfase estructural que puede alcanzar aproximadamente 45 días. |

---

## 📈 Diagramas finales entregados

- [`c1-contexto-final.drawio`](./c1-contexto-final.drawio)
- [`c2-contenedores-final.drawio`](./c2-contenedores-final.drawio)

---

## 📋 Tabla de actores, sistemas y componentes

| Nombre del elemento | Tipo | Descripción | Responsable |
|---|---|---|---|
| Gestoras de servicio | Actor | Consultan información para transferir llamadas | Jefatura de Cultura de Innovación y Servicio |
| Profesional de Experiencia y Servicio | Actor | Concilia nómina, actualiza directorio y gestiona novedades | Jefatura de Cultura de Innovación y Servicio |
| Analista de Aprovisionamiento | Actor | Gestiona aprovisionamiento y liberación de extensiones | Dirección de Tecnología |
| Directorio de Extensiones | Contenedor | Hoja de cálculo con información operativa de extensiones | Jefatura de Cultura de Innovación y Servicio |
| Repositorio del Directorio | Contenedor | Almacenamiento y compartición del archivo | Microsoft 365 / unidad responsable |
| Canal de Coordinación | Contenedor | Coordinación manual entre la unidad y Tecnología | Microsoft Teams / Universidad |
| Sistema de Desarrollo Humano | Sistema externo | Fuente de la nómina mensual | Desarrollo Humano |
| Plataforma PBX | Sistema externo | Gestión técnica de extensiones telefónicas | Dirección de Tecnología |

---

## 🔄 Diferencias con el caso base RedExpress

RedExpress presenta una arquitectura de software distribuida con aplicaciones, servicios backend, balanceador de carga, base de datos e integraciones mediante protocolos técnicos explícitos. El caso de la Universidad es más simple desde el punto de vista tecnológico y más dependiente de herramientas ofimáticas y pasos manuales.

Por ello, no es correcto copiar la estructura de RedExpress ni inventar microservicios, APIs o infraestructura. La adaptación al cliente consiste precisamente en mostrar que el proceso actual depende de Excel, OneDrive y Teams, y que varias transiciones importantes se realizan de forma humana y no mediante integración sistema-a-sistema.

---

## 🧭 Vista ArchiMate equivalente

La guía transversal del curso establece que el Taller 3 corresponde principalmente a la **capa de Aplicación** de ArchiMate. En esa equivalencia, los contenedores del C2 se pueden interpretar como **Application Components**, mientras que los datos gestionados por ellos pueden representarse como **Data Objects**.

Para este caso, la equivalencia de alto nivel es:

| C4 | Equivalente ArchiMate |
|---|---|
| Directorio de Extensiones (Excel) | Application Component |
| Repositorio del Directorio (OneDrive) | Application Component / servicio de aplicación según el viewpoint |
| Canal de Coordinación (Teams) | Application Component |
| Datos del directorio | Data Object |
| Flujo de información entre aplicaciones | Flow |
| Acceso de Excel al dato del directorio | Access |
| Dependencia funcional entre aplicaciones | Serving, cuando aplique |

Esta equivalencia no reemplaza los diagramas C4. C4 responde principalmente cómo está estructurado el ecosistema y cómo se comunican sus partes; ArchiMate permite posteriormente conectar la capa de aplicación con negocio y tecnología mediante relaciones semánticas.

---

## 🔍 Investigación complementaria

### Tema investigado: uso del modelo C4 para documentar arquitecturas de software en contextos académicos y universitarios

El modelo C4 organiza la documentación de arquitectura mediante niveles jerárquicos: Context, Containers, Components y Code. Para este taller se utilizan los dos primeros niveles porque permiten establecer claramente el límite del sistema, las personas y sistemas externos, y posteriormente realizar un “zoom” sobre las unidades ejecutables o almacenes principales. El sitio oficial de C4 destaca además la importancia de que las relaciones estén etiquetadas y de no mezclar niveles de abstracción.

En el contexto universitario existe evidencia académica del uso del modelo C4 para apoyar la comprensión de arquitectura de software y complementar UML. Investigadores de la Universidad de Salamanca han utilizado C4 en docencia de Ingeniería de Software y muestran que los niveles C1 y C2 son especialmente útiles al inicio del diseño porque permiten razonar sobre el sistema antes de entrar en detalles técnicos. También existen investigaciones recientes que emplean esquemas tipo C4 para representar ecosistemas tecnológicos universitarios, separando actores, plataformas, repositorios y sistemas de gestión académica.

Este enfoque resulta pertinente para el cliente estudiado porque permite describir de manera honesta una arquitectura actual sencilla, sin obligar a que el sistema tenga microservicios, APIs o infraestructura propia. El valor del modelo está en hacer explícitos los límites, dependencias y responsabilidades reales.

---

## 📚 Referencias

Las fuentes completas se encuentran en [`referencias.md`](./referencias.md).

---

Este documento hace parte de la entrega del Taller 3 del curso AREM (Arquitectura Empresarial) - Universidad de La Sabana.
