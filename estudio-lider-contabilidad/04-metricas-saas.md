# Módulo 04 — Métricas y unit economics SaaS ⭐

> Responsabilidad del aviso: *"Conocer, calcular y operar las métricas clave del modelo
> de negocio SAAS, conciliándolas con la información contable, y ponerlas a disposición
> de la gerencia como insumo para la toma de decisiones."*
>
> Y el **rol del cargo**: *"traducir estas métricas en tableros y análisis financieros
> que conecten la contabilidad con el desempeño comercial y de producto, trabajando de
> la mano con FP&A, Producto y Revenue."*

**Este es el módulo que te consigue el puesto.** Contadores que sepan NIIF hay muchos;
contadores que puedan sentarse con el CRO y explicarle por qué su MRR no cuadra con el
ingreso del estado de resultados, muy pocos.

---

## 4.1 Ingresos recurrentes: MRR y ARR

### Definiciones
- **MRR (Monthly Recurring Revenue):** ingreso recurrente **normalizado a un mes** de
  todas las suscripciones activas a una fecha. Es una **foto**, no un flujo del periodo.
- **ARR (Annual Recurring Revenue):** MRR × 12. En empresas con contratos anuales se
  calcula directo sobre el valor anualizado del contrato.

### Normalización (la parte que se equivoca todo el mundo)

| Situación | Cómo entra al MRR |
|---|---|
| Plan mensual de $500.000 | $500.000 |
| Plan anual de $6.000.000 pagado por anticipado | $500.000/mes (se divide en 12, no se cuenta el pago) |
| Contrato de 3 años por $21.600.000 | $600.000/mes |
| Implementación de $5.000.000 (una sola vez) | **$0** — no es recurrente |
| Overage por uso variable | Depende de la política: si es recurrente y predecible, se incluye normalizado; si es errático, se excluye y se reporta aparte |
| Descuento promocional de 3 meses | MRR neto del descuento durante la promoción |
| IVA facturado | **$0** — el MRR es neto de impuestos |

**Regla de oro:** el MRR debe reflejar el **valor contractual recurrente vigente hoy**,
neto de descuentos e impuestos, sin importar cómo o cuándo se factura o se cobra.

### El MRR bridge (waterfall) — la herramienta central

```
MRR inicio
  + New MRR            (clientes nuevos)
  + Expansion MRR      (upsell, cross-sell, upgrade de plan, más asientos)
  + Reactivation MRR   (clientes que habían churneado y vuelven)
  − Contraction MRR    (downgrade, reducción de asientos)
  − Churned MRR        (clientes que se van por completo)
= MRR final
```

Cada componente debe ser rastreable a nivel de cliente y suscripción. Si un cliente
sube y otro baja el mismo mes, **no se netean**: uno va a Expansion y el otro a
Contraction. Netearlos destruye la capacidad de diagnóstico.

---

## 4.2 Retención: churn, GRR y NRR

| Métrica | Fórmula | Qué mide |
|---|---|---|
| **Logo churn** | Clientes perdidos / clientes al inicio | Cuántos clientes se van |
| **Gross revenue churn** | (Churned MRR + Contraction MRR) / MRR inicio | Cuánto ingreso se pierde de la base |
| **Net revenue churn** | (Churn + Contraction − Expansion) / MRR inicio | Pérdida neta; **puede ser negativa** (bueno) |
| **GRR** (Gross Revenue Retention) | (MRR inicio − Churn − Contraction) / MRR inicio | Retención **sin** contar expansión. **Nunca supera 100 %** |
| **NRR / NDR** (Net Revenue Retention) | (MRR inicio − Churn − Contraction + Expansion) / MRR inicio | Retención **con** expansión. Puede superar 100 % |

**Convenciones que debes declarar antes de calcular** (y que un entrevistador puede
usar para probarte):
- La **reactivación** normalmente **no** entra en NRR, porque NRR mide qué pasa con una
  cohorte de clientes existentes, no con clientes que ya no estaban.
- NRR se suele medir **anual** (MRR de la misma cohorte hoy vs hace 12 meses), no mensual.
- Si logo churn < revenue churn, **se te están yendo los clientes grandes** o hay
  downgrades. Si logo churn > revenue churn, se van los pequeños. Ese contraste es el
  insight, no el número aislado.

**Anualización de un churn mensual:** no se multiplica por 12.

```
churn anual = 1 − (1 − churn mensual)^12
```
Ejemplo: 2 % mensual → 1 − 0,98^12 = **21,5 %** anual (no 24 %).

