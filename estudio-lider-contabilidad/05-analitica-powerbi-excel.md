# Módulo 05 — Analítica, Power BI y Excel avanzado

> Responsabilidad del aviso: *"Traducir la información contable en insights accionables
> para la gerencia (rentabilidad por línea de negocio o producto, análisis de costos,
> comportamiento de márgenes, flujo de caja proyectado)"*, con **Power BI**, **Excel
> avanzado** y **analítica avanzada** entre los conocimientos técnicos exigidos.

---

## 5.1 El principio: primero el dato, después el tablero

El error más común es empezar por los gráficos. El orden correcto es:

1. **Definiciones firmadas.** ¿Qué es un "cliente activo"? ¿Cuándo un cliente cuenta
   como churn: al no renovar, al vencer el servicio, o al cancelar? Sin esto, cada
   área trae un número distinto y el tablero pierde credibilidad en la primera reunión.
2. **Fuente única de verdad.** Contabilidad manda en el ingreso; el sistema de billing
   manda en las suscripciones; el CRM manda en el pipeline. Nadie más publica cifras.
3. **Modelo de datos.** Esquema estrella, no hojas sueltas.
4. **Métricas calculadas en el modelo**, no en el visual.
5. **Tablero**, al final.

---

## 5.2 Modelo de datos: esquema estrella

**Tablas de hechos** (una fila por evento, granularidad definida):

| Tabla | Grano | Campos clave |
|---|---|---|
| `fct_Asientos` | Un movimiento contable | Fecha, CuentaKey, CentroCostoKey, TerceroKey, Débito, Crédito |
| `fct_MRR` | Foto mensual por suscripción | FechaKey, ClienteKey, PlanKey, MRR |
| `fct_MovimientoMRR` | Un movimiento del bridge | FechaKey, ClienteKey, TipoMovimiento, Valor |
| `fct_Facturas` | Una factura/línea | Fecha, ClienteKey, Valor, IVA, IngresoDiferido |
| `fct_Recaudos` | Un pago recibido | Fecha, ClienteKey, FacturaKey, Valor |

**Tablas de dimensión:**
`dim_Fecha` (calendario completo y marcado como tabla de fechas) · `dim_Cliente`
(segmento, industria, ciudad, cohorte de alta) · `dim_Plan` · `dim_Cuenta` (con
jerarquía contable **y** el mapeo a la vista gerencial COGS/S&M/R&D/G&A) ·
`dim_CentroCosto` · `dim_Producto`.

**Reglas que un entrevistador valora:**
- Relaciones **uno a muchos** desde dimensión hacia hecho, en **una sola dirección**.
- Nunca relaciones muchos-a-muchos si se puede evitar; nunca filtros bidireccionales
  "por si acaso".
- **`dim_Fecha` propia**, generada, no derivada de la fecha del hecho.
- La `dim_Cuenta` es donde vive el **mapeo PUC → vista gerencial**: así el mismo asiento
  alimenta los estados financieros NIIF y el P&L SaaS sin doble contabilidad.

> **El truco profesional del MRR bridge:** no intentes calcular New/Expansion/
> Contraction/Churn con DAX comparando fotos. Calcúlalo en el **ETL** (Power Query o
> SQL), comparando la foto del mes N con la del mes N-1 por cliente, y materializa
> `fct_MovimientoMRR`. El DAX queda trivial, el resultado es auditable y puedes
> conciliarlo contra contabilidad. Decir esto en la entrevista demuestra que ya lo
> hiciste antes.

Lógica del ETL, por cliente, comparando mes N-1 vs N:

| MRR mes N-1 | MRR mes N | Tipo de movimiento | Valor |
|---|---|---|---|
| 0 | > 0 (y nunca antes tuvo) | New | MRR_N |
| 0 | > 0 (y tuvo antes) | Reactivation | MRR_N |
| > 0 | > MRR_N-1 | Expansion | MRR_N − MRR_N-1 |
| > 0 | < MRR_N-1, pero > 0 | Contraction | MRR_N − MRR_N-1 |
| > 0 | 0 | Churn | − MRR_N-1 |

---

