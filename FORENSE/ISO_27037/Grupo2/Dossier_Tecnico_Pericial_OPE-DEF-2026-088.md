**MAESTRÍA EN CIBERSEGURIDAD Y CIBERDEFENSA** · Asignatura: Informática Forense

# Dossier Técnico Pericial

**Intervención forense en escenario de crisis y cadena de custodia bajo ISO/IEC 27037**

**Caso OPE-DEF-2026-088 – Estación de operaciones crítica encendida con volúmenes cifrados**

| **Grupo sustentante**                           | Grupo 2                                                            |
|-------------------------------------------------|--------------------------------------------------------------------|
| **DEFR Líder de Escena**                        | Johan Camilo Tamara                                                |
| **Especialista en Evidencia Digital (DES)**     | Natalia Forero Lozano                                              |
| **Oficial de Registro y Cadena de Custodia**    | Laura Angélica Gutiérrez                                           |
| **Auditor de Calidad y Cumplimiento Normativo** | Ayda Castro Suárez                                                 |
| **Metodología**                                 | Aprendizaje Basado en Problemas (ABP), juego de roles y simulación |
| **Fecha de la intervención simulada**           | 15/10/2026                                                         |

> [!NOTE]
> *Documento académico. Todos los valores hash, números de precinto, horas y resultados técnicos son simulados para fines de entrenamiento.*

## Contenido

