# Módulo 07 — Banco de preguntas de entrevista

Las preguntas marcadas con **⭐** son las de mayor probabilidad y mayor impacto: si solo
tienes una hora, practica esas doce.

**Cómo responder:** usa siempre la estructura **definición → cómo lo calculo o lo hago →
qué decisión habilita → ejemplo de mi experiencia**. Para preguntas de comportamiento,
usa **STAR** (Situación, Tarea, Acción, Resultado) y cierra con un número.

---

## A. NIIF y reconocimiento de ingresos

**A1. ⭐ Explícame cómo reconoces el ingreso de una suscripción anual pagada por anticipado.**
Los cinco pasos de NIIF 15 aplicados: contrato → una obligación de desempeño (acceso
continuo a la plataforma) → precio de la transacción neto de descuentos → asignación →
reconocimiento **a lo largo del tiempo**, linealmente. Al facturar nace un **pasivo de
contrato** (ingreso diferido) que se libera 1/12 cada mes. Dibuja el asiento. Menciona
la separación corriente / no corriente en contratos multianuales.

**A2. ⭐ Un cliente paga $5.000.000 de implementación además de la suscripción. ¿Cómo lo tratas?**
Primero decide si la implementación es una obligación de desempeño **distinta**: ¿el
cliente puede beneficiarse de ella por sí sola o junto con recursos disponibles? En SaaS
casi siempre **no** lo es (sin la plataforma no vale nada), entonces se **difiere y se
reconoce durante el periodo de beneficio esperado**, que puede exceder el término
contractual si la renovación es probable. Los costos de esa implementación se
capitalizan como costos de cumplimiento (párr. 95) y se amortizan en el mismo horizonte.
Y cierra con el impacto en métricas: **ese ingreso no entra al MRR**.

**A3. ¿Qué haces con las comisiones de ventas?**
Son **costos incrementales de obtener un contrato** (NIIF 15 párr. 91): se capitalizan y
se amortizan sobre la vida esperada del cliente, no solo el término inicial. Excepción
práctica del párr. 94 si la amortización sería ≤ 12 meses. Añade el puente con el CAC:
la métrica usa el gasto incurrido, la contabilidad muestra el amortizado.

**A4. ¿Cuándo capitalizas software desarrollado internamente?**
NIC 38: investigación siempre gasto; desarrollo se capitaliza solo si se cumplen los
seis criterios del párr. 57 (viabilidad técnica, intención, capacidad de uso/venta,
beneficios futuros probables, recursos disponibles, medición fiable). Amortización
contra COGS. Y el reverso: configurar un SaaS de terceros que la empresa **usa** es
gasto, porque no se controla el activo.

**A5. ¿Cómo calculas el deterioro de cartera?**
NIIF 9, enfoque simplificado con **matriz de provisiones** por antigüedad, calibrada con
la experiencia histórica de recuperación y ajustada por expectativas futuras. En SaaS
añade el vínculo con el churn: la mora suele anticipar la cancelación, así que la matriz
y la curva de churn deben conversar.

**A6. ¿Qué diferencias temporarias esperarías encontrar en esta empresa?**
Ingreso diferido, software capitalizado, provisión de cartera, pérdidas fiscales
acumuladas, NIIF 16, y provisiones no deducibles. Menciona que el activo por impuesto
diferido de pérdidas solo se reconoce si es **probable** que haya renta futura, y que ese
juicio es de los que un auditor cuestiona primero.

**A7. Vendemos junto con un servicio de un tercero. ¿El ingreso va bruto o neto?**
NIIF 15 B34-B38: depende de si controlamos el bien/servicio antes de transferirlo
(indicadores: responsabilidad primaria del cumplimiento, riesgo de inventario,
discreción para fijar el precio). Principal → bruto; agente → solo la comisión. Impacto
enorme en ingreso reportado y en margen bruto.

---

## B. Impuestos

