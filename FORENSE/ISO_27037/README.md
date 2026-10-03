

# Taller Práctico Avanzado: Intervención Forense en Escenario de Crisis y Cadena de Custodia bajo ISO/IEC 27037
![](27037.png)
### 1. Ficha Técnica de la Actividad

* **Asignatura:** Informática Forense.
* **Programa:** Maestría en Ciberseguridad y Ciberdefensa.
* **Metodología:** Aprendizaje Basado en Problemas (ABP), juego de roles y simulación de incidentes en infraestructura crítica / defensa.
* **Modalidad de trabajo:** Tres (3) equipos multidisciplinarios.
* **Entregable formal:** Informe Técnico Pericial de Primer Respondiente y Registro de Cadena de Custodia (con defensa oral de 10 minutos por grupo).

---

### 2. Marco Normativo y Fundamentos Teóricos Obligatorios

Los equipos deberán fundamentar todas sus decisiones técnicas, procedimentales y jurídicas en:

1. **Los 4 pilares de la evidencia digital:** Auditabilidad (5.3.2), Repetibilidad (5.3.3), Reproducibilidad (5.3.4) y Justificabilidad (5.3.5).


2. **Las 4 fases del ciclo de vida:** Identificación (5.4.2), Recolección (5.4.3), Adquisición (5.4.4) y Preservación (5.4.5).


3. **Roles operativos:** Primer Respondedor (*Digital Evidence First Responder* - DEFR) y Especialista en Evidencia Digital (*Digital Evidence Specialist* - DES).


4. **Orden de volatilidad y datos en vivo:** Manejo de RAM, procesos, conexiones y contenedores cifrados previo a la desconexión o apagado (RFC 3227 y numeral 6.8 de la norma).


5. **Mitigación del sesgo inherente (*Inherent Bias*):** Neutralidad en la toma de decisiones basada en el *briefing* (numeral 6.7.5).


---

### 3. Contextualización del Escenario General

> Se ha detectado una fuga masiva de información clasificada y señales de persistencia avanzada (APT) en la sede de enlace de una agencia de mando y control del sector defensa. La alerta temprana sugiere que se han utilizado credenciales comprometidas y dispositivos no autorizados para exfiltrar fragmentos de planes operacionales hacia redes externas. El equipo forense recibe un mandato judicial/militar y un *briefing* inicial con tiempo limitado para intervenir y asegurar los potenciales elementos de evidencia física y lógica.

---

### 4. Distribución de Escenarios para los Tres Grupos de Trabajo

#### Grupo 1: Estación de Operaciones Crítica Encendida con Sospecha de Cifrado

* **Situación:** Una estación de trabajo de un operador se encuentra **encendida** (*powered-on*), con la sesión abierta. Se observan procesos desconocidos en ejecución, conexiones de red activas hacia direcciones IP externas y dos volúmenes montados con software de cifrado de disco completo (*full disk encryption*).


* **Reto técnico y operacional:**
* Aplicar el árbol de decisión de la norma (Figuras 1, 2 y 4): ¿recolección directa o adquisición previa?


* Documentar el triaje y la captura de memoria volátil (RAM, tablas de ruteo, llaves criptográficas residentes en memoria) sin alterar el estado del sistema más allá de lo técnicamente inevitable (justificación y auditabilidad).


* Protocolo para desconectar o aislar la interfaz de red (evitar comando remoto de autodestrucción) y determinación del método de apagado/transporte (¿extracción directa del cable de poder de la fuente o apagado regular?).




* **Roles a distribuir dentro del equipo:** DEFR líder de escena, DES especialista en extracción de RAM/análisis en vivo, Oficial de cadena de custodia y fotodocumentación.

#### Grupo 2: Dispositivos Móviles, Medios Extraíbles y Vectores Inalámbricos

* **Situación:** En el escritorio y en el área perimetral de la oficina se encuentran: un teléfono inteligente corporativo bloqueado pero encendido (conectado a la red Wi-Fi táctica), dos memorias USB sin rotular, una tarjeta micro-SD oculta en una gaveta y un adaptador inalámbrico no autorizado. El sospechoso ha manifestado que "solo usaba la USB para escuchar música", intentando inducir un sesgo en los actuantes.


* **Reto técnico y operacional:**
* Protocolos de aislamiento de radiofrecuencia (jaula/bolsa de Faraday, modo avión, bloqueo de señales, gestión de batería y drenaje energético) según los numerales 6.9.2 y 7.2.2.3.


* Análisis de la neutralidad investigativa frente al intento de sesgo del sospechoso (numeral 6.7.5).


* Selección de técnicas de preservación para medios de almacenamiento extraíbles: uso de bloqueadores de escritura (*write-blockers*), cálculo de funciones resumen (hashes MD5/SHA-256) antes y después del traslado.




* **Roles a distribuir dentro del equipo:** DEFR de escena, DES en telecomunicaciones y dispositivos móviles, Registrador forense y analista de empaque antiestático/RF.

#### Grupo 3: Infraestructura de Almacenamiento Centralizado (NAS/Servidor Local) y CCTV