1. [Resumen ejecutivo](#1-resumen-ejecutivo)
2. [Marco normativo aplicado](#2-marco-normativo-aplicado)
3. [Análisis de la escena, riesgos y mitigación del sesgo](#3-análisis-de-la-escena-riesgos-y-mitigación-del-sesgo)
4. [Respuestas analíticas a las preguntas clave](#4-respuestas-analíticas-a-las-preguntas-clave)
5. [Secuencia operativa cronológica](#5-secuencia-operativa-cronológica)
6. [Formato 1: Bitácora de Triaje y Justificación Técnica de la Intervención](#6-formato-1-bitácora-de-triaje-y-justificación-técnica-de-la-intervención)
7. [Formato 2: Registro de Cadena de Custodia y Trazabilidad de Evidencia](#7-formato-2-registro-de-cadena-de-custodia-y-trazabilidad-de-evidencia)
8. [Matriz de defensa técnica frente a acusaciones de alteración o sesgo](#8-matriz-de-defensa-técnica-frente-a-acusaciones-de-alteración-o-sesgo)
9. [Preparación para el contrainterrogatorio](#9-preparación-para-el-contrainterrogatorio)
10. [Kit de herramientas y validación (referencial)](#10-kit-de-herramientas-y-validación-referencial)
- [Referencias](#referencias)

# 1. Resumen ejecutivo

El Grupo 2 fue comisionado como equipo DEFR/DES para intervenir la oficina del Director de Proyectos Especiales del Comando Conjunto de Ciberdefensa, tras alertas del SIEM que reportan tráfico anómalo masivo a través de túneles DNS hacia un servidor en el extranjero, en el contexto de una fuga de información clasificada (planes operativos) con indicios de persistencia avanzada (APT), uso de credenciales certificadas y dispositivos no autorizados.

Al arribo (09:15 h) la estación de trabajo G1-E01 se encontraba **encendida, desbloqueada por un mouse jiggler (G1-E03), con un volumen cifrado montado (V:\\, dos consolas de PowerShell abiertas, una sesión de mensajería cifrada activa y tráfico de red intenso**, alimentada a través de una UPS (G1-E05). Sobre el teclado había una nota manuscrita con aparentes credenciales (G1-E04).

**Decisión técnica central:** con base en las Figuras 1, 2 y 4 y los numerales 6.8 y 7.1.3.1 de ISO/IEC 27037, se determinó que el desconectar o apagar el equipo destruiría de forma irreversible la evidencia más valiosa (claves del volumen cifrado en memoria, procesos maliciosos, conexiones al C2 y contenido descifrado de V:\\. Por tanto se ejecutó **adquisición en vivo** siguiendo el orden de volatilidad (RFC 3227): contención de red a nivel de infraestructura sin desconectar el host, volcado de RAM, respuesta en vivo, imagen lógica del volumen cifrado montado y de artefactos de C:\\ y solo después **recolección física** del equipo mediante corte de energía en el chasis (no en la pared, por la UPS), con embalaje técnico y cadena de custodia conforme al Anexo B.

> **Resultado de la intervención (simulado)**  
> • 5 elementos inventariados en escena; 3 recolectados físicamente (G1-E01, G1-E03, G1-E04) y 2 documentados in situ sin recolección (G1-E02, G1-E05) por no contener datos de interés.  
> • 6 elementos de evidencia digital derivados (D01–D06) con doble función resumen SHA-256 + MD5, calculada en escena y verificada.  
> • 9 alteraciones técnicas inevitables identificadas, minimizadas y documentadas (principio de justificabilidad 5.3.5).  
> • Pendiente en laboratorio: imagen física de los dos NVMe y reconstrucción del RAID 0; análisis de memoria para extracción de claves y artefactos de exfiltración.

## 1.1 Delimitación del alcance del mandato

| **Mandato y autoridad** | Orden de registro y allanamiento con facultad de recolección de elementos materiales probatorios (EMP) y evidencia física (EF) digital y de recuperación de información (Ley 906 de 2004, arts. 219-220 y 236), emitida por Juez de Control de Garantías a solicitud de Fiscalía delegada; con acompañamiento de Policía Judicial y del oficial de contrainteligencia de la unidad (Ley 1621 de 2013). No autoriza interceptación de comunicaciones en curso (art. 235). |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Dentro del alcance**  | Estación G1-E01 y sus periféricos en la oficina del Director; datos almacenados (C:\\ V:\\ RAID), memoria volátil, estado de red del host; elementos físicos asociados (G1-E03, G1-E04); registros de red del SOC asociados al host (SPAN, firewall, DNS).                                                                                                                                                                                                               |
| **Fuera del alcance**   | Lectura o interacción con el contenido de la sesión de mensajería en curso (equivaldría a interceptación – art. 235 Ley 906/2004; solo se fija lo visible en pantalla al arribo); uso de la clave del post-it para acceder a sistemas remotos o a la «VPN C2-Ext»; dispositivos personales del funcionario no presentes; otras oficinas.                                                                                                                                 |
| **Condición especial**  | La clave manuscrita «AES-K» solo podrá usarse en laboratorio, sobre copias, para descifrar evidencia ya adquirida y previa ampliación expresa de la orden.                                                                                                                                                                                                                                                                                                               |

# 2. Marco normativo aplicado

Las decisiones técnicas se fundamentan en ISO/IEC 27037:2012 (adoptada en Colombia como NTC-ISO/IEC 27037:2016), en RFC 3227 para el orden de volatilidad y en el marco procesal colombiano de cadena de custodia. La siguiente tabla resume cómo se aplicó cada fundamento obligatorio del taller.

| **Fundamento**           | **Numeral**    | **Aplicación concreta en el caso**                                                                                                                                        |
|--------------------------|----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Auditabilidad**        | 5.3.2          | Bitácora con hora, actor y comando de cada acción (Formato 1); fijación audiovisual continua; firma de testigos y del Auditor de Calidad.                                 |
| **Repetibilidad**        | 5.3.3          | Herramientas, versiones y parámetros registrados; hash de cada imagen recalculado dos veces con la misma herramienta y medio.                                             |
| **Reproducibilidad**     | 5.3.4          | Verificación cruzada de hashes con una segunda herramienta (sha256sum / FTK Imager); para RAM (no repetible) se reproduce el análisis sobre la imagen, no la adquisición. |
| **Justificabilidad**     | 5.3.5          | Cada decisión y cada alteración inevitable tiene justificación escrita y referencia normativa (columna «Fundamento» del Formato 1).                                       |
| **Identificación**       | 5.4.2 / 7.1.1  | Inventario G1-E01…E05, identificación de fuentes lógicas (RAM, V:\\ C:\\ red) y de datos fuera del host (SIEM, SPAN, DNS).                                                |
| **Recolección**          | 5.4.3 / 7.1.2  | Recolección física de G1-E01, G1-E03 y G1-E04 tras completar la adquisición en vivo.                                                                                      |
| **Adquisición**          | 5.4.4 / 7.1.3  | Adquisición en vivo: RAM, respuesta en vivo, imagen lógica de V:\\ y artefactos de C:\\ adquisición física de NVMe diferida a laboratorio.                                |
| **Preservación**         | 5.4.5 / 7.1.4  | Embalaje antiestático y rígido, sellos numerados, almacenamiento controlado y registro de transferencias (Anexo B).                                                       |
| **Roles DEFR / DES**     | 6.3 / Anexo A  | DEFR asegura escena y riesgos; DES decide y ejecuta adquisición en vivo; Oficial de Registro documenta; Auditor verifica cumplimiento en tiempo real.                     |
| **Orden de volatilidad** | 6.8 / RFC 3227 | Memoria → estado de red y procesos → sistemas de archivos montados → disco; ver Sección 4.                                                                                |
| **Sesgo inherente**      | 6.7.5          | Hipótesis alternativas formales y búsqueda de evidencia exculpatoria (Sección 3).                                                                                         |
| **Cadena de custodia**   | 6.1 / Anexo B  | Formato 2 con descripción, empaque, sello, hash, receptor y transferencias.                                                                                               |

# 3. Análisis de la escena, riesgos y mitigación del sesgo

## 3.1 Evaluación inicial de riesgos (numeral 6.2)

| **Tipo** | **Riesgo identificado**                                                         | **Control aplicado**                                                                                                             |
|----------|---------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| Físico   | Ingreso de terceros o del funcionario investigado a la escena                   | Perímetro con Policía Judicial; registro de toda persona que entra/sale; acceso solo a DEFR, DES y Oficial de Registro.          |
| Físico   | Corte accidental de energía / descarga de UPS                                   | Verificación de autonomía de la UPS (registro de % de batería); no manipular tomas; plan de corte controlado en el chasis.       |
| Físico   | Daño electrostático o contaminación de huellas                                  | Guantes de nitrilo, pulsera antiestática, manipulación mínima del teclado y del post-it.                                         |
| Lógico   | Orden remota de borrado (logic bomb) vía canal C2 / túnel DNS                   | Contención a nivel de switch/firewall (bloqueo de egreso y sinkhole DNS) sin desconectar el cable del host; captura SPAN pasiva. |
| Lógico   | «Dead man’s switch»: borrado si el malware pierde contacto con el C2            | Adquisición de RAM inmediatamente después de la contención; vigilancia de actividad de disco y procesos durante la intervención. |
| Lógico   | Bloqueo de sesión / desmontaje de V:\\ si se retira el jiggler                  | El jiggler NO se retira hasta terminar la adquisición en vivo; no se cambia la configuración de energía.                         |
| Lógico   | Scripts antiforenses en apagado ordenado (shutdown scripts, tareas programadas) | Apagado por corte de energía en el chasis tras asegurar datos volátiles y lógicos.                                               |
| Lógico   | Binarios del sistema troyanizados (rootkit)                                     | Uso exclusivo de herramientas estáticas confiables desde medio de solo lectura.                                                  |
| Jurídico | Exceder el mandato (interceptación de la mensajería)                            | Solo fijación de lo visible; no se lee ni desplaza la conversación.                                                              |

## 3.2 Mitigación del sesgo inherente (numeral 6.7.5)

El briefing inicial apunta al Director como responsable. Para evitar sesgo de confirmación, el equipo adoptó las siguientes medidas: (a) el DES documenta hechos observables y no conclusiones de autoría; (b) se formulan hipótesis alternativas y se recolecta evidencia que permita confirmarlas o descartarlas; (c) el Auditor de Calidad revisa que el lenguaje del acta sea neutral («el usuario de la sesión», no «el Director»).

| **\#** | **Hipótesis alternativa**                                                                           | **Evidencia que la confirmaría o descartaría**                                                                                  |
|--------|-----------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
| H1     | El Director exfiltró la información de forma deliberada.                                            | Autenticaciones interactivas, biometría/badge de acceso físico, historial de PowerShell coherente con su perfil, horarios.      |
| H2     | Las credenciales del Director fueron comprometidas y un tercero opera remotamente (APT).            | Procesos de acceso remoto, conexiones entrantes, tareas programadas, persistencia en RAM (inyección), logon type 10/3.          |
| H3     | Un tercero con acceso físico plantó el jiggler y la nota para incriminar o para mantener la sesión. | Registros de control de acceso físico, CCTV, huellas/ADN en G1-E03 y G1-E04, primer registro USB del dongle (setupapi.dev.log). |
| H4     | El tráfico DNS es un falso positivo (software legítimo).                                            | Análisis de dominios y volumen en PCAP SPAN, firma del proceso que genera las consultas.                                        |

# 4. Respuestas analíticas a las preguntas clave

## Pregunta 1. ¿Adquisición en vivo o recolección física directa?

**Respuesta: adquisición en vivo, seguida de recolección física.** Aplicando el árbol de decisión de la Figura 1 (¿el dispositivo está encendido? → sí) y la Figura 4 (adquisición de dispositivo encendido), la desconexión inmediata solo es preferible cuando no existen datos volátiles críticos o cuando el riesgo de destrucción en vivo supera el valor de los datos. En este caso se cumplen todas las condiciones que exigen adquirir en vivo:

- **Datos volátiles (definición 3.26 y numeral 6.8):** la RAM de 64 GB contiene las claves maestras del volumen cifrado V:\\ procesos de PowerShell (posible malware sin archivo / fileless), el proceso que genera el túnel DNS, la sesión de mensajería y las conexiones al C2. Todo se pierde al apagar.

- **Volumen cifrado montado:** V:\\ está accesible en claro solo mientras la sesión está activa. Apagar convertiría un contenedor legible en datos cifrados posiblemente irrecuperables (nota 1 del 7.1.2.1.2).

- **RAID 0 sobre NVMe:** la imagen física posterior exige reconstruir el arreglo; la vista lógica en vivo del sistema ya ensamblado reduce el riesgo de pérdida de interpretación del arreglo.

- **Valor investigativo vs. riesgo:** el riesgo de alteración por la ejecución de herramientas es mínimo, medible y documentable; la pérdida por apagado es total e irreversible. La justificabilidad (5.3.5) favorece la adquisición en vivo.

La **recolección física** (5.4.3) se realiza al final, una vez asegurados los datos volátiles y lógicos, para permitir en laboratorio la imagen bit a bit de los NVMe (repetible y reproducible).

> **Secuencia aplicada según orden de volatilidad (RFC 3227 / 6.8)**  
> 1. Fijación fotográfica y en video de escena y pantalla (sin tocar teclado ni ratón).  
> 2. Contención de red a nivel de infraestructura + captura SPAN pasiva.  
> 3. Volcado de memoria RAM completa.  
> 4. Respuesta en vivo: procesos, conexiones, ARP, caché DNS, rutas, sesiones, tareas programadas.  
> 5. Imagen lógica del volumen cifrado montado V:\\ y artefactos de C:\\ (pagefile, historial PowerShell, eventos).  
> 6. Retiro del jiggler, corte de energía en el chasis, embalaje y traslado.  
> 7. En laboratorio: imagen física de NVMe y reconstrucción del RAID 0.

## Pregunta 2. Aislamiento de red sin alterar ARP y conexiones TCP/IP

Desconectar el RJ-45 del equipo provoca un evento de «medio desconectado» en el sistema operativo: se vacían entradas ARP, las conexiones TCP pasan a estados de cierre o expiran y el malware puede detectar la pérdida de enlace. Por ello, de acuerdo con los numerales 6.2.3 (precauciones en el lugar) y 7.2.2.2 (dispositivos en red), **el aislamiento se hace aguas arriba, nunca en el host**:

1.  **Captura pasiva primero:** el SOC configura un puerto espejo (SPAN) en el switch de acceso y registra todo el tráfico del host (G1-NET-D06). Esto no altera el host y preserva la evidencia del túnel DNS.

2.  **Contención lógica en la infraestructura:** se aplica una ACL de denegación de egreso al exterior (o se reubica el puerto en una VLAN de cuarentena sin salida) y se hace sinkhole del dominio del túnel DNS en los resolutores internos. El enlace físico permanece activo (LED encendido), por lo que el host conserva su tabla ARP, su configuración IP y el estado de los sockets; solo se impide que llegue una orden remota de borrado.

3.  **Preservación de evidencia externa:** se solicitan con acta los registros de firewall, proxy, DNS y SIEM del período, con hash al recibirlos.

4.  **Captura del estado de red en el host** después del volcado de RAM (netstat -ano, arp -a, ipconfig /displaydns, route print) con herramientas estáticas confiables (D02).

5.  **Alternativa descartada:** jaula/bolsa Faraday no aplica a una conexión cableada; desconectar el cable se reserva solo si se observa borrado activo en curso (decisión del DES, documentada).

**Alteración inevitable reconocida:** la contención impide nuevas conexiones salientes, lo que se reflejará en la RAM como intentos fallidos al C2. Se documenta la hora exacta (09:24) para que el análisis distinga el estado previo y posterior a la contención.

## Pregunta 3. Consideraciones para extraer la memoria RAM (numeral 7.1.3.1.2)

| **Consideración**                                          | **Aplicación en el caso**                                                                                                                                                                                                                                                                                                            |
|------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Herramientas estáticas de confianza**                    | Binarios compilados estáticamente (WinPmem / Magnet RAM Capture, kit de respuesta en vivo) ejecutados desde un medio de solo lectura previamente verificado por hash; nunca se usan los binarios del sistema investigado (podrían estar troyanizados). Versión, hash de la herramienta y validación previa se registran en bitácora. |
| **Huella mínima y desplazamiento de memoria (paginación)** | Toda herramienta se carga en RAM y desplaza páginas, empujando parte de la memoria al archivo de paginación. Se elige la herramienta de menor tamaño, se ejecuta una sola vez y se documenta la huella aproximada (proceso, PID, memoria usada). Se adquiere luego pagefile.sys (D04) para recuperar lo paginado.                    |
| **Destino de la imagen**                                   | Medio externo estéril (borrado y verificado), con capacidad ≥ 128 GB para 64 GB de RAM, conectado a puerto USB 3.x trasero. Nunca se escribe sobre los discos del equipo investigado.                                                                                                                                                |
| **Cálculo de hash**                                        | SHA-256 (principal) y MD5 (compatibilidad) calculados sobre el archivo de imagen inmediatamente al finalizar, registrados en Formato 2 y firmados. La RAM no puede volver a «hashearse» en origen: el hash garantiza la integridad de la copia desde ese momento, no su igualdad con un original que ya cambió.                      |
| **Repetibilidad limitada**                                 | La adquisición de RAM no es repetible (5.3.3) porque la memoria cambia continuamente («memory smear»). Se compensa con justificabilidad (5.3.5) y con reproducibilidad del análisis sobre la imagen.                                                                                                                                 |
| **Orden y tiempo**                                         | La RAM se adquiere antes de cualquier comando de respuesta en vivo para no contaminarla con las salidas de esas herramientas. Tiempo estimado 20–25 min.                                                                                                                                                                             |
| **Riesgo de fallo**                                        | Si la herramienta provoca bloqueo del sistema (BSOD), se documenta y se procede a recolección física; por eso se prefiere una herramienta probada en hardware Dell/Xeon equivalente.                                                                                                                                                 |

## Pregunta 4. Apagado y transporte con disco parcialmente cifrado (Figura 2 y nota 1 del 7.1.2.1.2)

La norma advierte que, si existe cifrado, apagar el equipo puede dejar los datos inaccesibles y que el DEFR debe consultar al DES antes de decidir. El procedimiento aplicado fue:

1.  **Asegurar primero el contenido descifrado:** imagen lógica de V:\\ montado (D03) y verificación de hash. Se identifica el tipo de cifrado (manage-bde -status para BitLocker; lista de volúmenes del software de contenedores) y se registra.

2.  **Verificar cifrado del disco de sistema:** si C:\\ tiene BitLocker, se documenta el ID del protector y se solicita la clave de recuperación al custodio del directorio corporativo por la vía del mandato; adicionalmente se adquieren en vivo los artefactos críticos de C:\\ (D04). La RAM (D01) conserva además las claves para recuperación en laboratorio.

3.  **Documentar el RAID 0:** fotografía de la BIOS/controladora o salida de la herramienta del fabricante (tamaño de bloque, orden de discos); se rotula la posición física de cada NVMe.

4.  **Retirar el jiggler (G1-E03)** solo al final, con fotografía previa y posterior.

5.  **Apagado por corte de energía en el chasis:** se desconecta el cable de alimentación del lado de la torre. Desconectar en la pared no apaga el equipo porque la UPS mantiene la energía. Se prefiere el corte abrupto al apagado ordenado para no ejecutar scripts de apagado antiforenses ni desmontajes que borren llaves o sobrescriban datos; como los datos cifrados ya fueron asegurados en claro, el riesgo de corrupción del contenedor queda mitigado. Se anota la hora exacta del corte.

6.  **Embalaje y transporte:** torre en embalaje rígido acolchado; sellos sobre puertos, botón de encendido y tapa lateral; lejos de fuentes magnéticas y calor; transporte vertical y sin golpes; custodia continua hasta el laboratorio y registro de cada transferencia (Formato 2).

**Alternativa evaluada:** apagado ordenado. Solo se justificaría si el DES no lograra la imagen lógica de V:\\ y existiera evidencia de que el corte abrupto corrompe el contenedor; en ese caso se documentarían los efectos del apagado (escritura en logs, vaciado de caché).

# 5. Secuencia operativa cronológica

La siguiente bitácora sintetiza la intervención y soporta el principio de auditabilidad (5.3.2). Horas simuladas.

| **Hora** | **Responsable**  | **Acción**                                                                                                     |
|----------|------------------|----------------------------------------------------------------------------------------------------------------|
| 09:15    | DEFR             | Arribo; verificación del mandato y de la identidad del equipo; apertura del acta; aseguramiento del perímetro. |
| 09:17    | Oficial Registro | Fijación fotográfica y en video de escena, pantalla, jiggler, nota y UPS (D05). No se toca teclado ni ratón.   |
| 09:22    | DES + DEFR       | Evaluación de riesgos; decisión de adquisición en vivo (Fig. 1 y 4). Se solicita al SOC SPAN y contención.     |
| 09:24    | SOC / DEFR       | Inicio de captura SPAN (D06); bloqueo de egreso y sinkhole DNS. Enlace físico del host se mantiene.            |
| 09:26    | DES              | Conexión de medio de herramientas (solo lectura) y medio destino estéril; volcado de RAM (D01).                |
| 09:47    | Oficial Registro | Cálculo y registro de hash SHA-256/MD5 de D01.                                                                 |
| 09:49    | DES              | Respuesta en vivo con herramientas estáticas (D02); fijación de consolas PowerShell por captura de pantalla.   |
| 10:05    | DES              | Identificación de cifrado (V:\\ y C:\\; documentación del RAID 0.                                              |
| 10:08    | DES              | Imagen lógica de V:\\ (D03); verificación de hash.                                                             |
| 11:32    | DES              | Adquisición de artefactos de C:\\ (D04): pagefile, historial PowerShell, eventos, \$MFT.                       |
| 11:46    | Auditor          | Verificación cruzada de hashes D01–D06 con segunda herramienta; revisión de la bitácora.                       |
| 11:50    | DES + DEFR       | Retiro y embalaje del jiggler (G1-E03); corte de energía en el chasis de G1-E01; fin de SPAN.                  |
| 11:55    | Oficial Registro | Embalaje y sellado de G1-E01, G1-E04 y medios con D01–D06; diligenciamiento del Formato 2.                     |
| 12:20    | DEFR → Lab.      | Cierre del acta con firmas; transferencia de custodia y traslado al laboratorio pericial.                      |

# 6. Formato 1: Bitácora de Triaje y Justificación Técnica de la Intervención

*Entregable obligatorio del grupo sustentante \| Alineado con 5.3.2 Auditabilidad y 5.3.5 Justificabilidad.*

| **Número de caso**                                | OPE-DEF-2026-088                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|---------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Fecha y hora de arribo**                        | 15/10/2026 – 09:15 h                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| **Equipo pericial responsable**                   | Grupo 2 – Johan Camilo Tamara (DEFR Líder de Escena); Natalia Forero Lozano (Especialista en Evidencia Digital (DES)); Laura Angélica Gutiérrez (Oficial de Registro y Cadena de Custodia); Ayda Castro Suárez (Auditor de Calidad y Cumplimiento Normativo)                                                                                                                                                                                                             |
| **Mandato legal y autoridad emisora**             | Orden de registro y allanamiento con facultad de recolección de elementos materiales probatorios (EMP) y evidencia física (EF) digital y de recuperación de información (Ley 906 de 2004, arts. 219-220 y 236), emitida por Juez de Control de Garantías a solicitud de Fiscalía delegada; con acompañamiento de Policía Judicial y del oficial de contrainteligencia de la unidad (Ley 1621 de 2013). No autoriza interceptación de comunicaciones en curso (art. 235). |
| **Evaluación inicial de riesgos en escena (6.2)** | Físicos: acceso de terceros, energía soportada por UPS, daño electrostático, contaminación de huellas. Lógicos: borrado remoto vía C2/túnel DNS, dead man’s switch, bloqueo de sesión al retirar jiggler, desmontaje del volumen cifrado, scripts antiforenses al apagar, binarios troyanizados. Jurídicos: exceso de mandato frente a la mensajería. Controles: ver Sección 3.1.                                                                                        |

## Matriz de decisiones técnicas

| **ID dispositivo**                            | **Estado inicial (ON/OFF)** | **¿Datos volátiles críticos?** | **Determinación operativa (Colección física vs. Adquisición en vivo/lógica)**                                     | **Fundamento normativo (ISO 27037)**        | **Alteraciones técnicas inevitables introducidas**                                                                                |
|-----------------------------------------------|-----------------------------|--------------------------------|-------------------------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| **G1-E01 Torre Dell Precision 5820**          | ON                          | Sí                             | Adquisición en vivo (RAM, red, V:\\ artefactos C:\\ y luego recolección física; imagen física NVMe en laboratorio | 5.4.4, 6.8, 7.1.2.1, 7.1.3.1; Fig. 1, 2 y 4 | Huella de herramientas en RAM; entradas USB en registro (USBSTOR, setupapi); cambio de fechas de acceso; corte abrupto de energía |
| **G1-E01 / Memoria RAM 64 GB**                | ON                          | Sí                             | Adquisición en vivo (volcado completo)                                                                            | 3.26, 6.8, 7.1.3.1.2                        | Desplazamiento de páginas por la herramienta; memoria no repetible                                                                |
| **G1-E01 / Estado de red (Gigabit Ethernet)** | ON                          | Sí                             | Contención aguas arriba + SPAN; captura lógica de ARP, sockets y DNS                                              | 6.2.3, 7.2.2.2                              | Bloqueo de egreso: intentos fallidos al C2 posteriores a 09:24                                                                    |
| **G1-E01 / Volumen cifrado V:\\**             | ON (montado)                | Sí                             | Adquisición lógica en vivo del contenido descifrado                                                               | 7.1.2.1.2 nota 1, 7.1.3.1; Fig. 4           | Lectura de archivos (marcas de acceso según configuración NTFS)                                                                   |
| **G1-E02 Monitor Dell 27"**                   | ON                          | No                             | Fijación fotográfica; no se recolecta                                                                             | 5.4.2, 7.1.1 (proporcionalidad)             | Ninguna                                                                                                                           |
| **G1-E03 Dongle USB (jiggler)**               | ON (conectado)              | No (pero mantiene sesión)      | Se deja conectado durante la adquisición; recolección física al final                                             | 6.2, 7.1.2.1                                | Al retirarlo, la sesión podría bloquearse (se retira tras adquirir)                                                               |
| **G1-E04 Nota adhesiva**                      | N/A                         | No                             | Recolección física en sobre de papel                                                                              | 5.4.3, 6.1                                  | Ninguna (manipulación con guantes)                                                                                                |
| **G1-E05 Cable AC y UPS**                     | ON                          | No                             | Documentación; corte de energía en el chasis, no en la UPS                                                        | 7.1.2.1; Fig. 2                             | Corte abrupto de alimentación del equipo                                                                                          |

**Firmas**

- DEFR Líder de Escena: Johan Tamara
- DES: Natalia Forero
- Oficial de Registro: Laura Gutiérrez
- Auditor de Calidad: Ayda Castro

# 7. Formato 2: Registro de Cadena de Custodia y Trazabilidad de Evidencia

*Entregable obligatorio del grupo sustentante \| Alineado con numeral 6.1 y Anexo B de ISO/IEC 27037:2016.*

| **Referencia del caso / expediente** | OPE-DEF-2026-088                                                                                                                                  |
|--------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| **Entidad / unidad investigadora**   | Equipo Pericial Grupo 2 – Laboratorio de Informática Forense (simulación académica)                                                               |
| **Ubicación exacta de la escena**    | Oficina del Director de Proyectos Especiales – Sede de enlace del Comando Conjunto de Ciberdefensa (dirección exacta reservada por clasificación) |

## Registro de elementos materiales probatorios

| **Artículo n.°** | **Descripción detallada (marca, modelo, S/N)** | **Tipo de empaque** | **N.° precinto / sello** | **Algoritmo hash** | **Valor hash verificado** | **Nombre, rol y firma del receptor** |
|---|---|---|---|---|---|---|
| 1 | G1-E01 – Estación de trabajo Dell Precision 5820 Tower, S/N 4HG78Y2; Xeon, 64 GB RAM; 2× NVMe 1 TB en RAID 0 (orden de ranura rotulado: M.2-0 / M.2-1) | Rígido acolchado + bolsa antiestática interna; puertos y tapa sellados con cinta de evidencia | PR-088-0001 / PR-088-0002 | SHA-256 + MD5 | Pendiente: imagen física de NVMe en laboratorio (Fig. 5) | Laura Angélica Gutiérrez<br>Oficial de Registro<br>Firma: ________ |
| 2 | G1-E01-D01..D04 – Disco forense destino Seagate 4 TB, S/N [MEDIO-EST-01], esterilizado (verificación de borrado documentada) con D01–D04 | Bolsa antiestática + caja rígida | PR-088-0003 | SHA-256 + MD5 | Ver tabla de hashes por imagen (D01–D04) | Laura Angélica Gutiérrez<br>Oficial de Registro<br>Firma: ________ |
| 3 | G1-E01-D05 / G1-NET-D06 – Copia de trabajo y copia maestra en 2 medios USB cifrados (S/N [MEDIO-EST-02] y [MEDIO-EST-03]) | Bolsa antiestática | PR-088-0004 / PR-088-0005 | SHA-256 | Ver tabla de hashes (D05, D06) | Laura Angélica Gutiérrez<br>Oficial de Registro<br>Firma: ________ |
| 4 | G1-E03 – Dongle USB metálico sin marca; HID (VID/PID registrados en D02); función mouse jiggler | Bolsa antiestática + sobre rígido | PR-088-0006 | N/A (dispositivo HID) | N/A – se fija VID/PID y S/N lógico | Laura Angélica Gutiérrez<br>Oficial de Registro<br>Firma: ________ |
| 5 | G1-E04 – Nota adhesiva amarilla manuscrita: «AES-K: Gr@n4d0_2026! // VPN: C2-Ext» | Sobre de papel (no plástico) para preservar huellas/escritura | PR-088-0007 | N/A (evidencia física) | N/A – fijación fotográfica con testigo métrico | Laura Angélica Gutiérrez<br>Oficial de Registro<br>Firma: ________ |
| 6 | G1-E02 – Monitor Dell UltraSharp 27", S/N DL-99214 (sin capacidad de almacenamiento) | No embalado – documentado in situ | N/A | N/A | N/A – fijación fotográfica | Laura Angélica Gutiérrez<br>Oficial de Registro<br>Firma: ________ |
| 7 | G1-E05 – Cable AC y UPS APC 1500VA (respaldo de batería activo) | No embalado – documentado in situ | N/A | N/A | N/A – se registra estado y autonomía | Laura Angélica Gutiérrez<br>Oficial de Registro<br>Firma: ________ |

## Funciones resumen de la evidencia digital derivada (valores simulados)

| **ID** | **Descripción / archivo** | **Tamaño** | **SHA-256 (línea 1) / MD5 (línea 2)** |
|---|---|---|---|
| G1-E01-D01 | Imagen de memoria RAM (64 GB, formato raw .mem) de G1-E01, adquirida con WinPmem (versión validada) a medio estéril<br>Archivo: G1-E01-D01_RAM.mem (09:26–09:47 h) | 68,7 GB | 0e264a8be73703672b54d84e04027b9e376b585bf1d00c4b0801b8c8ed7e3ae9<br>b7bcad4b0c2d37a1441c00d6a583afca |
| G1-E01-D02 | Paquete de respuesta en vivo (procesos, conexiones TCP/UDP, tabla ARP, caché DNS, rutas, sesiones, tareas programadas, servicios) – salida de herramientas estáticas confiables<br>Archivo: G1-E01-D02_LiveResponse.zip (09:49–10:02 h) | 184 MB | fb6d062a1d3b66bb53361fe8c62c06fac43ae55918505a44d39f6bd0b922074b<br>cb68e12340720a4ef1e994e2222003c7 |
| G1-E01-D03 | Imagen lógica del volumen cifrado montado V:\\ (contenido descifrado) – formato E01 con verificación<br>Archivo: G1-E01-D03_VolV.E01 (10:08–11:31 h) | 212 GB | cef7612a6e8f16c3e514dc0fcd984421f013326cb19b80f9255f14fdc8dd3774<br>90e759045f56e26dac00752740adc02d |
| G1-E01-D04 | Artefactos lógicos de C:\\ en vivo: pagefile.sys, hiberfil.sys (si existe), historial PSReadLine, registros de eventos (.evtx), $MFT<br>Archivo: G1-E01-D04_ArtefactosC.ad1 (11:32–11:44 h) | 71 GB | 3b2d37c0e27a6ace9d59997f8144dabc4d6e7cdaaf2f937f14dbfb651f3c61a8<br>c05c75ee68812c99123316fbea5721d0 |
| G1-E01-D05 | Fijación audiovisual de pantalla (video 4K + 46 fotografías) de consolas PowerShell, explorador con V:\\ y sesión de mensajería visible<br>Archivo: G1-E01-D05_Fijacion.zip (09:17–09:23 h) | 3,9 GB | 9d71c6ec804b1228842af4ff9ccf309f75e8b76bd4f6215956fbe0043f01de9b<br>60203f993a562f066d1bac4b7b857fa7 |
| G1-NET-D06 | Captura de tráfico (PCAP) del puerto espejo (SPAN) del switch de acceso, entregada por el SOC con acta<br>Archivo: G1-NET-D06_SPAN.pcapng (09:24–11:50 h) | 1,2 GB | 54d8850d896e4e51c9c7843b88b43bd293c50d5c94acf913d5cddac5e9488717<br>5bc86e0dc8381c78afdfd07e2bce4200 |

## Control de movimiento y transferencia de custodia

| **Movimiento** | **Nombre**               | **Cargo / rol**                                      | **Fecha / hora**   | **Firma**                |
|----------------|--------------------------|------------------------------------------------------|--------------------|--------------------------|
| Entrega        | Laura Angélica Gutiérrez | Oficial de Registro y Cadena de Custodia             | 15/10/2026 – 12:20 | Laura Angélica Gutiérrez |
| Recibe         | Ayda Castro              | Perito custodio – Laboratorio de Informática Forense | 15/10/2026 – 13:05 | Ayda Castro              |
| Entrega        | Laura Gutiérrez          | Perito custodio – Laboratorio                        | 15/10/2026 – 13:20 | Laura Gutiérrez          |
| Recibe         | Natalia Forero           | Responsable de bodega de evidencias                  | 15/10/2026 – 13:25 | Natalia Forero           |

**Propósito del traslado:**

- Almacenamiento seguro en bodega de evidencias (medios con copia maestra D01–D06, G1-E03, G1-E04)

- Traslado a laboratorio pericial (G1-E01 para imagen física de NVMe y reconstrucción del RAID 0; copias de trabajo para análisis).

**Observaciones:** sellos verificados íntegros en cada transferencia; ninguna apertura de embalaje entre la escena y el laboratorio. Toda apertura posterior se registrará con nuevo sello y nueva entrada en este formato.

# 8. Matriz de defensa técnica frente a acusaciones de alteración o sesgo

| **Posible acusación de la contraparte**                                     | **Contramedida aplicada**                                                                                                              | **Evidencia de soporte**                                                                 | **Fundamento**           |
|-----------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------|--------------------------|
| **«El equipo alteró la memoria al ejecutar sus herramientas» (spoliation)** | Herramienta estática validada, ejecutada una sola vez, huella documentada; adquisición de RAM antes de cualquier otro comando.         | Bitácora con hora, PID y tamaño de la herramienta; hash de la herramienta; D01 con hash. | 5.3.5, 6.8, 7.1.3.1.2    |
| **«Desconectar la red destruyó el estado de las conexiones»**               | No se desconectó el host: contención aguas arriba con enlace activo; SPAN previo.                                                      | D06 (PCAP), acta del SOC, D02 con tabla ARP y sockets.                                   | 6.2.3, 7.2.2.2           |
| **«Se apagó el equipo y se perdieron datos cifrados»**                      | Imagen lógica de V:\\ en claro y RAM con claves antes del corte; corte en chasis para evitar scripts antiforenses.                     | D01, D03 con hash; fotografía de la hora del corte.                                      | 7.1.2.1.2 nota 1; Fig. 2 |
| **«Los peritos usaron la clave del post-it para entrar a sistemas»**        | La clave no se usó en escena; solo se fijó y recolectó. Uso futuro sobre copias y con ampliación de orden.                             | Video continuo D05; acta sin registro de uso.                                            | 6.1; mandato             |
| **«El jiggler o la nota fueron plantados por los investigadores»**          | Fijación fotográfica al arribo antes de cualquier manipulación; testigos; registro USB del primer uso del dongle (anterior al arribo). | D05 con marca de tiempo; setupapi.dev.log en D04; actas firmadas.                        | 5.3.2, 6.6               |
| **«La copia no es igual al original» (integridad)**                         | Doble hash SHA-256/MD5 calculado en escena y verificado con segunda herramienta y en cada transferencia.                               | Formato 2; reportes de verificación.                                                     | 5.3.3, 5.3.4, 6.1        |
| **«La cadena de custodia tiene vacíos»**                                    | Registro de cada entrega/recepción con hora, nombre, cargo y firma; sellos numerados íntegros.                                         | Formato 2 y Anexo B.                                                                     | 6.1, Anexo B             |
| **«El análisis está sesgado contra el Director» (inherent bias)**           | Hipótesis alternativas H1–H4 y búsqueda de evidencia exculpatoria; lenguaje neutral en actas.                                          | Sección 3.2; revisión del Auditor de Calidad.                                            | 6.7.5                    |
| **«El personal no era competente»**                                         | Roles DEFR/DES asignados según competencias del Anexo A; herramientas validadas.                                                       | Hojas de vida/certificaciones; registro de validación.                                   | 6.3, Anexo A             |

# 9. Preparación para el contrainterrogatorio

| **Pregunta probable**                                                            | **Respuesta pericial sugerida**                                                                                                                                                         |
|----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ¿Por qué no desconectaron de inmediato el equipo si había exfiltración en curso? | Porque la exfiltración se detuvo con la contención aguas arriba sin destruir evidencia volátil; desconectar el host habría perdido conexiones, ARP y posiblemente disparado el borrado. |
| ¿Cómo prueban que la imagen de RAM corresponde al equipo y no a otro?            | Por la cadena: video continuo de la adquisición (D05), metadatos del sistema dentro de la imagen (nombre de host, S/N de BIOS), hash calculado en escena y bitácora firmada.            |
| Si la RAM no es repetible, ¿por qué debería admitirse?                           | La norma reconoce que ciertas adquisiciones no son repetibles; se compensa con justificabilidad y con un análisis reproducible por terceros sobre la misma imagen verificada por hash.  |
| ¿Por qué usar MD5 si está «roto»?                                                | Se usa como hash secundario de compatibilidad; el principal es SHA-256. La colisión intencional sobre ambos simultáneamente no es práctica.                                             |
| ¿Leyeron los mensajes de la aplicación cifrada?                                  | No. Solo se fijó lo visible al arribo. Leer o desplazar la conversación habría excedido el mandato (art. 235 Ley 906 de 2004).                                                          |
| ¿Por qué no apagaron de forma ordenada?                                          | El apagado ordenado ejecuta scripts y tareas que pueden ser antiforenses; los datos cifrados ya estaban asegurados en claro, por lo que el corte en el chasis minimiza alteraciones.    |
| ¿Por qué no recolectaron el monitor ni la UPS?                                   | Por proporcionalidad y justificabilidad: no almacenan datos relevantes; se documentaron in situ.                                                                                        |

# 10. Kit de herramientas y validación (referencial)

| **Herramienta / medio**                                                         | **Uso**                                                         | **Control de validez**                                 |
|---------------------------------------------------------------------------------|-----------------------------------------------------------------|--------------------------------------------------------|
| WinPmem / Magnet RAM Capture                                                    | Volcado de RAM                                                  | Hash de binario; prueba previa en equipo de referencia |
| Kit estático de respuesta en vivo (Sysinternals, utilidades nativas compiladas) | Procesos, conexiones, ARP, DNS, tareas, sesiones                | Ejecución desde medio de solo lectura; hash del kit    |
| FTK Imager (portable)                                                           | Imagen lógica de V:\\ y artefactos de C:\\ verificación de hash | Versión registrada; verificación automática E01        |
| sha256sum / CertUtil                                                            | Verificación cruzada de hashes                                  | Segunda herramienta independiente                      |
| Bloqueador de escritura (laboratorio)                                           | Imagen física de NVMe                                           | Prueba funcional previa documentada                    |
| Medios destino estériles                                                        | Almacenar imágenes                                              | Borrado y verificación previa con acta                 |
| Bolsas antiestáticas, sobres de papel, cajas rígidas, cinta y sellos numerados  | Embalaje técnico                                                | Numeración controlada en Formato 2                     |

# Referencias

Brezinski, D., & Killalea, T. (2002). Guidelines for evidence collection and archiving (RFC 3227). Internet Engineering Task Force. https://doi.org/10.17487/RFC3227

Congreso de la República de Colombia. (2004). Ley 906 de 2004, por la cual se expide el Código de Procedimiento Penal. Diario Oficial No. 45.658.

Congreso de la República de Colombia. (2009). Ley 1273 de 2009, por medio de la cual se modifica el Código Penal, se crea un nuevo bien jurídico tutelado denominado «de la protección de la información y de los datos». Diario Oficial No. 47.223.

Congreso de la República de Colombia. (2013). Ley Estatutaria 1621 de 2013, por medio de la cual se expiden normas para fortalecer el marco jurídico que permite a los organismos que llevan a cabo actividades de inteligencia y contrainteligencia cumplir con su misión. Diario Oficial No. 48.764.

Fiscalía General de la Nación. (2018). Manual del sistema de cadena de custodia. FGN.

Instituto Colombiano de Normas Técnicas y Certificación. (2016). NTC-ISO/IEC 27037: Tecnología de la información. Técnicas de seguridad. Directrices para la identificación, recolección, adquisición y preservación de evidencia digital. ICONTEC.

International Organization for Standardization & International Electrotechnical Commission. (2012). ISO/IEC 27037:2012 Information technology — Security techniques — Guidelines for identification, collection, acquisition and preservation of digital evidence. ISO.

Kent, K., Chevalier, S., Grance, T., & Dang, H. (2006). Guide to integrating forensic techniques into incident response (NIST SP 800-86). National Institute of Standards and Technology. https://doi.org/10.6028/NIST.SP.800-86
