# Módulo 08 — Formulario y glosario

Página de repaso final. Imprímela o léela el día antes.

---

## 8.1 Todas las fórmulas SaaS

### Ingresos recurrentes
```
ARR                  = MRR × 12

MRR final            = MRR inicio + New + Expansion + Reactivation
                                  − Contraction − Churned

Net New MRR          = New + Expansion + Reactivation − Contraction − Churned

ARPU / ARPA          = MRR total / Nº de cuentas activas
```

### Retención
```
Logo churn           = Clientes perdidos / Clientes al inicio

Gross revenue churn  = (Churned MRR + Contraction MRR) / MRR inicio

Net revenue churn    = (Churned + Contraction − Expansion) / MRR inicio

GRR                  = (MRR inicio − Churned − Contraction) / MRR inicio      ≤ 100 %

NRR / NDR            = (MRR inicio − Churned − Contraction + Expansion) / MRR inicio

Churn anualizado     = 1 − (1 − churn mensual)^12          ← NO se multiplica por 12

Vida media (meses)   = 1 / churn mensual
```

### Unit economics
```
CAC                  = Gasto S&M del periodo / Clientes nuevos del periodo

CAC payback (meses)  = CAC / (ARPA nuevos × Margen bruto %)

LTV                  = ARPA × Margen bruto % × (1 / churn mensual)

LTV : CAC            = LTV / CAC                            ← objetivo ≥ 3×

Margen bruto %       = (Ingresos − COGS) / Ingresos
```

### Eficiencia y caja
```
Rule of 40           = Crecimiento de ingresos YoY % + Margen EBITDA %

Magic Number         = (Ingreso trimestre − Ingreso trimestre anterior) × 4
                       ───────────────────────────────────────────────────
                              Gasto S&M del trimestre anterior

Net burn             = Salidas de caja − Entradas de caja (del mes)

Runway (meses)       = Caja disponible / Net burn mensual

Burn Multiple        = Net burn del periodo / Net new ARR del periodo
```

### El puente contable ⭐
```
Billings             = Ingreso reconocido + Δ Ingreso diferido

Ingreso diferido final = Ingreso diferido inicial + Billings − Ingreso reconocido

Ingreso NIIF 15 del mes = MRR de cierre
                          − efecto de prorrateo intramensual
                          + servicios no recurrentes reconocidos
                          ± diferencia por TRM
                          − créditos por SLA
```

### Capital de trabajo
```
DSO = (Cuentas por cobrar / Ingresos del periodo) × días del periodo
DPO = (Cuentas por pagar / Compras del periodo) × días del periodo
Ciclo de conversión de efectivo = DSO + DIO − DPO
```

---

## 8.2 Valores de referencia (benchmarks)

| Métrica | Malo | Aceptable | Bueno | Excelente |
|---|---|---|---|---|
| Margen bruto SaaS | < 60 % | 60–70 % | 70–80 % | > 80 % |
| NRR (SMB) | < 90 % | 90–100 % | 100–110 % | > 110 % |
| NRR (Enterprise) | < 100 % | 100–110 % | 110–120 % | > 120 % |
| GRR | < 80 % | 80–90 % | 90–95 % | > 95 % |
| Logo churn anual | > 30 % | 20–30 % | 10–20 % | < 10 % |
| LTV : CAC | < 1 | 1–3 | 3–5 | > 5 (ojo: puede ser subinversión) |
| CAC payback | > 24 m | 18–24 m | 12–18 m | < 12 m |
| Rule of 40 | < 20 | 20–40 | 40–60 | > 60 |
| Magic Number | < 0,5 | 0,5–0,75 | 0,75–1,0 | > 1,0 |
| Burn Multiple | > 2 | 1,5–2 | 1–1,5 | < 1 |
| Runway | < 6 m | 6–12 m | 12–18 m | > 18 m |

---

## 8.3 Datos fiscales clave — Colombia 2026