* **Situación:** En el cuarto técnico se identifica un servidor de almacenamiento en red (NAS configurado en RAID) que aloja repositorios documentales compartidos y continúa en producción prestando servicio a otros departamentos. Adicionalmente, existe un grabador digital (DVR/CCTV) de circuito cerrado que registró los accesos físicos a la sala durante las últimas 48 horas.


* **Reto técnico y operacional:**
* Aplicación de las directrices para sistemas de misión crítica (*mission-critical systems*) según numerales 6.5, 7.1.3.3 y 7.1.3.4 (adquisición lógica y parcial vs. desconexión física total).


* Procedimiento específico para CCTV bajo el numeral 7.3: verificación de desviación temporal (*time offset* o desfase entre la hora del grabador y la hora real legal), determinación de sobreescritura, exportación en formato nativo con software de reproducción verificado (*replay software*) y preservación sin pérdidas por recompresión.


* Registro de auditoría para garantizar que la recolección parcial de datos no vulneró la confidencialidad de terceros ni alteró los metadatos.




* **Roles a distribuir dentro del equipo:** DEFR de infraestructura, DES de redes y sistemas de almacenamiento, Auditor de integridad y trazabilidad legal.

---

### 5. Guía de Ejecución en Clase

* **Fase 1: Asignación y Briefing Operacional (20 minutos)**
* Cada grupo recibe su caso detallado y una ficha física con el inventario simulado de elementos.
* Los estudiantes deben revisar el mandato y definir las competencias y herramientas requeridas (herramientas estáticas, contenedores forenses, bolsas Faraday, precintos de seguridad).




* **Fase 2: Taller de Toma de Decisiones y Trazabilidad (40 minutos)**
* Cada equipo elabora el diagrama de flujo de intervención siguiendo taxativamente las figuras 1 a 5 de la norma ISO/IEC 27037.


* Diligenciamiento de las actas de cadena de custodia, registro de inventario y justificación técnica de cada acción ejecutada.




* **Fase 3: Sustentación y Juicio de Admisibilidad (40 minutos)**
* Cada grupo expone su caso ante la clase (10 minutos por grupo).
* Los otros dos grupos actúan como contraparte/peritos de la defensa, buscando cuestionar la cadena de custodia, el riesgo de *spoliation* (alteración de la evidencia) o la existencia de sesgos en el levantamiento.





---

### 6. Estructura Requerida para el Informe Escrito (Entregable en Grupo)

El trabajo final de cada grupo deberá presentarse en formato de informe técnico-pericial y contener obligatoriamente las siguientes secciones:

1. **Identificación y Mandato:** Alcance de la investigación, marco legal de actuación y prevención de conflictos de interés (numeral 6.7.5).


2. **Evaluación de Riesgos y Precauciones en la Escena:** Análisis de riesgos al personal y a la evidencia (numeral 6.2).


3. **Procedimiento Técnico Ejecutado:**
* Orden de volatilidad aplicado.


* Justificación técnica del método elegido (adquisición en vivo, lógica, clonación física o recolección del hardware).


* Herramientas empleadas y validación previa de las mismas.




4. **Garantía de Principios Forenses:** Explicación concreta de cómo se garantizó la repetibilidad, reproducibilidad, auditabilidad y no repudio (funciones hash, bitácora de comandos).


5. **Formulario de Cadena de Custodia (Anexo B):** Registro detallado con identificadores únicos, números de serie, marcas, descripciones de empaque, sellos de seguridad y firmas de los custodios.

---

# GUÍA METODOLÓGICA GENERAL PARA EL ESTUDIANTE

### 1. Instrucciones de Trabajo Autónomo


* **Asignación de roles por equipo (3 a 5 maestrandos por grupo):**
1. *DEFR Líder de Escena:* Coordina el perímetro, evalúa riesgos físicos/técnicos y valida los sellos de seguridad.


2. *Digital Evidence Specialist (DES):* Diseña la estrategia técnica de adquisición, justifica herramientas estáticas/validadas y supervisa el orden de volatilidad.


3. *Oficial de Registro y Cadena de Custodia:* Diligencia las actas, calcula y registra funciones resumen (hash), y documenta la trazabilidad.


4. *Auditor de Calidad y Cumplimiento Normativo:* Contrasta cada decisión frente a los principios de auditabilidad, repetibilidad, reproducibilidad y justificabilidad (numerales 5.3.2 a 5.3.5).




* **Criterio de Evaluación:** El éxito del ejercicio radica en la justificación metodológica y la preservación inmaculada de la evidencia para evitar acusaciones de *spoliation* (alteración no controlada) o *inherent bias* (sesgo en la recolección).



---

# CASOS DETALLADOS Y FICHAS DE INVENTARIO SIMULADO

---

## GRUPO 1: ESTACIÓN DE TRABAJO CRÍTICA EN EJECUCIÓN CON VOLÚMENES CIFRADOS

Aplicación estricta de la norma: Numerales 5.3, 5.4, 6.2, 6.6, 6.8, 7.1.1, 7.1.2.1, 7.1.3.1; Figuras 1, 2 y 4.

### 1. Expediente del Caso (Mandato y Escena)

