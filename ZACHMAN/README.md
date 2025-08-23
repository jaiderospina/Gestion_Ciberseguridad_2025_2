# FRAMEWORK DE ZACHMAN
## FRAMEWORK DE ZACHMAN
**Framework de Zachman**, también conocido como **Zachman Framework for Enterprise Architecture**, que es uno de los marcos de referencia más influyentes en **arquitectura empresarial**.

El **Framework de Zachman** es una **matriz de clasificación** que organiza la arquitectura empresarial a partir de **6 perspectivas (filas)** y **6 dimensiones (columnas)**, permitiendo alinear estrategia, negocio y tecnología de manera estructurada.


---

# ¿Qué es el Framework de Zachman?

El **Framework de Zachman**, creado por **John Zachman en 1987** en IBM, es un **modelo de clasificación** que organiza y estructura los distintos aspectos de una organización.
No es una metodología ni un proceso, sino una **matriz de referencia** que ayuda a entender, diseñar y gestionar la arquitectura empresarial.

Su objetivo principal es **alinear los diferentes puntos de vista de la empresa** (directivos, arquitectos, diseñadores, constructores, usuarios, etc.) con las **dimensiones críticas de un sistema empresarial**.

---

# Estructura del Framework de Zachman

El framework se representa como una **matriz de 6 columnas × 6 filas**:

## 🔹 Columnas: Interrogantes Fundamentales

Cada columna responde a una de las **6 preguntas básicas** de la comunicación (basadas en periodismo clásico y lógica aristotélica):

1. **¿Qué? (Datos / Inventario)**
   Representa las cosas importantes para la empresa (entidades, objetos, información).

2. **¿Cómo? (Función / Procesos)**
   Describe las funciones y procesos que transforman los datos.

3. **¿Dónde? (Red / Localización)**
   Indica la distribución geográfica, redes, ubicaciones físicas o virtuales.

4. **¿Quién? (Personas / Responsabilidad)**
   Roles, responsabilidades, unidades organizativas.

5. **¿Cuándo? (Tiempo / Eventos)**
   Aspectos temporales: cronogramas, secuencias, ciclos.

6. **¿Por qué? (Motivación / Estrategia)**
   La razón de ser: objetivos, estrategias, reglas de negocio.

---

## 🔹 Filas: Perspectivas de la Organización

Cada fila representa un **nivel de abstracción** o **punto de vista**:

1. **Alcance (Scope – Planner’s view)**
   Vista del **estratega** o planificador. Describe la visión general de la organización.

2. **Modelo de Negocio (Business Model – Owner’s view)**
   Vista del **propietario**. Define cómo debe funcionar la organización desde la lógica del negocio.

3. **Modelo del Sistema de Información (System Model – Designer’s view)**
   Vista del **arquitecto**. Traduce los requerimientos de negocio en modelos de sistemas.

4. **Modelo Tecnológico (Technology Model – Builder’s view)**
   Vista del **diseñador técnico**. Define las tecnologías específicas para implementar el sistema.

5. **Representaciones Detalladas (Detailed Representations – Subcontractor’s view)**
   Vista del **constructor**. Especificaciones detalladas de implementación.

6. **Funcionamiento Real (Functioning Enterprise – User’s view)**
   Vista de la **realidad operacional**. El sistema funcionando en producción.

---

# Representación Gráfica (simplificada)

| Perspectiva / Pregunta      | ¿Qué? (Datos)              | ¿Cómo? (Procesos)             | ¿Dónde? (Localización)           | ¿Quién? (Personas)              | ¿Cuándo? (Tiempo)     | ¿Por qué? (Motivación)   |
| --------------------------- | -------------------------- | ----------------------------- | -------------------------------- | ------------------------------- | --------------------- | ------------------------ |
| **Alcance** (Planner)       | Lista de cosas importantes | Lista de procesos críticos    | Mapa de ubicaciones              | Lista de unidades organizativas | Eventos clave         | Objetivos estratégicos   |
| **Negocio** (Owner)         | Modelo de información      | Modelo de procesos de negocio | Modelo de distribución logística | Organigrama                     | Calendario de negocio | Estrategia de negocio    |
| **Sistema** (Designer)      | Modelo lógico de datos     | Modelo de aplicaciones        | Arquitectura de red lógica       | Modelo de roles                 | Diagrama de estados   | Reglas de negocio        |
| **Tecnología** (Builder)    | Modelo físico de datos     | Especificaciones de programas | Arquitectura física              | Sistemas de seguridad           | Cronogramas técnicos  | Reglas de implementación |
| **Detalle** (Subcontractor) | Esquema de base de datos   | Código fuente                 | Configuración de red             | Scripts de acceso               | Planes de prueba      | Políticas configuradas   |
| **Funcionamiento** (User)   | Datos en operación         | Procesos ejecutados           | Localizaciones activas           | Usuarios y grupos               | Eventos reales        | Resultados alcanzados    |

---

# Beneficios del Framework de Zachman

