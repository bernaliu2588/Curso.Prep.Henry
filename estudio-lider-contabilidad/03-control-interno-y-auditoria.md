# Módulo 03 — Control interno y auditoría

> Responsabilidad del aviso: *"Diseñar, implementar y supervisar políticas de control
> interno que garanticen la razonabilidad, veracidad y soporte documental de cada
> asiento contable; ser punto de contacto para auditorías externas, revisoría fiscal y
> auditorías tributarias."*

---

## 3.1 El marco: COSO 2013

Cinco componentes, diecisiete principios. Memoriza los componentes con un ejemplo
contable de cada uno:

| Componente | Qué significa | Ejemplo en tu área |
|---|---|---|
| **Entorno de control** | Cultura, ética, estructura, competencia | Código de conducta, línea ética, organigrama contable con segregación real |
| **Evaluación de riesgos** | Identificar y valorar lo que puede salir mal | Matriz de riesgos por ciclo; riesgo de fraude en ingresos y en tesorería |
| **Actividades de control** | Los controles propiamente dichos | Conciliaciones, aprobaciones, four-eyes, controles automáticos del ERP |
| **Información y comunicación** | Que el dato correcto llegue a quien decide | Calendario de cierre, definiciones firmadas de métricas, reportes al comité |
| **Supervisión** | Monitoreo continuo y evaluaciones independientes | Auditoría interna, autoevaluación de controles, seguimiento de hallazgos |

**Presunción de fraude en ingresos:** las normas de auditoría presumen que existe
riesgo de fraude en el reconocimiento de ingresos. En una SaaS con ingresos diferidos y
contratos multianuales, ese riesgo es alto por definición — anticípalo en la entrevista.

**Triángulo del fraude:** presión + oportunidad + racionalización. Los controles atacan
la **oportunidad**; la cultura ataca la racionalización.

---

## 3.2 Controles clave por ciclo

### Order-to-Cash (ingresos) — el ciclo crítico de una SaaS

| Riesgo | Control |
|---|---|
| Contratos con condiciones no estándar que rompen el reconocimiento | Aprobación de descuentos y cláusulas no estándar por Finanzas antes de firmar (*deal desk*) |
| Ingreso reconocido antes de tiempo | Motor de reconocimiento parametrizado; el reconocimiento no depende de un asiento manual |
| Facturación no emitida o duplicada | Conciliación **billing ↔ ERP ↔ DIAN**, tres vías, mensual |
| Notas crédito para "arreglar" cifras | Aprobación independiente de toda nota crédito por encima de un umbral |
| Cartera irrecuperable no provisionada | Comité de cartera mensual + matriz ECL automática por antigüedad |
| Ingreso diferido mal calculado | Prueba de recálculo independiente sobre muestra + cuadre del *roll-forward* del pasivo |

### Procure-to-Pay
Solicitud → aprobación por matriz de autorizaciones → orden de compra → recepción →
factura con tres vías (OC / recepción / factura) → contabilización → pago con doble
aprobación bancaria. Maestro de proveedores con **segregación**: quien crea un
proveedor no puede pagarle. Control de **proveedores fantasma** y de cambios de cuenta
bancaria (verificación por canal distinto — riesgo de fraude por suplantación).

### Nómina
Altas y bajas conciliadas con RR. HH.; variación mes a mes explicada por headcount;
conciliación de nómina electrónica con la contabilidad y con los pagos de seguridad
social (PILA).

### Tesorería
Conciliación bancaria diaria o al menos semanal; ningún usuario con capacidad de
crear un beneficiario **y** aprobar el pago; posiciones de caja proyectadas;
control de tarjetas corporativas y legalización de anticipos.

### Cierre y reporte (record-to-report)
Ver módulo 01, sección 1.5. Los controles de cierre son controles de la entidad,
y son los primeros que revisa un auditor.

---

## 3.3 Segregación de funciones

Regla mental: **nadie debe poder iniciar, aprobar, ejecutar y registrar la misma
transacción.** Con equipos pequeños hay conflicto inevitable; la respuesta madura no es
"lo segregamos todo", es:

> *"Donde el tamaño del equipo no permite segregar, se compensa con controles
> detectivos: revisión posterior por un tercero, reportes de excepciones, límites de
> autorización más bajos y revisión de logs del ERP. Y se documenta explícitamente el
> control compensatorio, no se deja implícito."*

Herramienta a nombrar: **matriz de autoridad / DOA (Delegation of Authority)**, y
revisión periódica de **perfiles y roles del ERP** (que es donde realmente vive la
segregación).

---

## 3.4 Revisoría fiscal, auditoría externa y auditoría interna

| | Revisoría fiscal | Auditoría externa | Auditoría interna |
|---|---|---|---|
| **Origen** | Ley: Código de Comercio arts. 203–217; Ley 43 de 1990 | Contrato / requerimiento de inversionistas o matriz | Decisión de la administración/junta |
| **Nombra** | Asamblea de accionistas | Administración o junta | Junta / comité de auditoría |
| **Alcance** | Permanente e integral: financiero, legal, control interno, cumplimiento | El pactado (usualmente dictamen sobre EEFF) | Riesgos y procesos definidos en el plan anual |
| **Producto** | **Dictamen** e informes a la asamblea | Informe/dictamen de auditoría | Informes de hallazgos y recomendaciones |
| **Independencia** | Estricta, con inhabilidades legales | Normas de ética profesional | Independencia funcional |