* **Referencia Operacional:** Caso OPE-DEF-2026-088.
* **Contexto:** Se comisiona al equipo DEFR/DES para intervenir la oficina del Director de Proyectos Especiales del Comando Conjunto de Ciberdefensa. Las alertas del SIEM indican tráfico anómalo masivo mediante túneles DNS hacia un servidor en el extranjero.
* **Escena al arribar:**
* Al ingresar a la oficina (09:15 horas), la estación de trabajo principal está **encendida** (*powered-on*).


* La pantalla se encuentra desbloqueada gracias a un dispositivo USB desconocido conectado en el panel frontal que emula actividad de ratón (*mouse jiggler*).


* En pantalla se observan dos consolas de PowerShell abiertas, una ventana de explorador de archivos con una unidad montada `V:\ (Volumen Seguro)` y una sesión activa de mensajería instantánea cifrada.
* El cable de red RJ-45 está conectado a la roseta de pared y el LED de actividad parpadea intensamente.
* El funcionario investigado no se encuentra presente, pero sobre el escritorio hay una nota manuscrita con palabras clave y contraseñas tentativas.





### 2. Ficha de Inventario y Evidencia Simulada (Grupo 1)

| ID Ítem | Descripción del Elemento | Estado Inicial | Particularidades Técnicas / Identificadores |
| --- | --- | --- | --- |
| **G1-E01** | Torre Workstation Dell Precision 5820 | Encendido (En ejecución) | S/N: 4HG78Y2; CPU Xeon, 64 GB RAM, 2x 1TB NVMe en RAID 0. Conexión Gigabit Ethernet activa.

 |
| **G1-E02** | Pantalla Dell UltraSharp 27" | Encendido | S/N: DL-99214; Muestra escritorio con volúmenes montados y consolas activas.

 |
| **G1-E03** | Dongle USB metálico sin marca | Conectado (Frontal) | Identificado lógicamente como HID USB (*Mouse Jiggler* continuo).

 |
| **G1-E04** | Nota adhesiva (Post-it amarillo) | Sobre el teclado | Contiene texto manuscrito: *"AES-K: Gr@n4d0_2026! // VPN: C2-Ext"*.

 |
| **G1-E05** | Cable de alimentación AC y UPS | Conectado a UPS APC 1500VA | El equipo cuenta con respaldo eléctrico activo de batería.

 |

### 3. Preguntas Clave y Retos Metodológicos para el Equipo

1. Siguiendo el árbol de decisión de la Figura 1 y 4: ¿Se debe realizar adquisición en vivo (*live acquisition*) o recolección física directa (*collection*)? Justificar con base en el concepto de *volatile data* (sección 3.26 y 6.8).


2. ¿Cómo se aísla la estación de la red para mitigar el riesgo de una instrucción remota de borrado (*logic-bomb* o autodestrucción) sin alterar las tablas ARP y conexiones TCP/IP activas (numerales 6.2.3 y 7.2.2.2)?


3. En caso de extraer la memoria RAM: ¿Qué consideraciones técnicas de la norma (numeral 7.1.3.1.2) deben aplicarse respecto a herramientas estáticas de confianza, desplazamiento de memoria (*paging*) y cálculo de hash?


4. ¿Cuál es el procedimiento normativo para apagar o transportar el equipo garantizando que los datos no se corrompan si el disco estuviera parcialmente cifrado (Figura 2 y nota 1 del 7.1.2.1.2)?



---

## GRUPO 2: VECTORES MÓVILES, DISPOSITIVOS INALÁMBRICOS Y MANEJO DEL SESGO

Aplicación estricta de la norma: Numerales 6.7.5, 6.9, 7.1.3.5, 7.2.1, 7.2.2.1, 7.2.2.3.

### 1. Expediente del Caso (Mandato y Escena)

* **Referencia Operacional:** Caso OPE-DEF-2026-089.
* **Contexto:** Durante una inspección contrainteligencia imprevista en un Puesto de Mando Unificado, se interviene a un oficial de comunicaciones sospechoso de filtrar coordenadas tácticas a través de aplicaciones celulares y dispositivos externos.
* **Escena al arribar:**
* El oficial está sentado con un teléfono inteligente Samsung Galaxy encendido sobre la mesa, con la pantalla bloqueada mediante patrón biométrico/PIN.


* En el bolsillo de su chaleco se encuentra una memoria USB rotulada *"Música Personal - MP3"*. El oficial insiste repetidamente: *"No pierdan el tiempo con esa memoria, solo tiene música de mi uso personal, revisen el computador del compañero que él sí maneja las órdenes de marcha"* (Tentativa explícita de inducir sesgo).


* En una gaveta abierta se observa una tarjeta MicroSD suelta de 128 GB, adaptadores de SIM y un dongle USB Wi-Fi de alta potencia configurado en modo monitor.


* Las redes celulares 4G/5G y la red Wi-Fi táctica tienen cobertura total y alta potencia en el recinto.





### 2. Ficha de Inventario y Evidencia Simulada (Grupo 2)

| ID Ítem | Descripción del Elemento | Estado Inicial | Particularidades Técnicas / Identificadores |
| --- | --- | --- | --- |
| **G2-E01** | Smartphone Samsung Galaxy S23 | Encendido / Bloqueado | IMEI: 358912345678901; Conectado a Wi-Fi y red móvil LTE; batería al 38%.

 |
