# Procesos Contables IES — 2026
**ERP:** Siigo | **Sistema fiscal:** DIAN / RADIAN

## Equipo

| Integrante | Rol |
|---|---|
| Beatriz | Insumos Facturación |
| Edgar Metatute | Automatización / Siigo (Externo) |
| Isnardi Sanches | Tesorera |
| Luis Amador | Aux. Contable |
| Cristian Leonardo | Contador |

---

## Fase 1 — Facturación Electrónica

| Proceso | Responsable | Frecuencia |
|---|---|---|
| Prepara insumos: cantidades, valores y tipos de productos/servicios | **Beatriz** | Periódico |
| Organiza el archivo plano a partir del insumo de Beatriz | **Edgar Metatute** (Siigo) | Periódico |
| Procesa y emite las facturas electrónicas desde Siigo ERP | **Edgar Metatute** (Siigo) → **FE** | Automático |
| Siigo envía automáticamente a la DIAN — registro en **RADIAN** | Siigo → DIAN | Automático |

## Fase 2 — Ingresos: Recibo de Caja (RC)

| Proceso | Responsable | Frecuencia |
|---|---|---|
| El cliente paga — Isnardi recibe el dinero en caja o bancos | **Isnardi Sanches** | Según ocurra |
| Genera el **RC (Recibo de Caja)** en Siigo — registra el ingreso en contabilidad | **Isnardi Sanches** (Siigo) | Diario |
| Selecciona las facturas correspondientes → baja la cartera del cliente | **Isnardi Sanches** (Siigo) | Mismo acto |

## Fase 3 — Control RADIAN / DIAN

| Proceso | Responsable | Frecuencia |
|---|---|---|
| Revisa el RADIAN: documentos registrados ante la DIAN que no están en el radar | **Luis Amador** | Mensual |
| Cruza información RADIAN vs. sistema — actúa como filtro de control | **Luis Amador** | Mensual |
| Identifica y gestiona documentos faltantes o no conciliados | **Luis Amador** | Mensual |
| Revisa el RADIAN del período del mes: facturas electrónicas emitidas en la segunda quincena que deben quedar registradas ante la DIAN antes del cierre — cualquier documento faltante o inconsistente se gestiona de inmediato | **Luis Amador** | Días **20–25** |
| Valida desde la perspectiva contable el RADIAN del período del mes — verifica la consistencia de los documentos registrados y da el visto bueno para proceder con el archivo plano del ciclo de facturación siguiente | **Cristian Leonardo** | Días **20–25** |
| Con la revisión del RADIAN finalizada y el visto bueno del Contador, genera y desarrolla el archivo plano para que la facturación electrónica del primer día del próximo mes salga sin demoras — se entrega a Edgar para procesar en Siigo | **Luis Amador** → Edgar Metatute | Días **25–30** |

## Fase 4 — Causación de Gastos: CXP Cuenta 23 / Anticipo Cuenta 13

| Proceso | Responsable | Frecuencia |
|---|---|---|
| Revisa el RADIAN y causa cada documento: con **FE (Factura Electrónica)** para costo/gasto, o con **Documento Soporte** cuando no existe FE | **Luis Amador** (Siigo) | Continuo |
| Registra el gasto y crea la **CXP del proveedor en Cuenta 23** — queda pendiente de pago | **Luis Amador** (Siigo) | Continuo |
| La CXP Cuenta 23 queda visible en Siigo — Isnardi consulta qué pagar, a quién y cuánto | Siigo → **Isnardi Sanches** | Automático |
| Si Isnardi debe pagar sin soporte documental: registra el desembolso como **Anticipo en Cuenta 13** (no como gasto directo) | **Isnardi Sanches** (Siigo) | Según ocurra |
| Cuando llega la FE o cuenta de cobro: Luis la causa y **cruza la CXP Cuenta 23 contra el Anticipo Cuenta 13** — las cuentas se saldan | **Luis Amador** (Siigo) | Según ocurra |
| Garantiza que **todas las causaciones del mes** queden registradas en Siigo antes del cierre: revisa CXP pendientes, documentos por cruzar y cualquier FE no causada — nada puede quedar abierto para el siguiente período | **Luis Amador** (Siigo) | Días **25–30** |