**Obligatoriedad de revisor fiscal** (parágrafo art. 13 Ley 43 de 1990): sociedades
cuyos **activos brutos** al 31 de diciembre del año anterior superen **5.000 SMMLV** o
cuyos **ingresos brutos** superen **3.000 SMMLV**, además de las S.A. y las sucursales
de sociedades extranjeras, entre otras.

**Normas aplicables:** las **NIA** (Normas Internacionales de Auditoría) están
incorporadas en el **Decreto 2420 de 2015**. Términos que conviene manejar:
materialidad (de planeación, de ejecución/*performance*, y umbral de errores
triviales), riesgo de auditoría, evidencia suficiente y apropiada, muestreo,
carta de representación, **carta de gerencia (management letter)** con deficiencias
de control, y las opiniones: **limpia, con salvedades, adversa y abstención**.

### Cómo se es un buen "punto de contacto"
1. **PBC list** (*Prepared By Client*) negociada antes de que arranque la auditoría,
   con dueño y fecha por ítem.
2. **Data room** ordenado por ciclo, con la carpeta de cierre mensual ya lista — si el
   cierre está bien documentado, la auditoría es un trámite.
3. Un solo canal de comunicación (tú) para evitar respuestas contradictorias.
4. Seguimiento formal de hallazgos: cada uno con causa raíz, plan de acción, dueño y
   fecha; reporte de avance a la junta.
5. Discusión temprana de los **juicios contables**: reconocimiento de ingresos,
   capitalización de software, ECL, impuesto diferido. Nunca los descubras el día del
   dictamen.

---

## 3.5 Auditoría tributaria de la DIAN

Ver módulo 02, sección 2.9, para la secuencia procesal. Desde control interno:

- **Expediente por declaración:** cada declaración con su papel de trabajo, soportes,
  conciliación con contabilidad y evidencia de pago. Si te llega un requerimiento dos
  años después, debe poder responderse sin reconstruir nada.
- **Conciliación fiscal (art. 772-1 ET / Formato 2516)** hecha durante el año, no en
  marzo.
- **Trazabilidad de la deducibilidad:** factura electrónica válida, documento soporte,
  medio de pago bancarizado (art. 771-5 ET), retención practicada, y en pagos al
  exterior el cumplimiento de precios de transferencia.
- Registro de **posiciones fiscales inciertas** y su provisión (NIC 37 / CINIIF 23).

---

## 3.6 Cumplimiento no financiero que toca a Contabilidad

- **SAGRILAFT** — Sistema de Autocontrol y Gestión del Riesgo LA/FT/FPADM,
  Circular Externa 100-000016 de 2020 de la Superintendencia de Sociedades. Obliga por
  umbrales de ingresos/activos. Implica **debida diligencia de contrapartes** y un
  **oficial de cumplimiento**. Contabilidad aporta la información de terceros y las
  señales de alerta transaccionales.
- **PTEE** — Programa de Transparencia y Ética Empresarial (antisoborno,
  misma circular). Aplica sobre todo si hay operaciones con el sector público.
- **Ley 1581 de 2012 (habeas data)** — crítica para una plataforma de empleo que
  procesa datos de candidatos. No es tu norma, pero saber que existe y que impacta
  contratos y riesgos te posiciona bien.
- **Reportes a la Superintendencia de Sociedades** (estados financieros anuales) y
  **régimen cambiario del Banco de la República** si hay inversión extranjera, créditos
  externos o ingresos de divisas (declaración de cambio, registro de inversión
  extranjera ante el BR — condición para poder remitir dividendos).

---

## 3.7 Due diligence e inversionistas

Una scaleup levanta capital; el líder de contabilidad es protagonista.

- **Quality of Earnings (QoE):** el comprador/inversionista normaliza el EBITDA y
  valida la **calidad del ARR**. Preguntas típicas: ¿qué parte del ingreso es
  realmente recurrente? ¿hay ingresos de una sola vez inflando el run-rate?
  ¿cómo se define un cliente activo?
- **Data room** con: EEFF auditados, conciliación MRR ↔ ingreso, MRR bridge por mes,
  cohortes de retención, contratos de los top clientes, declaraciones tributarias,
  estudios de precios de transferencia, contratos laborales y de opciones.
- **Puntos rojos frecuentes**: reconocimiento de ingresos agresivo, capitalización
  excesiva de software, ingresos diferidos mal cuadrados, pasivos tributarios no
  provisionados, ICA no declarado en municipios, y participaciones en el capital sin
  reconocimiento bajo NIIF 2.

---

## 3.8 Checklist de autoevaluación

- [ ] Nombro los 5 componentes de COSO con un ejemplo contable de cada uno.
- [ ] Puedo listar 5 controles del ciclo de ingresos de una SaaS.
- [ ] Sé qué responder cuando no se puede segregar funciones por tamaño del equipo.
- [ ] Distingo revisoría fiscal, auditoría externa y auditoría interna.
- [ ] Conozco los umbrales de obligatoriedad de revisor fiscal.
- [ ] Sé cómo preparar y gobernar una auditoría (PBC, data room, seguimiento).
- [ ] Sé qué es SAGRILAFT y por qué me involucra.
- [ ] Entiendo qué mira un QoE en una SaaS.