| **G2-E02** | Unidad Flash USB Kingston DataTraveler 64GB | Desconectada | Etiquetada a mano *"Música Personal"*; conector tipo USB 3.2.

 |
| **G2-E03** | Tarjeta MicroSD SanDisk Extreme 128GB | Suelta (sin adaptador) | S/N: SD-88301-C10; sin rotulación visible.

 |
| **G2-E04** | Tarjeta nano-SIM (en el teléfono G2-E01) | Insertada | Operador Claro Colombia; ICCID visible parcialmente en bandeja.

 |
| **G2-E05** | Adaptador USB Wi-Fi Alfa Network AWUS036ACM | Desconectado | Antenas desmontables de alta ganancia; chipset compatible con inyección de paquetes de red. |

### 3. Preguntas Clave y Retos Metodológicos para el Equipo

1. Respecto a la manifestación del sospechoso sobre la memoria USB: ¿Cómo se fundamenta metodológicamente la actuación del DEFR frente al **sesgo inherente (*inherent bias*)** según el numeral 6.7.5 de la ISO 27037?


2. ¿Cuáles son los riesgos inmediatos asociados al teléfono encendido (bloqueo por temporizador, comandos de borrado remoto vía iCloud/Google Find My Device, recepción de tráfico push) y qué medidas de aislamiento físico/RF y preservación energética exige la norma (numerales 6.9.2 y 7.2.2.3)?


3. Si el teléfono se coloca dentro de una bolsa/jaula de Faraday: ¿Qué ocurre con el consumo de batería y cómo debe proceder el DEFR para evitar la pérdida del estado encendido (numeral 6.9.2 nota técnica)?


4. Para la tarjeta MicroSD y la memoria USB: Describir la secuencia de preservación física (materiales antiestáticos, precintos) y adquisición forense (bloqueador de escritura y cálculo de hash).



---

## GRUPO 3: SERVIDOR CRÍTICO DE ALMACENAMIENTO (NAS/RAID) Y SISTEMA CCTV

Aplicación estricta de la norma: Numerales 6.5, 6.6, 7.1.3.3, 7.1.3.4, 7.3.

### 1. Expediente del Caso (Mandato y Escena)

* **Referencia Operacional:** Caso OPE-DEF-2026-090.
* **Contexto:** Se ha detectado la manipulación y borrado de bitácoras de auditoría en un servidor central que soporta operaciones logísticas conjuntas. Simultáneamente, se sospecha que una persona no autorizada ingresó físicamente al centro de cableado para conectar un dispositivo de espionaje (*drop-box*) durante el fin de semana.
* **Escena al arribar:**
* En el rack de comunicaciones se encuentra un servidor de almacenamiento en red **NAS Synology RackStation** con 8 bahías en arreglo **RAID 5**. El sistema presta servicios simultáneos e ininterrumpidos al área médica y de transporte de la institución militar (sistema de misión crítica).


* En el mismo bastidor opera un grabador de video digital en red (**NVR/CCTV Hikvision**) conectado a 16 cámaras IP, con 4 discos duros internos grabando en bucle.


* La orden judicial autoriza únicamente la búsqueda y extracción de información relacionada con el directorio `/vol1/operaciones_especiales/` y las grabaciones de video del pasillo de acceso entre las 02:00 y las 06:00 horas del 2 de octubre de 2026.





### 2. Ficha de Inventario y Evidencia Simulada (Grupo 3)

| ID Ítem | Descripción del Elemento | Estado Inicial | Particularidades Técnicas / Identificadores |
| --- | --- | --- | --- |
| **G3-E01** | Servidor NAS Synology RS2423+ | En producción / Crítico | S/N: 2280SYN-9011; 8 discos HDD SATA de 4TB en RAID 5 (28 TB útiles). Aloja datos de múltiples áreas.

 |
| **G3-E02** | Unidad NVR CCTV Hikvision DS-7716NI | En grabación continua | S/N: HK-88402-V; Reloj interno desincronizado con respecto al NTP nacional. 16 canales activos.

 |
| **G3-E03** | Switch de Distribución Cisco Catalyst 3850 | Operacional | Conexiones de fibra óptica y cobre interconectando el NAS, NVR y red troncal.

 |
| **G3-E04** | Monitor de Gestión y Consola KVM | En reposo | Conectado directamente a las interfaces de video del NAS y del NVR.

 |

### 3. Preguntas Clave y Retos Metodológicos para el Equipo

1. Frente al servidor NAS: Considerando que es un sistema de misión crítica (*mission-critical system*) que comparte almacenamiento con unidades operativas y médicas inocentes (numerales 6.5 y 7.1.3.3): ¿Por qué es técnicamente inadmisible apagar el equipo o remover físicamente los discos duros?


2. ¿Cómo se planifica y documenta una **adquisición parcial / lógica (*partial/logical acquisition*)** conforme a los numerales 5.4.4 y 7.1.3.4, garantizando que no se extraiga información por fuera del mandato legal?


3. En el sistema CCTV (numeral 7.3):


* ¿Por qué es crítico documentar el desfase temporal (*time offset*) del reloj del DVR frente a una fuente horaria confiable y trazable antes de iniciar la exportación?