## 5.3 DAX esencial

### Conceptos que debes poder explicar
- **Medida vs columna calculada:** la columna se evalúa fila a fila al refrescar y ocupa
  memoria; la medida se evalúa en el contexto del visual. **Casi todo debe ser medida.**
- **Contexto de filtro vs contexto de fila.**
- **`CALCULATE`** es la única función que *modifica* el contexto de filtro. Es el corazón de DAX.
- **`DIVIDE(a, b)`** en lugar de `a / b`: maneja la división por cero.
- **Time intelligence** requiere una `dim_Fecha` marcada como tabla de fechas y continua.

### Medidas base

```dax
MRR = SUM ( fct_MRR[MRR] )

MRR Cierre =
CALCULATE ( [MRR], LASTDATE ( dim_Fecha[Fecha] ) )

MRR Mes Anterior =
CALCULATE ( [MRR Cierre], DATEADD ( dim_Fecha[Fecha], -1, MONTH ) )

ARR = [MRR Cierre] * 12
```

### Componentes del bridge (sobre `fct_MovimientoMRR`)

```dax
New MRR =
CALCULATE ( SUM ( fct_MovimientoMRR[Valor] ),
            fct_MovimientoMRR[TipoMovimiento] = "New" )

Expansion MRR =
CALCULATE ( SUM ( fct_MovimientoMRR[Valor] ),
            fct_MovimientoMRR[TipoMovimiento] = "Expansion" )

Contraction MRR =
CALCULATE ( SUM ( fct_MovimientoMRR[Valor] ),
            fct_MovimientoMRR[TipoMovimiento] = "Contraction" )

Churned MRR =
CALCULATE ( SUM ( fct_MovimientoMRR[Valor] ),
            fct_MovimientoMRR[TipoMovimiento] = "Churn" )

Net New MRR = [New MRR] + [Expansion MRR] + [Contraction MRR] + [Churned MRR]
```
*(Contraction y Churn se almacenan con signo negativo, por eso se suman.)*

### Retención

```dax
GRR % =
DIVIDE (
    [MRR Mes Anterior] + [Contraction MRR] + [Churned MRR],
    [MRR Mes Anterior]
)

NRR % =
DIVIDE (
    [MRR Mes Anterior] + [Expansion MRR] + [Contraction MRR] + [Churned MRR],
    [MRR Mes Anterior]
)

Gross Revenue Churn % =
DIVIDE ( - ( [Contraction MRR] + [Churned MRR] ), [MRR Mes Anterior] )

Churn Anualizado % =
1 - POWER ( 1 - [Gross Revenue Churn %], 12 )
```

### Unit economics

```dax
Gasto S&M = CALCULATE ( [Gasto], dim_Cuenta[VistaGerencial] = "S&M" )

Clientes Nuevos =
CALCULATE ( DISTINCTCOUNT ( fct_MovimientoMRR[ClienteKey] ),
            fct_MovimientoMRR[TipoMovimiento] = "New" )

CAC = DIVIDE ( [Gasto S&M], [Clientes Nuevos] )

Margen Bruto % = DIVIDE ( [Ingresos] - [COGS], [Ingresos] )

ARPA Nuevos = DIVIDE ( [New MRR], [Clientes Nuevos] )

CAC Payback (meses) = DIVIDE ( [CAC], [ARPA Nuevos] * [Margen Bruto %] )

LTV = DIVIDE ( [ARPA] * [Margen Bruto %], [Gross Revenue Churn %] )

LTV a CAC = DIVIDE ( [LTV], [CAC] )
```

### Comparativos y eficiencia

```dax
Ingresos AA = CALCULATE ( [Ingresos], SAMEPERIODLASTYEAR ( dim_Fecha[Fecha] ) )

Crecimiento YoY % = DIVIDE ( [Ingresos] - [Ingresos AA], [Ingresos AA] )

Rule of 40 = [Crecimiento YoY %] + [Margen EBITDA %]

Magic Number =
VAR IngTrimActual   = [Ingresos]
VAR IngTrimAnterior = CALCULATE ( [Ingresos], DATEADD ( dim_Fecha[Fecha], -1, QUARTER ) )
VAR SMTrimAnterior  = CALCULATE ( [Gasto S&M], DATEADD ( dim_Fecha[Fecha], -1, QUARTER ) )
RETURN
DIVIDE ( ( IngTrimActual - IngTrimAnterior ) * 4, SMTrimAnterior )
```