### Documento Soporte — Proveedores del Exterior (Invoice)

| Proceso | Responsable | Frecuencia |
|---|---|---|
| A lo largo del mes llegan facturas (**invoice**) de proveedores extranjeros que no emiten FE colombiana — el único documento habilitante para generar el **Documento Soporte (DS)** ante la DIAN es el invoice recibido; cotización, contrato o proyecto **no son válidos** como soporte | Proveedores del exterior | Continuo |
| En cuanto llega el invoice, genera el **Documento Soporte** en Siigo: causa el gasto y crea la **CXP del proveedor en Cuenta 23** — el DS vincula el invoice con el registro contable ante la DIAN | **Luis Amador** (Siigo) | Continuo |
| Revisión conjunta al cierre del mes: verifica que cada invoice del exterior recibido en el período tenga su Documento Soporte generado y su causación completa en Siigo — ningún proveedor extranjero puede quedar sin causar al cierre | **Luis Amador** + **Cristian Leonardo** | Días **25–30** |
| Da el visto bueno contable a la causación de proveedores del exterior: verifica consistencia de los Documentos Soporte, los invoice asociados y las CXP generadas | **Cristian Leonardo** | Días **25–30** |

## Fase 5 — Pagos: Recibo de Pago (RP)

| Proceso | Responsable | Frecuencia |
|---|---|---|
| Busca el proveedor en Siigo — el sistema muestra la CXP Cuenta 23 pendiente | **Isnardi Sanches** (Siigo) | Según vencimiento |
| Selecciona la CXP, elige de dónde sale el dinero y el medio de pago | **Isnardi Sanches** (Siigo) | Según vencimiento |
| Genera el **RP (Recibo de Pago)** — registra salida de dinero y medio de pago | **Isnardi Sanches** (Siigo) | Según vencimiento |

## Fase 6 — Conciliación Bancaria

| Proceso | Responsable | Ventana |
|---|---|---|
| Los extractos bancarios llegan (bancos, caja, tarjeta de crédito) | Bancos externos → **Luis Amador** | Días **3–6** |
| Inicia la conciliación: extracto vs. libro contable, saldo caja, movimientos tarjeta | **Luis Amador** | Días **3–9** |
| Genera el documento formal de conciliación con diferencias, ajustes y saldos definitivos | **Luis Amador** | Días **7–9** |
| Valida los saldos contables y da el visto bueno — cierre de la conciliación | **Cristian Leonardo** | Días **7–9** |

## Fase 7 — Nómina y Seguridad Social

### 1ª Quincena — pago día 15

| Proceso | Responsable | Ventana |
|---|---|---|
| Proyecta y causa la nómina — valida deducciones: préstamos, embargos y descuentos | **Luis Amador** (Siigo) | Días **10–14** |
| Elabora el comparativo de nómina y valida novedades del período | **Luis Amador** | Días **10–14** |
| Realiza el desembolso de la primera quincena | **Isnardi Sanches** | Día **15** |

### 2ª Quincena — pago día 30

| Proceso | Responsable | Ventana |
|---|---|---|
| Proyecta y causa la nómina — valida deducciones: préstamos, embargos y descuentos | **Luis Amador** (Siigo) | Días **25–29** |
| Elabora el comparativo de nómina y valida novedades del período | **Luis Amador** | Días **25–29** |
| Realiza el desembolso de la segunda quincena | **Isnardi Sanches** | Día **30** |

### Seguridad Social — mensual

