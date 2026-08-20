# Módulo 02 — Impuestos Colombia

> Responsabilidad del aviso: *"Garantizar la correcta liquidación, declaración y pago
> oportuno de obligaciones tributarias (renta, IVA, ICA, retención en la fuente,
> autorretenciones, industria y comercio), incluyendo planeación tributaria y gestión
> de vencimientos ante la DIAN y entes territoriales."*

**Dato base 2026:** UVT = **$52.374** (Resolución DIAN 000238 del 15-dic-2025; el
incremento se calculó sobre una variación del IPC de ingresos medios de 5,17 %).
Todo umbral del Estatuto Tributario se expresa en UVT — memoriza el valor, no los pesos.

---

## 2.1 Mapa de obligaciones de una SaaS en Medellín

| Tributo | Autoridad | Periodicidad típica | Formulario |
|---|---|---|---|
| Renta y complementarios | DIAN | Anual (+ anticipo) | 110 |
| Autorretención especial de renta | DIAN | Mensual | 350 |
| Retención en la fuente (renta, IVA, timbre) | DIAN | Mensual | 350 |
| IVA | DIAN | Bimestral o cuatrimestral | 300 |
| Precios de transferencia — declaración informativa | DIAN | Anual | 120 |
| Impuesto al patrimonio PJ (temporal 2026) | DIAN | Anual 2026 | ver decreto |
| ICA | Distrito de Medellín | Régimen ordinario: anual | ICA distrital |
| ReteICA | Distrito de Medellín | Bimestral | ReteICA |
| Impuesto de avisos y tableros / sobretasa bomberil | Distrito de Medellín | Con el ICA | — |
| GMF (4×1000) | Banco (agente retenedor) | Se soporta, no se declara | — |
| Facturación electrónica / nómina electrónica | DIAN | Continua | XML/UBL |

---

## 2.2 Impuesto de renta

- **Tarifa general personas jurídicas: 35 %** (art. 240 ET, modificado por el art. 10
  de la Ley 2277 de 2022). Sigue vigente para el año gravable 2026: la reforma
  tributaria estructural radicada en septiembre de 2025 se hundió en el Congreso el
  9 de diciembre de 2025.
- **Sobretasas:** entidades financieras +5 pp (40 %) hasta el año gravable 2027;
  generación hidroeléctrica +3 pp (38 %) entre 2023 y 2026.
- **Tasa mínima de tributación (TTD del 15 %)** — art. 240 par. 6 ET. Si la tasa
  efectiva calculada sobre la utilidad depurada cae por debajo del 15 %, se paga un
  impuesto adicional hasta alcanzarla. **Muy relevante para una empresa con beneficios
  o pérdidas fiscales**: te pueden preguntar cómo la monitoreas durante el año.
- **Renta presuntiva: 0 %** desde el año gravable 2021 (art. 188 ET).
- **Pérdidas fiscales:** compensables en los **12** periodos gravables siguientes
  (art. 147 ET), sin reajuste. Compensarlas **amplía la firmeza** de la declaración a
  5 años.
- **Autorretención especial de renta** (Decreto 2201 de 2016): mensual, sobre ingresos
  brutos, a la tarifa según actividad económica CIIU. Es un **anticipo**, no un
  impuesto adicional.
- **Anticipo del impuesto** del año siguiente (art. 807 ET): 75 % en general.
- **Descuentos tributarios** que conviene conocer para planeación: ICA pagado
  (descuento del 50 % del ICA, art. 115 ET — verificar vigencia y opción de deducción),
  IVA en adquisición de activos fijos reales productivos (art. 258-1 ET), donaciones,
  e **inversiones en ciencia, tecnología e innovación / deducción por proyectos
  calificados por MinCiencias** — este último es *el* incentivo natural para una
  empresa de software con equipo de desarrollo.

### Impuesto al patrimonio de personas jurídicas — 2026 ⚠️

Creado de forma **temporal para el año 2026** por el **Decreto Legislativo 173 del
24 de febrero de 2026**, expedido bajo el estado de emergencia económica, social y
ecológica del Decreto 150 de 2026 (motivado por eventos hidrometeorológicos).

- **Sujeto pasivo:** personas jurídicas y sociedades de hecho contribuyentes de renta.
- **Hecho generador:** poseer al **1 de marzo de 2026** un patrimonio líquido ≥
  **200.000 UVT** (≈ $10.474.800.000).