### Referencias de mercado (para contextualizar, no para citar como dogma)

| Segmento | NRR sano | Logo churn anual |
|---|---|---|
| SMB / self-serve | 90–105 % | 15–40 % |
| Mid-market | 100–115 % | 10–20 % |
| Enterprise | 110–130 % | 5–10 % |

---

## 4.3 Unit economics: ARPU, CAC, LTV

### ARPU / ARPA
```
ARPU = MRR total / número de cuentas (o usuarios) activos
```
Se lee siempre **por segmento y por plan**, porque el promedio global esconde mezcla:
el ARPU puede subir solo porque murieron clientes pequeños.

### CAC (Customer Acquisition Cost)
```
CAC = Gasto total de Ventas y Marketing del periodo / Nº de clientes nuevos del periodo
```
- **Blended CAC:** todo el S&M (incluye orgánico y marca).
- **Paid CAC:** solo el gasto de adquisición pagada.
- El S&M debe incluir salarios, comisiones, herramientas y publicidad — **no solo el
  ad spend**. Aquí está el choque clásico con Marketing.
- **Desfase temporal:** el gasto de hoy trae clientes en 2–3 meses. Un CAC calculado
  mes contra mes es ruidoso; usa el gasto rezagado o promedios trimestrales.
- **Puente con contabilidad:** las comisiones de venta pueden estar **capitalizadas**
  bajo NIIF 15 párr. 91. El CAC de la métrica usa el gasto *incurrido*; el P&L muestra
  el gasto *amortizado*. Debes poder explicar la diferencia.

### CAC Payback
```
CAC Payback (meses) = CAC / (ARPA de clientes nuevos × Margen bruto %)
```
Meses que tarda el margen bruto de un cliente en devolver lo que costó adquirirlo.
Referencia: **< 12 meses excelente, 12–18 aceptable, > 24 problemático**.
Se calcula con **margen bruto**, no con ingreso — omitirlo es el error más común.

### LTV (Lifetime Value)
```
Vida media del cliente (meses) = 1 / churn mensual
LTV = ARPA × Margen bruto % × (1 / churn mensual)
```
- Usa **margen bruto**, no ingreso.
- Usa el churn **de ingresos** si quieres capturar contracciones y expansiones;
  usa **logo churn** si quieres el valor de un cliente "promedio". Declara cuál usas.
- Versión más fina: descontar el flujo (LTV con tasa de descuento) y limitar el
  horizonte a 3–5 años, porque proyectar 10 años con un churn de hoy es fantasía.
- **LTV:CAC ≥ 3×** es la referencia clásica. Un ratio de 8× no es "mejor": suele
  significar **subinversión en crecimiento**.

---

## 4.4 Margen bruto SaaS

```
Margen bruto % = (Ingresos − COGS) / Ingresos
```

**Qué va en COGS** (ver también módulo 01, sección 1.2):
hosting e infraestructura cloud · soporte al cliente · la porción de Customer Success
dedicada a servicio (no a upsell) · fees de pasarela de pago · licencias de terceros
embebidas en el producto · amortización del software capitalizado · costos de entrega
de servicios profesionales.

**Qué NO va:** desarrollo de nuevas funcionalidades (R&D), ventas, marketing, back office.

Referencia: **75–85 %** en SaaS puro; baja al 60–70 % si hay mucho servicio profesional
o si el producto es intensivo en cómputo (por ejemplo, **IA generativa**, donde el costo
de inferencia es COGS real y variable — punto muy pertinente para Magneto).

Analiza siempre el margen bruto **separando suscripción de servicios**: la suscripción
puede estar al 85 % y los servicios al 20 %, y el promedio no dice nada.

---

## 4.5 Eficiencia de crecimiento

### Rule of 40
```
Rule of 40 = Crecimiento de ingresos YoY (%) + Margen EBITDA (o FCF) (%)
```
≥ 40 se considera saludable. Declara siempre **qué margen** usas (EBITDA, FCF o
margen operativo) y **qué crecimiento** (ARR o ingreso reconocido): cambia el resultado
varios puntos.

### Magic Number
```
Magic Number = (Ingreso del trimestre − Ingreso del trimestre anterior) × 4
               ─────────────────────────────────────────────────────────────
                       Gasto de S&M del trimestre anterior
```
Mide cuánto ARR nuevo genera cada peso invertido en ventas y marketing, con el rezago
de un trimestre.
- **> 1,0** → la máquina comercial funciona: invierte más.
- **0,5 – 1,0** → zona de ajuste.
- **< 0,5** → no escales el gasto comercial hasta arreglar la eficiencia.

