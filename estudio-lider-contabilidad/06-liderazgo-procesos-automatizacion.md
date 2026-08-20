# Módulo 06 — Liderazgo, procesos y automatización

> Responsabilidades del aviso: *"Liderar, formar y evaluar al equipo de analistas
> contables, distribuyendo cargas de trabajo, asegurando calidad en el trabajo
> entregado y desarrollando capacidades técnicas del equipo"* y *"optimizar y
> automatizar procesos contables, con especial atención a las particularidades de un
> modelo SAAS (reconocimiento de ingresos recurrentes, ingresos diferidos,
> suscripciones)"*.

---

## 6.1 Liderar un equipo contable

### Estructura típica que vas a liderar
Analista de ingresos y facturación · analista de cuentas por pagar y gastos · analista
de tesorería y conciliaciones · analista de nómina e impuestos (o un especialista
tributario). En una scaleup pueden ser 2 a 6 personas, con roles solapados.

### Las cuatro cosas que hace un líder contable

**1. Distribuir la carga con criterio.**
No es repartir tareas: es diseñar el **RACI del cierre** y de las obligaciones
tributarias. Cada actividad con un responsable (R), un aprobador (A), consultados (C)
e informados (I). Con eso se acaban los "yo pensé que lo hacías tú" del día 5.

**2. Asegurar calidad.**
- Revisión de **cuatro ojos** en todo asiento manual relevante y en toda declaración.
- **Papeles de trabajo estandarizados**: mismo formato, mismo lugar, misma nomenclatura.
- Métrica de calidad: **asientos de ajuste post-cierre** y **hallazgos de auditoría
  repetidos**. Si el mismo hallazgo aparece dos años seguidos, el problema es de
  proceso, no de la persona.
- La revisión es **sobre el trabajo, no sobre la persona**: se retroalimenta con hechos.

**3. Desarrollar capacidades.**
- **Matriz de habilidades**: filas = personas, columnas = competencias
  (NIIF 15, impuestos, Power BI, ERP, inglés). Semáforo de nivel actual vs requerido.
  De ahí sale el plan de formación y, de paso, el mapa de **riesgo de dependencia**
  (procesos que solo una persona sabe hacer → **rotación planificada** y
  documentación).
- **Actualización normativa** como rutina, no como emergencia: sesión mensual de 45
  minutos donde alguien del equipo presenta un cambio normativo del mes. Rota el
  expositor: enseñar es la forma más rápida de aprender, y responde directo a la
  responsabilidad de *"mantenerse actualizado frente a cambios regulatorios"*.
- Uno a uno quincenal, con agenda del colaborador, no del jefe.

**4. Evaluar.**
Objetivos claros y medibles por rol (días de cierre, cero extemporaneidades, %
conciliaciones al día, calidad de papeles de trabajo), retroalimentación continua y
evaluación formal sin sorpresas. Modelo útil para dar feedback: **SBI** —
*Situación, Comportamiento, Impacto*: "En el cierre de marzo (S), la conciliación de
bancos se entregó el día 6 sin las partidas explicadas (B), lo que retrasó el reporte a
gerencia y me obligó a rehacer el análisis (I). ¿Qué necesitas para que no se repita?".

### Trabajar con las otras áreas
El aviso lo pide explícitamente: **FP&A, Producto y Revenue**.
- Con **Revenue/Ventas**: gobierno de descuentos y cláusulas no estándar (*deal desk*),
  y definición conjunta de qué cuenta como churn.
- Con **FP&A**: una sola versión del P&L; contabilidad entrega el real, FP&A el plan;
  las variaciones se explican juntos.
- Con **Producto**: costo de servir por funcionalidad, costo de cloud y de inferencia
  de IA por uso, e impacto contable de cambios en el empaquetado de planes (cada
  cambio de pricing es un cambio de reconocimiento de ingresos: hay que sentarse antes
  del lanzamiento, no después).

---

## 6.2 Rediseñar procesos

### Método
1. **Mapear el AS-IS** con quien hace el trabajo, no desde el escritorio. Herramientas:
   **SIPOC** (Proveedor-Entrada-Proceso-Salida-Cliente) y flujograma con carriles.
