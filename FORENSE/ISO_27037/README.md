En la imagen adjunta se evidencia que el problema de visualización en el archivo `README.md` se origina por dos factores de sintaxis Markdown:

1. Las líneas que fallan inician con una doble barra vertical (`||`) en vez de una sola (`|`).
2. Entre la primera fila y las siguientes se introdujo un salto de línea en blanco o un carácter invisible no imprimible (como `\u00a0`), lo cual rompe el bloque de la tabla en los motores de renderizado estándar (como GitHub, GitLab o editores Markdown).

A continuación se presenta la versión corregida y estructurada del documento, con los entregables claramente especificados (incluyendo el archivo PowerPoint de sustentación y su estructura requerida) y todas las tablas formateadas en Markdown estricto y limpio.

---

# Taller Práctico Avanzado: Intervención Forense en Escenario de Crisis y Cadena de Custodia bajo ISO/IEC 27037

### 1. Ficha Técnica y Entregables Formales

* **Asignatura:** Informática Forense.
* **Programa:** Maestría en Ciberseguridad y Ciberdefensa.
* **Metodología:** Aprendizaje Basado en Problemas (ABP), simulación en infraestructura crítica y juicio oral de admisibilidad.
* **Modalidad de trabajo:** Tres (3) equipos multidisciplinarios (3 a 5 estudiantes por equipo).
* **Duración total:** 150 minutos.

#### Entregables Formales Obligatorios por Equipo:

Cada equipo debe cargar en la plataforma académica y disponer para la sesión los siguientes tres (3) productos:

1. **Documento Técnico Pericial (PDF / Informe Escrito):**
* Respuestas analíticas a las preguntas clave del caso asignado.
* **Formato 1 diligenciado:** Bitácora de Triaje y Justificación Técnica de la Intervención.
* **Formato 2 diligenciado:** Registro de Cadena de Custodia y Trazabilidad (Anexo B, ISO 27037).


2. **Presentación de Sustentación (PowerPoint - PPTX):**
* Diapositivas diseñadas para la defensa pericial de **10 minutos**.
* Estructura requerida en la presentación:
* *Diapositiva 1:* Carátula institucional, integrantes, roles asignados y referencia del caso.
* *Diapositiva 2:* Resumen ejecutivo de la escena intervenida y delimitación del mandato legal.
* *Diapositivas 3-4:* Diagrama de flujo de toma de decisiones (justificación bajo Figuras 1 a 5 de ISO 27037).
* *Diapositiva 5:* Procedimiento de preservación, contención de riesgos y orden de volatilidad aplicado.
* *Diapositiva 6:* Cuadro consolidado de evidencias, empaque técnico y funciones de integridad (hash).
* *Diapositiva 7:* Matriz de defensa contra riesgos de *spoliation* (alteración) o sesgo inherente (*bias*).




3. **Defensa Pericial Oral y Evaluación Cruzada (En Clase):**
* Exposición pericial del grupo empleando el material de PowerPoint (10 min).
* Sustentación oral ante contra-interrogatorio de los equipos pares y el tribunal docente (10 min), evaluada mediante el **Formato 3**.



---

### 2. Marco Normativo Obligatorio

Las decisiones y justificaciones del equipo deben sustentarse en:

1. **Los 4 pilares de la evidencia digital:** Auditabilidad (5.3.2), Repetibilidad (5.3.3), Reproducibilidad (5.3.4) y Justificabilidad (5.3.5).
2. **Las 4 fases del ciclo de vida:** Identificación (5.4.2), Recolección (5.4.3), Adquisición (5.4.4) y Preservación (5.4.5).
3. **Roles normativos:** *Digital Evidence First Responder* (DEFR) y *Digital Evidence Specialist* (DES).
4. **Orden de volatilidad:** Manejo de RAM, conexiones y volúmenes cifrados previo a la desconexión (RFC 3227 y numeral 6.8).
5. **Mitigación del sesgo (*Inherent Bias*):** Neutralidad en la recolección frente a manifestaciones de terceros (numeral 6.7.5).