### Burn rate y runway
```
Gross burn  = Total de salidas de caja operativas del mes
Net burn    = Gross burn − entradas de caja del mes
Runway      = Caja disponible / Net burn mensual  (meses)
```
Regla práctica de una startup: **nunca bajar de 12 meses de runway** sin un plan de
financiación activo.

### Burn Multiple
```
Burn Multiple = Net burn del periodo / Net new ARR del periodo
```
Cuánta caja se quema por cada peso de ARR nuevo. **< 1 excelente · 1–1,5 bueno ·
1,5–2 aceptable · > 2 alarma.** Es hoy la métrica preferida de los inversionistas
porque combina crecimiento y eficiencia en un solo número.

---

## 4.6 Cohortes

Una **cohorte** agrupa clientes por el mes/trimestre en que se adquirieron y sigue su
comportamiento en el tiempo. Es la única forma honesta de ver si el producto mejora.

**Ejemplo — retención de ingresos por cohorte (% del MRR inicial de la cohorte):**

| Cohorte | Mes 0 | Mes 3 | Mes 6 | Mes 9 | Mes 12 |
|---|---|---|---|---|---|
| 2024-Q3 | 100 % | 94 % | 92 % | 94 % | 97 % |
| 2024-Q4 | 100 % | 95 % | 94 % | 96 % | 100 % |
| 2025-Q1 | 100 % | 97 % | 97 % | 101 % | 106 % |
| 2025-Q3 | 100 % | 98 % | 100 % | 104 % | — |

**Cómo se lee:**
1. **Verticalmente** (mismo mes de vida, distintas cohortes): las cohortes recientes
   retienen mejor → el producto y el onboarding están mejorando. Ese es el hallazgo.
2. **Horizontalmente:** la "curva sonrisa" — cae al inicio por churn temprano y luego
   sube porque la expansión de los que quedan supera las pérdidas. Cuando la curva
   vuelve a cruzar el 100 %, tienes **NRR > 100 %** estructural.
3. Un churn temprano alto (mes 1–3) casi siempre es un problema de **onboarding o de
   calificación del lead**, no de producto.

También se hacen cohortes de **recuperación de CAC**, **conversión de trial a pago** y
**expansión por segmento**.

---

## 4.7 EJEMPLO NUMÉRICO COMPLETO ⭐

*SaaS B2B colombiana. Datos de marzo de 2026. Cifras en COP. Haz los cálculos tú
primero, tapando la columna de resultados.*

### Datos de entrada

**MRR bridge de marzo**

| Componente | Valor |
|---|---|
| MRR inicio (1-mar) | 500.000.000 |
| + New MRR | 16.000.000 |
| + Expansion MRR | 14.000.000 |
| − Contraction MRR | (3.000.000) |
| − Churned MRR | (7.000.000) |
| **= MRR final (31-mar)** | **520.000.000** |

**Clientes:** 1.000 al inicio · 32 nuevos · 12 perdidos · **1.020 al cierre**

**Estado de resultados de marzo**

| Línea | Valor | % |
|---|---|---|
| Ingreso por suscripción reconocido | 510.000.000 | |
| Ingreso por servicios profesionales | 35.000.000 | |
| **Ingresos totales** | **545.000.000** | 100 % |
| COGS | (136.250.000) | 25 % |
| **Margen bruto** | **408.750.000** | **75 %** |
| S&M | (160.000.000) | 29,4 % |
| R&D | (190.000.000) | 34,9 % |
| G&A | (110.000.000) | 20,2 % |
| **EBITDA** | **(51.250.000)** | **−9,4 %** |

**Otros datos:** ARR a marzo de 2025 = $4.200.000.000 · Ingreso Q1-2026 = $1.600.000.000 ·
Ingreso Q4-2025 = $1.450.000.000 · S&M Q4-2025 = $450.000.000 · Caja = $1.800.000.000 ·
Net burn mensual = $60.000.000

### Resultados

