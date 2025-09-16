# QNTX – Reportes Inteligentes para PyMEs

## Resumen
QNTX es un proyecto demostrativo que aplica **ingeniería de prompts** para generar reportes ejecutivos y visualizaciones conceptuales a partir de datos de ventas de PyMEs.  
El flujo combina:
- **Texto → Texto**: un prompt estructurado que produce un informe ejecutivo (~150 palabras), tendencias y 5 acciones concretas.  
- **Texto → Imagen**: prompts diseñados para crear imágenes estilo dashboard corporativo con **DALL·E de ChatGPT Plus**.  

El objetivo es mostrar cómo las PyMEs pueden acceder a reportes claros y visuales usando herramientas accesibles (Google Colab + ChatGPT Plus), sin depender de infraestructuras complejas.

---

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
- **Texto→Imagen:** creación de visualizaciones estilo dashboard corporativo con **DALL·E** para reforzar el informe.  

**Viabilidad:**  
El proyecto es factible utilizando ChatGPT Plus (texto e imágenes). Los datos provienen de un dataset de ejemplo (ventas diarias).  
**Limitaciones:** las imágenes son conceptuales y los modelos de texto pueden alucinar.  
**Cómo resolverlo:** prompts estructurados que obliguen a cálculos paso a paso y definan el formato de salida.

---

## Objetivos
- Automatizar la generación de reportes ejecutivos para PyMEs a partir de sus datos de ventas y marketing.  
- Reducir el tiempo de análisis y presentación de información clave.  
- Estandarizar la lectura de KPIs esenciales: Crecimiento, CAC, ROAS y Ticket Promedio.  
- Complementar los reportes con visualizaciones conceptuales que refuercen la comunicación con directivos.  
- Demostrar la viabilidad de integrar prompts en procesos de Business Intelligence de bajo costo.

---

## KPIs del proyecto
- **Crecimiento (%)**: mide el cambio porcentual de un período respecto al anterior.  
- **CAC (Costo de Adquisición de Clientes)**: gasto en marketing ÷ clientes nuevos.  
- **ROAS (Retorno sobre la inversión en publicidad)**: ingresos ÷ gasto en marketing.  
- **Ticket Promedio**: ingresos ÷ órdenes.

---

## Metodología
1. **Carga de datos**: dataset de ventas diarias (ejemplo: 60 días).  
2. **Cálculo de KPIs**: Crecimiento, CAC, ROAS, Ticket Promedio.  
3. **Prompt Texto→Texto**: generación de informe ejecutivo (~150 palabras) con KPIs y 5 acciones.  
4. **Prompt Texto→Imagen**: generación de prompts para visualizaciones tipo dashboard con **DALL·E**.  
5. **Documentación en Notebook**: todo el flujo en `notebooks/QNTX_Final.ipynb`.

---

## Herramientas y técnicas de prompting
**Herramientas utilizadas**
- **Python + Pandas**: manipulación de datos.  
- **Google Colab**: entorno de ejecución.  
- **ChatGPT Plus (GPT-4o mini + DALL·E)**: para texto e imágenes.  

**Técnicas aplicadas**
- **Zero/One/Few-shot prompting** según el contexto.  
- Instrucciones claras, formato fijo, delimitadores y longitud objetivo.  
- Temperature baja (0.3–0.5) para consistencia.  

---

## Optimización del uso de tokens
Para mantener el costo bajo y las respuestas enfocadas, este proyecto aplica:

- **Modelo económico:** se utiliza `gpt-4o-mini`.  
- **Entrada mínima:** en lugar de enviar todo el CSV, se mandan solo los **últimos 7 días de ventas** para que el modelo genere el informe.  
- **Salida acotada:** informe ejecutivo de ~150 palabras + 5 acciones + tabla de KPIs.  
- **Parámetros de control:** `temperature=0.3–0.5`, `max_output_tokens=300`.  
- **Estimación con tokenizer de OpenAI:**  
  - Prompt: ~250 tokens.  
  - Respuesta: ~180 tokens.  
  - Total: ~430 tokens.  

> En esta entrega se trabajó sin APIs externas, utilizando únicamente ChatGPT Plus.

---

## Implementación
El notebook `notebooks/QNTX_Final.ipynb` incluye:
1. Setup de entorno y datos.  
2. Cálculo de KPIs y exportación a `outputs/kpis_resumen.csv`.  
3. Prompt estructurado (texto→texto) y copia manual en ChatGPT Plus.  
4. Prompts para imágenes (texto→imagen) ejecutados en **DALL·E**.  
5. Exportación de resultados en `outputs/reporte_QNTX.md` y `outputs/imagen_dashboard_*.png`.

---

## Resultados
- **`outputs/kpis_resumen.csv`**: tabla con KPIs calculados.  
- **`outputs/reporte_QNTX.md`**: informe ejecutivo (~150 palabras) + 5 acciones + prompts de imagen.  
- **`outputs/imagen_dashboard_1.png` y `outputs/imagen_dashboard_2.png`**: visualizaciones conceptuales tipo dashboard.  

---

## Conclusiones
QNTX demuestra que la **Generación de prompts** aplicada a datos de PyMEs permite:
- Reducir el tiempo de análisis.  
- Generar reportes ejecutivos estandarizados.  
- Apoyar decisiones con imágenes conceptuales que refuercen la comunicación.  

La solución es accesible, replicable y puede escalarse a más indicadores y fuentes de datos en futuros desarrollos.

  