---

### 3. Asignación de Roles por Equipo

* **DEFR Líder de Escena:** Perímetro, riesgos físicos/lógicos y apertura de actas.
* **DES (Especialista en Evidencia Digital):** Definición técnica de adquisición en vivo o colección física, orden de volatilidad y validación de software forense.
* **Oficial de Cadena de Custodia:** Diligenciamiento de actas, empaque técnico y cálculo de hashes.
* **Auditor de Cumplimiento (Para equipos de 4 o 5; asumido por el DEFR en equipos de 3):** Control de trazabilidad y prevención de objeciones por *spoliation*.

---

### 4. Cronograma de la Sesión (150 Minutos)

| Bloque | Tiempo | Actividad Operativa |
| --- | --- | --- |
| **Parte I: Gabinete y Triaje Documental** | **90 min** | • **00–20 min:** Análisis de caso, verificación del mandato y selección de herramientas.<br>

<br>• **20–60 min:** Resolución de preguntas técnicas y diagramación del árbol de decisiones.<br>

<br>• **60–90 min:** Diligenciamiento formal de Formatos 1 y 2, y compilación del PowerPoint. |
| **Parte II: Sustentación y Juicio de Admisibilidad** | **60 min** | • **90–110 min:** Sustentación y contra-interrogatorio Grupo 1.<br>

<br>• **110–130 min:** Sustentación y contra-interrogatorio Grupo 2.<br>

<br>• **130–150 min:** Sustentación y contra-interrogatorio Grupo 3. |

---

### 5. Casos Detallados y Fichas de Inventario Simulado

---

#### GRUPO 1: Estación de Operaciones Crítica Encendida con Volúmenes Cifrados

*Alineación normativa: Numerales 5.3, 5.4, 6.2, 6.6, 6.8, 7.1.1, 7.1.2.1, 7.1.3.1; Figuras 1, 2 y 4.*

* **Referencia Operacional:** Caso OPE-DEF-2026-088.
* **Contexto:** Se comisiona al equipo DEFR/DES para intervenir la oficina del Director de Proyectos Especiales del Comando Conjunto de Ciberdefensa. Las alertas del SIEM indican tráfico anómalo masivo mediante túneles DNS hacia un servidor externo no identificado.
* **Escena al arribar (09:15 horas):**
* Estación encendida (*powered-on*).
* Pantalla desbloqueada mediante un emulador de ratón (*mouse jiggler*) conectado al puerto USB frontal.
* Se aprecian consolas PowerShell abiertas, explorador con unidad montada `V:\ (Volumen Seguro)` y mensajería cifrada activa.
* Interfaz de red cableada RJ-45 transmitiendo a alta velocidad.
* Post-it manuscrito sobre el teclado con posibles credenciales.



| ID Ítem | Descripción del Elemento | Estado Inicial | Particularidades Técnicas / Identificadores |
| --- | --- | --- | --- |
| **G1-E01** | Torre Workstation Dell Precision 5820 | Encendido (En ejecución) | S/N: 4HG78Y2; CPU Xeon, 64 GB RAM, 2x 1TB NVMe en RAID 0. Conexión Gigabit Ethernet activa. |
| **G1-E02** | Pantalla Dell UltraSharp 27" | Encendido | S/N: DL-99214; Muestra escritorio con volúmenes montados y consolas activas. |
| **G1-E03** | Dongle USB metálico sin marca | Conectado (Frontal) | Identificado lógicamente como HID USB (*Mouse Jiggler* continuo). |
| **G1-E04** | Nota adhesiva (Post-it amarillo) | Sobre el teclado | Contiene texto manuscrito: *"AES-K: Gr@n4d0_2026! // VPN: C2-Ext"*. |
| **G1-E05** | Cable de alimentación AC y UPS | Conectado a UPS APC 1500VA | El equipo cuenta con respaldo eléctrico activo de batería. |

