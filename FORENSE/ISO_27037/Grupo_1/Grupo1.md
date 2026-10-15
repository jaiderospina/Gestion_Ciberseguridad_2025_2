# Vectores Móviles, Medios Extraíbles y Manejo del Sesgo
**Análisis Pericial Forense Digital bajo Norma ISO/IEC 27037:2012**[cite: 3, 10]

---

### Integrantes del Equipo
* **Carolina Salinas** — *Auditor de Calidad y Cumplimiento Normativo*[cite: 51]
* **David Mora Fierro** — *Especialista en Evidencia Digital (DES)*[cite: 51]
* **Juan Nikolas Hernández** — *Primer Interviniente en Evidencia Digital (DEFR Líder de Escena)*[cite: 51]
* **Johana Iden Lambuley Contreras** — *Oficial de Registro y Cadena de Custodia*[cite: 51]

**Docente / Asesor:**  
Jaider Ospina  

**Programa Académico:**  
Maestría en Ciberseguridad y Ciberdefensa  
Escuela Superior de Guerra “General Rafael Reyes Prieto”  
Bogotá D.C., Colombia  
**2026**[cite: 51]

---

## Tabla de Contenido
1. [Contexto Operacional y Roles Asignados](#1-contexto-operacional-y-roles-asignados)
2. [Respuestas Analíticas y Metodológicas](#2-respuestas-analíticas-y-metodológicas)
3. [Bitácora de Triaje y Justificación Técnica de la Intervención](#3-bitácora-de-triaje-y-justificación-técnica-de-la-intervención)
4. [Registro de Cadena de Custodia y Trazabilidad (Anexo B, ISO 27037)](#4-registro-de-cadena-de-custodia-y-trazabilidad-anexo-b-iso-27037)

---

## 1. Contexto Operacional y Roles Asignados

### 1.1 Resumen del Incidente
Se ha detectado una fuga masiva de información clasificada y señales de persistencia avanzada (APT) en la sede de enlace de una agencia de mando y control del sector defensa. La alerta temprana sugiere el uso de credenciales comprometidas y dispositivos no autorizados para exfiltrar fragmentos de planes operacionales hacia redes externas. El equipo pericial interviene bajo mandato legal y operativo con ventana de tiempo crítica.

* **Referencia Operacional:** Caso `OPE-DEF-2026-089`
* **Escenario:** Puesto de Mando Unificado (PMU). Se interviene a un oficial de comunicaciones sospechoso de filtrar coordenadas tácticas mediante aplicaciones celulares y periféricos no autorizados[cite: 50].

### 1.2 Hallazgos Iniciales en Escena
* **Dispositivo Móvil:** Teléfono inteligente Samsung Galaxy S23 encendido sobre el escritorio, bloqueado mediante patrón biométrico/PIN, con 38% de batería y conectividad activa a red Wi-Fi táctica y datos celulares 4G/5G[cite: 50].
* **Medio Extraíble en Persona:** Memoria USB Kingston DataTraveler 64 GB rotulada *"Música Personal – MP3"* en el chaleco del sospechoso[cite: 50]. El investigado manifiesta verbalmente: *"No pierdan el tiempo con esa memoria, solo tiene música de mi uso personal, revisen el computador del compañero que él sí maneja las órdenes de marcha"* (tentativa explícita de inducir sesgo investigativo)[cite: 27].
* **Evidencias en Gaveta Abierta:** Tarjeta MicroSD SanDisk suelta de 128 GB (S/N `SD-88301-C10`), adaptadores SIM y un adaptador USB Wi-Fi de alta potencia Alfa Network (AWUS036ACM) en modo monitor[cite: 50].
* **Entorno Electromagnético:** Cobertura total y alta potencia de señales RF en el recinto[cite: 43].

---

## 2. Respuestas Analíticas y Metodológicas

### Pregunta 1: Actuación del DEFR frente al sesgo inherente (*Inherent Bias*)
> **Fundamentación:** ISO/IEC 27037:2012, Numeral 6.7.5 (*Otra información informativa*)[cite: 6, 26, 27].

* **Principio Normativo:** El numeral 6.7.5 exige que el DEFR evite de manera rigurosa cualquier circunstancia que dé lugar a acusaciones de sesgo inherente (*inherent bias*)[cite: 27]. La norma explicita el caso clásico de un perito que procesa un equipo y descarta otro debido a valoraciones subjetivas o influencias externas generadas en el sitio del suceso[cite: 27].
* **Evaluación del Caso:** La aseveración del oficial de comunicaciones constituye una maniobra de distracción para desviar la atención pericial hacia el equipo de un tercero inocente y propiciar la desestimación o destrucción probatoria de la memoria USB[cite: 20, 24, 27].
* **Protocolo de Actuación:** El DEFR rechaza la sugerencia del investigado, mantiene neutralidad analítica, documenta en la bitácora la manifestación verbal del oficial como un factor de interés dentro de la diligencia, y asegura prioritariamente la memoria USB aplicando protocolos forenses estandarizados[cite: 17, 21, 27].

---

### Pregunta 2: Riesgos inmediatos en smartphone encendido y medidas exigidas
> **Fundamentación:** ISO/IEC 27037:2012, Numerales 6.2.3, 6.9.2 y 7.2.2.3[cite: 6, 23, 28, 43].

#### Riesgos Inmediatos Identificados
1. **Bloqueo por Temporizador:** Transcurrido el límite de inactividad, la pantalla se bloquea y el dispositivo puede pasar a un estado de cifrado fuerte en reposo (*Before First Unlock* o *After First Unlock*), dificultando la extracción lógica avanzada o adquisición de RAM[cite: 20, 36, 43].
2. **Borrado Remoto / Manipulación Cloud:** Ante la disponibilidad de redes 4G/5G y Wi-Fi, un actor remoto puede ejecutar comandos MDM, *Find My Mobile* o enviar un wipeout total de particiones de datos[cite: 23, 43].
3. **Sobrescritura por Tráfico Push:** Notificaciones entrantes, mensajes en tránsito y sincronizaciones automáticas alteran la memoria volátil y sobrescriben archivos temporales y registros del sistema[cite: 15, 42].

#### Medidas Obligatorias de Mitigación
* **Aislamiento de Señales RF (Cláusula 7.2.2.3):** Ubicación inmediata del dispositivo en una bolsa o jaula de Faraday validada, o habilitación física de modo avión sin desconectar la energía[cite: 28, 43].
* **Preservación Energética (Cláusula 6.9.2):** Suministro de energía ininterrumpida mediante un banco de batería externo conectado por cable con filtrado de datos dentro del contenedor apantallado[cite: 28].

---

### Pregunta 3: Comportamiento de batería en jaula de Faraday y procedimiento DEFR
> **Fundamentación:** ISO/IEC 27037:2012, Numeral 6.9.2 (Nota técnica)[cite: 6, 28].

* **Impacto Electromagnético:** Al perder contacto con las estaciones base celular (BTS) y puntos de acceso Wi-Fi, el transmisor de potencia del teléfono conmuta al límite superior de ganancia buscando balizas de red (*beaconing* constante)[cite: 28]. Este comportamiento agota la carga remanente (38%) en una fracción del tiempo ordinario[cite: 28, 50].
* **Procedimiento Operativo:** El DEFR debe conectar una fuente de poder auxiliar (Power Bank de respaldo continuo) antes de completar el sellado del blindaje de Faraday, verificando que no existan fugas de radiofrecuencia a través de los cables de carga ni calentamiento excesivo que comprometa el hardware del teléfono móvil[cite: 28].

---

### Pregunta 4: Secuencia de preservación y adquisición para MicroSD y USB
> **Fundamentación:** ISO/IEC 27037:2012, Numerales 5.4.4, 6.9.3 y 7.1.3.5[cite: 6, 20, 28, 39].

#### Secuencia de Preservación Física
1. **Neutralización ESD:** Manipulación con guantes antiestáticos libres de pelusa para prevenir daños por descargas electrostáticas sobre los contactos y la controladora NAND[cite: 28, 29].
2. **Empaque Seguro:** Disposición en bolsas antiestáticas independientes y contenedores rígidos que mitiguen vibraciones y torsión física[cite: 28, 50].
3. **Etiquetado y Precintado:** Sellado con cinta de seguridad *tamper-evident* firmada, sin tapar números de serie ni marcas del fabricante (Cláusula 6.9.3.1)[cite: 28, 40].

#### Secuencia de Adquisición Forense
1. **Interconexión con Bloqueador de Escritura:** Conexión del medio a la estación forense a través de un bloqueador de escritura por hardware debidamente validado (*Write-Blocker*)[cite: 20].
2. **Duplicación Bit a Bit:** Generación de la imagen en formato RAW/DD o E01 sin interactuar con el sistema de archivos del origen[cite: 14, 20].
3. **Verificación Criptográfica:** Cálculo cruzado de función resumen (SHA-256) antes y después de la clonación[cite: 15, 20]. Los hashes del medio físico y de la imagen deben ser idénticos[cite: 20].

---

## 3. Bitácora de Triaje y Justificación Técnica de la Intervención

| ID Dispositivo[cite: 1] | Descripción del Elemento[cite: 1] | Estado Inicial[cite: 1] | ¿Datos Volátiles?[cite: 1] | Determinación Operativa[cite: 1] | Fundamentación Normativa (ISO 27037)[cite: 1] | Alteraciones Técnicas Inevitables[cite: 1] |
| :---: | :--- | :---: | :---: | :---: | :--- | :---: |
| **G2-E01**[cite: 1] | Smartphone Samsung Galaxy S23[cite: 1] | ON / Bloqueado[cite: 1] | **SÍ**[cite: 1] | Recolección Física con aislamiento RF[cite: 1, 28] | **Cláusula 5.4.3 y Cláusula 7.2.2.2** (Dispositivos móviles en red)[cite: 6, 7] | Ninguna[cite: 1] |
| **G2-E02**[cite: 1] | Unidad Flash USB Kingston 64 GB[cite: 1] | Desconectada[cite: 1] | **NO**[cite: 1] | Recolección Física[cite: 1] | **Cláusula 5.4.3 y Cláusula 7.1.3.5** (Medios de almacenamiento)[cite: 6, 7] | Ninguna[cite: 1] |
| **G2-E03**[cite: 1] | Tarjeta MicroSD SanDisk 128 GB[cite: 1] | Suelta[cite: 1] | **NO**[cite: 1] | Recolección Física[cite: 1] | **Cláusula 5.4.3 y Cláusula 7.1.3.5** (Memorias flash externas)[cite: 6, 7] | Ninguna[cite: 1] |
| **G2-E04**[cite: 1] | Tarjeta nano-SIM (en el teléfono G2-E01)[cite: 1] | Insertada[cite: 1] | **SÍ**[cite: 1] | Recolección Física conjunta[cite: 1] | **Cláusula 5.4.3, 7.2.1.2 y 7.2.2.3** (Accesorios y SIM)[cite: 6, 7, 41] | Ninguna[cite: 1] |
| **G2-E05**[cite: 1] | Adaptador USB Wi-Fi Alfa Network[cite: 1] | Desconectado[cite: 1] | **NO**[cite: 1] | Recolección Física[cite: 1] | **Cláusula 5.4.3, 7.1.1.1 y 6.9.3** (Hardware periférico)[cite: 6, 7, 28, 30] | Ninguna[cite: 1] |

---

## 4. Registro de Cadena de Custodia y Trazabilidad (Anexo B, ISO 27037)

### 4.1 Inventario de Elementos Materiales Probatorios

| Ítem[cite: 51] | Descripción Detallada (Marca, Modelo, S/N)[cite: 51] | Empaque Primario[cite: 51] | Precinto / Sello[cite: 51] | Algoritmo Hash[cite: 51] | Valor Hash Verificado[cite: 51] | Receptor[cite: 51] |
| :---: | :--- | :---: | :---: | :---: | :--- | :--- |
| **1**[cite: 51] | Samsung Galaxy S23, pantalla bloqueada, PIN/Biometría facial, batería al 38%, Wi-Fi y datos activos[cite: 50, 51]. | Bolsa Faraday[cite: 51] | Sello de Seguridad[cite: 51] | N/A[cite: 51] | *N/A (Aislado para adquisición en laboratorio)*[cite: 51] | DEFR Líder de Escena[cite: 51] |
| **2**[cite: 51] | Memoria USB Kingston DataTraveler 64 GB, USB 3.2, rotulada *"Música Personal – MP3"*[cite: 50, 51]. | Rígido / Antiestático[cite: 51] | Sello de Seguridad[cite: 51] | SHA-256 (vía Bloqueador)[cite: 51] | `e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855`[cite: 51] | DEFR Líder de Escena[cite: 51] |
| **3**[cite: 51] | Tarjeta MicroSD SanDisk 128 GB, S/N: `SD-88301-C10`, hallada suelta en gaveta[cite: 50, 51]. | Rígido / Antiestático[cite: 51] | Sello de Seguridad[cite: 51] | SHA-256 (vía Bloqueador)[cite: 51] | `7f83b1657ff1fc53b92dc18148a1d65dfc2d4b1fa3d677284addd200126d9069`[cite: 51] | DEFR Líder de Escena[cite: 51] |
| **4**[cite: 51] | Adaptador USB Wi-Fi Alfa Network AWUS036ACM, hallado en gaveta[cite: 50, 51]. | Rígido / Antiestático[cite: 51] | Sello de Seguridad[cite: 51] | N/A[cite: 51] | *N/A (Dispositivo periférico sin almacenamiento)*[cite: 51] | DEFR Líder de Escena[cite: 51] |

---

### 4.2 Registro Cronológico de Transferencias de Custodia

#### Transferencia N° 1
* **Entrega:** Juan Nikolas Hernandez | **Cargo:** DEFR Líder de Escena | **Firma:** `NikoH_1`[cite: 51]
* **Fecha y Hora de Entrega:** 03/10/2026 – 15:05[cite: 51]
* **Recibe:** David Mora | **Cargo:** Especialista en Evidencia Digital (DES) | **Firma:** `DavidM_0`[cite: 51]
* **Fecha y Hora de Recepción:** 03/10/2026 – 15:10[cite: 51]
* **Propósito del Traslado:** Garantizar que el entorno esté seguro, controlado y preservado para que el especialista proceda a la identificación, recolección o adquisición técnica sin riesgo de alteración o contaminación[cite: 51].

---

#### Transferencia N° 2
* **Entrega:** David Mora | **Cargo:** Especialista en Evidencia Digital (DES) | **Firma:** `DavidM_0`[cite: 51]
* **Fecha y Hora de Entrega:** 10/10/2026 – 08:00[cite: 51]
* **Recibe:** Johana Iden Lambuley | **Cargo:** Oficial de Registro y Cadena de Custodia | **Firma:** `Johanall_1`[cite: 51]
* **Fecha y Hora de Recepción:** 10/10/2026 – 08:15[cite: 51]
* **Propósito del Traslado:** Garantizar que los elementos digitales recolectados y adquiridos queden debidamente asentados en el libro oficial de evidencias, respaldando la trazabilidad, indemnidad e integridad formal de las muestras[cite: 51].

---

### 4.3 Control de Calidad y Supervisión Normativa
* **Auditor Responsable:** Carolina Salinas[cite: 51]
* **Cargo:** Auditor de Calidad y Cumplimiento Normativo[cite: 51]
* **Periodo de Seguimiento:** Del 03/10/2026 al 12/10/2026[cite: 51]
* **Firma de Conformidad:** `CarolSS_4`[cite: 51]
* **Dictamen:** Se certifica que las actuaciones de recolección física, embalaje en escena, adquisición forense bajo bloqueador de escritura y transferencias de custodia se ejecutaron bajo estricto cumplimiento de los principios de repetibilidad, auditabilidad y reproducibilidad de la norma ISO/IEC 27037:2012[cite: 18, 51].