| Proceso | Responsable | Ventana |
|---|---|---|
| Causa la seguridad social del mes anterior (salud, pensión, ARL, caja de compensación) | **Luis Amador** (Siigo) | Días **10–13** |
| Valida la nómina y la seguridad social antes del desembolso | **Cristian Leonardo** | Días **10–13** |
| Recibe el soporte y realiza el pago a las entidades correspondientes | **Isnardi Sanches** | Días **13–15** |

## Fase 8 — Informes y Reportes a Socios

### 8.1 Flujo de Efectivo — insumo base para el dashboard

| Proceso | Responsable | Ventana |
|---|---|---|
| Descarga el documento de flujo de efectivo directamente desde Siigo ERP y organiza el archivo clasificando los movimientos por tipo de actividad: operación, inversión y financiación | **Cristian Leonardo** (Siigo) | Días **10–11** |
| Valida los terceros involucrados en cada transacción y verifica la coherencia entre la data descargada de Siigo y los registros del libro mayor — cualquier diferencia se investiga y ajusta antes de continuar | **Cristian Leonardo** | Días **11–12** |
| Con la data validada, genera la estructura y los datos fuente que alimentarán el componente de flujo de efectivo dentro del dashboard de socios | **Cristian Leonardo** | Día **12** |

### 8.2 Cartera y Recaudo — análisis de cobro y antigüedad

| Proceso | Responsable | Ventana |
|---|---|---|
| Genera el informe de cartera desglosado por vigencias: corriente, vencida a +30 días, +60 días, +90 días y saldos de años anteriores — permite identificar el nivel de riesgo de incobrabilidad según la antigüedad de cada saldo | **Cristian Leonardo** | Día **12** |
| Consolida la cartera por tercero con vista desplegable: una fila por cliente con el total acumulado que al expandirse muestra el detalle de cada factura pendiente — facilita el seguimiento individual y la gestión de cobro cliente a cliente | **Cristian Leonardo** | Día **12** |
| Construye el análisis de recaudo del mes: cuánto se cobró durante el período y de qué antigüedad proviene ese cobro — corriente, +30 días, +60 días, +90 días y años anteriores | **Cristian Leonardo** | Días **12–13** |
| El análisis de recaudo evidencia el comportamiento real del proceso de cobro en el mes: qué vigencias respondieron, cuáles siguen represadas y cómo evolucionó la recuperación frente a períodos anteriores | **Cristian Leonardo** | Días **12–13** |

### 8.3 Estados Financieros — desarrollo y validación contra Siigo

| Proceso | Responsable | Ventana |
|---|---|---|
| Desarrolla el Estado de Situación Financiera (Balance General) con corte al cierre del mes: activo corriente y no corriente, pasivo corriente y no corriente, y patrimonio | **Cristian Leonardo** | Días **12–13** |
| Valida que los valores totales del EESF sean estrictamente consistentes con el reporte generado en Siigo ERP — solo cuando los saldos cuadran al centavo se procede a estructurar el informe para el dashboard | **Cristian Leonardo** (Siigo) | Días **12–13** |
| Desarrolla el Estado de Resultados del período: ingresos operacionales, costos de ventas, gastos operacionales y no operacionales, hasta llegar a la utilidad neta del mes | **Cristian Leonardo** | Días **12–13** |
| Valida que los totales del Estado de Resultados sean consistentes con el informe de Siigo — con los valores conciliados, estructura el layout final para el dashboard | **Cristian Leonardo** (Siigo) | Días **12–13** |

### 8.4 Dashboard Integral — construcción, entrega y proceso con socios

| Proceso | Responsable | Ventana |
|---|---|---|
| Con todos los insumos validados — flujo de efectivo, cartera por vigencias, análisis de recaudo, EESF y Estado de Resultados — construye el dashboard integral en formato ejecutivo para la junta de socios | **Cristian Leonardo** | Días **13–14** |
| Entrega el informe completo a Don Edgar (Gerente) para revisión y apertura del proceso formal con los socios — punto de partida del análisis ejecutivo | **Cristian Leonardo** | Día **15** |
| Acompaña el proceso completo con los socios: revisión del informe, análisis de resultados del mes y cierre de la sesión de gestión — fecha límite de entrega definitiva | **Cristian Leonardo** | Días **15–20** |