| Métrica | Cálculo | Resultado | Lectura |
|---|---|---|---|
| **ARR** | 520.000.000 × 12 | **$6.240.000.000** | |
| **Net new MRR** | 16 + 14 − 3 − 7 | **+$20.000.000** (4,0 % m/m) | ≈ 60 % anualizado |
| **ARPU** | 520.000.000 / 1.020 | **$509.804** | |
| **ARPA nuevos** | 16.000.000 / 32 | **$500.000** | Los nuevos entran ligeramente por debajo del promedio |
| **Logo churn mensual** | 12 / 1.000 | **1,2 %** → 13,5 % anual | |
| **Gross revenue churn** | (7 + 3) / 500 | **2,0 %** → 21,5 % anual | > logo churn ⇒ se van clientes **grandes** o hay downgrades ⚠️ |
| **Net revenue churn** | (7 + 3 − 14) / 500 | **−0,8 %** | Expansión neta positiva |
| **GRR** | (500 − 3 − 7) / 500 | **98,0 %** | Sólido |
| **NRR** | (500 − 3 − 7 + 14) / 500 | **100,8 %** | Típico de SMB; lejos del 115 % enterprise |
| **Margen bruto** | 408,75 / 545 | **75,0 %** | En rango, con margen de mejora |
| **CAC** | 160.000.000 / 32 | **$5.000.000** | |
| **CAC payback** | 5.000.000 / (500.000 × 0,75) | **13,3 meses** | Aceptable; objetivo < 12 |
| **LTV** (churn de ingresos) | 509.804 × 0,75 / 0,02 | **$19.117.650** | |
| **LTV:CAC** | 19.117.650 / 5.000.000 | **3,8×** | Sano (≥ 3×) |
| **LTV:CAC** (con logo churn 1,2 %) | 31.862.750 / 5.000.000 | **6,4×** | ⚠️ **Mismo negocio, número muy distinto** |
| **Crecimiento ARR YoY** | 6.240 / 4.200 − 1 | **48,6 %** | |
| **Rule of 40** | 48,6 + (−9,4) | **39,2** | A un punto del umbral |
| **Magic Number** | (1.600 − 1.450) × 4 / 450 | **1,33** | > 1 ⇒ hay espacio para invertir más en S&M |
| **Runway** | 1.800 / 60 | **30 meses** | Cómodo |
| **Burn Multiple** (Q1) | 180 / 600 | **0,30** | Excelente (< 1) |

### El insight que entregarías a gerencia

> *"El negocio crece al 49 % anual con un Burn Multiple de 0,30 y un Magic Number de
> 1,33: la máquina comercial es eficiente y hay caja para acelerar. Los dos focos son:
> **(1)** el gross revenue churn (2,0 % mensual) es mayor que el logo churn (1,2 %),
> lo que significa que estamos perdiendo o reduciendo cuentas grandes — hay que abrir
> el churn por segmento antes de invertir más en adquisición; **(2)** el CAC payback
> de 13,3 meses y el NRR de 100,8 % indican que el crecimiento depende demasiado de
> clientes nuevos y poco de la base instalada. Subir el NRR a 110 % vale más que bajar
> el CAC, porque además nos pondría por encima del Rule of 40 sin quemar más caja."*

Fíjate en la forma: **número → diagnóstico → decisión.** Así es como el aviso quiere
que "pongas las métricas a disposición de la gerencia".

---

## 4.8 CONCILIACIÓN MRR ↔ INGRESO NIIF 15 ⭐⭐

**Esta es la pregunta que define la entrevista.** El MRR y el ingreso del estado de
resultados casi nunca coinciden, y saber por qué es exactamente lo que pide el aviso
al decir *"conciliándolas con la información contable"*.

### Por qué difieren

| Causa | Efecto |
|---|---|
| **Prorrateo intramensual** | Un cliente que entra el día 20 aporta MRR completo a la foto de cierre, pero solo 1/3 de mes de ingreso |
| **MRR es una foto, el ingreso es un flujo** | MRR = saldo al 31; ingreso = lo devengado del 1 al 31 |
| **Servicios no recurrentes** | Implementación, capacitación, consultoría: son ingreso NIIF 15 pero **no** entran al MRR |
| **Setup diferido** | Un setup no distinto se difiere en el periodo de beneficio: genera ingreso contable sin MRR asociado |
| **Facturación anticipada** | No afecta el ingreso reconocido; sí afecta caja e ingreso diferido |
| **Contratos multianuales** | El MRR normaliza a mes; el reconocimiento sigue el patrón de transferencia del servicio |
| **Moneda extranjera** | El MRR suele reportarse a **TRM constante/presupuestada**; la contabilidad va a TRM real (NIC 21) |
| **Créditos por SLA y descuentos retroactivos** | Reducen el precio de la transacción (menos ingreso) pero no siempre se reflejan en el MRR |
| **Impuestos** | El MRR es neto de IVA; la facturación es bruta |
| **Principal vs agente** | Reventa de terceros: el MRR puede ir bruto y el ingreso NIIF 15 neto |

