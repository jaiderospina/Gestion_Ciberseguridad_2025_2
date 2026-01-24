# FASE 1 - MATRIZ COMPARATIVA DE TÉCNICAS SEMICUANTITATIVAS #
## GRUPO # 2 ##
### Integrantes: Carolina Salinas; Natalia Forero; Johan Tamara; Laura Gutierrez; Ayda Castro ###
### ###
| Técnica | Objetivo | Tipo de incertidumbre que aborda | Nivel de complejidad | Ventajas | Limitaciones | Requisitos de información | Nivel de madurez organizacional | Aplicabilidad en ciberseguridad / ciberdefensa |
|-------|---------|----------------------------------|---------------------|----------|--------------|---------------------------|--------------------------------|-----------------------------------------------|
| Puntuación de Riesgo | Jerarquizar riesgos mediante un puntaje que integra múltiples factores. | Incertidumbre por múltiples factores que influyen en el riesgo (exposición, controles, criticidad). | Media | Puntaje sencillo para priorizar riesgos; integra múltiples factores en un solo número. | Puede generar falsa sensación de precisión si el modelo no está bien validado. | Análisis del sistema, comprensión de fuentes de riesgo y datos históricos para validación. | Media–Alta | Excelente para priorizar criticidad de activos, debilidades, exposición e impacto operacional. |
| Matriz de Consecuencias / Posibilidades | Visualizar riesgos según consecuencia y posibilidad para asignar importancia. | Incertidumbre cualitativa basada en juicio experto y datos disponibles. | Baja–Media | Fácil, rápida y visual; ideal para comunicación ejecutiva. | Alta subjetividad; dificultad para definir escalas consistentes. | Matriz adaptada al contexto y datos de apoyo para escalas realistas. | Media | Muy útil para SOC y CISO: priorización de incidentes, vulnerabilidades y amenazas. |
| Análisis de Corbatín (Bow-Tie) | Analizar causas, consecuencias y barreras preventivas y mitigadoras de un evento peligroso. | Incertidumbre epistémica y aleatoria moderada. | Media | Visual, integrador, facilita comunicación y priorización de controles. | Simplifica relaciones complejas; depende del juicio experto. | Descripción del proceso, identificación de eventos, causas, consecuencias y controles. | Intermedia | Muy alta: ideal para análisis de ataques APT, ransomware y evaluación de controles en ciberdefensa. |
| Curvas en S | Representar la relación entre consecuencias y probabilidad mediante distribución acumulada. | Incertidumbre variable y epistemológica. | Media | Representa impactos en rangos; mejora con datos confiables. | Puede aparentar mayor precisión de la real; depende de supuestos. | Datos históricos o juicios expertos para valores mínimo, probable y máximo. | Moderada–Alta | Útil para modelar impactos variables de ransomware e indisponibilidad de servicios críticos. |


---

# FASE 2 Y 3 - APLICACIÓN PRÁCTICA EN ESCENARIOS DE CIBERSEGURIDAD/CIBERDEFENSA Y LECCIONES APRENDIDAS
# EJERCICIO # 1
# Ataque a Infraestructura TI Crítica  
## Análisis de Corbatín (Bow-Tie) – ISO 31010

---

## Evento de Riesgo Central (Nudo del Corbatín)

**Compromiso de sistemas críticos que soportan la operación esencial de la infraestructura**, generando indisponibilidad del servicio y pérdida de control operacional.

---

## Análisis Bow-Tie Aplicado (ISO 31010)

### Tabla de Análisis – Técnica de Corbatín (Escenario Realista)

### Amenazas / Causas (Lado Izquierdo)
- Phishing dirigido a personal con acceso privilegiado  
- Explotación de vulnerabilidades en accesos remotos (VPN / Jump Server)  
- Credenciales comprometidas sin autenticación multifactor (MFA)  
- Segmentación inadecuada entre redes IT/OT  
- Monitoreo insuficiente de actividad anómala  

---

### Riesgos que Pueden Materializarse
- Acceso no autorizado a sistemas críticos  
- Movimiento lateral dentro de la red  
- Ejecución de malware o ransomware  
- Alteración de configuraciones críticas  
- Pérdida de visibilidad operacional  

---

### Evento de Riesgo Central
**Compromiso de infraestructura crítica que soporta servicios esenciales**

---

### Consecuencias (Lado Derecho)
- Interrupción prolongada del servicio  
- Corrupción o pérdida de datos críticos  
- Paralización de procesos de negocio  
- Activación de planes de contingencia manuales  

---

## Impactos Asociados

### Impacto Económico
- Pérdidas financieras por indisponibilidad del servicio  
- Costos de recuperación tecnológica y análisis forense  
- Penalidades contractuales y afectación de SLA  
- Incremento en primas de seguros o pérdida de cobertura  