### Cohortes
Añade a `dim_Cliente` la columna `CohorteAlta` (mes de la primera suscripción) y crea
una medida de **meses de vida**:

```dax
Meses Desde Alta =
DATEDIFF ( MAX ( dim_Cliente[FechaAlta] ), MAX ( dim_Fecha[Fecha] ), MONTH )

Retención de Cohorte % =
VAR MRRInicialCohorte =
    CALCULATE ( [MRR Cierre],
        ALLEXCEPT ( dim_Cliente, dim_Cliente[CohorteAlta] ),
        dim_Fecha[Fecha] = MAX ( dim_Cliente[FechaAlta] ) )
RETURN
DIVIDE ( [MRR Cierre], MRRInicialCohorte )
```
Se visualiza como matriz: **filas = cohorte, columnas = meses desde el alta**, con
formato condicional de escala de color.

---

## 5.4 Excel avanzado — lo que realmente se usa

### Power Query (la parte que más rinde)
Es el ETL dentro de Excel. Úsalo para:
- Cargar extractos bancarios de varios bancos con formatos distintos y **unificarlos**
  (carpeta como origen: `Origen → Carpeta`).
- Traer el auxiliar del ERP y **transformarlo sin tocar el original** (pasos
  reproducibles, refresco de un clic).
- **Conciliación automática**: dos consultas (contabilidad y banco), `Combinar
  consultas → Anti-unión` para aislar las partidas conciliatorias de cada lado.
- Anular dinamización (*unpivot*) de reportes que vienen con meses en columnas.

> Si automatizas la conciliación bancaria con Power Query, pasas de horas a minutos.
> Es el ejemplo de automatización más concreto y creíble que puedes dar en la entrevista.

### Funciones y patrones

| Uso | Función |
|---|---|
| Búsqueda moderna, con valor si no encuentra | `XLOOKUP` |
| Sumas condicionales multi-criterio | `SUMIFS`, `COUNTIFS`, `SUMPRODUCT` |
| Filtrar y ordenar dinámicamente | `FILTER`, `SORT`, `UNIQUE`, `SEQUENCE` |
| Legibilidad de fórmulas largas | `LET` |
| Funciones propias sin VBA | `LAMBDA` (+ `MAP`, `REDUCE`, `SCAN`) |
| Modelo de datos y medidas DAX dentro de Excel | **Power Pivot** |
| Escenarios | `Buscar objetivo`, `Administrador de escenarios`, tabla de datos de 2 variables |

Ejemplo de `LET` + `LAMBDA` para churn anualizado reutilizable:
```excel
=LAMBDA(churn_mensual; 1 - (1 - churn_mensual)^12)
```
(guardado en el Administrador de nombres como `ChurnAnual`, se usa `=ChurnAnual(2%)`).

### Higiene de modelos financieros
- Una hoja por función: **entradas → cálculos → salidas**. Nunca mezclar.
- **Convención de colores**: azul = dato duro de entrada, negro = fórmula,
  verde = referencia a otra hoja. Es un estándar y los auditores lo esperan.
- Sin números "quemados" dentro de fórmulas.
- Controles de cuadre visibles (`= 0` en rojo/verde) en cada bloque.
- Documentar supuestos en la misma hoja, no en un correo.

---

## 5.5 Flujo de caja

### Los dos métodos
- **Indirecto** (para los EEFF, NIC 7): parte de la utilidad y ajusta partidas que no
  son caja (depreciación, provisiones, diferencia en cambio) y variaciones de capital
  de trabajo.
- **Directo** (para gestión): entradas y salidas reales. Es el que sirve para operar.

### Proyección rodante de 13 semanas (*13-week cash flow*)
El estándar de tesorería en empresas en crecimiento. Estructura:

```
Semana                        S1   S2   S3  ...  S13
Caja inicial
+ Recaudo de cartera (por antigüedad y probabilidad de cobro)
+ Nuevos cobros de suscripción (según renovaciones programadas)
+ Otros ingresos (devoluciones de saldos a favor de IVA, financiación)
− Nómina y seguridad social
− Proveedores (según condiciones y días de pago)
− Impuestos (según el calendario tributario)
− Arriendos, cloud, licencias
= Flujo neto
= Caja final          →  y el saldo mínimo de seguridad como línea de alerta
```
Se **rueda cada semana** (se corre una semana y se agrega una nueva) y se hace
**backtesting**: proyectado vs real de la semana anterior, con explicación de la
desviación. Ese backtesting es lo que convierte la proyección en una herramienta
confiable en vez de un ejercicio.

### Drivers de capital de trabajo
```
DSO (días de cartera)   = (Cuentas por cobrar / Ingresos del periodo) × días
DPO (días de pago)      = (Cuentas por pagar / Compras del periodo) × días
Ciclo de conversión de efectivo = DSO + DIO − DPO
```
En SaaS el DSO baja mucho con **domiciliación / pago con tarjeta automática**, y la
facturación anual anticipada puede llevar el capital de trabajo a **negativo**
(el cliente financia la operación) — que es una de las virtudes financieras del modelo
y algo que conviene saber explicar.

---

## 5.6 Rentabilidad por línea y análisis de costos

Lo que pide el aviso como "insights accionables":

1. **Contribución por plan/producto:** ingreso − COGS directo asignable. Requiere
   asignar el costo de cloud por producto (etiquetado de recursos en AWS/GCP) y el
   costo de soporte por volumen de tickets.
2. **Rentabilidad por segmento de cliente:** SMB vs mid-market vs enterprise, con su
   CAC, su margen y su costo de servir. Es común descubrir que un segmento entero
   destruye valor.
3. **Rentabilidad por cliente (top 20):** concentración de ingreso y riesgo.
4. **Análisis de costos:** fijos vs variables, costo por usuario activo, costo de cloud
   por transacción o por consulta de IA — este último crítico si el producto usa
   modelos de lenguaje.
5. **Bridge de márgenes:** descomponer la variación del margen bruto en efecto
   **precio**, efecto **volumen**, efecto **mezcla** y efecto **costo**. Un análisis de
   este tipo, bien hecho, vale más que veinte gráficos.

---

## 5.7 El tablero gerencial: qué debe tener

| Bloque | Contenido |
|---|---|
| **Encabezado** | ARR, crecimiento YoY, NRR, margen bruto, EBITDA, runway — seis números y nada más |
| **Crecimiento** | MRR bridge en cascada, net new MRR por mes, ARR por segmento |
| **Retención** | GRR, NRR, logo churn, matriz de cohortes |
| **Eficiencia** | CAC, CAC payback, LTV:CAC, Magic Number, Burn Multiple, Rule of 40 |
| **P&L** | Real vs presupuesto vs año anterior, con bridge de variaciones |
| **Caja** | Saldo, net burn, runway, proyección 13 semanas, DSO y cartera por antigüedad |
| **Conciliación** | Puente MRR → ingreso NIIF 15 y roll-forward de ingreso diferido |

Reglas de diseño: una pregunta por visual · comparativo siempre (vs plan, vs mes
anterior, vs año anterior) · la fecha de actualización y la fuente visibles · y un
**diccionario de métricas** enlazado desde el propio tablero.

---

## 5.8 Checklist de autoevaluación

- [ ] Sé diseñar un esquema estrella para datos contables y de suscripción.
- [ ] Explico por qué el MRR bridge se calcula en el ETL y no en DAX.
- [ ] Escribo de memoria las medidas de MRR, NRR, GRR, CAC y Rule of 40.
- [ ] Sé automatizar una conciliación bancaria con Power Query.
- [ ] Puedo construir un flujo de caja rodante de 13 semanas y hacerle backtesting.
- [ ] Sé descomponer una variación de margen en precio, volumen, mezcla y costo.
- [ ] Puedo listar los seis números que van en el encabezado del tablero gerencial.