**B1. ⭐ ¿Qué obligaciones tributarias manejarías aquí y con qué periodicidad?**
Recita el mapa del módulo 02, sección 2.1: renta anual, autorretención y retención en la
fuente mensuales, IVA bimestral o cuatrimestral según ingresos del año anterior,
declaración informativa de precios de transferencia anual, ICA anual en Medellín en
régimen ordinario y ReteICA bimestral, más facturación y nómina electrónica continuas.
Cierra con **cómo** las gestionas: calendario único, fecha objetivo tres días antes,
preparador y revisor distintos.

**B2. ⭐ ¿Cómo tributa en ICA una empresa que presta servicios digitales desde Medellín a
todo el país?**
Ley 1819 de 2016 art. 343: los servicios se gravan donde **se ejecutan**; para servicios
prestados por medios electrónicos, en la sede del prestador. El riesgo es que otros
municipios reclamen el ingreso si hay establecimiento o presencia allí. Respuesta madura:
*"revisaría dónde hay establecimiento real, aplicaría la regla de territorialidad, y
documentaría la posición; donde haya duda material, evaluaría una consulta o una
posición fiscal incierta provisionada bajo CINIIF 23."*

**B3. Exportamos servicios. ¿Qué implicaciones de IVA tiene?**
Servicios prestados desde Colombia y utilizados **exclusivamente en el exterior** por un
contratante sin negocios en el país son **exentos** (art. 481 lit. c ET): tarifa 0 % con
derecho a IVA descontable, lo que genera **saldos a favor solicitables en devolución**.
Requiere cumplir requisitos formales. Cierra con el ángulo de caja: la devolución es una
palanca de liquidez que hay que gestionar activamente.

**B4. ⭐ ¿Qué son los precios de transferencia y cómo los manejarías?**
Principio de plena competencia; sujetos: operaciones con vinculados del exterior, zonas
francas y jurisdicciones no cooperantes. Obligaciones: declaración informativa,
informe local, informe maestro, y país por país para grupos grandes. Métodos: PC, PR,
CA, MTU y PU, escogiendo el más apropiado. Luego aterriza al caso de la empresa:
servicios de desarrollo/soporte a la matriz por **costo adicionado**, licencia de marca
o software por **PC**, management fees con **benefit test**. Y remata con gestión:
*"el estudio se contrata en el primer semestre, no en septiembre, y las políticas
intragrupo se definen antes de operar, no después."*

**B5. ¿Qué es la tasa mínima de tributación?**
Art. 240 par. 6 ET: si la tasa efectiva sobre la utilidad depurada queda por debajo del
**15 %**, se liquida un impuesto adicional hasta alcanzarla. Añade el ángulo de gestión:
se monitorea trimestralmente, no en la declaración.

**B6. Nos llega un requerimiento especial de la DIAN. ¿Qué haces?**
Verifica términos (2 años desde el vencimiento para notificarlo; 3 meses para responder),
arma el expediente con los papeles de trabajo y soportes de esa declaración, evalúa el
mérito con asesoría tributaria, cuantifica la contingencia y provisiónala si corresponde
(NIC 37 / CINIIF 23), responde en término, y prepara el escenario de recurso de
reconsideración. Menciona que si el expediente estaba bien armado desde el cierre, esto
es un trámite de días, no de semanas.

**B7. ¿Qué revisas antes de deducir un pago al exterior?**
Retención en la fuente aplicable (art. 408 ET, 20 % general) o el convenio de doble
imposición correspondiente con certificado de residencia fiscal; cumplimiento de precios
de transferencia si es vinculado; límite del art. 122 ET; subcapitalización (art. 118-1);
documento soporte y medio de pago bancarizado (art. 771-5); y el registro cambiario si
aplica.

---

## C. Métricas SaaS (el bloque decisivo)

**C1. ⭐⭐ ¿Por qué el MRR no coincide con el ingreso del estado de resultados?**
La pregunta estrella. Responde con las causas del módulo 04, sección 4.8: prorrateo
intramensual, foto vs flujo, servicios no recurrentes, setup diferido, facturación
anticipada, contratos multianuales, TRM, créditos por SLA, IVA, principal vs agente.
Y luego ofrece la solución: *"por eso publico un puente formal MRR → ingreso NIIF 15
cada mes, firmado por Contabilidad y aceptado por Revenue y FP&A."*