### Impacto Legal / Regulatorio
- Incumplimiento de normativas sectoriales (continuidad y seguridad de la información)  
- Investigaciones por entes reguladores  
- Sanciones administrativas  
- Demandas de clientes o terceros  

### Impacto Reputacional
- Pérdida de confianza de clientes y aliados estratégicos  
- Cobertura negativa en medios de comunicación  
- Deterioro de la imagen corporativa  
- Afectación al valor de marca y percepción de resiliencia  

---

## Controles

### Controles Preventivos (Antes del Evento)
- Autenticación multifactor (MFA) obligatoria  
- Segmentación estricta de redes IT/OT  
- Gestión continua de vulnerabilidades  
- Programas de concienciación avanzada contra phishing  
- Hardening y control de accesos privilegiados  

### Controles Mitigantes (Después del Evento)
- Plan de respuesta a incidentes (CSIRT / SOC)  
- Backups inmutables y pruebas periódicas de restauración  
- Aislamiento rápido de sistemas comprometidos  
- Plan de Continuidad del Negocio (PCN)  
- Gestión de crisis y comunicación externa  

---

## Lectura Experta del Análisis

Desde el enfoque de **ISO 31010**, el Análisis de Corbatín permite:

- Visualizar cómo un ciberataque escala desde amenazas técnicas hasta impactos de negocio.  
- Evidenciar que los mayores daños no siempre provienen del ataque inicial, sino de fallas en controles preventivos y tiempos de reacción.  
- Demostrar que la resiliencia organizacional depende del equilibrio entre:
  - **Controles preventivos** (evitar que ocurra)  
  - **Controles mitigantes** (reducir el daño cuando ocurre)  

En infraestructura crítica, este enfoque resulta clave para justificar inversiones en ciberseguridad, fortalecer la defensa en profundidad y mejorar la capacidad de respuesta estratégica.

---

## Conclusión Ejecutiva

La aplicación de la técnica de **Análisis de Corbatín** a un escenario realista de ciberataque evidencia que los riesgos tecnológicos se transforman rápidamente en riesgos **económicos, legales y reputacionales**.

Su principal valor reside en **conectar la ciberseguridad con el impacto real en el negocio**, facilitando decisiones informadas a nivel de alta dirección, comités de riesgo y autoridades regulatorias.

---

## Lecciones Aprendidas

### ¿Qué funcionó?
Permitió visualizar claramente la relación causa–evento–consecuencia, evidenciar el rol de los controles preventivos y mitigantes, y traducir riesgos técnicos a impactos de negocio comprensibles para tomadores de decisión.

### ¿Qué no funcionó?
No cuantifica el riesgo por sí sola, depende del conocimiento del equipo y puede simplificar en exceso escenarios complejos si no se complementa con otras técnicas.

### ¿Cuándo no usar la técnica?
No es adecuada como técnica principal cuando se requiere análisis cuantitativo, escenarios altamente dinámicos o análisis técnico profundo de fallas.

### Recomendaciones Prácticas
- Usarla como herramienta de comunicación estratégica.  
- Construirla desde eventos de negocio.  
- Validar controles con evidencia real.  
- Complementarla con otras técnicas ISO 31010.  
- Actualizarla tras incidentes reales.

### Valor Académico y Profesional
Facilita el entendimiento integral del riesgo, fortalece la resiliencia organizacional y conecta la ciberseguridad con impactos económicos, legales y reputacionales.

# EJERCICIO # 2
# Ataque DDoS a la Red Transaccional  
## Análisis de Curvas en S – ISO 31010

---

## Evento: Ataque DDoS a la Red Transaccional

En este escenario se analiza un **ataque de Denegación de Servicio Distribuido (DDoS)** dirigido contra la **red transaccional de una entidad bancaria**, cuyo objetivo principal es **interrumpir la disponibilidad de los servicios financieros** ofrecidos a los clientes.

---

## Supuesto Base del Ataque

Se asume un ataque **DDoS mixto**, combinando:

- **Ataques volumétricos**, orientados a saturar el ancho de banda.
- **Ataques a nivel de aplicación**, dirigidos a los servicios críticos del banco.

Como consecuencia, se produce una **indisponibilidad total de los canales de atención y operación**.

> No existe exfiltración de información; el impacto del evento es **estrictamente operativo**, sin afectación a la confidencialidad de los datos.

---

## Base del Ataque

- **Tipo de ataque:** DDoS volumétrico + DDoS a nivel de aplicación  
- **Impacto principal:** Indisponibilidad total de canales  
- **Servicios afectados:**
  - Core bancario  
  - Canales digitales (aplicación móvil y web)  
  - Cajeros automáticos  
  - Pagos y transferencias  