- **Tarifas:** **0,5 %** general; **1,6 %** para los sectores financiero y minero-energético.
- **Base:** patrimonio fiscal, con exclusión del valor patrimonial neto de acciones o
  participaciones en sociedades nacionales (para evitar doble imposición).
- **No deducible** del impuesto de renta.

> **Cuidado en la entrevista:** es una norma de emergencia sujeta a control automático
> de constitucionalidad por la Corte Constitucional. Menciónalo como *"vigente al
> momento, pendiente/sujeto a control constitucional"* — demuestra que sigues la
> coyuntura y que eres prudente.

---

## 2.3 IVA

- **Tarifa general: 19 %.** Existen tarifas del 5 %, bienes/servicios **excluidos**
  (sin derecho a descontables) y **exentos** (tarifa 0 % **con** derecho a descontables).
- **Periodicidad** (art. 600 ET):
  - **Bimestral** si los ingresos brutos del año anterior fueron **≥ 92.000 UVT**, y
    para responsables de bienes exentos.
  - **Cuatrimestral** si fueron **< 92.000 UVT**.
- **IVA descontable y prorrateo:** si hay ingresos gravados y excluidos, el IVA común
  se prorratea. Una SaaS que exporta servicios necesita tener clarísima esta parte.
- **Exportación de servicios:** los servicios prestados desde Colombia y **utilizados
  exclusivamente en el exterior** por un contratante sin negocios en Colombia son
  **exentos** de IVA (art. 481 lit. c ET), sujetos al cumplimiento de requisitos
  formales (registro y contrato/declaración juramentada). Da derecho a **devolución de
  saldos a favor** — palanca de caja importante para una SaaS que vende afuera.
- **Servicios digitales desde el exterior** (art. 437 par. 2 ET): prestadores del
  exterior deben recaudar IVA, o se aplica **retención de IVA por parte del emisor del
  medio de pago**. Aplica al gasto de Magneto en AWS, Google, herramientas SaaS, etc.
- **ReteIVA:** 15 % general del IVA facturado (art. 437-2 ET); 100 % en pagos al exterior.

---

## 2.4 Retención en la fuente (renta)

Declaración **mensual**. Tarifas de referencia (verificar bases mínimas en UVT del año):

| Concepto | Tarifa |
|---|---|
| Compras generales (declarante) | 2,5 % |
| Compras generales (no declarante) | 3,5 % |
| Servicios generales (declarante) | 4 % |
| Servicios generales (no declarante) | 6 % |
| Honorarios y comisiones (persona jurídica) | 11 % |
| Honorarios (persona natural, según reglas) | 10 % / 11 % |
| Arrendamiento de bienes inmuebles | 3,5 % |
| Arrendamiento de bienes muebles | 4 % |
| Rendimientos financieros | 7 % |
| Pagos laborales | Procedimiento 1 o 2, tabla art. 383 ET |
| **Pagos al exterior — regla general** (art. 408 ET) | **20 %** |

**Pagos al exterior:** consultoría, servicios técnicos y asistencia técnica (prestados
en Colombia o desde el exterior) → 20 %. Regalías por explotación de intangibles → 20 %
(con reglas especiales para software). Antes de retener, verifica si hay
**convenio para evitar la doble imposición** (España, Chile, Canadá, México, Suiza,
Portugal, Reino Unido, Francia, Italia, Japón, entre otros) y la **Decisión 578 de la
CAN** para Bolivia, Ecuador y Perú. Requiere certificado de residencia fiscal.

**Presencia económica significativa (PES, art. 20-3 ET):** grava a no residentes que
venden bienes/servicios digitales a clientes en Colombia superando umbrales de ingresos
y de número de usuarios. Relevante como *contraparte* si Magneto vende a Colombia desde
una entidad del exterior — o si sus proveedores del exterior están sujetos.

---

## 2.5 ICA — Industria y Comercio (Medellín)

- Impuesto **municipal** sobre ingresos brutos por actividades industriales,
  comerciales y de servicios (Ley 14 de 1983; Ley 1819 de 2016 art. 343 fijó las
  **reglas de territorialidad**).
- **Regla clave de territorialidad para servicios:** el ingreso se grava en el
  municipio donde **se ejecuta** el servicio. Para servicios prestados por medios
  electrónicos, en el municipio donde el prestador tiene su sede/establecimiento.
  → **Esta es la pregunta difícil de una plataforma digital:** si Magneto atiende
  clientes en 20 municipios desde Medellín, ¿dónde tributa? Argumenta desde el art. 343
  y la existencia o no de establecimiento en cada municipio; menciona el riesgo de
  requerimientos de municipios que reclaman el ingreso.
