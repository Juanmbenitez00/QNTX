# QNTX – Reportes Inteligentes para PyMEs

## Introducción

Las PyMEs generan gran cantidad de datos de ventas, marketing y clientes, pero en muchos casos no logran transformarlos en información útil para la toma de decisiones.

**Problema:**  
Los principales desafíos que enfrentan son:
- Procesos manuales con altos márgenes de error.  
- Informes poco ejecutivos.  
- Falta de visualizaciones claras para detectar tendencias.  

Esto impacta directamente en la velocidad y calidad de la toma de decisiones estratégicas, generando pérdida de oportunidades comerciales.

**Propuesta:**  
QNTX – Reportes Inteligentes para PyMEs propone un conjunto de prompts diseñados para automatizar el análisis de datos y la comunicación de resultados.  
- **Texto→Texto:** generación de reportes ejecutivos con KPIs, tendencias y recomendaciones.  
- **Texto→Imagen:** creación de visualizaciones estilo dashboard corporativo que refuercen el informe.  

**Viabilidad:**  
El proyecto es factible utilizando ChatGPT (texto) y DALL·E (imagen). Los datos provendrán de un dataset de ejemplo (ventas diarias).  
Limitaciones: los modelos de imagen no garantizan cifras exactas y los modelos de texto pueden alucinar.  
Cómo resolverlo: prompts estructurados que obliguen a cálculos paso a paso y definan el formato de salida.

## Objetivos
- Automatizar la generación de reportes ejecutivos para PyMEs a partir de sus datos de ventas y marketing.  
- Reducir el tiempo de análisis y presentación de información clave.  
- Estandarizar la lectura de KPIs esenciales: Crecimiento, CAC, ROAS y Ticket Promedio.  
- Complementar los reportes con visualizaciones conceptuales que refuercen la comunicación con directivos.  
- Demostrar la viabilidad de integrar prompts en procesos de Business Intelligence de bajo costo.

## KPIs del proyecto

Los indicadores clave que se utilizan en este proyecto son:

- **Crecimiento (%)**  
  Mide el cambio porcentual de un período respecto al anterior.  
  Ejemplo: si ayer ingresaste $100.000 y hoy $110.000 → crecimiento = +10%.  
  Ayuda a detectar tendencias positivas o caídas rápidas.

- **CAC (Costo de Adquisición de Clientes)**  
  Fórmula: gasto en marketing ÷ clientes nuevos.  
  Ejemplo: $10.000 ÷ 20 clientes = $500.  
  Permite saber si atraer clientes resulta rentable.

- **ROAS (Retorno sobre la Inversión en Publicidad)**  
  Fórmula: ingresos ÷ gasto en marketing.  
  Ejemplo: $25.000 ÷ $5.000 = 5.  
  Indica cuántos pesos se recuperan por cada peso invertido en publicidad.

- **Ticket Promedio**  
  Fórmula: ingresos ÷ órdenes.  
  Ejemplo: $50.000 ÷ 100 ventas = $500.  
  Mide cuánto gasta en promedio un cliente por compra.

  ## Metodología

El proyecto se lleva a cabo en cinco etapas principales:

1. **Carga de datos**  
   Se utiliza un dataset de ventas diarias (ejemplo: enero 2024).  

2. **Cálculo de KPIs**  
   A partir de los datos se calculan Crecimiento, CAC, ROAS y Ticket Promedio.  

3. **Prompt Texto→Texto**  
   Los KPIs se envían a un prompt estructurado que:  
   - Resume resultados en un informe ejecutivo (~150 palabras).  
   - Identifica tendencias y anomalías.  
   - Propone 5 acciones concretas en formato lista.  

4. **Prompt Texto→Imagen**  
   Se generan visualizaciones conceptuales estilo dashboard corporativo para reforzar la comunicación de los resultados.  

5. **Documentación en Notebook**  
   Todo el flujo se implementa en un cuaderno Jupyter (`QNTX.ipynb`) con celdas claras: carga de datos, KPIs, prompts y salidas.

## Herramientas y técnicas de prompting

**Herramientas utilizadas**
- **Python y librería Pandas**: para la carga y manipulación de datos de ventas.  
- **Google Colab**: entorno online que permite trabajar con notebooks sin instalación local.  
- **OpenAI API (gpt-4o-mini)**: modelo económico para generar reportes ejecutivos en texto.  
- **DALL·E / Stable Diffusion**: para crear visualizaciones conceptuales tipo dashboard.  

**Técnicas de Fast Prompting aplicadas**
- **Zero shot prompting:** cuando se pide al modelo un análisis directo de los datos de ventas sin dar ejemplos previos, confiando en su capacidad de generalización.  
- **One shot prompting:** se incluye un ejemplo breve de salida esperada, como un informe en tres secciones: *Qué pasó / Por qué / Qué hacer*.  
- **Few shot prompting:** se proporcionan varios ejemplos de KPIs calculados correctamente para reforzar la consistencia de resultados en nuevas ejecuciones.  

## Optimización del uso de tokens

Para mantener el costo bajo y las respuestas enfocadas, este proyecto aplica:

- **Modelo económico:** se utiliza `gpt-4o-mini`.
- **Entrada mínima:** en lugar de enviar todo el CSV, se mandan solo los **últimos 7 días de ventas** para que el modelo calcule los KPIs.  
- **Salida acotada:** se limita a un informe ejecutivo de ~150 palabras (≈180 tokens), acompañado de una lista de 5 acciones y una tabla resumen de KPIs.  
- **Parámetros de control:** `temperature=0.3–0.5` para respuestas consistentes y `max_output_tokens=300` como límite de longitud.  
- **Estimación exacta con Tokenizer de OpenAI:**  
  - El prompt principal ocupa **250 tokens de entrada**.  
  - La salida prevista (~150 palabras) ocupa aprox **180 tokens**.  
  - Total por consulta ≈ **430 tokens**.
  