**C2. ⭐ Diferencia entre GRR y NRR, y cuál te preocupa más.**
GRR excluye expansión y nunca supera 100 %: mide **cuánto no perdiste**. NRR incluye
expansión y puede superar 100 %: mide **cuánto creciste dentro de la base**. Un NRR alto
con GRR bajo significa que unos pocos clientes en expansión están tapando una fuga real.
*"Miro GRR para diagnosticar el producto y el servicio; NRR para evaluar la estrategia
de crecimiento."*

**C3. ⭐ Nuestro logo churn es 1,2 % mensual y el revenue churn 2 %. ¿Qué me dices?**
Que se están yendo (o reduciendo) los **clientes grandes**. Ordena: abrir el churn por
decil de facturación y por segmento, revisar las cuentas perdidas de mayor valor,
revisar si hay downgrades concentrados en un plan. Advierte que invertir más en CAC
antes de arreglar esto es llenar un balde agujereado.

**C4. ⭐ Calcula el LTV:CAC con estos datos.** *(te darán números en el momento)*
`LTV = ARPA × Margen bruto % / churn mensual`; `CAC = S&M del periodo / clientes nuevos`.
Di en voz alta los supuestos: qué churn usas (de ingresos o de logos), que el margen
bruto es indispensable, y que un ratio muy alto puede indicar **subinversión**, no
excelencia. Referencia: ≥ 3×.

**C5. ¿Qué es el CAC payback y por qué importa más que el CAC?**
`CAC / (ARPA nuevos × margen bruto %)`. Importa más porque conecta con la **caja**: dice
en cuántos meses recuperas la inversión, que es lo que determina si puedes financiar el
crecimiento con la operación o necesitas capital. < 12 meses excelente.

**C6. ¿Qué es el Rule of 40 y cómo estamos?**
Crecimiento YoY % + margen EBITDA %. ≥ 40 es sano. Aclara siempre qué margen y qué
crecimiento usas, porque cambia el resultado. Úsalo para hablar del trade-off:
*"se puede cumplir creciendo mucho y quemando, o creciendo poco y siendo rentable; lo
que no se puede es incumplir en ambas."*

**C7. ¿Qué es el Magic Number y qué decisión habilita?**
`(Ingreso del trimestre − ingreso del trimestre anterior) × 4 / S&M del trimestre
anterior`. > 1 → invierte más en ventas; < 0,5 → arregla la eficiencia antes de escalar.

**C8. ⭐ El ingreso diferido cayó 15 % este trimestre pero el ingreso creció. ¿Qué pasó?**
Alerta temprana: se está reconociendo ingreso de contratos antiguos sin que entren
renovaciones o nuevos contratos prepagados que repongan el pasivo. Si sigue, el ingreso
de los próximos trimestres caerá. Verifica: `Billings = Ingreso + Δ ingreso diferido` →
los billings cayeron. Investiga renovaciones vencidas, cambio de anual a mensual en el
mix de facturación, y descuentos por pago anticipado que dejaron de ofrecerse.

**C9. ¿Qué metes en el COGS de una SaaS?**
Hosting, soporte, la parte de servicio de Customer Success, fees de pasarela, licencias
embebidas, amortización del software capitalizado, entrega de servicios profesionales.
No: R&D de nuevas funcionalidades, ventas, marketing, back office. Y para una empresa con
IA: **el costo de inferencia es COGS variable y hay que medirlo por transacción.**

**C10. ¿Cómo lees una tabla de cohortes?**
Vertical (misma edad, distintas cohortes) para ver si el producto mejora; horizontal para
la curva de retención y la "sonrisa" cuando la expansión supera al churn. Churn temprano
alto = problema de onboarding o de calificación del lead.

**C11. ¿Cómo definirías "cliente activo" y "churn"?**
Trampa deliberada: no hay una respuesta correcta, hay una respuesta **gobernada**.
*"Lo definiría con Revenue y Producto, lo documentaría en un diccionario de métricas
aprobado, y lo congelaría: lo peor no es una definición imperfecta, es una que cambia
cada trimestre y hace incomparables las series."* Propón una: cliente con suscripción
vigente y facturación activa al cierre; churn cuando termina la vigencia sin renovación,
con una ventana de gracia definida.

