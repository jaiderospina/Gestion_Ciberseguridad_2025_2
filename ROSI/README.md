
### ROSI: El Enfoque en la Inversión en Seguridad

El **ROSI** es una métrica específica que se utiliza para cuantificar el retorno financiero de una inversión en seguridad o reducción de riesgos. Se calcula como el beneficio neto de la reducción del riesgo dividido por el costo de la inversión.

*  Se emplea para cuantificar el valor económico que genera una inversión en ciberseguridad.


* **¿Cuál es su objetivo?** Demostrar el retorno de la inversión al comparar el **costo de implementar una contramedida** con la **pérdida económica esperada** que se evita al reducir la probabilidad o el impacto de un ataque.
* **Diferencia Clave:** A diferencia del ROI tradicional (donde el retorno es una ganancia directa de ingresos), en el ROSI el retorno es una **pérdida evitada**.

#### Fórmula del ROSI (Simplificada)

La fórmula básica para calcular el ROSI es:

$$ROSI = \frac{(\text{Pérdida Esperada Evitada} - \text{Costo de la Inversión en Seguridad})}{\text{Costo de la Inversión en Seguridad}}$$

* **Pérdida Esperada Evitada:** Se calcula como (Probabilidad del ataque sin la contramedida * Impacto económico del ataque) - (Probabilidad del ataque con la contramedida * Impacto económico del ataque).

En conclusión, **ROSI es una métrica de análisis costo-beneficio para evaluar inversiones específicas de mitigación de riesgos**.

**Pregunta Clave:** ¿Invertir $100,000 en este nuevo firewall nos ahorrará más de $100,000 en pérdidas esperadas por ataques cibernéticos?
* **Alcance:** Táctico, de proyecto. Se usa para justificar el presupuesto de seguridad.
* **Unidad:** Multiplicador o porcentaje (ej: 2.5x ROSI, o 250% de ROSI).
* **Foco en el Riesgo:** El riesgo es la "pérdida evitada". El retorno se calcula como la diferencia entre la pérdida que habrías tenido sin la inversión y el costo de la inversión misma.

---


#### 3. Ejemplo Práctico: Implementación de Autenticación de Múltiples Factores (MFA)

Imaginemos una empresa de comercio electrónico que quiere reducir el riesgo de que los ciberdelincuentes se apoderen de las cuentas de sus empleados (Account Takeover).

* **Paso 1: Evaluar la Pérdida Esperada Sin MFA.**
    * La empresa estima que, sin MFA, hay una probabilidad anual del **10% (0.10)** de sufrir una brecha de seguridad grave por robo de credenciales.
    * El impacto económico estimado de una brecha de este tipo es de **$500,000** (costos de respuesta, multas, pérdida de datos, reputación).
    * **Pérdida Esperada Anual (Sin MFA):** $500,000 * 0.10 = **$50,000**

* **Paso 2: Calcular el Costo de la Inversión.**
    * La empresa decide implementar una solución de MFA para sus 200 empleados.
    * El costo total de la inversión (licencias, software, implementación, capacitación) es de **$15,000** el primer año.

* **Paso 3: Estimar la Pérdida Esperada Con MFA.**
    * Con el MFA implementado, la probabilidad de que un ataque de robo de credenciales sea exitoso se reduce drásticamente al **1% (0.01)**.
    * El impacto económico se mantiene en $500,000.
    * **Pérdida Esperada Anual (Con MFA):** $500,000 * 0.01 = **$5,000**

* **Paso 4: Calcular la Pérdida Esperada Evitada.**
    * **Pérdida Evitada:** $50,000 (Sin MFA) - $5,000 (Con MFA) = **$45,000**

* **Paso 5: Calcular el ROSI.**

$$ROSI = \frac{(\$45,000 - \$15,000)}{\$15,000}$$
$$ROSI = \frac{\$30,000}{\$15,000}$$
$$ROSI = 2$$

#### 4. Interpretación del Resultado

* El ROSI es de **2**. Esto significa que por cada dólar que la empresa invirtió en MFA, evitó una pérdida de **dos dólares**.
* Se puede expresar como un porcentaje: **200% de ROSI**.
* Un ROSI mayor que 0 indica que la inversión en ciberseguridad es financieramente justificable. En este ejemplo, la inversión en MFA es altamente rentable.

**Beneficios de Presentar el ROSI:**

* **Justificación de Presupuesto:** Ayuda a los CISO y directores de IT a obtener aprobación para inversiones en seguridad.
* **Priorización de Proyectos:** Permite comparar diferentes soluciones de seguridad y elegir las que ofrezcan el mayor retorno.
* **Comunicación:** Traduce el lenguaje técnico de la ciberseguridad a un lenguaje financiero que la alta dirección puede entender.