* ¿Qué riesgos probatorios existen si se decide exportar el video recodificándolo a formato AVI o MPEG genérico en lugar de exportar el flujo nativo propietario junto con su reproductor validado (*player software*)?




4. ¿Qué acciones deben realizarse para verificar que el NVR continúe su funcionamiento normal tras la extracción de las secuencias requeridas (numeral 7.3)?



---

# FORMATOS Y PLANTILLAS ESTANDARIZADAS PARA EL INFORME DE ENTREGA

Cada equipo de trabajo deberá entregar un dossier técnico formal que incorpore las siguientes tres herramientas diligenciadas:

### FORMATO 1: Bitácora de Triaje y Justificación Técnica de la Intervención

(Diseñado para dar cumplimiento a los numerales 5.3.2 - Auditabilidad y 5.3.5 - Justificabilidad).

* **Caso N°:** ____________________  **Fecha y Hora de Arribo:** _______________
* **Equipo Forense Responsable:** _____________________________________________
* **Mandato Legal y Autoridad que Ordena:** __________________________________
* **Evaluación de Riesgos en Escena (Riesgos físicos y lógicos identificados - Numeral 6.2):**

---


* **Matriz de Decisiones Técnicas:**

| Identificador del Dispositivo | Estado Encontrado (ON / OFF) | ¿Contiene Datos Volátiles Relevantes? (Sí/No) | Decisión Adoptada (Colección Física vs. Adquisición en Vivo/Lógica) | Justificación Técnica Normativa (Citar cláusula ISO 27037) | Alteraciones Inevitables Introducidas en el Sistema |
| --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |

---

### FORMATO 2: Registro de Cadena de Custodia y Transferencia de Evidencia

(Alineado con el numeral 6.1 y el Anexo B de la norma ISO/IEC 27037:2016).

* **Número Único de Noticia Criminal / Caso:** _________________________________
* **Organización / Entidad Interviniente:** ____________________________________
* **Dirección Física del Lugar de los Hechos:** ________________________________

| Ítem N° | Descripción Detallada (Marca, Modelo, S/N) | Tipo de Empaque (Antiestático, Faraday, Contenedor Rígido) | Número de Precinto / Sello de Seguridad | Algoritmo Hash Utilizado | Valor Hash de Verificación (MD5 / SHA-256) | Nombre y Firma del DEFR / DES que Colecta |
| --- | --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |

**Historial de Transferencia y Movimiento:**

* *Entrega:* ________________________ *Cargo:* ____________ *Fecha/Hora:* __________ *Firma:* _________
* *Recibe:* _________________________ *Cargo:* ____________ *Fecha/Hora:* __________ *Firma:* _________
* *Motivo de la Transferencia / Disposición:* (Traslado a Laboratorio / Almacenamiento Seguro)



---

### FORMATO 3: Rúbrica de Evaluación Cruzada y Juicio de Admisibilidad

*(Utilizada por los grupos opositores y el docente evaluador durante la sustentación oral).*

| Criterio Evaluado | Criterio Normativo ISO 27037 | Puntuación Máxima | Puntuación Obtenida | Observaciones del Tribunal / Contraparte |
| --- | --- | --- | --- | --- |
| **1. Neutralidad y Control de Sesgo** | Demuestra recolección objetiva sin omitir evidencias exculpatorias (6.7.5).

 | 20 pts |  |  |
| **2. Manejo de Volatilidad y Orden de Priorización** | Justifica técnicamente el tratamiento de RAM, tráfico activo o estado de apagado (6.8, 7.1, 7.2).

 | 25 pts |  |  |
| **3. Integridad y Verificación Criptográfica** | Aplica funciones de hash validadas, evita el uso de herramientas no confiables y documenta cambios residuales (5.3, 5.4.4).

 | 25 pts |  |  |
| **4. Cadena de Custodia y Empaque Técnico** | Documentación exhaustiva (Anexo B), empaque antiestático/Faraday y sellos inviolables (6.1, 6.9).

 | 20 pts |  |  |
| **5. Defensa Argumentativa y Justificabilidad** | Capacidad técnica para responder objeciones de spoliation o extralimitación en el mandato (5.3.5).

 | 10 pts |  |  |
| **TOTAL** |  | **100 pts** |  |  |



## Paquete instruccional

---

# GUÍA METODOLÓGICA GENERAL PARA EL ESTUDIANTE

### 1. Instrucciones de Trabajo Autónomo

* **Duración total:** 150 minutos (Fase de gabinete y triaje: 80 min | Consolidación documental: 40 min | Juicio oral de admisibilidad cruzado: 30 min).
* **Asignación de roles por equipo (3 a 5 maestrandos por grupo):**
1. *DEFR Líder de Escena:* Coordina el perímetro, evalúa riesgos físicos/técnicos y valida los sellos de seguridad.


2. *Digital Evidence Specialist (DES):* Diseña la estrategia técnica de adquisición, justifica herramientas estáticas/validadas y supervisa el orden de volatilidad.


3. *Oficial de Registro y Cadena de Custodia:* Diligencia las actas, calcula y registra funciones resumen (hash), y documenta la trazabilidad.


4. *Auditor de Calidad y Cumplimiento Normativo:* Contrasta cada decisión frente a los principios de auditabilidad, repetibilidad, reproducibilidad y justificabilidad (numerales 5.3.2 a 5.3.5).