---

## D. Control interno, auditoría y proceso

**D1. ⭐ ¿Cómo garantizas que cada asiento tenga soporte?**
Política de documentación obligatoria por tipo de asiento, plantillas de papeles de
trabajo, four-eyes en asientos manuales, revisión obligatoria de asientos de fin de mes y
de importe redondo, y **carpeta de cierre mensual** archivada con todos los soportes.
Métrica de control: asientos sin soporte detectados en revisión = 0.

**D2. Somos un equipo pequeño, no podemos segregar todo. ¿Qué haces?**
Ver módulo 03, sección 3.3: se compensa con controles detectivos (revisión posterior
independiente, reportes de excepción, límites de autorización más bajos, revisión de
logs del ERP) y se **documenta explícitamente el control compensatorio**.

**D3. Describe tu proceso de cierre mensual.**
Dibuja el calendario D+1 a D+5 del módulo 01, sección 1.5, con responsables y controles.
Cierra con los KPIs del cierre y una mejora concreta que hayas logrado.

**D4. ¿Cómo preparas una auditoría?**
PBC list negociada con antelación, data room por ciclo, discusión temprana de los juicios
contables, un solo canal de comunicación, y seguimiento formal de hallazgos con causa
raíz y plan de acción.

**D5. ¿Qué diferencia hay entre revisoría fiscal y auditoría externa?**
Origen legal vs contractual, alcance permanente e integral vs el pactado, nombramiento
por asamblea vs administración, y dictamen a la asamblea vs informe al contratante.

---

## E. Liderazgo y situacionales

**E1. ⭐ Cuéntame de una vez que redujiste los días de cierre o automatizaste un proceso.**
STAR con número. Si no lo has hecho, usa el caso más cercano y explica el método;
nunca inventes cifras.

**E2. Un analista comete el mismo error dos meses seguidos. ¿Qué haces?**
Primero determina si es competencia, claridad del proceso o carga de trabajo. Feedback
SBI, ajuste del procedimiento o del control, acompañamiento y verificación al siguiente
cierre. Si persiste, plan formal. **Y arregla el proceso**: un error repetible es una
falla de diseño, no solo de la persona.

**E3. El CRO dice que el ARR es X y tú dices Y. ¿Cómo lo resuelves?**
No en la reunión de junta. Reconstruye el puente cliente por cliente, identifica las
diferencias por causa (prorrateo, servicios en el run-rate, contratos no firmados,
moneda), acuerda la definición, documéntala y publica una sola cifra en adelante.
*"El objetivo no es tener la razón, es que la empresa tenga un solo número."*

**E4. Descubres un error material de periodos anteriores justo antes de publicar.**
NIC 8: si es material, **reexpresión retroactiva** del comparativo. Evalúa si es hecho
posterior ajustable (NIC 10). Escala inmediatamente a Gerencia Financiera y al revisor
fiscal; documenta causa raíz e implementa el control que faltó. Nunca lo escondas ni lo
"diluyas" en el periodo actual.

**E5. Ventas quiere cerrar un contrato con condiciones no estándar el último día del trimestre.**
Evalúa el impacto en el reconocimiento (derecho de devolución, condiciones suspensivas,
descuentos escalonados, entregables futuros) **antes** de la firma. Ofrece alternativas
que logren el objetivo comercial sin comprometer la contabilidad. Y propón el mecanismo
permanente: un *deal desk* donde Finanzas revisa lo no estándar antes de firmar.

**E6. ¿Cómo te mantienes actualizado?**
Rutina, no anécdota: seguimiento de doctrina DIAN y conceptos del CTCP, boletines de
firmas, INCP, sesiones mensuales internas de actualización con expositor rotativo, y
evaluación del impacto de cada cambio en la operación — que es literalmente lo que pide
el aviso ("anticipando su impacto en la operación").