### Puente formal (marzo de 2026, del ejemplo anterior)

| Concepto | Valor |
|---|---|
| MRR al cierre (31-mar) | 520.000.000 |
| (−) Efecto de prorrateo de altas, bajas y cambios ocurridos dentro del mes | (10.000.000) |
| **= Ingreso de suscripción reconocido en el mes** | **510.000.000** |
| (+) Servicios profesionales e implementación reconocidos | 35.000.000 |
| (+/−) Diferencia por TRM entre MRR a tasa presupuestada e ingreso a TRM real | — |
| (−) Créditos por SLA otorgados en el mes | — |
| **= Ingreso NIIF 15 del periodo (ERI)** | **545.000.000** |

Esta tabla debería ser un **entregable mensual estándar**, firmado por Contabilidad y
aceptado por Revenue y FP&A. Cuando existe, se acaban las discusiones de "tus números
no cuadran con los míos".

### Ingreso diferido: el roll-forward

| Concepto | Valor |
|---|---|
| Ingreso diferido inicial (1-mar) | 2.400.000.000 |
| (+) Facturación del mes (billings) | 700.000.000 |
| (−) Ingreso reconocido en el mes | (545.000.000) |
| **= Ingreso diferido final (31-mar)** | **2.555.000.000** |

De aquí sale la identidad que **siempre** debes poder recitar:

```
Billings = Ingreso reconocido + Δ Ingreso diferido
700 = 545 + (2.555 − 2.400) = 545 + 155  ✓
```

**Diagnóstico rápido con esta identidad:**
- Ingreso diferido **crece** más rápido que el ingreso → se está vendiendo más y/o
  con más contratos anuales prepagados. **Señal positiva** de crecimiento futuro.
- Ingreso diferido **cae** mientras el ingreso se sostiene → las renovaciones no están
  entrando; el ingreso de los próximos meses va a caer. **Alerta temprana**, y una de
  las cosas más valiosas que Contabilidad puede aportar a gerencia.

### RPO / backlog
**NIIF 15 párr. 120** exige revelar el precio asignado a las **obligaciones de
desempeño pendientes** y cuándo se espera reconocerlas. Ese RPO es, en la práctica, el
**backlog contractual**: incluye lo facturado y aún no reconocido (ingreso diferido)
**más** lo contratado y aún no facturado. Es el puente entre el lenguaje del
inversionista y el de la nota a los estados financieros.

---

## 4.9 Errores clásicos (que un entrevistador usa como trampa)

1. Calcular **LTV con ingreso** en vez de margen bruto.
2. **Anualizar el churn multiplicando por 12.**
3. Netear expansión y contracción en el MRR bridge.
4. Meter ingresos de una sola vez (implementación) en el ARR → infla el *run-rate* y
   es lo primero que castiga un *Quality of Earnings*.
5. Calcular CAC solo con el gasto publicitario, sin salarios ni comisiones.
6. Comparar el CAC de un mes con los clientes de ese mismo mes, ignorando el rezago.
7. Reportar NRR incluyendo reactivaciones.
8. Presentar un ARPU global cuando el negocio tiene segmentos con economía distinta.
9. Decir "MRR" cuando en realidad se está reportando facturación (**billings**) del mes.
10. Dejar hosting fuera de COGS y presumir un margen bruto del 90 %.

---

## 4.10 Checklist de autoevaluación

- [ ] Puedo dibujar un MRR bridge de memoria con sus seis componentes.
- [ ] Sé normalizar al MRR un contrato anual, uno trianual y una implementación.
- [ ] Distingo GRR de NRR y sé por qué GRR nunca supera 100 %.
- [ ] Sé anualizar correctamente un churn mensual.
- [ ] Calculo CAC, CAC payback, LTV y LTV:CAC usando margen bruto.
- [ ] Sé qué va y qué no va en el COGS de una SaaS.
- [ ] Calculo Rule of 40, Magic Number, runway y Burn Multiple.
- [ ] **Puedo explicar en 2 minutos por qué el MRR no es igual al ingreso NIIF 15.**
- [ ] Recito la identidad `Billings = Ingreso + Δ Ingreso diferido` y sé qué diagnostica.
- [ ] Sé leer una tabla de cohortes vertical y horizontalmente.