**Preguntas Clave a Responder en el Informe y PowerPoint:**

1. ¿Adquisición en vivo (*live acquisition*) o recolección física directa (*collection*)? Justificar mediante Figuras 1 y 4 y numeral 6.8.
2. ¿Cómo aislar la interfaz de red para evitar un comando remoto de autodestrucción sin perder conexiones volátiles activas ni tablas ARP (6.2.3 y 7.2.2.2)?
3. Procedimiento para captura de RAM: herramientas confiables, impacto en memoria paginada y cálculo de hash (7.1.3.1.2).
4. Procedimiento técnico y normativo para el apagado seguro de un sistema con volúmenes cifrados montados (Figura 2 y 7.1.2.1.2).

---

#### GRUPO 2: Vectores Móviles, Medios Extraíbles y Manejo del Sesgo

*Alineación normativa: Numerales 6.7.5, 6.9, 7.1.3.5, 7.2.1, 7.2.2.1, 7.2.2.3.*

* **Referencia Operacional:** Caso OPE-DEF-2026-089.
* **Contexto:** Intervención en un Puesto de Mando Unificado a un operador de comunicaciones sospechoso de filtrar coordenadas tácticas.
* **Escena al arribar:**
* Smartphone Samsung bloqueado con PIN/patrón pero encendido sobre la mesa.
* Memoria USB en posesión del sujeto con la leyenda *"Música Personal - MP3"*. El operador insiste reiteradamente que solo contiene archivos de audio propios para intentar desviar la recolección.
* MicroSD suelta de 128 GB y dongle Wi-Fi de alta potencia en un cajón.
* Cobertura de red celular y Wi-Fi en pleno nivel de señal.



| ID Ítem | Descripción del Elemento | Estado Inicial | Particularidades Técnicas / Identificadores |
| --- | --- | --- | --- |
| **G2-E01** | Smartphone Samsung Galaxy S23 | Encendido / Bloqueado | IMEI: 358912345678901; Conectado a Wi-Fi y LTE; batería al 38%. |
| **G2-E02** | Unidad Flash USB Kingston DataTraveler 64GB | Desconectada | Rotulada a mano *"Música Personal"*; interfaz USB 3.2. |
| **G2-E03** | Tarjeta MicroSD SanDisk Extreme 128GB | Suelta (sin adaptador) | S/N: SD-88301-C10; sin marcas externas adicionales. |
| **G2-E04** | Tarjeta nano-SIM (en teléfono G2-E01) | Insertada | Operador Claro Colombia; ICCID legible parcialmente. |
| **G2-E05** | Adaptador USB Wi-Fi Alfa Network AWUS036ACM | Desconectado | Antenas desmontables; compatible con modo monitor e inyección. |

**Preguntas Clave a Responder en el Informe y PowerPoint:**

1. ¿Cómo fundamenta el perito la incautación de la USB frente al intento de inducir sesgo (*inherent bias*, numeral 6.7.5)?
2. ¿Qué riesgos inmediatos enfrenta el terminal móvil encendido y qué medidas de aislamiento RF y soporte de carga deben aplicarse (6.9.2 y 7.2.2.3)?
3. ¿Por qué el confinamiento en bolsa de Faraday acelera el drenaje de batería y cómo se contrarresta técnicamente en campo?
4. Protocolo de empaque antiestático, precintado y adquisición forense mediante *write-blocker* para la MicroSD y la USB.

---

#### GRUPO 3: Almacenamiento Centralizado (NAS/RAID) y Sistema CCTV

*Alineación normativa: Numerales 6.5, 6.6, 7.1.3.3, 7.1.3.4, 7.3.*

* **Referencia Operacional:** Caso OPE-DEF-2026-090.
* **Contexto:** Fuga de registros de auditoría y sospecha de conexión física de un dispositivo malicioso en el centro de cableado durante el fin de semana.
* **Escena al arribar:**
* Servidor NAS Synology en RAID 5 en producción ininterrumpida para dependencias médicas y de transporte.
* Grabador de video digital NVR Hikvision grabando en bucle con 16 cámaras IP activas.
* La orden judicial se delimita expresamente al directorio `/vol1/operaciones_especiales/` y grabaciones del pasillo entre las 02:00 y las 06:00 del 02/10/2026.