- **Complementarios:** avisos y tableros (15 % del ICA), sobretasa bomberil.
- **Calendario de Medellín 2026** — Resolución 202550100057 del 9 de diciembre de 2025
  de la Secretaría de Hacienda:
  - **Régimen ordinario: declaración anual**, entre el **17 y el 30 de abril de 2026**,
    según el último dígito del NIT.
  - **Régimen simplificado: pagos bimestrales.**
  - **ReteICA: declaración y pago bimestral.**
- Cada municipio donde haya establecimiento exige **registro** (RIT o equivalente) y
  declaración propia. Bogotá, por ejemplo, es **bimestral**.

---

## 2.6 Precios de transferencia ⭐

El aviso lo menciona explícitamente, lo que confirma **operaciones con vinculadas del
exterior**. Marco: arts. **260-1 a 260-11 ET**, alineado con las Guías OCDE.

### ¿Quién está sujeto?
Contribuyentes del impuesto de renta que realicen operaciones con:
1. **Vinculados económicos del exterior**,
2. Vinculados ubicados en **zonas francas**,
3. Personas o entidades en **jurisdicciones no cooperantes, de baja o nula
   imposición, o regímenes tributarios preferenciales** (aquí la vinculación no
   se requiere: la sola operación obliga).

### Obligaciones formales (umbrales en UVT, verificar el decreto de plazos del año)

| Obligación | Umbral de referencia |
|---|---|
| **Declaración informativa** (Form. 120) | Patrimonio bruto ≥ **100.000 UVT** o ingresos brutos ≥ **61.000 UVT** al cierre |
| **Informe local** (Local File) | Además de lo anterior, operaciones **por tipo** ≥ **45.000 UVT** (≥ **10.000 UVT** con jurisdicciones no cooperantes) |
| **Informe maestro** (Master File) | Pertenecer a un grupo multinacional |
| **Informe país por país** (CbC) | Grupos multinacionales con ingresos consolidados ≥ **81.000.000 UVT** |

