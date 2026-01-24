# Grupo 3 – Laboratorio Colaborativo de Evaluación del Riesgo  
## Técnicas Cuantitativas aplicadas a Ciberseguridad y Ciberdefensa
## Por: 
## Juan Sebastían Ibarra Quintero
## Arturo José Navarro Do Santos
## Jhon Esteban Vargas Carranza
**NTC-IEC/ISO 31010:2020**

> **Advertencia académica**  
> El presente documento corresponde a un ejercicio académico aplicado sobre un escenario hipotético.  
> No representa incidentes reales, información clasificada ni capacidades operacionales.

---

## FASE 1 – Estudio dirigido y comprensión profunda

**Producto:**  
Matriz de comprensión de técnicas (Documento técnico para GitHub)

### Técnicas analizadas (enfoque cuantitativo)

- Árboles de fallas (Fault Tree Analysis – FTA)
- Árboles de eventos (Event Tree Analysis – ETA)
- Simulación Monte Carlo
- Análisis Bayesiano

### Matriz comparativa de comprensión

| Técnica | Objetivo | Tipo de incertidumbre | Nivel de complejidad | Ventajas | Limitaciones | Requisitos de información | Madurez organizacional requerida | Aplicabilidad en ciberseguridad/ciberdefensa |
|--------|----------|----------------------|---------------------|----------|--------------|---------------------------|----------------------------------|----------------------------------------------|
| Árbol de Fallas (FTA) | Identificar combinaciones lógicas de fallas que conducen a un evento crítico | Epistémica | Media–Alta | Permite análisis causal profundo; identifica fallas críticas | Requiere modelado experto; dependencia de supuestos | Arquitectura del sistema, fallas históricas, controles | Media–Alta | Análisis de colapso de C2, fallas de controles defensivos |
| Árbol de Eventos (ETA) | Analizar consecuencias tras un evento iniciador | Aleatoria y epistémica | Media | Visualiza escenarios y efectos en cascada | Sensible a probabilidades asignadas | Tasas de éxito/fracaso de controles | Media | Impacto de incidentes APT, propagación de ataques |
| Simulación Monte Carlo | Estimar distribuciones de resultados bajo incertidumbre | Aleatoria | Alta | Modela miles de escenarios; cuantificación robusta | Alta dependencia de datos y supuestos | Datos estadísticos, rangos probabilísticos | Alta | Riesgo agregado, impacto económico-operacional |
| Análisis Bayesiano | Actualizar probabilidades con nueva evidencia | Epistémica | Alta | Integra inteligencia dinámica; aprendizaje continuo | Complejidad matemática; dependencia de priors | Priors, evidencia observada, modelos causales | Alta | Inteligencia de amenazas, evaluación adaptativa |

---

## FASE 2 – Aplicación práctica en escenario de Ciberseguridad/Ciberdefensa

**Producto:**  
Ejercicio aplicado de evaluación del riesgo

### Escenario seleccionado

Interrupción de sistemas C2 (Command & Control) en una operación militar conjunta por ataque APT persistente.

### Contexto

- Infraestructura crítica militar  
- Dependencia de comunicaciones seguras y disponibilidad continua  
- Amenaza avanzada con capacidades de persistencia, sigilo y explotación de vulnerabilidades *zero-day*

---

### Técnicas aplicadas

### 1. Árbol de Fallas (FTA)

**Justificación (ISO 31010):**  
Técnica adecuada para identificar causas múltiples y dependencias lógicas que conducen a un evento no deseado crítico  

**Norma-ISO-31010-2020**

- **Evento superior:** Pérdida total de capacidad C2  
- **Fallas básicas:**
  - Compromiso de credenciales privilegiadas  
  - Fallo de redundancia de comunicaciones  
  - Error humano en respuesta a incidentes  

**Resultados:**  
Identificación de puntos únicos de falla y controles críticos con alta contribución al riesgo.

**Limitaciones:**  
No modela la evolución temporal del ataque ni la probabilidad dinámica.