* **Criterio de Evaluación:** El éxito del ejercicio radica en la justificación metodológica y la preservación inmaculada de la evidencia para evitar acusaciones de *spoliation* (alteración no controlada) o *inherent bias* (sesgo en la recolección).



---

# CASOS DETALLADOS Y FICHAS DE INVENTARIO SIMULADO

---

## GRUPO 1: ESTACIÓN DE TRABAJO CRÍTICA EN EJECUCIÓN CON VOLÚMENES CIFRADOS

Aplicación estricta de la norma: Numerales 5.3, 5.4, 6.2, 6.6, 6.8, 7.1.1, 7.1.2.1, 7.1.3.1; Figuras 1, 2 y 4.

### 1. Expediente del Caso (Mandato y Escena)

* **Referencia Operacional:** Caso OPE-DEF-2026-088.
* **Contexto:** Se comisiona al equipo DEFR/DES para intervenir la oficina del Director de Proyectos Especiales del Comando Conjunto de Ciberdefensa. Las alertas del SIEM indican tráfico anómalo masivo mediante túneles DNS hacia un servidor en el extranjero.
* **Escena al arribar:**
* Al ingresar a la oficina (09:15 horas), la estación de trabajo principal está **encendida** (*powered-on*).


* La pantalla se encuentra desbloqueada gracias a un dispositivo USB desconocido conectado en el panel frontal que emula actividad de ratón (*mouse jiggler*).


* En pantalla se observan dos consolas de PowerShell abiertas, una ventana de explorador de archivos con una unidad montada `V:\ (Volumen Seguro)` y una sesión activa de mensajería instantánea cifrada.
* El cable de red RJ-45 está conectado a la roseta de pared y el LED de actividad parpadea intensamente.
* El funcionario investigado no se encuentra presente, pero sobre el escritorio hay una nota manuscrita con palabras clave y contraseñas tentativas.





### 2. Ficha de Inventario y Evidencia Simulada (Grupo 1)

| ID Ítem | Descripción del Elemento | Estado Inicial | Particularidades Técnicas / Identificadores |
| --- | --- | --- | --- |
| **G1-E01** | Torre Workstation Dell Precision 5820 | Encendido (En ejecución) | S/N: 4HG78Y2; CPU Xeon, 64 GB RAM, 2x 1TB NVMe en RAID 0. Conexión Gigabit Ethernet activa.

 |
| **G1-E02** | Pantalla Dell UltraSharp 27" | Encendido | S/N: DL-99214; Muestra escritorio con volúmenes montados y consolas activas.

 |
| **G1-E03** | Dongle USB metálico sin marca | Conectado (Frontal) | Identificado lógicamente como HID USB (*Mouse Jiggler* continuo).

 |
| **G1-E04** | Nota adhesiva (Post-it amarillo) | Sobre el teclado | Contiene texto manuscrito: *"AES-K: Gr@n4d0_2026! // VPN: C2-Ext"*.

 |
| **G1-E05** | Cable de alimentación AC y UPS | Conectado a UPS APC 1500VA | El equipo cuenta con respaldo eléctrico activo de batería.

 |

### 3. Preguntas Clave y Retos Metodológicos para el Equipo

1. Siguiendo el árbol de decisión de la Figura 1 y 4: ¿Se debe realizar adquisición en vivo (*live acquisition*) o recolección física directa (*collection*)? Justificar con base en el concepto de *volatile data* (sección 3.26 y 6.8).


2. ¿Cómo se aísla la estación de la red para mitigar el riesgo de una instrucción remota de borrado (*logic-bomb* o autodestrucción) sin alterar las tablas ARP y conexiones TCP/IP activas (numerales 6.2.3 y 7.2.2.2)?


3. En caso de extraer la memoria RAM: ¿Qué consideraciones técnicas de la norma (numeral 7.1.3.1.2) deben aplicarse respecto a herramientas estáticas de confianza, desplazamiento de memoria (*paging*) y cálculo de hash?


4. ¿Cuál es el procedimiento normativo para apagar o transportar el equipo garantizando que los datos no se corrompan si el disco estuviera parcialmente cifrado (Figura 2 y nota 1 del 7.1.2.1.2)?



---

## GRUPO 2: VECTORES MÓVILES, DISPOSITIVOS INALÁMBRICOS Y MANEJO DEL SESGO

Aplicación estricta de la norma: Numerales 6.7.5, 6.9, 7.1.3.5, 7.2.1, 7.2.2.1, 7.2.2.3.

### 1. Expediente del Caso (Mandato y Escena)

* **Referencia Operacional:** Caso OPE-DEF-2026-089.
* **Contexto:** Durante una inspección contrainteligencia imprevista en un Puesto de Mando Unificado, se interviene a un oficial de comunicaciones sospechoso de filtrar coordenadas tácticas a través de aplicaciones celulares y dispositivos externos.
* **Escena al arribar:**
* El oficial está sentado con un teléfono inteligente Samsung Galaxy encendido sobre la mesa, con la pantalla bloqueada mediante patrón biométrico/PIN.