| ID Ítem | Descripción del Elemento | Estado Inicial | Particularidades Técnicas / Identificadores |
| --- | --- | --- | --- |
| **G3-E01** | Servidor NAS Synology RS2423+ | En producción / Crítico | S/N: 2280SYN-9011; 8 discos HDD SATA 4TB en RAID 5 (28 TB útiles). |
| **G3-E02** | Unidad NVR CCTV Hikvision DS-7716NI | En grabación continua | S/N: HK-88402-V; Reloj interno con desfase respecto a la hora legal. |
| **G3-E03** | Switch Distribución Cisco Catalyst 3850 | Operacional | Enlaces de fibra/cobre interconectando el NAS, NVR y red de datos. |
| **G3-E04** | Monitor de Gestión y Consola KVM | En reposo | Conectado a consolas de administración locales. |

**Preguntas Clave a Responder en el Informe y PowerPoint:**

1. ¿Por qué resulta improcedente apagar o extraer físicamente los discos del arreglo RAID de misión crítica (6.5 y 7.1.3.3)?
2. ¿Cómo se planifica y ejecuta una adquisición lógica/parcial circunscrita estrictamente al mandato judicial (5.4.4 y 7.1.3.4)?
3. Procedimiento para CCTV: ¿Por qué documentar el *time offset* del reloj del NVR y qué riesgo probatorio genera la transcodificación no nativa a formatos genéricos (7.3)?
4. ¿Cómo se valida y certifica que el NVR reanuda su servicio de forma íntegra tras la extracción pericial?

---

### 6. Formatos Estandarizados para los Entregables

---

#### FORMATO 1: Bitácora de Triaje y Justificación Técnica de la Intervención

*(Cumplimiento de los numerales 5.3.2 - Auditabilidad y 5.3.5 - Justificabilidad).*

* **Número de Caso:** __________________________________ **Fecha y Hora de Arribo:** ____________________
* **Equipo Pericial Responsable:** ____________________________________________________________________
* **Mandato Legal y Autoridad Emisora:** _______________________________________________________________
* **Evaluación Inicial de Riesgos en Escena (Numeral 6.2):**
---



| ID Dispositivo | Estado Inicial (ON / OFF) | ¿Contiene Datos Volátiles Críticos? (Sí / No) | Determinación Operativa (Colección Física vs. Adquisición en Vivo/Lógica) | Fundamentación Normativa (Cláusula ISO 27037) | Alteraciones Técnicas Inevitables Introducidas |
| --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |

---

#### FORMATO 2: Registro de Cadena de Custodia y Trazabilidad de Evidencia

*(Alineado con el numeral 6.1 y el Anexo B de la norma ISO/IEC 27037:2016).*

* **Referencia del Caso / Expediente:** _________________________________________________________________
* **Entidad / Unidad Investigadora:** ___________________________________________________________________
* **Ubicación Exacta de la Escena:** __________________________________________________________________

| Ítem N° | Descripción Detallada (Marca, Modelo, S/N) | Tipo de Empaque (Antiestático / Faraday / Rígido) | Número de Precinto / Sello de Seguridad | Algoritmo Hash (MD5 / SHA-256) | Valor Hash Verificado | Nombre, Rol y Firma del Receptor |
| --- | --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |

**Control de Movimiento y Transferencia de Custodia:**

* **Entrega:** ____________________________ **Cargo:** __________________ **Fecha/Hora:** ______________ **Firma:** ________________
* **Recibe:** _____________________________ **Cargo:** __________________ **Fecha/Hora:** ______________ **Firma:** ________________
* **Propósito del Traslado:** [  ] Almacenamiento en bodega de evidencias | [  ] Traslado a laboratorio forense

---