## Fase 9 — Obligaciones Fiscales · Revisoría Fiscal

| Proceso | Responsable | Frecuencia |
|---|---|---|
| Liquidación retención en la fuente | **Cristian Leonardo** → Revisoría Fiscal | Mensual (vence días 15–21) |
| Declaración de IVA bimestral | **Cristian Leonardo** → Revisoría Fiscal | Bimestral (Ene, Mar, May, Jul, Sep, Nov) |
| Declaración ICA | **Cristian Leonardo** → Revisoría Fiscal | Anual (Abril) |
| Información exógena municipal | **Cristian Leonardo** → Revisoría Fiscal | Anual (Marzo) |
| Otros requerimientos fiscales | **Cristian Leonardo** | Según aplique |

---

## Documentos Clave

| Sigla | Documento | Quien lo genera |
|---|---|---|
| **FE** | Factura Electrónica | Edgar Metatute (Siigo) |
| **RC** | Recibo de Caja | Isnardi Sanches |
| **RP** | Recibo de Pago | Isnardi Sanches |
| **CXP 23** | Cuenta por Pagar — Cuenta Contable 23 | Luis Amador (causación) |
| **ANT 13** | Anticipo — Cuenta Contable 13 | Isnardi Sanches (pago sin soporte) |
| **RADIAN** | Registro DIAN de facturas electrónicas | Siigo → DIAN (automático) |
| **DS** | Documento Soporte — compra a proveedor sin FE colombiana (exterior / régimen simplificado) · solo se genera con el invoice | Luis Amador (Siigo) |

---

## Calendario Fiscal 2026 — Carga Real por Franja de Días

| Días | Proceso | Responsable |
|---|---|---|
| Día 1+ (continuo) | RC: cobros en caja/bancos · RP: pagos y anticipos Cta. 13 | Isnardi Sanches |
| Días 3–6 | Llegan extractos bancarios → inicio conciliación bancaria | Luis Amador |
| Días 7–9 | Validación saldos + visto bueno conciliación bancaria | Cristian Leonardo |
| Días 10–13 | Causación seguridad social → soporte a Tesorería para pago | Luis Amador |
| Días 10–14 | Nómina 1ª quincena: proyección, causación y comparativa | Luis Amador |
| Día 12 | Retención en la fuente (mes anterior) | Cristian Leonardo |
| Días 10–13 | Insumos socios: flujo de efectivo · cartera por vigencias · recaudo · EESF · E.Resultados — todo validado contra Siigo | Cristian Leonardo |
| Días 13–15 | Pago seguridad social a entidades | Isnardi Sanches |
| Día 15 | Pago nómina 1ª quincena · Entrega informe a Don Edgar (Gerente) | Isnardi + Cristian |
| **Ene, Mar, May, Jul, Sep, Nov** | Declaración IVA bimestral (vence días 15–21) | Cristian Leonardo |
| Días 15–20 | Proceso completo con socios + dashboard junta | Cristian Leonardo |
| Días 20–25 | RADIAN período del mes — revisión (Luis) y validación contable (Cristian) | Luis Amador + Cristian Leonardo |
| Días 25–29 | Nómina 2ª quincena: proyección, causación y comparativa | Luis Amador |
| Días 25–30 | Causaciones cierre mes garantizadas + archivo plano facturación día 1 | Luis Amador |
| Día 30 | Pago nómina 2ª quincena | Isnardi Sanches |
| **Marzo** | Información exógena municipal (anual) | Cristian Leonardo |
| **Abril** | Declaración ICA (anual) | Cristian Leonardo |
| **31 Diciembre** | Cierre contable anual — todos los módulos | Cristian Leonardo |