2. **Medir**: tiempo por actividad, reprocesos, esperas, errores.
3. **Identificar desperdicio** (lean): esperas, reprocesos, movimientos de información,
   sobreprocesamiento, controles duplicados que no agregan valor.
4. **Diseñar el TO-BE** priorizando por **impacto × facilidad**.
5. **Pilotear un ciclo** (un cierre), medir, ajustar y estandarizar.
6. **Documentar** en el manual de procedimientos y capacitar.

### KPIs de proceso que debes proponer

| KPI | Meta razonable |
|---|---|
| Días hábiles hasta el cierre | ≤ 5 |
| % de asientos automáticos sobre el total | > 85 % |
| % de conciliación bancaria automática | > 90 % |
| Partidas conciliatorias con más de 60 días | 0 |
| Asientos de ajuste post-cierre | Tendencia a 0 |
| Obligaciones tributarias presentadas fuera de plazo | 0 |
| DSO | Según política comercial, con tendencia |
| Horas del equipo dedicadas a captura manual de datos | Reducción sostenida |

---

## 6.3 Automatización: el stack

| Proceso | Qué se automatiza | Cómo |
|---|---|---|
| **Facturación y reconocimiento** | Emisión, prorrateo, ingreso diferido, notas crédito | Integración **billing ↔ ERP**; motor de reconocimiento parametrizado por tipo de contrato |
| **Facturación electrónica** | Validación DIAN, CUFE, contingencias | Proveedor tecnológico integrado al ERP, con conciliación diaria de rechazos |
| **Conciliación bancaria** | Emparejamiento automático por referencia, valor y fecha | Extractos por API o archivo; reglas + emparejamiento difuso para el resto |
| **Cuentas por pagar** | Captura de facturas de proveedor | **OCR** + validación de tres vías + flujo de aprobación digital |
| **Gastos de viaje y tarjetas** | Legalización | App de gastos con política embebida y contabilización automática |
| **Nómina** | Provisión, contabilización, nómina electrónica | Integración nómina ↔ ERP |
| **Cierre** | Asientos recurrentes, depreciación, ECL, diferencia en cambio | Plantillas y jobs programados; checklist de cierre en herramienta, no en Excel |
| **Reporte** | Estados financieros y tablero | Power BI con refresco programado sobre el ERP |

**Sistemas que se ven en el mercado colombiano:** Siigo, World Office, SAP Business
One, Oracle NetSuite, Odoo, Microsoft Dynamics 365 Business Central. Del lado de
suscripciones: Stripe Billing, Chargebee, Recurly, Paddle. Para reconocimiento y cierre:
módulos de *revenue recognition* del ERP o herramientas dedicadas.

**Cómo se prioriza (respuesta de líder, no de técnico):**
> *"Priorizo por volumen × riesgo × horas manuales. Lo primero que automatizaría es la
> conciliación entre el sistema de billing y el ERP, porque es el punto donde nacen los
> errores de ingreso, es el de mayor riesgo de auditoría y hoy consume el mayor número
> de horas del equipo. Empezaría con un piloto de un ciclo de cierre, midiendo horas
> y errores antes y después, y con eso justifico la inversión del resto."*

---

## 6.4 Inteligencia artificial aplicada a contabilidad

El aviso pide "inteligencia artificial" entre los conocimientos técnicos, y la empresa
vende IA. Ten una posición **concreta y prudente**.

### Casos de uso reales y de bajo riesgo
1. **Clasificación de gastos** y sugerencia de cuenta contable a partir del histórico.
2. **Extracción documental** (OCR + modelo de lenguaje) de facturas de proveedor,
   contratos y extractos, con validación humana.
3. **Emparejamiento difuso** en conciliaciones cuando la referencia no coincide exacto.
4. **Detección de anomalías** en asientos: importes atípicos, terceros nuevos, asientos
   fuera de horario, patrones de redondeo — apoyo directo al control interno y al
   riesgo de fraude.
5. **Lectura de contratos** para extraer términos que afectan el reconocimiento
   (plazo, renovación automática, SLA, descuentos escalonados) y alimentar el motor de
   ingresos.