* En el bolsillo de su chaleco se encuentra una memoria USB rotulada *"Música Personal - MP3"*. El oficial insiste repetidamente: *"No pierdan el tiempo con esa memoria, solo tiene música de mi uso personal, revisen el computador del compañero que él sí maneja las órdenes de marcha"* (Tentativa explícita de inducir sesgo).


* En una gaveta abierta se observa una tarjeta MicroSD suelta de 128 GB, adaptadores de SIM y un dongle USB Wi-Fi de alta potencia configurado en modo monitor.


* Las redes celulares 4G/5G y la red Wi-Fi táctica tienen cobertura total y alta potencia en el recinto.





### 2. Ficha de Inventario y Evidencia Simulada (Grupo 2)

| ID Ítem | Descripción del Elemento | Estado Inicial | Particularidades Técnicas / Identificadores |
| --- | --- | --- | --- |
| **G2-E01** | Smartphone Samsung Galaxy S23 | Encendido / Bloqueado | IMEI: 358912345678901; Conectado a Wi-Fi y red móvil LTE; batería al 38%.

 |
| **G2-E02** | Unidad Flash USB Kingston DataTraveler 64GB | Desconectada | Etiquetada a mano *"Música Personal"*; conector tipo USB 3.2.

 |
| **G2-E03** | Tarjeta MicroSD SanDisk Extreme 128GB | Suelta (sin adaptador) | S/N: SD-88301-C10; sin rotulación visible.

 |
| **G2-E04** | Tarjeta nano-SIM (en el teléfono G2-E01) | Insertada | Operador Claro Colombia; ICCID visible parcialmente en bandeja.

 |
| **G2-E05** | Adaptador USB Wi-Fi Alfa Network AWUS036ACM | Desconectado | Antenas desmontables de alta ganancia; chipset compatible con inyección de paquetes de red. |

### 3. Preguntas Clave y Retos Metodológicos para el Equipo

1. Respecto a la manifestación del sospechoso sobre la memoria USB: ¿Cómo se fundamenta metodológicamente la actuación del DEFR frente al **sesgo inherente (*inherent bias*)** según el numeral 6.7.5 de la ISO 27037?


2. ¿Cuáles son los riesgos inmediatos asociados al teléfono encendido (bloqueo por temporizador, comandos de borrado remoto vía iCloud/Google Find My Device, recepción de tráfico push) y qué medidas de aislamiento físico/RF y preservación energética exige la norma (numerales 6.9.2 y 7.2.2.3)?


3. Si el teléfono se coloca dentro de una bolsa/jaula de Faraday: ¿Qué ocurre con el consumo de batería y cómo debe proceder el DEFR para evitar la pérdida del estado encendido (numeral 6.9.2 nota técnica)?


4. Para la tarjeta MicroSD y la memoria USB: Describir la secuencia de preservación física (materiales antiestáticos, precintos) y adquisición forense (bloqueador de escritura y cálculo de hash).



---

## GRUPO 3: SERVIDOR CRÍTICO DE ALMACENAMIENTO (NAS/RAID) Y SISTEMA CCTV

Aplicación estricta de la norma: Numerales 6.5, 6.6, 7.1.3.3, 7.1.3.4, 7.3.

### 1. Expediente del Caso (Mandato y Escena)

* **Referencia Operacional:** Caso OPE-DEF-2026-090.
* **Contexto:** Se ha detectado la manipulación y borrado de bitácoras de auditoría en un servidor central que soporta operaciones logísticas conjuntas. Simultáneamente, se sospecha que una persona no autorizada ingresó físicamente al centro de cableado para conectar un dispositivo de espionaje (*drop-box*) durante el fin de semana.
* **Escena al arribar:**
* En el rack de comunicaciones se encuentra un servidor de almacenamiento en red **NAS Synology RackStation** con 8 bahías en arreglo **RAID 5**. El sistema presta servicios simultáneos e ininterrumpidos al área médica y de transporte de la institución militar (sistema de misión crítica).


* En el mismo bastidor opera un grabador de video digital en red (**NVR/CCTV Hikvision**) conectado a 16 cámaras IP, con 4 discos duros internos grabando en bucle.


* La orden judicial autoriza únicamente la búsqueda y extracción de información relacionada con el directorio `/vol1/operaciones_especiales/` y las grabaciones de video del pasillo de acceso entre las 02:00 y las 06:00 horas del 2 de octubre de 2026.





### 2. Ficha de Inventario y Evidencia Simulada (Grupo 3)

| ID Ítem | Descripción del Elemento | Estado Inicial | Particularidades Técnicas / Identificadores |
| --- | --- | --- | --- |
| **G3-E01** | Servidor NAS Synology RS2423+ | En producción / Crítico | S/N: 2280SYN-9011; 8 discos HDD SATA de 4TB en RAID 5 (28 TB útiles). Aloja datos de múltiples áreas.

 |
| **G3-E02** | Unidad NVR CCTV Hikvision DS-7716NI | En grabación continua | S/N: HK-88402-V; Reloj interno desincronizado con respecto al NTP nacional. 16 canales activos.

 |
| **G3-E03** | Switch de Distribución Cisco Catalyst 3850 | Operacional | Conexiones de fibra óptica y cobre interconectando el NAS, NVR y red troncal.

 |