**E7. ¿Por qué quieres trabajar en Magneto?**
Conecta tres cosas: (1) es un modelo SaaS donde la contabilidad **es** estratégica, no
solo cumplimiento; (2) tu interés genuino en la intersección contabilidad-datos-producto;
(3) algo específico y verificable de la empresa (su producto, su expansión regional, su
uso de IA en selección). Evita el elogio genérico.

**E8. ¿Cuáles son tus expectativas salariales?**
El rango publicado es $6.000.000–$10.000.000. Ancla dentro del rango con justificación:
*"Con mi experiencia en cierre bajo NIIF, tributaria colombiana y métricas SaaS, me
ubico en la parte alta del rango que ustedes publicaron; me interesa entender el paquete
completo antes de fijar un número."* Nunca des una cifra por debajo del rango publicado.

---

## F. Caso práctico (prepárate para uno en vivo)

Formato probable: te dan un P&L, un MRR bridge y unos datos de caja, y tienes 15–20
minutos.

**Guion de ataque, en orden:**
1. **Cuadra primero.** Verifica que el MRR bridge cierre y que `Billings = Ingreso +
   Δ ingreso diferido`. Si algo no cuadra, dilo — es medio punto ganado.
2. **Calcula el paquete básico:** ARR, crecimiento, NRR, GRR, churn, margen bruto,
   CAC, payback, LTV:CAC, Rule of 40, runway.
3. **Busca la contradicción.** Siempre hay una plantada: revenue churn > logo churn,
   margen bruto que cae mientras crece el ingreso, ingreso diferido que se desploma,
   ARPU que sube por muerte de clientes pequeños, CAC que baja porque se dejó de
   invertir.
4. **Formula el diagnóstico en una frase.**
5. **Propón dos o tres acciones priorizadas, con su métrica de seguimiento.**
6. **Declara tus supuestos y lo que pedirías** si tuvieras más datos.

Lo que evalúan no es la aritmética: es si conviertes números en una **decisión**.

---

## G. Preguntas que TÚ debes hacer

Tener buenas preguntas es parte de la evaluación. Elige tres o cuatro:

1. ¿Bajo qué grupo NIIF reporta la compañía y hay obligación de reportar a una matriz
   en el exterior?
2. ¿Cuántos días toma hoy el cierre mensual y cuál es la meta?
3. ¿Quién publica hoy el MRR y el ARR, y existe una conciliación formal contra
   contabilidad?
4. ¿Cómo está compuesto el equipo contable y qué brechas ve la compañía?
5. ¿Qué ERP y qué sistema de facturación/suscripciones usan, y están integrados?
6. ¿Hay estudio de precios de transferencia vigente y cuál es la estructura del grupo?
7. ¿La compañía tiene revisor fiscal y auditoría externa? ¿Hay hallazgos abiertos?
8. ¿Hay procesos de levantamiento de capital o due diligence previstos?
9. ¿Cómo se relacionan hoy Contabilidad, FP&A, Revenue y Producto?
10. ¿Qué tendría que haber pasado en 12 meses para que ustedes digan que esta
    contratación fue un éxito?

La 10 es la mejor de todas: te da el criterio de evaluación y te permite cerrar
diciendo cómo lo lograrías.

---

## H. Tu presentación de 2 minutos

Estructura sugerida:

> *"Soy contador público con N años en cierre y reporte bajo NIIF y en tributaria
> colombiana. En [empresa] lideré un equipo de N analistas y llevamos el cierre de X a
> Y días automatizando [proceso concreto]. Manejo el ciclo tributario completo —renta,
> IVA, ICA, retenciones— y he sido el punto de contacto de revisoría fiscal y de
> requerimientos de la DIAN. En los últimos años me especialicé en el modelo de
> suscripción: NIIF 15, ingresos diferidos y la conciliación de las métricas de negocio
> —MRR, NRR, CAC, LTV— contra la contabilidad, que es donde normalmente se rompe la
> conversación entre Finanzas y Revenue. Me interesa este cargo porque une exactamente
> esas dos mitades: cumplimiento impecable y contabilidad que sirve para decidir."*

Ajústalo a tu experiencia real, cronométralo y practícalo en voz alta hasta que suene
natural. Debe durar entre 90 y 120 segundos.