| Concepto | Valor / regla |
|---|---|
| **UVT 2026** | **$52.374** (Res. DIAN 000238 del 15-dic-2025) |
| Renta personas jurídicas | **35 %** (art. 240 ET) |
| Sobretasa entidades financieras | +5 pp (40 %), hasta año gravable 2027 |
| Tasa mínima de tributación (TTD) | **15 %** (art. 240 par. 6 ET) |
| Renta presuntiva | **0 %** desde 2021 |
| Compensación de pérdidas fiscales | 12 años (art. 147 ET) |
| Impuesto al patrimonio PJ 2026 (temporal) | Patrimonio líquido ≥ 200.000 UVT al 1-mar-2026; **0,5 %** general, **1,6 %** financiero y minero-energético (Dcto. Legislativo 173 de 2026) ⚠️ sujeto a control constitucional |
| IVA general | **19 %** |
| Periodicidad IVA | Bimestral si ingresos año anterior ≥ 92.000 UVT; cuatrimestral si < 92.000 UVT |
| Exportación de servicios | **Exenta** de IVA (art. 481 lit. c ET) → da derecho a devolución |
| ReteIVA | 15 % del IVA facturado; 100 % en pagos al exterior |
| ReteFuente servicios (declarante) | 4 % |
| ReteFuente honorarios PJ | 11 % |
| ReteFuente compras (declarante) | 2,5 % |
| ReteFuente arrendamiento inmuebles | 3,5 % |
| ReteFuente pagos al exterior (general) | **20 %** (art. 408 ET) |
| GMF | 4 × 1.000 |
| ICA Medellín — régimen ordinario | **Anual**, del 17 al 30 de abril de 2026 (Res. 202550100057 de 2025) |
| ReteICA Medellín | **Bimestral** |
| Firmeza general de la declaración | 3 años (art. 714 ET) |
| Firmeza con pérdidas o precios de transferencia | 5 años |
| Sanción mínima | 10 UVT |
| Sanción por inexactitud | 100 % de la diferencia (200 % en casos agravados) |
| Precios de transferencia — declaración informativa | Patrimonio bruto ≥ 100.000 UVT o ingresos ≥ 61.000 UVT |
| Precios de transferencia — informe local | Operaciones por tipo ≥ 45.000 UVT (≥ 10.000 UVT con jurisdicciones no cooperantes) |
| Informe país por país | Grupos con ingresos consolidados ≥ 81.000.000 UVT |
| Revisor fiscal obligatorio | Activos brutos > 5.000 SMMLV o ingresos brutos > 3.000 SMMLV (Ley 43 de 1990) |

> Verifica siempre contra el decreto de plazos del año y la resolución de calendario
> del Distrito de Medellín antes de usar una fecha concreta.

---

## 8.4 Normas NIIF que debes poder citar

| Norma | Tema | Por qué importa aquí |
|---|---|---|
| **NIIF 15** | Ingresos de contratos con clientes | **La norma del cargo**: suscripciones, ingresos diferidos, comisiones capitalizadas |
| NIIF 16 | Arrendamientos | Oficinas; sube el EBITDA y afecta el Rule of 40 |
| NIIF 9 | Instrumentos financieros | Cartera y deterioro esperado (ECL) |
| NIIF 2 | Pagos basados en acciones | Stock options y phantom shares |
| NIIF 8 | Segmentos de operación | Reporte por línea de negocio |
| NIC 1 | Presentación de EEFF | Juego completo y revelaciones |
| NIC 7 | Flujos de efectivo | Método directo e indirecto |
| NIC 8 | Políticas, estimaciones y errores | Reexpresión retroactiva |
| NIC 10 | Hechos posteriores | Ajustables vs no ajustables |
| NIC 12 | Impuesto a las ganancias | Impuesto diferido |
| NIC 19 | Beneficios a empleados | Prima, cesantías, vacaciones |
| NIC 21 | Moneda extranjera | Facturación en USD, moneda funcional |
| NIC 36 | Deterioro de activos | Software capitalizado y goodwill |
| NIC 37 | Provisiones y contingencias | Litigios y contingencias fiscales |
| NIC 38 + SIC-32 | Intangibles y sitios web | Capitalización de software |
| CINIIF 23 | Incertidumbre en tratamientos fiscales | Posiciones fiscales inciertas |

---

## 8.5 Glosario español – inglés