6. **Pronóstico de recaudo y de churn** a partir de comportamiento de pago y de uso.
7. **Asistente de consulta normativa** sobre un corpus controlado (ET, doctrina DIAN,
   políticas internas), **con cita a la fuente**.
8. **Redacción de primeras versiones** de notas a los estados financieros y de análisis
   de variaciones, revisadas por una persona.

### Los controles que debes nombrar (esto es lo que separa a un líder de un entusiasta)
- **Humano en el circuito** en toda decisión contable: la IA propone, la persona aprueba.
  Ningún asiento se contabiliza sin aprobación humana.
- **Trazabilidad**: registro de qué modelo sugirió qué, con qué entrada y quién aprobó.
  Sin esto no hay soporte documental, y el aviso exige "soporte documental de cada
  asiento contable".
- **Datos personales**: la Ley 1581 de 2012 aplica; cuidado con enviar información de
  terceros a servicios externos sin base legal y sin acuerdo de tratamiento.
- **Riesgo de alucinación** en consultas normativas: exigir cita verificable y verificar
  la norma en la fuente oficial antes de actuar.
- **Segregación**: la IA no puede ser a la vez preparador y revisor.
- **Política de uso de IA** escrita y aprobada, y capacitación al equipo.

### La frase que deja buena impresión
> *"La IA me sirve para eliminar la captura y la clasificación manual, que es donde el
> equipo pierde tiempo y donde se cometen los errores. No la usaría para decidir
> tratamientos contables: ahí el criterio profesional y la trazabilidad no son
> negociables. El indicador de éxito no es 'usamos IA', es 'bajamos el cierre de 10 a
> 5 días y los asientos post-cierre a cero'."*

---

## 6.5 Tu plan de 30-60-90 días

Prepáralo. Es muy probable que te lo pidan, y si no, ofrécelo: cierra la entrevista
con fuerza.

### Días 1–30 — Entender y estabilizar
- Levantar el mapa real de procesos, sistemas y personas; una sesión con cada analista.
- Revisar el último cierre completo y las últimas declaraciones presentadas.
- Diagnóstico de riesgos: obligaciones tributarias al día, conciliaciones pendientes,
  partidas antiguas, políticas contables documentadas, estado de precios de
  transferencia.
- Entender el modelo de negocio: planes, contratos tipo, cómo se factura, cómo se
  define el churn, quién reporta el MRR hoy y con qué fuente.
- **Entregable:** diagnóstico con riesgos priorizados y quick wins.

### Días 31–60 — Ordenar
- Calendario de cierre formal con RACI y calendario tributario único con dueños.
- Conciliaciones de balance con dueño, soporte y fecha; limpiar partidas antiguas.
- Primera versión del **puente MRR ↔ ingreso NIIF 15**, acordada con Revenue y FP&A.
- Documentar las políticas contables críticas: reconocimiento de ingresos,
  capitalización de software, ECL, capitalización de comisiones.
- **Entregable:** primer cierre bajo el nuevo calendario, con reporte gerencial.

### Días 61–90 — Escalar
- Automatizar el primer proceso priorizado (billing ↔ ERP o conciliación bancaria),
  con medición antes/después.
- Tablero en Power BI con las métricas SaaS conciliadas contra contabilidad.
- Plan de formación del equipo a partir de la matriz de habilidades.
- Preparación anticipada de la auditoría y de precios de transferencia.
- **Entregable:** cierre en 5 días, tablero en producción y hoja de ruta a 12 meses.

---

## 6.6 Checklist de autoevaluación

- [ ] Tengo un RACI de cierre que puedo dibujar en un tablero.
- [ ] Sé explicar cómo aseguro calidad sin microgestionar.
- [ ] Puedo describir una matriz de habilidades y para qué sirve.
- [ ] Sé dar retroalimentación con el modelo SBI.
- [ ] Tengo 8 KPIs de proceso con metas.
- [ ] Puedo priorizar automatizaciones con un criterio explícito y justificarlo.
- [ ] Tengo 5 casos de uso de IA y los 5 controles que exigiría.
- [ ] Mi plan de 30-60-90 está escrito y lo puedo contar en 3 minutos.