* **Visión integral** de la organización desde múltiples perspectivas.
* **Alineación** entre estrategia, negocio, sistemas y tecnología.
* **Clasificación clara** de artefactos de arquitectura empresarial.
* **Soporte a la transformación digital**, asegurando coherencia y trazabilidad.
* **Estandarización**: evita duplicidad y vacíos en el modelado empresarial.

---

# Limitaciones

* No es una metodología → no explica *cómo* implementar la arquitectura.
* Puede ser **complejo y difícil de aplicar** en organizaciones pequeñas.
* Requiere un **alto nivel de madurez empresarial** para ser efectivo.

---


**Framework de Zachman** a una **empresa que está implementando un Sistema de Gestión de Seguridad de la Información (SGSI)** con base en la **ISO/IEC 27001:2022**.

**Matriz simplificada** para visualizar cómo cada columna y fila se articula con el contexto de la seguridad de la información.

---

# 📊 Ejemplo: SGSI con Zachman Framework (ISO/IEC 27001:2022)

| **Perspectiva / Pregunta**                 | **¿Qué? (Datos / Información)**                                                              | **¿Cómo? (Procesos / Funciones)**                                                | **¿Dónde? (Localización / Red)**                                  | **¿Quién? (Personas / Roles)**                                 | **¿Cuándo? (Tiempo / Eventos)**                             | **¿Por qué? (Motivación / Estrategia)**                                |
| ------------------------------------------ | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | ----------------------------------------------------------------- | -------------------------------------------------------------- | ----------------------------------------------------------- | ---------------------------------------------------------------------- |
| **Alcance** (Planner – Alta Dirección)     | Activos de información críticos (bases de datos, documentos legales, registros de clientes). | Procesos clave de negocio a proteger (finanzas, I+D, clientes).                  | Sedes, datacenter, nube, oficinas remotas.                        | Alta dirección, comité de seguridad.                           | Ciclo anual de auditorías ISO, reportes trimestrales.       | Cumplir ISO 27001, proteger reputación y cumplir regulaciones.         |
| **Negocio** (Owner – Dueños de procesos)   | Clasificación de información (pública, interna, confidencial).                               | Procedimientos de gestión de riesgos, respuesta a incidentes, control de acceso. | Redes corporativas, entornos cloud (AWS, Azure), VPN.             | Responsables de procesos, dueños de activos, usuarios finales. | Gestión de incidentes en tiempo real, revisiones mensuales. | Continuidad de negocio, confianza de clientes, cumplimiento normativo. |
| **Sistema** (Designer – Arquitecto TI)     | Modelo lógico de seguridad de datos (encriptación, control de accesos).                      | Diseño de flujos de seguridad (detección de intrusos, backups, gestión de logs). | Arquitectura de red lógica: DMZ, firewalls, SIEM.                 | Roles: CISO, analistas SOC, administradores TI.                | Diagrama de estados: detección → contención → recuperación. | Reglas de negocio en SGSI, políticas de acceso mínimo.                 |
| **Tecnología** (Builder – Ingeniero)       | Esquema físico: bases de datos cifradas, certificados digitales, claves.                     | Configuración de firewalls, SIEM, EDR, DLP.                                      | Topología de red física: servidores, switches, IDS/IPS.           | Técnicos de seguridad, proveedores de servicios cloud.         | Cronograma de despliegues de parches y actualizaciones.     | Implementación de controles ISO 27001 (Anexo A).                       |
| **Detalle** (Subcontractor – Proveedor)    | Scripts de cifrado, configuraciones de GPO, reglas de firewall.                              | Código fuente de automatización (ej. scripts de backup).                         | Configuración detallada de routers, firewalls, balanceadores.     | Soporte externo, contratistas de ciberseguridad.               | Plan de pruebas, ejecución de simulacros de ciberataques.   | Cumplir SLA y controles contractuales de seguridad.                    |
| **Funcionamiento** (User – Operación real) | Datos protegidos y monitoreados (logs, auditorías).                                          | Procesos en ejecución: detección de incidentes, respuesta.                       | Usuarios trabajando desde oficinas y teletrabajo de forma segura. | Empleados usando MFA, equipo SOC atendiendo alertas.           | Eventos reales: incidentes, auditorías, revisiones ISO.     | Mejora continua, reducción de riesgos y resiliencia.                   |

---

# ✅ Interpretación del Ejemplo

* **Columna "Qué" (Datos):** define qué información y activos se protegen.
* **Columna "Cómo" (Procesos):** describe cómo se gestionan riesgos, incidentes y controles.
* **Columna "Dónde" (Localización):** detalla la infraestructura donde está la información (cloud, oficinas, redes).
* **Columna "Quién" (Personas):** muestra los responsables de la seguridad (CISO, comité, técnicos, usuarios).
* **Columna "Cuándo" (Tiempo):** define periodicidad (auditorías, incidentes, mantenimiento).
* **Columna "Por qué" (Motivación):** refleja objetivos estratégicos (cumplimiento ISO, resiliencia, reputación).

---

El **Framework de Zachman** permite alinear **ISO 27001:2022** con todas las dimensiones de la organización, asegurando que la **estrategia, los procesos y la tecnología** estén en coherencia con los objetivos de seguridad.

---