### Principio y métodos
Todo se mide contra el **principio de plena competencia** (*arm's length*): la
operación entre vinculadas debe pactarse como se habría pactado entre independientes.

Métodos (art. 260-3 ET):
1. **PC** — Precio comparable no controlado (CUP)
2. **PR** — Precio de reventa
3. **CA** — Costo adicionado (Cost Plus)
4. **MTU** — Márgenes transaccionales de utilidad de operación (TNMM) — *el más usado*
5. **PU** — Partición de utilidades (Profit Split)

Se selecciona el **método más apropiado**; el PC es de aplicación preferente cuando hay
comparables confiables. Se construye un **rango intercuartil** de comparables y se
verifica que el indicador de rentabilidad caiga dentro.

### El caso típico de una SaaS multinacional (prepara esta respuesta)

| Operación intragrupo | Método usual | Qué documentar |
|---|---|---|
| Servicios de desarrollo/soporte prestados por la filial colombiana a la matriz | **CA / TNMM** con margen sobre costos (*cost plus*, típicamente 5–10 %) | Base de costos, drivers, contrato intercompañía, evidencia de la prestación |
| Licencia de software o marca desde la matriz | **PC** o Profit Split | Regalía de mercado, propiedad del intangible, funciones DEMPE |
| Servicios administrativos compartidos (management fee) | **CA**, o el **safe harbour OCDE de servicios de bajo valor añadido** (costo + 5 %) | *Benefit test*: probar que el servicio se prestó y benefició a la filial |
| Préstamos intragrupo | **PC** (tasa de mercado) | Calificación crediticia implícita, plazo, moneda |

**Puntos que separan a un candidato bueno de uno excelente:**
- Hablar de **análisis funcional** (funciones, activos y riesgos) como el corazón del
  estudio, no del rango estadístico.
- Mencionar **DEMPE** (Development, Enhancement, Maintenance, Protection, Exploitation)
  para intangibles: quién crea valor decide quién se queda la utilidad residual.
- Recordar que la **deducción** de pagos a vinculados del exterior exige cumplir precios
  de transferencia y practicar la retención correspondiente, y que hay **límite a la
  deducción** de pagos a vinculados del exterior (art. 122 ET) y **subcapitalización**
  (art. 118-1 ET, relación deuda/patrimonio 2:1 con vinculados).
- **Sanciones** (art. 260-11 ET): por extemporaneidad, inconsistencias, omisión de
  información y por no presentar la documentación comprobatoria — son de las más
  costosas del ET, lo que justifica el control de vencimientos.

---

## 2.7 Facturación electrónica y documentos equivalentes

- **Resolución 000165 de 2023** consolidó el sistema de facturación.
- **Factura electrónica de venta** con validación previa DIAN (CUFE), representación
  gráfica y XML/UBL.
- **Documento soporte en adquisiciones con no obligados a facturar** — obligatorio para
  poder deducir el costo (incluye pagos a proveedores del exterior).
- **Nómina electrónica** — soporte de costos y deducciones laborales.
- **RADIAN** — registro de facturas como título valor.
- **Documento equivalente POS** con límites de valor.
- Control mensual imprescindible: **conciliar las ventas del ERP contra lo efectivamente
  validado por la DIAN**, y las notas crédito/débito. Es el control #1 que un auditor
  tributario mira.

---

## 2.8 Gestión de vencimientos y planeación

### Cómo lo diría un líder
> *"Manejo un calendario tributario único con dueño, fecha límite, fecha objetivo
> (siempre 3 días antes), estado y soporte de pago, revisado en comité de cierre. Cada
> obligación tiene un preparador y un revisor distintos, y el pago requiere doble
> aprobación en el portal bancario. Ninguna declaración se presenta el último día."*

### Planeación tributaria legítima (no evasión)
- Aprovechamiento de **exención de IVA en exportación de servicios** y solicitud de
  devolución de saldos a favor (efecto caja).
- **Descuento/deducción del ICA** pagado.
- **Beneficios por I+D+i** para el equipo de desarrollo (calificación MinCiencias).
- Optimización del **anticipo** y de las **autorretenciones** para no generar saldos a
  favor improductivos.
- **Monitoreo de la TTD del 15 %** durante el año, no en marzo del siguiente.
- Estructuración correcta de **operaciones intragrupo** con soporte de precios de
  transferencia desde el inicio, no a posteriori.

---

## 2.9 Firmeza, fiscalización y sanciones

| Concepto | Regla |
|---|---|
| **Firmeza general** (art. 714 ET) | 3 años desde el vencimiento del plazo para declarar (o desde la presentación si fue extemporánea) |
| Firmeza si se compensan o determinan **pérdidas fiscales** | 5 años |
| Firmeza para contribuyentes sujetos a **precios de transferencia** | 5 años |
| **Corrección** que aumenta impuesto (art. 588) | Dentro de 3 años, con sanción por corrección |
| **Corrección** que disminuye impuesto (art. 589) | Dentro del año siguiente al vencimiento |
| **Sanción por extemporaneidad** (art. 641) | 5 % del impuesto por mes o fracción (10 % si es después de emplazamiento) |
| **Sanción por corrección** (art. 644) | 10 % o 20 % del mayor valor |
| **Sanción por inexactitud** (art. 648) | 100 % de la diferencia (200 % en casos de abuso/omisión de activos) |
| **Sanción mínima** (art. 639) | 10 UVT |

**Ruta de fiscalización:** requerimiento ordinario de información → emplazamiento →
**requerimiento especial** (2 años desde el vencimiento) → respuesta (3 meses) →
**liquidación oficial de revisión** → recurso de reconsideración → contencioso
administrativo. Saber esta secuencia es lo que te vuelve el "punto de contacto para
auditorías tributarias" que pide el aviso.

---

## 2.10 Checklist de autoevaluación

- [ ] Sé el valor de la UVT 2026 y por qué importa.
- [ ] Puedo listar todas las obligaciones de la empresa con su periodicidad y autoridad.
- [ ] Entiendo la tasa mínima de tributación del 15 % y cómo monitorearla.
- [ ] Sé cuándo el IVA es bimestral vs cuatrimestral y por qué.
- [ ] Puedo explicar la exención de IVA en exportación de servicios y su efecto en caja.
- [ ] Sé argumentar dónde tributa ICA una plataforma digital.
- [ ] Conozco umbrales, formularios y métodos de precios de transferencia.
- [ ] Puedo describir la ruta de una fiscalización de la DIAN de principio a fin.
