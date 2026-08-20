# Módulo 01 — NIIF, cierre y estados financieros

> Responsabilidad del aviso: *"Generar estados financieros bajo NIIF y reportes
> gerenciales con cierre mensual dentro de plazos definidos"* y *"asegurar la
> aplicación correcta del marco NIIF vigente"*.

---

## 1.1 El marco normativo colombiano

La convergencia arranca con la **Ley 1314 de 2009** y hoy se compila en el
**Decreto Único Reglamentario 2420 de 2015** (con sus decretos modificatorios
anuales). El **CTCP** (Consejo Técnico de la Contaduría Pública) propone y la
**Superintendencia** correspondiente vigila.

| Grupo | Marco aplicable | A quién aplica (regla general) |
|---|---|---|
| **1** | NIIF Plenas (Full IFRS) | Emisores de valores, entidades de interés público, y empresas grandes que cumplan tamaño + vinculación con el exterior o inversión extranjera |
| **2** | NIIF para las Pymes | Empresas que no clasifican en Grupo 1 ni 3 |
| **3** | Contabilidad simplificada | Microempresas |

**Para la entrevista:** una scaleup SaaS con inversión extranjera y matriz/filiales en
el exterior típicamente cae en **Grupo 1**, o migra a Grupo 1 cuando entra un fondo.
Buena respuesta: *"Confirmaría el grupo con base en la composición accionaria, el
tamaño y si hay obligación de reportar al grupo bajo NIIF plenas; y si la empresa está
en Grupo 2 pero el inversionista pide NIIF plenas, evaluaría el costo/beneficio de
migrar frente a llevar un paquete de conversión."*

Ojo con la distinción que casi siempre se pregunta:

- **Contabilidad financiera (NIIF)** → estados financieros.
- **Contabilidad fiscal (Estatuto Tributario)** → declaración de renta.
- El puente entre ambas es la **conciliación fiscal** (art. 772-1 ET, Formato 2516/2517),
  y de ahí sale el **impuesto diferido** (NIC 12).

---

## 1.2 Juego completo de estados financieros (NIC 1)

1. **Estado de situación financiera** (ESF) — corriente/no corriente.
2. **Estado de resultados y otro resultado integral** (ERI + ORI) — por función o por naturaleza.
3. **Estado de cambios en el patrimonio**.
4. **Estado de flujos de efectivo** (NIC 7) — método directo o indirecto.
5. **Notas**, incluidas políticas contables significativas y juicios (NIC 1 párr. 117 y ss.).
6. ESF de apertura del periodo comparativo más antiguo si hubo reexpresión (NIC 8).

**Detalle que suma puntos:** en Colombia se presenta bajo NIIF pero se *lleva* el
detalle en un plan de cuentas operativo. Explicar cómo mapeas el PUC operativo a la
vista gerencial SaaS (COGS / S&M / R&D / G&A) es exactamente lo que pide la
responsabilidad de "reportes gerenciales".

### El P&L de una SaaS (vista gerencial)

```
  Ingresos por suscripción (recurrente)
+ Ingresos por servicios (implementación, profesional)
= Ingresos totales
- Costo de servicio (COGS):
    · Hosting / cloud / infraestructura
    · Soporte al cliente y parte de Customer Success
    · Fees de pasarela de pago
    · Licencias de terceros embebidas en el producto
    · Amortización de software capitalizado
= MARGEN BRUTO  →  objetivo SaaS: 70–85 %
- Sales & Marketing (S&M)
- Research & Development (R&D)
- General & Administrative (G&A)
= EBITDA / Resultado operacional
```

Errores frecuentes que te pueden preguntar:
- Meter **todo** el equipo de Customer Success en COGS (parte es S&M si hace upsell).
- Dejar el hosting en gastos de administración → infla artificialmente el margen bruto.
- No amortizar contra COGS el software capitalizado.

---

## 1.3 NIIF 15 — Ingresos de contratos con clientes ⭐

**El tema central del cargo.** Los cinco pasos:

| Paso | Qué es | Trampa en SaaS |
|---|---|---|
| **1. Identificar el contrato** | Acuerdo con derechos exigibles, sustancia comercial y cobro probable | Contratos con renovación automática, órdenes de compra, términos y condiciones online |
| **2. Identificar las obligaciones de desempeño** | Bienes/servicios *distintos* | ¿La implementación/setup es distinta de la suscripción? Casi siempre **no** lo es si el cliente no puede beneficiarse de ella por separado |
| **3. Determinar el precio de la transacción** | Incluye contraprestación variable, componente financiero, descuentos | Overages por uso, créditos por SLA, descuentos escalonados, rappels |
| **4. Asignar el precio a las obligaciones** | En proporción al **precio de venta independiente** (standalone selling price) | Bundles plataforma + servicios; descuentos que hay que repartir |
| **5. Reconocer el ingreso** | Cuando (o a medida que) se satisface la obligación | SaaS = **a lo largo del tiempo**, normalmente lineal sobre el periodo de servicio |

