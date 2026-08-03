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

## Fase 4 — Causación de Gastos: CXP Cuenta 23

| Proceso | Responsable | Frecuencia |
|---|---|---|
| Causa todos los documentos a pagar, siempre con factura electrónica | **Luis Amador** (Siigo) | Continuo |
| Registra el gasto y deja la **CXP del proveedor en Cuenta 23** | **Luis Amador** (Siigo) | Continuo |
| La CXP Cuenta 23 queda visible en Siigo para que Isnardi sepa qué pagar | Siigo (automático) | — |

## Fase 5 — Pagos: Recibo de Pago (RP)

| Proceso | Responsable | Frecuencia |
|---|---|---|
| Busca el proveedor en Siigo — el sistema muestra la CXP Cuenta 23 pendiente | **Isnardi Sanches** (Siigo) | Según vencimiento |
| Selecciona la CXP, elige de dónde sale el dinero y el medio de pago | **Isnardi Sanches** (Siigo) | Según vencimiento |
| Genera el **RP (Recibo de Pago)** — registra salida de dinero y medio de pago | **Isnardi Sanches** (Siigo) | Según vencimiento |

## Fase 6 — Conciliación Bancaria

| Proceso | Responsable | Frecuencia |
|---|---|---|
| Realiza las conciliaciones bancarias de todos los meses | **Luis Amador** | Mensual |
| Valida la conciliación bancaria | **Cristian Leonardo** | Mensual |

## Fase 7 — Nómina y Seguridad Social

| Proceso | Responsable | Frecuencia |
|---|---|---|
| Genera la nómina mensual | **Luis Amador** | Mensual |
| Elabora la comparativa de nómina | **Luis Amador** | Mensual |
| Valida la nómina y la seguridad social | **Cristian Leonardo** | Mensual |

## Fase 8 — Informes y Reportes a Socios

| Proceso | Responsable | Frecuencia |
|---|---|---|
| Genera informe detallado de socios — archivo Excel | **Cristian Leonardo** | Mensual |
| Elabora el dashboard integral completo para junta de socios | **Cristian Leonardo** | Mensual |

## Fase 9 — Obligaciones Fiscales · Revisoría Fiscal

| Proceso | Responsable | Frecuencia |
|---|---|---|
| Liquidación retención en la fuente | **Cristian Leonardo** → Revisoría Fiscal | Mensual |
| Declaración de IVA bimestral | **Cristian Leonardo** → Revisoría Fiscal | Bimestral |
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
| **RADIAN** | Registro DIAN de facturas electrónicas | Siigo → DIAN (automático) |

---

## Calendario Fiscal 2026 — Fechas Clave Recurrentes

| Fecha | Proceso | Responsable |
|---|---|---|
| Día 1+ (continuo) | RC: cobros en caja/bancos · RP: pagos a proveedores | Isnardi Sanches |
| Día 5 de cada mes | Revisión RADIAN | Luis Amador |
| Día 10 de cada mes | Inicio conciliación bancaria (mes anterior) | Luis Amador |
| Día 12 de cada mes | Retención en la fuente (mes anterior) | Cristian Leonardo |
| **Enero, Marzo, Mayo, Julio, Septiembre, Noviembre** | Declaración IVA bimestral | Cristian Leonardo |
| Día 20 de cada mes | Nómina mensual + comparativa | Luis Amador |
| Día 22 de cada mes | Validación conciliación + nómina + seguridad social | Cristian Leonardo |
| Día 28 de cada mes | Informe socios Excel + Dashboard junta | Cristian Leonardo |
| **Marzo** | Información exógena municipal (anual) | Cristian Leonardo |
| **Abril** | Declaración ICA (anual) | Cristian Leonardo |
| **31 Diciembre** | Cierre contable anual — todos los módulos | Cristian Leonardo |