#### Diagrama – Árbol de Fallas (FTA)

[![Analisis-de-Arbol-de-Fallos.png](https://i.postimg.cc/3xrrZ2x4/Analisis-de-Arbol-de-Fallos.png)](https://postimg.cc/crjNxgY0)

---

### 2. Simulación Monte Carlo

**Justificación (ISO 31010):**  
Recomendada para agregación de riesgos y análisis de distribuciones bajo alta incertidumbre  

**Norma-ISO-31010-2020**

- **Variables simuladas:**
  - Tiempo de detección  
  - Eficacia de controles  
  - Impacto operacional (horas de indisponibilidad)  

**Resultados:**
- Distribución de pérdidas operacionales  
- Percentil 95 como escenario crítico de planificación  

**Limitaciones:**  
Resultados sensibles a la calidad de los datos de entrada.

#### Diagrama – Simulación Monte Carlo

[![Evaluacion-de-Riesgos-de-Ataque-APT-Simulacion-Monte-Carlo.png](https://i.postimg.cc/T2rRMtyf/Evaluacion-de-Riesgos-de-Ataque-APT-Simulacion-Monte-Carlo.png)](https://postimg.cc/pyLNKYY6)

---

### 3. Identificación de riesgos, incertidumbres y consecuencias

#### 3.1 Riesgos identificados

| Código | Riesgo | Descripción |
|------|-------|-------------|
| R1 | Compromiso de credenciales críticas | Acceso persistente del APT a cuentas privilegiadas |
| R2 | Fallo de redundancia de comunicaciones | Inoperancia de enlaces alternos |
| R3 | Detección tardía del ataque | Incremento del tiempo de indisponibilidad |
| R4 | Error humano en respuesta | Decisiones incorrectas durante el incidente |

---

#### 3.2 Incertidumbres relevantes

| Tipo de incertidumbre | Descripción |
|----------------------|-------------|
| Epistémica | Desconocimiento total de TTPs del APT |
| Aleatoria | Variabilidad en tiempos de detección y respuesta |
| Organizacional | Comportamiento humano bajo presión |
| Tecnológica | Eficacia real de controles defensivos |

---

#### 3.3 Consecuencias analizadas

- Operacionales: pérdida de coordinación y retraso en órdenes.  
- Estratégicas: degradación de superioridad informacional.  
- Reputacionales: pérdida de confianza interinstitucional.  
- De seguridad nacional: aumento del riesgo en el teatro de operaciones.

---

### 4. Comparación visual final

**FTA:** ¿POR QUÉ ocurre el fallo?  
**Monte Carlo:** ¿QUÉ TAN GRAVE puede ser?

| Técnica | Aporta | Decisión que apoya |
|------|--------|-------------------|
| FTA | Comprensión causal | Diseño y prevención |
| Monte Carlo | Magnitud del impacto | Resiliencia y planeación |
| Juntas | Visión integral | Estrategia de ciberdefensa |

---

## FASE 3 – Socialización y transferencia de conocimiento

**Producto:**  
Presentación académica + guía práctica

### Contenido de la presentación

#### 1. Explicación didáctica de las técnicas

- FTA: “pensar desde el fallo final hacia atrás”  
- Monte Carlo: “explorar miles de futuros posibles”

#### 2. Demostración del ejercicio aplicado

- Visualización del árbol de fallas  
- Resultados gráficos de la simulación  

#### 3. Lecciones aprendidas

**¿Qué funcionó?**
- Complementariedad causal (FTA) + cuantitativa (Monte Carlo)

**¿Qué no funcionó?**
- Supuestos débiles generan falsa precisión

**¿Cuándo NO usar estas técnicas?**
- Entornos con baja madurez en datos  
- Decisiones tácticas inmediatas sin tiempo de modelado  

#### 4. Recomendaciones prácticas

- Usar FTA para decisiones de diseño y arquitectura  
- Usar Monte Carlo para planeación estratégica y resiliencia  
- Documentar supuestos y comunicar incertidumbre explícitamente