### Los cinco casos SaaS que debes dominar

**(1) Suscripción anual facturada por anticipado**
Cliente paga $12.000.000 el 1 de enero por 12 meses.

```
1-ene   Cuentas por cobrar        12.000.000
            Ingreso diferido (pasivo del contrato)   12.000.000

31-ene  Ingreso diferido           1.000.000
            Ingreso por suscripción                   1.000.000     (y así 12 veces)
```

El ingreso diferido es un **pasivo de contrato**, corriente hasta 12 meses y no
corriente el excedente en contratos multianuales.

**(2) Setup / implementación no distinta**
Si el setup no tiene beneficio autónomo para el cliente, **no** es obligación separada:
su ingreso se difiere y se reconoce a lo largo del **periodo de beneficio esperado**
(que puede ser mayor al término contractual si hay renovaciones probables). Los costos
de ese setup se capitalizan como **costos de cumplimiento del contrato** (NIIF 15
párr. 95) y se amortizan en el mismo horizonte.

**(3) Comisiones de ventas — costos incrementales de obtener el contrato (párr. 91–94)**
Las comisiones pagadas *solo si se gana el contrato* se **capitalizan** como activo y
se amortizan sobre la vida esperada del cliente (no solo el año contratado). Excepción
práctica: amortización ≤ 12 meses se puede llevar a gasto directo (párr. 94).

> Esta es una pregunta favorita, porque conecta contabilidad con **CAC**: el CAC de la
> métrica usa el gasto de S&M del periodo (caja/devengo del periodo), mientras que la
> contabilidad puede estar capitalizando esa misma comisión. Saber explicar la
> diferencia es señal de nivel.

**(4) Contraprestación variable — overages y créditos por SLA**
Se estima por valor esperado o importe más probable, **limitada** para que no haya
reversión significativa (constraint, párr. 56). Los créditos por incumplimiento de SLA
se tratan como **reducción del precio de la transacción**, no como gasto.

**(5) Principal vs agente (párr. B34–B38)**
Si Magneto revende un servicio de un tercero (por ejemplo pruebas de talento de un
proveedor externo), la pregunta es si controla el servicio antes de transferirlo.
Principal → ingreso **bruto**. Agente → ingreso **neto** (solo la comisión).
Impacto directo en el ingreso reportado y en el margen bruto.

### Revelaciones que importan
- **RPO / obligaciones de desempeño pendientes** (párr. 120): monto del precio asignado
  a obligaciones no satisfechas y cuándo se reconocerá. Es el equivalente contable del
  *backlog* que mira un inversionista.
- Movimiento de saldos de contrato: ingreso diferido inicial → facturado → reconocido → final.

---

## 1.4 Otras normas críticas para una SaaS

### NIC 38 + SIC-32 — Software desarrollado internamente
- **Fase de investigación** → siempre gasto.
- **Fase de desarrollo** → se **capitaliza** solo si se cumplen los **seis criterios**
  del párr. 57: viabilidad técnica, intención de completar, capacidad de usar/vender,
  generación de beneficios futuros probables, disponibilidad de recursos, y capacidad
  de medir el desembolso con fiabilidad.
- **SIC-32** regula costos de sitio web con lógica análoga.
- Amortización: vida útil estimada (típico 3–5 años), contra **COGS** si el software es
  el producto.
- **Al revés (muy preguntado):** los costos de *configurar y personalizar* un SaaS de
  terceros que la empresa **usa** (no vende) generalmente **son gasto**, no activo,
  según la decisión de agenda del IFRIC de 2021 — porque no se controla el software.

### NIIF 16 — Arrendamientos
Oficinas y equipos generan **activo por derecho de uso** y **pasivo por arrendamiento**
descontado a la tasa incremental de endeudamiento. Excepciones: plazo ≤ 12 meses y
activos de bajo valor. Efecto colateral: sube el EBITDA (la renta deja de ser gasto
operativo y pasa a depreciación + interés) — relevante para el **Rule of 40**.

### NIIF 9 — Instrumentos financieros
- Clasificación de cuentas por cobrar a costo amortizado.
- **Deterioro por pérdida crediticia esperada (ECL)**: para cuentas comerciales se usa
  el **enfoque simplificado** con una **matriz de provisiones** por antigüedad
  (ej. 0–30 días 0,5 %; 31–60 2 %; 61–90 10 %; >90 40 %; >180 100 %), calibrada con
  la experiencia histórica y ajustada por expectativas futuras.
- Para SaaS: la mora suele preceder al churn, así que la matriz de provisión y la curva
  de churn deberían conversar.

### NIC 12 — Impuesto diferido
Diferencias temporarias típicas en una SaaS colombiana:

| Partida | Contable | Fiscal | Efecto |
|---|---|---|---|
| Ingreso diferido | Pasivo, se reconoce en el tiempo | Puede gravarse al facturar | Activo por impuesto diferido |
| Software capitalizado | Activo amortizable | Deducción distinta / inmediata | Pasivo por impuesto diferido |
| Provisión de cartera (ECL) | Gasto ahora | Deducible al cumplir requisitos del ET | Activo por impuesto diferido |
| Pérdidas fiscales | — | Compensables (12 años, art. 147 ET) | Activo por impuesto diferido, **solo si es probable** que haya renta futura |
| NIIF 16 | ROU + pasivo | Canon deducible | Diferido neto |

### NIIF 2 — Pagos basados en acciones
Stock options y phantom shares son habituales en startups. Liquidados en instrumentos
de patrimonio → se mide al valor razonable **en la fecha de concesión** y se reconoce
gasto durante el periodo de irrevocabilidad. Liquidados en efectivo (phantom) → pasivo
remedido en cada cierre.

### NIC 21 — Moneda extranjera
Si Magneto factura en USD: definir **moneda funcional**, registrar a TRM de la
transacción, remedir partidas monetarias a TRM de cierre y llevar la diferencia en
cambio a resultados. Consecuencia para métricas: **el MRR se suele reportar en USD
constante** mientras el ingreso contable va a TRM variable — esa es una de las
partidas del puente del módulo 04.

### Otras
- **NIC 37** provisiones y contingencias (litigios laborales, sanciones).
- **NIC 10** hechos posteriores al periodo (ajustables vs no ajustables).
- **NIC 19** beneficios a empleados (prima, cesantías, vacaciones — devengo mensual).
- **NIC 8** políticas, cambios en estimaciones y corrección de errores.

---

## 1.5 El cierre mensual: cómo diseñarlo

El aviso pide "cierre mensual dentro de plazos definidos". Ten un **calendario de
cierre** listo para dibujar en la entrevista.

### Cronograma tipo (objetivo: cerrar en 5 días hábiles)

| Día | Actividades | Responsable |
|---|---|---|
| **D-3 a D-0** | Corte de facturación, corte de compras, recordatorio de legalización de gastos y anticipos | Analistas + Compras |
| **D+1** | Cargue de extractos bancarios y conciliación; cierre de tesorería; cierre de nómina | Analista tesorería |
| **D+2** | Motor de reconocimiento de ingresos; conciliación *billing ↔ ERP*; facturación electrónica cuadrada con DIAN; cálculo de ingreso diferido | Analista de ingresos |
| **D+3** | Provisiones y devengos (accruals), depreciación/amortización, deterioro de cartera (ECL), diferencia en cambio, impuestos del mes | Analistas |
| **D+4** | Conciliación de auxiliares contra mayor (*subledger tie-out*), revisión de cuentas de balance, análisis de variaciones (flux) contra mes anterior y presupuesto | Líder |
| **D+5** | Estados financieros, reporte gerencial, MRR bridge conciliado, cierre del periodo en el sistema, carpeta de cierre archivada | Líder |

### Controles de cierre que debes nombrar
- **Balance sheet reconciliations**: cada cuenta de balance tiene un dueño, un soporte
  y una fecha; ninguna partida conciliatoria envejece más de 60 días.
- **Flux analysis**: explicar toda variación > X % o > $Y contra mes anterior y presupuesto.
- **Cut-off**: pruebas de corte de ingresos y de gastos alrededor del último día.
- **Four-eyes**: quien prepara un asiento no lo aprueba.
- **Journal entry review**: revisión obligatoria de asientos manuales, especialmente
  los de fin de mes, los de importe redondo y los que tocan ingresos.
- **Carpeta de cierre (close binder)**: un legajo por mes con todos los soportes,
  listo para auditoría — esto responde directo a la responsabilidad de "soporte
  documental de cada asiento contable".

### KPIs del propio cierre
Días hasta cierre · número de asientos post-cierre (*post-close adjustments*) ·
% de conciliaciones automáticas · antigüedad de partidas conciliatorias ·
% de asientos manuales sobre el total.

---

## 1.6 Checklist de autoevaluación

- [ ] Puedo explicar los 5 pasos de NIIF 15 con un contrato SaaS real.
- [ ] Sé decidir si un setup es obligación de desempeño separada y justificarlo.
- [ ] Sé cuándo se capitaliza una comisión de ventas y por cuánto tiempo se amortiza.
- [ ] Distingo capitalizar software propio (NIC 38) de configurar un SaaS de terceros (gasto).
- [ ] Sé armar una matriz de provisión ECL.
- [ ] Puedo listar las 5 diferencias temporarias más comunes de una SaaS.
- [ ] Tengo dibujado un calendario de cierre de 5 días con responsables y controles.