| **G3-E04** | Monitor de Gestión y Consola KVM | En reposo | Conectado directamente a las interfaces de video del NAS y del NVR.

 |

### 3. Preguntas Clave y Retos Metodológicos para el Equipo

1. Frente al servidor NAS: Considerando que es un sistema de misión crítica (*mission-critical system*) que comparte almacenamiento con unidades operativas y médicas inocentes (numerales 6.5 y 7.1.3.3): ¿Por qué es técnicamente inadmisible apagar el equipo o remover físicamente los discos duros?


2. ¿Cómo se planifica y documenta una **adquisición parcial / lógica (*partial/logical acquisition*)** conforme a los numerales 5.4.4 y 7.1.3.4, garantizando que no se extraiga información por fuera del mandato legal?


3. En el sistema CCTV (numeral 7.3):


* ¿Por qué es crítico documentar el desfase temporal (*time offset*) del reloj del DVR frente a una fuente horaria confiable y trazable antes de iniciar la exportación?


* ¿Qué riesgos probatorios existen si se decide exportar el video recodificándolo a formato AVI o MPEG genérico en lugar de exportar el flujo nativo propietario junto con su reproductor validado (*player software*)?




4. ¿Qué acciones deben realizarse para verificar que el NVR continúe su funcionamiento normal tras la extracción de las secuencias requeridas (numeral 7.3)?



---

# FORMATOS Y PLANTILLAS ESTANDARIZADAS PARA EL INFORME DE ENTREGA

Cada equipo de trabajo deberá entregar un dossier técnico formal que incorpore las siguientes tres herramientas diligenciadas:

### FORMATO 1: Bitácora de Triaje y Justificación Técnica de la Intervención

(Diseñado para dar cumplimiento a los numerales 5.3.2 - Auditabilidad y 5.3.5 - Justificabilidad).

* **Caso N°:** ____________________  **Fecha y Hora de Arribo:** _______________
* **Equipo Forense Responsable:** _____________________________________________
* **Mandato Legal y Autoridad que Ordena:** __________________________________
* **Evaluación de Riesgos en Escena (Riesgos físicos y lógicos identificados - Numeral 6.2):**

---


* **Matriz de Decisiones Técnicas:**

| Identificador del Dispositivo | Estado Encontrado (ON / OFF) | ¿Contiene Datos Volátiles Relevantes? (Sí/No) | Decisión Adoptada (Colección Física vs. Adquisición en Vivo/Lógica) | Justificación Técnica Normativa (Citar cláusula ISO 27037) | Alteraciones Inevitables Introducidas en el Sistema |
| --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |

---

### FORMATO 2: Registro de Cadena de Custodia y Transferencia de Evidencia

(Alineado con el numeral 6.1 y el Anexo B de la norma ISO/IEC 27037:2016).

* **Número Único de Noticia Criminal / Caso:** _________________________________
* **Organización / Entidad Interviniente:** ____________________________________
* **Dirección Física del Lugar de los Hechos:** ________________________________

| Ítem N° | Descripción Detallada (Marca, Modelo, S/N) | Tipo de Empaque (Antiestático, Faraday, Contenedor Rígido) | Número de Precinto / Sello de Seguridad | Algoritmo Hash Utilizado | Valor Hash de Verificación (MD5 / SHA-256) | Nombre y Firma del DEFR / DES que Colecta |
| --- | --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |

**Historial de Transferencia y Movimiento:**

* *Entrega:* ________________________ *Cargo:* ____________ *Fecha/Hora:* __________ *Firma:* _________
* *Recibe:* _________________________ *Cargo:* ____________ *Fecha/Hora:* __________ *Firma:* _________
* *Motivo de la Transferencia / Disposición:* (Traslado a Laboratorio / Almacenamiento Seguro)



---

### FORMATO 3: Rúbrica de Evaluación Cruzada y Juicio de Admisibilidad

*(Utilizada por los grupos opositores y el docente evaluador durante la sustentación oral).*

| Criterio Evaluado | Criterio Normativo ISO 27037 | Puntuación Máxima | Puntuación Obtenida | Observaciones del Tribunal / Contraparte |
| --- | --- | --- | --- | --- |
| **1. Neutralidad y Control de Sesgo** | Demuestra recolección objetiva sin omitir evidencias exculpatorias (6.7.5).

 | 20 pts |  |  |
| **2. Manejo de Volatilidad y Orden de Priorización** | Justifica técnicamente el tratamiento de RAM, tráfico activo o estado de apagado (6.8, 7.1, 7.2).

 | 25 pts |  |  |
| **3. Integridad y Verificación Criptográfica** | Aplica funciones de hash validadas, evita el uso de herramientas no confiables y documenta cambios residuales (5.3, 5.4.4).

 | 25 pts |  |  |
| **4. Cadena de Custodia y Empaque Técnico** | Documentación exhaustiva (Anexo B), empaque antiestático/Faraday y sellos inviolables (6.1, 6.9).

 | 20 pts |  |  |
| **5. Defensa Argumentativa y Justificabilidad** | Capacidad técnica para responder objeciones de spoliation o extralimitación en el mandato (5.3.5).

 | 10 pts |  |  |
| **TOTAL** |  | **100 pts** |  |  |