---

## Escenarios de Crisis Financiera

### Escenario 1 – Crisis Baja

**Duración del ataque:** 2 a 7 horas  

#### Impacto Operativo
- Ventana corta de indisponibilidad  
- Pico de congestión en horario laboral  
- Recuperación el mismo día  

#### Pérdidas Financieras Estimadas

| Concepto | Estimación |
|--------|-----------|
| Transacciones no realizadas | USD 20 – 35 millones |
| Ingresos por comisiones perdidos | USD 120.000 – 1.4 millones |
| Costos de mitigación (CDN, scrubbing, SOC) | USD 50.000 – 300.000 |
| Pérdida financiera directa | USD 250.000 – 1.8 millones |

#### Impacto Reputacional
- Bajo  
- Reclamos en redes sociales  
- Comunicaciones de contingencia suficientes  

#### Pérdida de Clientes
- < 0,1 %  
- Principalmente clientes digitales jóvenes  

#### Riesgo Legal / Regulatorio
- No hay sanción  
- Reporte informativo al regulador  
- Sin demandas colectivas  

**Conclusión financiera:** Evento absorbible por provisiones operativas.

---

### Escenario 2 – Crisis Media

**Duración del ataque:** 7 a 24 horas  

#### Impacto Operativo
- Día completo sin operación  
- Caída en comercios y pagos  
- Clientes corporativos afectados  
- Interrupción de pagos críticos (nómina y proveedores)  

#### Pérdidas Financieras Estimadas

| Concepto | Estimación |
|--------|-----------|
| Transacciones no realizadas | USD 150 – 250 millones |
| Ingresos por comisiones perdidos | USD 600.000 – 1.4 millones |
| Penalizaciones contractuales | USD 900.000 – 1.1 millones |
| Costos técnicos y refuerzo de infraestructura | USD 250.000 – 400.000 |
| Pérdida financiera directa | USD 1.8 – 2.8 millones |

#### Impacto Reputacional
- Medio  
- Cobertura en medios nacionales  
- Caída temporal de la confianza  
- Downtime reportado públicamente  

#### Pérdida de Clientes
- 0,5 % – 1 %  
- Migración a fintechs y bancos digitales  
- Riesgo elevado en clientes empresariales  

#### Riesgo Legal / Regulatorio
- Investigación del regulador  
- Posibles multas leves  
- Exigencia de plan de mejora  
- Demandas individuales de baja cuantía  

**Conclusión financiera:** Impacto material en los resultados trimestrales.

---

### Escenario 3 – Crisis Alta / Crítica

**Duración del ataque:** 24 a 72 horas o más  

#### Impacto Operativo
- Paralización total del banco  
- Incumplimiento de SLA críticos  
- Riesgo sistémico interbancario  
- Activación de planes de continuidad externos  

#### Pérdidas Financieras Estimadas

| Concepto | Estimación |
|--------|-----------|
| Transacciones no realizadas | USD 400 – 700 millones |
| Ingresos por comisiones perdidos | USD 1.5 – 2.5 millones |
| Demandas colectivas y conciliaciones | USD 2.5 – 6 millones |
| Multas regulatorias | USD 1 – 2 millones |
| Costos reputacionales | USD 1.5 – 2.8 millones |
| Pérdida financiera total estimada | USD 2.9 – 3.5+ millones |

#### Impacto Reputacional
- Severo  
- Riesgo de “bank run” digital  
- Pérdida de calificación de confianza  
- Afectación al valor de marca y acciones  

#### Pérdida de Clientes
- 3 % – 7 %  
- Alta fuga de clientes premium y corporativos  
- Reducción sostenida de ingresos futuros  

#### Riesgo Legal / Regulatorio
- Sanción grave del regulador  
- Auditoría forense obligatoria  
- Riesgo de intervención o vigilancia especial  
- Demandas colectivas de alto valor  

**Conclusión financiera:** Evento potencialmente existencial que afecta solvencia y proyección del negocio.

---

## Resumen Ejecutivo

### Impacto por Nivel de Crisis

| Nivel de crisis | Tiempo | Pérdida estimada |
|---------------|--------|------------------|
| Baja | 2 – 7 h | USD 0.25 – 1.8 M |
| Media | 7 – 24 h | USD 1.8 – 2.8 M |
| Crítica | 25 – 72 h | USD 2.9 – 3.5+ M |

### Probabilidad Consensuada

| Nivel de crisis | Probabilidad |
|---------------|-------------|
| Baja (2 – 7 h) | 99 % – 45 % |
| Media (7 – 24 h) | 44 % – 8 % |
| Alta / Crítica (24 – 72 h) | 7 % – 1 % |