| Español | Inglés | Definición corta |
|---|---|---|
| Ingreso recurrente mensual | MRR (Monthly Recurring Revenue) | Ingreso recurrente normalizado a un mes |
| Ingreso recurrente anual | ARR | MRR × 12 |
| Ingreso diferido | Deferred revenue / Contract liability | Facturado y aún no reconocido |
| Activo del contrato | Contract asset | Reconocido y aún no facturable |
| Facturación del periodo | Billings | Ingreso + variación del ingreso diferido |
| Obligaciones pendientes | RPO (Remaining Performance Obligations) | Backlog contractual revelado por NIIF 15 párr. 120 |
| Obligación de desempeño | Performance obligation | Compromiso de transferir un bien o servicio distinto |
| Precio de venta independiente | Standalone selling price | Base de asignación del precio de la transacción |
| Contraprestación variable | Variable consideration | Overages, bonos, penalidades |
| Costo de adquisición de cliente | CAC | Gasto de S&M / clientes nuevos |
| Periodo de recuperación del CAC | CAC payback | Meses para recuperar el CAC con margen bruto |
| Valor de vida del cliente | LTV / CLV | Margen bruto acumulado esperado por cliente |
| Fuga de clientes | Logo churn | Clientes perdidos sobre clientes iniciales |
| Fuga de ingresos | Revenue churn | Ingreso perdido sobre ingreso inicial |
| Retención bruta de ingresos | GRR | Retención sin expansión |
| Retención neta de ingresos | NRR / NDR | Retención con expansión |
| Expansión | Expansion / Upsell | Aumento de ingreso en clientes existentes |
| Contracción | Contraction / Downgrade | Reducción de ingreso en clientes existentes |
| Margen bruto | Gross margin | (Ingresos − COGS) / Ingresos |
| Costo de servicio | COGS / Cost of revenue | Costo directo de prestar el servicio |
| Quema de caja | Burn rate | Caja consumida por periodo |
| Autonomía de caja | Runway | Meses de caja al ritmo actual de quema |
| Cascada de MRR | MRR bridge / waterfall | Descomposición del movimiento del MRR |
| Cohorte | Cohort | Grupo de clientes por mes de adquisición |
| Calidad de las utilidades | Quality of Earnings (QoE) | Análisis de sostenibilidad del resultado |
| Días de cartera | DSO | Días promedio de cobro |
| Días de pago | DPO | Días promedio de pago a proveedores |
| Estado de situación financiera | Statement of financial position | Balance |
| Estado de resultados | Income statement / P&L | |
| Papeles de trabajo | Workpapers | Soporte documental del cierre |
| Conciliación | Reconciliation | |
| Cierre contable | Financial close | |
| Devengo / causación | Accrual | |
| Corte | Cut-off | Asignación al periodo correcto |
| Análisis de variaciones | Flux analysis | |
| Segregación de funciones | Segregation of duties (SoD) | |
| Debida diligencia | Due diligence | |
| Precios de transferencia | Transfer pricing | |
| Plena competencia | Arm's length | |
| Informe local / maestro / país por país | Local File / Master File / CbCR | |

---

## 8.6 Repaso de 10 minutos (el día de la entrevista)

1. **MRR bridge:** inicio + new + expansion + reactivation − contraction − churn.
2. **GRR nunca pasa de 100 %; NRR sí.**
3. **Churn anualizado = 1 − (1 − mensual)^12.**
4. **LTV y CAC payback usan MARGEN BRUTO.**
5. **Billings = Ingreso + Δ Ingreso diferido.**
6. **El MRR es una foto; el ingreso es un flujo.** Por eso no cuadran, y por eso existe
   el puente.
7. **NIIF 15 en cinco pasos**, y el setup casi nunca es obligación separada.
8. **Comisiones de venta se capitalizan** (párr. 91) y se amortizan sobre la vida del cliente.
9. **UVT 2026 = $52.374; renta 35 %; IVA 19 %; pagos al exterior 20 %.**
10. **Precios de transferencia:** plena competencia, declaración informativa + informe
    local + informe maestro, método más apropiado, análisis funcional.

Y la frase con la que quieres que se queden:

> *"Mi trabajo no termina cuando el estado financiero cuadra. Termina cuando la gerencia
> puede tomar una decisión con él."*
