
# Capítulo I: Introducción

## 1.1. Startup Profile

### 1.1.1. Descripción de la Startup

**Energix** es una startup formada por estudiantes de Ingeniería de Software de la Universidad
Peruana de Ciencias Aplicadas. Desarrollamos **SEMS (Smart Energy Management System)**, una
plataforma de gestión energética dirigida a **establecimientos comerciales de mediana y gran
superficie**: supermercados, tiendas por departamento, minimarkets, restaurantes y almacenes.

En este tipo de local la factura eléctrica no se explica solo por cuánta energía se consume.
Bajo las categorías tarifarias comerciales del pliego peruano, el recibo suma tres conceptos
distintos: la energía consumida en hora punta, la consumida fuera de punta y un **cargo por
potencia** calculado sobre la **demanda máxima** registrada en el mes. Ese tercer concepto es el
que suele pasar desapercibido y el que puede representar cerca de la mitad del costo variable
del recibo.

SEMS mide el consumo por local y por zona, calcula la factura estimada con la tarifa comercial
que corresponde a cada suministro, y avisa **antes** de que la demanda supere la potencia
contratada, cuando todavía se puede evitar el recargo.

**Misión**

Dar a los establecimientos comerciales visibilidad y control sobre su consumo y su demanda
eléctrica, para que reduzcan su costo energético con decisiones basadas en datos y no en
suposiciones.

**Visión**

Ser la plataforma de referencia en gestión energética para el retail y los servicios en el Perú,
capaz de acompañar tanto a un local independiente como a una cadena con decenas de sedes.

**Logo de la Startup**

<div align="center">
  <img src="assets/images/others/energix-logo.jpg" alt="Startup Logo" width="200">
</div>

### 1.1.2. Perfiles de integrantes del equipo

| Foto | Integrante | Código | Carrera | Perfil |
| :--: | :-- | :-- | :-- | :-- |
| `<Foto>` | `<Apellidos, Nombres>` **(Team Leader)** | `<Código>` | Ingeniería de Software | `<Párrafo de resumen con los principales conocimientos técnicos y habilidades que aporta al equipo.>` |
| <img src="assets/images/team-photos/profile-winnie.jpg" alt="Profile Picture" width="100"> | Merino Ordinola, Winnie Lisbeth | U20231E504 | Ingeniería de Software | Estudiante de la carrera de Ingeniería de Software. Mis principales destrezas son las habilidades para trabajar en equipo, la creatividad y la investigación. Mi mayor interés es tanto proponer ideas innovadoras que solucionen problemas cercanos en nuestra realidad, como llevarlas a cabo a través del software. |
| <img src="assets/images/team-photos/profile-nestor.png" alt="Profile Picture" width="100"> | Rojas Tello, Nestor Alonso | U202317099 | Ingeniería de Software | Estudiante de Ingeniería de Software. Tengo conocimientos en C++, Python, JavaScript y CSS. Me considero una persona colaborativa, responsable y con disposición para resolver dudas y proponer soluciones ante cualquier desafío. |
| `<Foto>` | `<Apellidos, Nombres>` | `<Código>` | Ingeniería de Software | `<Párrafo de resumen con los principales conocimientos técnicos y habilidades que aporta al equipo.>` |
| `<Foto>` | `<Apellidos, Nombres>` | `<Código>` | Ingeniería de Software | `<Párrafo de resumen con los principales conocimientos técnicos y habilidades que aporta al equipo.>` |

## 1.2. Solution Profile

### 1.2.1. Antecedentes y problemática

El sector comercial y de servicios es uno de los mayores consumidores de electricidad del país,
y dentro de él los establecimientos con refrigeración continua —supermercados, minimarkets,
restaurantes— presentan la particularidad de operar cargas que no se apagan nunca. A esto se
suma que, a partir de cierto nivel de consumo, el suministro deja de facturarse bajo una tarifa
residencial de precio único y pasa a categorías comerciales (BT3, BT4, MT2, MT3) que introducen
dos conceptos ausentes en una vivienda: la **diferenciación por franja horaria** y el **cargo por
potencia sobre la demanda máxima**.

**Estructura tarifaria (fuente verificada).** El Anexo B de la Resolución de OSINERGMIN define
literalmente el horario de punta:

> *"Se entenderá por horas de punta (HP) el período comprendido entre las 18:00 horas y 23:00 horas
> de cada día de todos los meses del año, exceptuándose a solicitud del cliente, los días domingos,
> días de descanso que correspondan a feriados y feriados que coincidan con días de descanso."*
>
> — OSINERGMIN, *Anexo B: Opciones Tarifarias y Condiciones de Aplicación de las Tarifas*.
> Disponible en https://www.osinergmin.gob.pe/Resoluciones/pdf/ANEXO_B_Resolucion_1908.pdf

Dos consecuencias de esta definición condicionan el modelo de la solución. La primera es que la
hora punta rige **todos los días**, domingos incluidos: la exclusión de domingos y feriados existe,
pero es una opción que el cliente debe solicitar a la distribuidora, no una regla general. Para un
supermercado la diferencia es relevante, porque el domingo es uno de sus días de mayor afluencia.
La segunda es que la opción tarifaria MT2 —y sus equivalentes BT2, BT3 y BT4— es una tarifa con
medición doble de energía y contratación o medición de dos potencias, lo que significa que la
factura incorpora un cargo por potencia independiente de la energía consumida.

**Dimensión del segmento (fuente verificada).** El *Anuario Estadístico de Electricidad 2024* del
MINEM registra una venta de energía eléctrica a cliente final a nivel nacional de **53 288,7 GWh**,
repartida por sector económico de la siguiente manera:

| Sector económico | Energía vendida (GWh) | Participación |
| :-- | --: | --: |
| Industrial | 31 834,9 | 59,74 % |
| Residencial | 11 112,7 | 20,85 % |
| **Comercial** | **9 157,3** | **17,18 %** |
| Alumbrado público | 1 183,9 | 2,22 % |
| **Total** | **53 288,7** | **100,00 %** |

> MINEM, *Anuario Estadístico de Electricidad 2024*, Capítulo 5 «Distribución de energía eléctrica»,
> cuadro 5.3.3.1 «Venta mensual de energía eléctrica por sector económico (GWh)». Disponible en
> <https://www.gob.pe/institucion/minem/informes-publicaciones/7324144-anuario-estadistico-de-electricidad-2024>

El sector comercial es, por tanto, un mercado de **9 157 GWh anuales**: menor que el industrial en
volumen, pero con una diferencia estructural que resulta determinante para el producto. El consumo
industrial se concentra en un número reducido de clientes de gran tamaño, muchos de ellos del
mercado libre, que cuentan con personal e instrumentación propios para la gestión energética. El
consumo comercial, en cambio, se reparte entre miles de establecimientos —supermercados, tiendas
por departamento, farmacias, cadenas de conveniencia— que enfrentan la misma estructura tarifaria
con cargo por potencia y hora punta, pero sin un área de energía que la administre. Ese desajuste
entre la complejidad de la tarifa y la capacidad instalada del cliente es el espacio que ocupa SEMS.

El problema operativo es concreto. La demanda máxima que fija el cargo por potencia del mes se
determina por el pico más alto registrado, aunque ese pico haya durado quince minutos. En un
supermercado, el arranque simultáneo de los compresores de las cámaras frigoríficas tras un
corte, una jornada de alta afluencia o la puesta en marcha del aire acondicionado a primera hora
bastan para producirlo. El administrador del local no dispone de ninguna señal en el momento en
que ocurre: se entera treinta días después, cuando llega el recibo, y para entonces el recargo ya
está aplicado a todo el periodo.

A esa ceguera se añade una segunda: el recibo llega agregado por suministro. No indica qué zona
del local ni qué equipo originó el consumo, de modo que aunque el responsable quiera actuar, no
sabe dónde actuar. En una cadena con varias sedes el problema se multiplica, porque tampoco
existe forma sencilla de comparar el desempeño energético entre locales de tamaño y tipo
similares.

**Análisis de la problemática — 5W2H**

| Elemento | Descripción |
| :-- | :-- |
| **Who** (Quién) | Responsables de operaciones y de mantenimiento de cadenas de retail, y propietarios o administradores de establecimientos comerciales independientes de mediana superficie. Ambos responden por el costo energético del local pero carecen de información oportuna para gestionarlo. |
| **What** (Qué) | Sobrecosto eléctrico originado por dos causas que el recibo mensual no permite atacar: picos de demanda que disparan el cargo por potencia, y consumo concentrado en hora punta que podría desplazarse a franjas más baratas. A ello se suma la imposibilidad de atribuir el consumo a una zona o equipo concreto. |
| **Where** (Dónde) | Perú, en establecimientos comerciales urbanos con suministro en categorías tarifarias que incluyen cargo por potencia (BT3, BT4, MT2, MT3), principalmente en Lima Metropolitana y capitales de provincia. |
| **When** (Cuándo) | De forma continua durante la operación del local. El pico de demanda se produce típicamente en el arranque de la jornada y en las horas de mayor afluencia, que además coinciden con la hora punta del sistema (18:00–23:00 de todos los días, salvo que la distribuidora haya concedido la exclusión de domingos a solicitud del cliente). |
| **Why** (Por qué) | Porque la medición disponible es agregada y diferida: un único medidor por suministro y una única lectura mensual. No existe visibilidad por zona, ni distinción por franja horaria, ni ninguna alerta que llegue mientras el problema todavía se puede corregir. |
| **How** (Cómo) | Mediante medición por zona dentro de cada local, cálculo de la factura estimada con la tarifa comercial correspondiente al suministro, y alertas de demanda que se disparan al aproximarse a la potencia contratada, antes de superarla. |
| **How Much** (Cuánto) | El cargo por potencia puede representar cerca de la mitad del costo variable de un recibo comercial. Evitar un único pico mensual de exceso, o desplazar parte del consumo fuera de hora punta, produce ahorros directos y recurrentes. `<Sustentar con el cálculo del caso de estudio del equipo y con el pliego tarifario vigente.>` |

### 1.2.2. Lean UX Process

#### 1.2.2.1. Lean UX Problem Statements

**Domain**

Gestión del consumo y de la demanda eléctrica en establecimientos comerciales sujetos a
tarifas con cargo por potencia.

**Customer Segments**

Responsables de operaciones y mantenimiento de cadenas de retail, y propietarios o
administradores de establecimientos comerciales independientes.

**Pain Points**

- La factura eléctrica llega agregada y con un mes de retraso, cuando ya no se puede actuar.
- El cargo por potencia se fija por un pico puntual que nadie observa en el momento en que ocurre.
- No se puede atribuir el consumo a una zona concreta del local, así que no se sabe dónde intervenir.
- En una cadena no hay forma de comparar el desempeño entre locales para identificar cuáles están mal.
- Las soluciones existentes están diseñadas para el hogar y no modelan potencia contratada ni franjas horarias.

**Gap**

Existen medidores y plataformas de monitoreo energético, pero orientados al consumo doméstico:
reportan kilovatios-hora a un precio único. Ninguno de los que analizamos modela la estructura
tarifaria comercial peruana —hora punta, fuera de punta y demanda máxima— que es precisamente
donde se origina el sobrecosto del segmento.

**Vision / Strategy**

Convertir la factura eléctrica de un establecimiento en algo observable y accionable: medir por
zona, calcular con la tarifa real del suministro y avisar mientras todavía queda margen para
reaccionar.

**Initial Segment**

Establecimientos comerciales de Lima Metropolitana con superficie entre 200 y 2.000 m² y
suministro en categoría tarifaria con cargo por potencia.

**Enunciado del problema**

> Los establecimientos comerciales pagan un sobrecosto eléctrico que no pueden explicar ni
> anticipar, porque su única fuente de información es un recibo mensual agregado que llega
> cuando el cargo por potencia del periodo ya está determinado.
>
> Hemos observado que las plataformas de monitoreo energético disponibles fueron diseñadas para
> el consumo doméstico y reportan energía a precio único, lo que deja fuera los dos conceptos que
> más pesan en una factura comercial: la franja horaria y la demanda máxima.
>
> **¿Cómo podríamos** dar a los responsables de un establecimiento visibilidad por zona y avisos
> oportunos sobre su demanda, de modo que puedan evitar el recargo por potencia y desplazar
> consumo fuera de hora punta, sin exigirles conocimientos de ingeniería eléctrica?

#### 1.2.2.2. Lean UX Assumptions

**Business Assumptions**

1. Creemos que nuestros clientes necesitan visibilidad de su demanda eléctrica en el momento en que se produce, y no un mes después.
2. Estas necesidades se pueden resolver con una plataforma que mida por zona y calcule con la tarifa comercial del suministro.
3. Nuestros clientes iniciales son responsables de operaciones y propietarios de establecimientos comerciales con cargo por potencia.
4. El valor número uno que un cliente quiere de nuestro servicio es **evitar el recargo por exceso de demanda**.
5. El cliente también puede obtener beneficios adicionales como el desglose de consumo por zona y la comparación entre locales de la cadena.
6. Vamos a adquirir la mayoría de nuestros clientes mediante venta directa a cadenas y a través de gremios de comerciantes.
7. Generaremos ingresos mediante una suscripción mensual escalonada por número de locales gestionados.
8. Nuestra principal competencia en el mercado serán los proveedores de medidores inteligentes y las empresas de eficiencia energética que ofrecen auditorías puntuales.
9. Los venceremos porque entregamos monitoreo continuo y modelamos la tarifa comercial peruana, en lugar de un informe estático o un reporte de kWh.
10. Nuestro mayor riesgo es que la instalación del hardware de medición por zona resulte demasiado costosa o invasiva para el local.
11. Resolveremos esto permitiendo empezar con un solo medidor por local y añadir zonas de forma incremental.

**User Assumptions**

| Pregunta | Supuesto |
| :-- | :-- |
| ¿Quién es el usuario? | El responsable de operaciones o mantenimiento de una cadena, y el propietario o administrador de un local independiente. |
| ¿Dónde encaja nuestro producto en su trabajo o vida? | En la revisión operativa diaria del local y en el cierre mensual de costos. |
| ¿Qué problemas tiene nuestro producto que resolver? | La imposibilidad de anticipar el cargo por potencia y de atribuir el consumo a una zona. |
| ¿Cuándo y cómo es usado nuestro producto? | Consulta diaria breve desde el panel web, y reacción inmediata cuando llega una alerta de demanda. |
| ¿Qué características son importantes? | Alerta de demanda con margen, factura estimada desglosada, consumo por zona y comparación entre locales. |
| ¿Cómo debe verse y comportarse nuestro producto? | Directo y legible por personal no técnico: la alerta debe decir qué está pasando y cuánto margen queda, no mostrar una curva que haya que interpretar. |

#### 1.2.2.3. Lean UX Hypothesis Statements

**Hipótesis 1**

> **Creemos que** al notificar al responsable del local cuando la demanda alcanza el 85% de la
> potencia contratada
> **lograremos** que reduzca carga a tiempo y evite el recargo por exceso.
> **Sabremos que** hemos tenido éxito **cuando** al menos el 60% de las alertas de nivel *warning*
> vayan seguidas de un descenso de la demanda por debajo del umbral en los siguientes 30 minutos.

**Hipótesis 2**

> **Creemos que** al mostrar la factura estimada desglosada en energía, potencia y cargo fijo
> **lograremos** que el responsable identifique el peso real del cargo por potencia.
> **Sabremos que** hemos tenido éxito **cuando** más del 70% de los usuarios entrevistados sepa
> indicar, tras usar el panel, qué concepto pesa más en su recibo.

**Hipótesis 3**

> **Creemos que** al desglosar el consumo por zona dentro del local
> **lograremos** que las acciones de ahorro se dirijan a las zonas de mayor gasto.
> **Sabremos que** hemos tenido éxito **cuando** al menos el 50% de los locales con más de una
> zona registrada consulte la vista por zona al menos una vez por semana.

**Hipótesis 4**

> **Creemos que** al permitir comparar el consumo entre locales de una misma cadena
> **lograremos** que el responsable de operaciones detecte los locales con peor desempeño.
> **Sabremos que** hemos tenido éxito **cuando** las cuentas con tres o más locales usen la
> comparación al menos una vez al mes.

**Hipótesis 5**

> **Creemos que** al informar qué proporción del consumo cae en hora punta
> **lograremos** que el local desplace cargas desplazables a franjas más baratas.
> **Sabremos que** hemos tenido éxito **cuando** los locales que reciben la recomendación reduzcan
> su proporción de consumo en punta en al menos 5 puntos porcentuales en dos meses.

#### 1.2.2.4. Lean UX Canvas

*Figura 1 (Lean Product Canvas)*  
<img src="assets/images/figures/01-uxcanva.png" alt="uxCanva" style="width: 100vw;">

| Cuadrante | Contenido |
| :-- | :-- |
| 1. Business Problem | Los establecimientos comerciales pagan un sobrecosto eléctrico que no pueden anticipar, porque el recibo mensual agregado llega cuando el cargo por potencia del periodo ya está fijado. |
| 2. Business Outcomes | Suscripciones activas de locales, tasa de renovación mensual, número de alertas de demanda atendidas a tiempo. |
| 3. Users | Responsable de operaciones o mantenimiento de cadena; propietario o administrador de local independiente. |
| 4. User Outcomes & Benefits | Evitar el recargo por exceso de demanda; saber en qué zona se va la energía; reducir el consumo en hora punta; comparar locales. |
| 5. Solutions | Medición por local y por zona; alerta de demanda con umbral configurable; factura estimada con tarifa comercial desglosada; comparación entre locales. |
| 6. Hypotheses | Las cinco hipótesis enunciadas en la sección 1.2.2.3. |
| 7. Lo más importante que necesitamos aprender primero | Si el aviso anticipado de demanda efectivamente provoca una acción de reducción de carga en el local, o si el responsable lo ignora por falta de margen operativo. |
| 8. Trabajo mínimo para aprenderlo | Instrumentar un local piloto con un único medidor, configurar la regla de demanda y registrar durante un mes qué ocurre tras cada alerta. |

## 1.3. Segmentos objetivo

Se han definido dos segmentos objetivo. Ambos responden por el costo energético de un
establecimiento comercial, pero se diferencian en la escala que gestionan, en el margen de
decisión que tienen y en el tipo de evidencia que necesitan para adoptar la solución.

### Segmento objetivo #1: Responsables de operaciones y mantenimiento de cadenas de retail

**Aspectos demográficos**

- Sexo: hombres y mujeres.
- Edad: entre 30 y 55 años.
- Formación: técnica o universitaria, con frecuencia en ingeniería industrial, electromecánica o administración.
- Cargo: jefe de operaciones, jefe de mantenimiento, coordinador de facilities o gerente de tienda regional.

**Aspectos geográficos**

- Nacionalidad: principalmente peruanos.
- Zona: urbana. Lima Metropolitana y capitales de provincia.
- Ámbito de responsabilidad: entre 2 y 40 locales.

**Aspectos psicográficos**

Responden ante una gerencia por indicadores de costo operativo y deben justificar cada inversión
con retorno demostrable. Valoran la evidencia por encima del argumento comercial: prefieren una
prueba en un local antes que una propuesta para toda la cadena. Están habituados a trabajar con
tableros e indicadores y toleran cierta complejidad si el dato es fiable.

**Aspectos conductuales**

Revisan indicadores de forma periódica, no continua. Reaccionan ante desviaciones, no ante
tendencias. Necesitan poder delegar la operación diaria en el personal de cada local, lo que
implica que la herramienta debe admitir varios usuarios con permisos distintos por sede.

### Segmento objetivo #2: Propietarios y administradores de establecimientos independientes

**Aspectos demográficos**

- Sexo: hombres y mujeres.
- Edad: entre 28 y 60 años.
- Formación: variable, frecuentemente sin especialización técnica en energía.
- Situación: propietario, socio o administrador de un único local de entre 200 y 800 m².

**Aspectos geográficos**

- Nacionalidad: principalmente peruanos.
- Zona: urbana, en distritos con actividad comercial densa.

**Aspectos psicográficos**

El recibo eléctrico es uno de sus costos fijos más altos y una fuente recurrente de
incertidumbre. No tienen formación eléctrica y desconfían de las propuestas que no puedan
verificar. Su criterio de adopción es el retorno inmediato y comprensible.

**Aspectos conductuales**

Descubren el problema cuando el recibo sube y no saben por qué. Tienen poca disponibilidad para
configurar herramientas y baja tolerancia a instalaciones invasivas que interrumpan la operación
del local. Necesitan que la herramienta les diga qué hacer, no que les entregue datos para que
ellos los interpreten.

# Capítulo II: Requirements Elicitation & Analysis

## 2.1. Competidores

El mercado de gestión energética para establecimientos comerciales en el Perú combina tres tipos
de oferta: fabricantes de medidores y hardware de monitoreo, empresas de servicios de eficiencia
energética que realizan auditorías puntuales, y plataformas internacionales de energy management
orientadas a grandes industrias. Ninguna de las tres resuelve por completo el problema de un
local comercial de mediana superficie.

**Schneider Electric (EcoStruxure Power)** es el referente global en gestión de energía. Ofrece
medición avanzada, análisis de calidad de energía y control de demanda, con integración a
sistemas de automatización de edificios. Su fortaleza es la profundidad técnica y la fiabilidad
del hardware. Su limitación para nuestro segmento es el costo y la complejidad: está diseñado
para plantas industriales y edificios corporativos, requiere integrador certificado y su modelo
comercial no se ajusta a un local de 500 m².

**Sistemas de gestión de las distribuidoras (Enel Perú, Luz del Sur)** ofrecen a sus clientes
comerciales portales de consulta de consumo y, en algunos casos, información de demanda máxima
facturada. Su fortaleza evidente es que la fuente del dato es la propia empresa que factura. Su
limitación es que el dato es diferido y agregado por suministro: sirve para consultar lo ocurrido,
no para actuar durante el mes, y no desglosa por zona ni por equipo.

**Empresas de eficiencia energética y auditoría (consultoras locales)** realizan diagnósticos
puntuales, miden durante un periodo acotado y entregan un informe con recomendaciones. Su
fortaleza es el criterio experto aplicado al caso concreto. Su limitación es que el resultado es
una fotografía: no hay seguimiento continuo, y meses después el local vuelve a no tener
visibilidad. Además el costo por intervención es elevado para un establecimiento independiente.

**Refoss / Shelly / medidores inteligentes de consumo** son dispositivos accesibles que permiten
ver el consumo en tiempo real desde una aplicación móvil. Su fortaleza es el precio y la
facilidad de instalación. Su limitación es determinante para este segmento: reportan energía a
un precio único por kWh, sin modelar franja horaria ni cargo por potencia, que es donde se
origina el sobrecosto comercial.

### 2.1.1. Análisis competitivo

<table width="100%"><tr><th colspan="2">Competitive Analysis Landscape</th><th width="18%"><strong>Energix — SEMS</strong><br><img src="assets/images/others/energix-logo.jpg" alt="Energix Logo" width="80"></th><th width="18%"><strong>Schneider Electric</strong><br><img src="assets/images/others/schneider-logo.png" alt="Schneider Electric Logo" width="80"></th><th width="17%"><strong>Portal de la distribuidora</strong><br><img src="assets/images/others/luzdelsur-logo.jpg" alt="Distribuidora Logo" width="80"></th><th width="17%"><strong>Medidores tipo Refoss / Shelly</strong><br><img src="assets/images/others/refoss-logo.jpg" alt="Refoss Logo" width="80"></th></tr><tr><td colspan="2"><strong>¿Por qué llevar a cabo este análisis?</strong></td><td colspan="4">Determinar qué necesidad del segmento de establecimientos comerciales no está siendo atendida por la oferta actual, y sobre qué base construir la ventaja competitiva de SEMS.</td></tr><tr><td rowspan="2"><strong>Perfil</strong></td><td>Overview</td><td>Plataforma web de gestión energética para establecimientos comerciales. Mide por local y por zona, calcula con la tarifa comercial peruana y avisa antes de superar la potencia contratada.</td><td>Suite empresarial de gestión de energía y automatización para industria y edificios corporativos.</td><td>Portal de consulta de consumo y facturación que la distribuidora ofrece a sus clientes.</td><td>Dispositivos de medición de consumo con aplicación móvil, orientados al mercado doméstico.</td></tr><tr><td>Ventaja competitiva</td><td>Modela la estructura tarifaria comercial peruana completa (punta, fuera de punta y demanda máxima) y alerta con margen antes del exceso.</td><td>Profundidad técnica, calidad de energía, integración con control industrial y respaldo de marca global.</td><td>El dato proviene de la misma empresa que emite la factura.</td><td>Precio bajo e instalación sencilla.</td></tr><tr><td rowspan="2"><strong>Perfil de Marketing</strong></td><td>Mercado objetivo</td><td>Establecimientos comerciales de 200 a 2.000 m² y cadenas de retail pequeñas y medianas.</td><td>Industria, minería, edificios corporativos y grandes superficies.</td><td>Todos los clientes de la concesionaria.</td><td>Consumidor doméstico y pequeño negocio.</td></tr><tr><td>Estrategias de marketing</td><td>Venta directa a cadenas, alianzas con gremios de comerciantes y prueba piloto gratuita en un local.</td><td>Red de integradores certificados y venta consultiva de alto ticket.</td><td>Canal propio incluido en el servicio.</td><td>Comercio electrónico y retail de tecnología.</td></tr><tr><td rowspan="3"><strong>Perfil de Producto</strong></td><td>Productos y servicios</td><td>Landing page, aplicación web, API RESTful y aplicación móvil. Alertas de demanda, factura estimada desglosada, consumo por zona y comparación entre locales.</td><td>Medidores, software de supervisión, servicios de ingeniería y analítica avanzada.</td><td>Consulta de recibos, histórico de consumo y demanda facturada.</td><td>Medidor con aplicación de consumo y automatizaciones básicas.</td></tr><tr><td>Precios y costos</td><td>Suscripción mensual escalonada por número de locales. Plan de entrada gratuito para un local.</td><td>Licenciamiento e implementación de alto costo, con proyecto de integración.</td><td>Sin costo adicional, incluido en el servicio eléctrico.</td><td>Pago único por dispositivo.</td></tr><tr><td>Canales de distribución</td><td>Web y móvil.</td><td>Integradores y fuerza de ventas directa.</td><td>Web y aplicación de la distribuidora.</td><td>Comercio electrónico.</td></tr><tr><td rowspan="4"><strong>Análisis SWOT</strong></td><td>Fortalezas</td><td>Modela la tarifa comercial peruana; alerta preventiva de demanda; desglose por zona; equipo con conocimiento del contexto regulatorio local.</td><td>Marca consolidada, robustez técnica, catálogo completo de hardware y software.</td><td>Acceso directo al dato oficial de facturación.</td><td>Costo bajo, gran base instalada y facilidad de uso.</td></tr><tr><td>Debilidades</td><td>Startup sin trayectoria ni base instalada; depende de hardware de medición de terceros; sin histórico de casos de éxito.</td><td>Costo y complejidad desproporcionados para el segmento; ciclo de venta largo.</td><td>Dato diferido y agregado; sin desglose por zona; sin capacidad de alerta preventiva.</td><td>No modela franja horaria ni demanda máxima; orientado al hogar; sin gestión multi-local.</td></tr><tr><td>Oportunidades</td><td>Segmento desatendido entre el medidor doméstico y la suite industrial; presión creciente sobre los costos operativos del retail.</td><td>Expansión hacia edificios comerciales medianos.</td><td>Ampliar los servicios digitales al cliente comercial.</td><td>Adaptar su producto al segmento comercial.</td></tr><tr><td>Amenazas</td><td>Que la distribuidora o un fabricante de medidores incorporen alertas de demanda en su propia oferta.</td><td>Competidores especializados más ágiles en nichos concretos.</td><td>Regulación y competencia en la comercialización eléctrica.</td><td>Saturación del mercado y competencia por precio.</td></tr></table>

### 2.1.2. Estrategias y tácticas frente a competidores

**Frente a la debilidad de los medidores domésticos (no modelan la tarifa comercial)**

Nuestra estrategia es hacer de la tarifa el núcleo del producto y no un añadido. La táctica
concreta es mostrar en el panel la factura estimada **desglosada** en energía de punta, energía
fuera de punta y cargo por potencia, de modo que el usuario vea con sus propios números qué
proporción de su recibo depende del pico y no del consumo. Ese desglose es la demostración más
directa de por qué un medidor doméstico no le sirve.

**Frente a la fortaleza de las suites industriales (profundidad técnica y marca)**

No competimos en profundidad técnica. Nuestra estrategia es competir en **tiempo hasta el primer
valor**: mientras una implementación industrial requiere un proyecto de integración, SEMS permite
dar de alta una organización, un local y un medidor en minutos, y empezar a recibir alertas de
demanda el mismo día. La táctica es un plan de entrada gratuito para un local, pensado para que
el responsable pruebe sin autorización de compra.

**Frente a la ventaja del portal de la distribuidora (dato oficial)**

No disputamos la fuente del dato de facturación. Nuestra estrategia es posicionarnos en el
**momento** en que el dato es útil: el portal informa de lo ocurrido, SEMS avisa mientras todavía
se puede evitar. La táctica es explicitar en la comunicación que el cargo por potencia se fija por
un pico de minutos y que ninguna consulta mensual permite prevenirlo.

**Frente a la amenaza de que un competidor incorpore alertas de demanda**

Nuestra estrategia es construir el diferencial en la capa que es más difícil de copiar: el
modelado por **zona** y la comparación entre locales de una cadena, que requieren estructura de
dominio y no solo un umbral sobre una señal. La táctica es priorizar en el backlog las
funcionalidades multi-local desde los primeros sprints.

**Aprovechando nuestra oportunidad (segmento desatendido)**

La estrategia es concentrarnos en un nicho concreto y ganarlo antes de ampliar: establecimientos
con refrigeración continua, donde el problema del pico de demanda es más agudo y más fácil de
demostrar. La táctica es construir el caso de negocio con un local piloto y usar sus cifras
reales como argumento de venta ante cadenas del mismo rubro.

## 2.2. Entrevistas

### 2.2.1. Diseño de entrevistas

Las entrevistas buscan validar las hipótesis del *Lean UX Process* y recoger la información
necesaria para construir los arquetipos: características demográficas, contexto operativo del
local, comportamiento frente al recibo, canales digitales de interacción y disposición a adoptar
la solución.

Se realizarán entre **3 y 5 entrevistas por segmento**, registradas en video. Cada entrevista se
inicia explicando el propósito de la investigación y solicitando consentimiento para la grabación.

> **Nota metodológica.** Las preguntas están formuladas de manera abierta y evitan sugerir la
> respuesta. En particular, las preguntas sobre el cargo por potencia se plantean **sin nombrarlo**
> al inicio (preguntas 6 y 7 del segmento 1), para comprobar si el entrevistado lo identifica por
> sí mismo. Si se le explica primero, la respuesta pierde valor como evidencia.

#### Entrevista — Segmento #1: Responsables de operaciones y mantenimiento de cadenas de retail

**Bloque A. Perfil y contexto**

1. ¿Podría contarnos su cargo, cuánto tiempo lleva en él y cuántos locales están bajo su responsabilidad?
2. ¿Qué tipo de establecimientos son y qué superficie aproximada tienen?
3. ¿Quién decide en su organización una inversión en equipamiento o software para los locales, y qué necesita usted para sustentarla?

**Bloque B. Situación actual del costo energético**

4. ¿Qué lugar ocupa el costo eléctrico dentro de los costos operativos que usted gestiona?
5. ¿Cómo se entera hoy de cuánto consumió cada local y con qué frecuencia lo revisa?
6. Cuando el recibo de un local sube respecto del mes anterior, ¿cómo averigua a qué se debió?
7. ¿Qué conceptos aparecen en el recibo de sus locales? ¿Cuál de ellos le resulta más difícil de explicar o de controlar?
8. ¿Ha tenido alguna vez un recibo que le sorprendiera? ¿Qué hizo al respecto?

**Bloque C. Operación y equipos**

9. ¿Qué equipos considera que consumen más en sus locales y en qué momento del día?
10. ¿Existe algún procedimiento cuando se produce un corte y los equipos vuelven a arrancar todos a la vez?
11. ¿Puede identificar qué zona de un local (sala de ventas, cámaras, almacén, oficinas) consume más? ¿Cómo lo sabría?
12. ¿Tiene forma de comparar el desempeño energético entre locales similares de la cadena?

**Bloque D. Solución y adopción**

13. Si pudiera recibir un aviso mientras el consumo de un local se está disparando, ¿qué haría con ese aviso? ¿Quién debería recibirlo?
14. ¿Quién en cada local debería poder ver esta información y quién debería poder modificar la configuración?
15. ¿Qué tendría que demostrarle una herramienta de este tipo para que usted la lleve a su gerencia?
16. ¿Qué le haría desconfiar o abandonar una herramienta así?

**Bloque E. Perfil digital**

17. ¿Desde qué dispositivo revisaría esta información: computadora de oficina, teléfono, ambos?
18. ¿Qué herramientas digitales usa hoy para gestionar la operación de los locales?
19. ¿Cómo prefiere recibir una alerta urgente: correo, mensajería, notificación en la aplicación?

#### Entrevista — Segmento #2: Propietarios y administradores de establecimientos independientes

**Bloque A. Perfil y contexto**

1. ¿Podría contarnos qué tipo de negocio tiene, hace cuánto y qué superficie aproximada ocupa?
2. ¿Cuál es su rol en el día a día del local?
3. ¿Cuántas personas trabajan en el local y quién se ocupa de temas como el mantenimiento o los servicios?

**Bloque B. Situación actual del costo energético**

4. ¿Cuánto representa el recibo de luz dentro de sus gastos fijos mensuales?
5. ¿Cómo revisa su recibo? ¿Mira solo el total o entra en el detalle?
6. ¿Ha notado variaciones entre meses que no supiera explicar? ¿Qué hizo?
7. ¿Sabe qué potencia tiene contratada para su local? ¿Sabe qué pasa si la supera?
8. ¿Alguna vez le han ofrecido una revisión o auditoría eléctrica? ¿Qué resultado tuvo?

**Bloque C. Operación y equipos**

9. ¿Qué equipos de su local funcionan las 24 horas y cuáles solo durante la atención?
10. ¿En qué momento del día siente que el local consume más?
11. Si tuviera que reducir consumo mañana, ¿sabría por dónde empezar?

**Bloque D. Solución y adopción**

12. Si recibiera un aviso en el momento en que su local se acerca a un consumo que le va a costar caro, ¿qué haría?
13. ¿Qué información le gustaría ver para saber en qué parte del local se le está yendo la energía?
14. ¿Cuánto estaría dispuesto a pagar mensualmente por una herramienta que le ahorre una parte de su recibo? ¿Qué ahorro tendría que demostrarle para que valga la pena?
15. ¿Qué tan dispuesto estaría a que le instalen un equipo de medición en su tablero eléctrico? ¿Qué le preocuparía de eso?
16. ¿Qué le haría abandonar una herramienta así después de probarla?

**Bloque E. Perfil digital**

17. ¿Qué dispositivo usa habitualmente para temas del negocio?
18. ¿Usa alguna aplicación para llevar cuentas, inventario o ventas? ¿Cuál y por qué esa?
19. ¿Cómo prefiere que le llegue un aviso urgente del local?

### 2.2.2. Registro de entrevistas

> **Pendiente de ejecución por el equipo.** Esta sección se completa con las entrevistas reales.
> Por cada entrevista se debe registrar: nombres y apellidos, edad, distrito, cargo, un screenshot
> del cuadro de video, el URL del video subido a Microsoft Stream con el *timing* de inicio y la
> duración, y un resumen descriptivo de las principales respuestas.
>
> **El resumen debe incluir todas las características objetivas y subjetivas** (personalidad,
> marcas e influencias, tecnología, canales de interacción, navegador y dispositivos), porque cada
> característica de los arquetipos de la sección 2.3 debe poder rastrearse hasta un dato recogido
> aquí.

#### Segmento #1 — Entrevista 1

| Campo | Dato |
| :-- | :-- |
| Nombres y apellidos | Fabrizzio Estefano Varela Tapia |
| Edad | 24 años |
| Distrito | Lima (Santa Paula 375, Lima) |
| Cargo / tipo de establecimiento | Coordinador de operaciones de cadena (Minimarkets) |
| Número de locales a cargo | 3 locales |
| URL del video | [Ver video en SharePoint](https://upcedupe-my.sharepoint.com/:v:/g/personal/u202310342_upc_edu_pe/IQB5nwCliWL5S6uU__Jhf6JZAWlwk4Z6HWyNSsf2NyK_DOo?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJPbmVEcml2ZUZvckJ1c2luZXNzIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXciLCJyZWZlcnJhbFZpZXciOiJNeUZpbGVzTGlua0NvcHkifX0&e=OrbLbV) |
| Timing de inicio | 00:00 |
| Duración | 08:11 |
| Screenshot | <img src="assets/images/interviews/needfinding/01-entrevista-responsable01.png" alt="Captura Entrevista Fabrizzio" width="250"> |

**Resumen de la entrevista**

Fabrizzio es coordinador de operaciones de una cadena de 3 minimarkets. Gestiona la operación de forma reactiva, enterándose del costo eléctrico solo al llegar el recibo mensual, lo que representa su segundo mayor gasto después del alquiler. Su mayor frustración es el cargo por potencia, ya que al carecer de medidores por zonas (como frigoríficos) no puede detectar ineficiencias ni sustentar excesos tarifarios ante la gerencia. Indica gran disposición a usar una solución que envíe alertas de demanda con margen a su celular, siempre que esto logre evitar penalidades tarifarias (retorno de inversión) y permita dar accesos acotados a los jefes de cada tienda. A nivel tecnológico, usa ERP corporativo en su laptop, pero depende intensamente de WhatsApp y notificaciones *push* en su smartphone para emergencias.


#### Segmento #1 — Entrevista 2 (Plantilla)

| Campo | Dato |
| :-- | :-- |
| Nombres y apellidos | `<...>` |
| Edad | `<...>` |
| Distrito | `<...>` |
| Cargo / tipo de establecimiento | `<...>` |
| Número de locales a cargo | `<...>` |
| URL del video | `<...>` |
| Timing de inicio | `<mm:ss>` |
| Duración | `<mm:ss>` |
| Screenshot | `<Insertar captura del cuadro de video>` |

**Resumen de la entrevista**

`<Resumen descriptivo de las respuestas del entrevistado a las preguntas realizadas, incluyendo características objetivas y subjetivas.>`

#### Segmento #2 — Entrevista 1

| Campo | Dato |
| :-- | :-- |
| Nombres y apellidos | Jasmin Adriana Urrutia Peña |
| Edad | 25 años |
| Distrito | Santiago de Surco (Monterrico, Lima) |
| Cargo / tipo de establecimiento | Propietario y administrador (Cafetería de especialidad) |
| Número de locales a cargo | 1 local |
| URL del video | [Ver video en SharePoint](https://upcedupe-my.sharepoint.com/:v:/g/personal/u202310342_upc_edu_pe/IQAfFVq1XrLSRatizFEVTM9nAYfxtQ5KC_BEae9a9BF9UVo?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJPbmVEcml2ZUZvckJ1c2luZXNzIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXciLCJyZWZlcnJhbFZpZXciOiJNeUZpbGVzTGlua0NvcHkifX0&e=uPpjgo) |
| Timing de inicio | 00:00 |
| Duración | 08:08 |
| Screenshot | <img src="assets/images/interviews/needfinding/03-entrevista-propetario01.png" alt="Captura Entrevista Jasmin" width="250"> |

**Resumen de la entrevista**

El entrevistado es propietario y administrador de una cafetería de especialidad de 80 m² y gestiona todas las operaciones diarias de manera empírica. El costo de energía representa una parte significativa de sus gastos fijos (20%). Sin embargo, no revisa el detalle de su recibo, ignorando conceptos técnicos como el cargo por potencia y la tarifa comercial. Suele encender los equipos de manera rutinaria, generando picos de consumo por las tardes (hora punta) al activar luces y aire acondicionado simultáneamente por la afluencia de clientes. Ante un recibo inexplicable en campaña pasada, su única acción fue apagar equipos al azar sin conocer realmente cuáles consumían más. Estaría dispuesto a pagar una herramienta mensual si se le demuestra un ahorro tangible en el recibo, y ve con gran interés recibir avisos de exceso de consumo en tiempo real mediante notificaciones *push* en su smartphone, el cual es su principal herramienta de gestión, junto con apps bancarias.

#### Segmento #2 — Entrevista 2 (Plantilla)

| Campo | Dato |
| :-- | :-- |
| Nombres y apellidos | `<...>` |
| Edad | `<...>` |
| Distrito | `<...>` |
| Cargo / tipo de establecimiento | `<...>` |
| Número de locales a cargo | `<...>` |
| URL del video | `<...>` |
| Timing de inicio | `<mm:ss>` |
| Duración | `<mm:ss>` |
| Screenshot | `<Insertar captura del cuadro de video>` |

**Resumen de la entrevista**

`<Resumen descriptivo de las respuestas del entrevistado a las preguntas realizadas, incluyendo características objetivas y subjetivas.>`

### 2.2.3. Análisis de entrevistas

El análisis se realiza **por segmento**, identificando con sustento estadístico (porcentajes) las
características objetivas y subjetivas más comunes, que son las que sostienen la construcción de
los arquetipos. Cada porcentaje debe poder verificarse contra los resúmenes de la sección 2.2.2.

**Estructura del análisis por segmento**

| Característica | Hallazgo | Porcentaje | Entrevistas que lo sustentan |
| :-- | :-- | :-- | :-- |
| Rango de edad predominante | `<...>` | `<X %>` | `<E1, E2, E4>` |
| Dispositivo principal de consulta | `<...>` | `<X %>` | `<...>` |
| Canal preferido para alertas | `<...>` | `<X %>` | `<...>` |
| Conoce su potencia contratada | `<...>` | `<X %>` | `<...>` |
| Identifica el cargo por potencia sin ayuda | `<...>` | `<X %>` | `<...>` |
| Ha tenido un recibo inexplicable | `<...>` | `<X %>` | `<...>` |
| Puede atribuir consumo a una zona | `<...>` | `<X %>` | `<...>` |
| Frustración más mencionada | `<...>` | `<X %>` | `<...>` |
| Disposición a pagar una suscripción | `<...>` | `<X %>` | `<...>` |

## 2.3. Needfinding

Los artefactos de esta sección derivan de las entrevistas y deben elaborarse una vez registradas y analizadas. Se incluye aquí la estructura y las herramientas indicadas por el enunciado. Construirlos antes de entrevistar invalidaría el proceso: los arquetipos dejarían de representar a personas reales y pasarían a ser suposiciones del equipo.

### 2.3.1. User Personas

Elaborados en **UXPressia**, uno por segmento objetivo. Cada User Persona debe incluir datos
demográficos, rasgos de personalidad, motivaciones, frustraciones, objetivos, marcas e
influencias, canales digitales y dispositivos, **todos derivados del análisis de la sección 2.2.3**.

**User Persona — Segmento #1: Responsables de operaciones y mantenimiento de cadenas de retail**

*Figura 2 (User Persona 1)*  
<img src="assets/images/figures/02-user-persona-1.png" alt="User Persona Renzo" style="width: 100vw;">

> El arquetipo de Renzo Varela se construyó a partir de la entrevista a Fabrizzio, coordinador de tres minimarkets. Se caracteriza por priorizar el control, la prevención de sobrecostos y la reacción rápida ante incidencias, a partir de su necesidad de anticipar excesos de consumo, recibir alertas móviles y conocer el consumo por local o zona.

**User Persona — Segmento #2: Propietarios y administradores de establecimientos independientes**

*Figura 3 (User Persona 2)*  
<img src="assets/images/figures/03-user-persona-2.png" alt="User Persona Valeria" style="width: 100vw;">

> El arquetipo de Valeria Mendoza se construyó a partir de la entrevista a Jasmin, propietaria y administradora de una cafetería de especialidad. Se caracteriza por priorizar el ahorro, la simplicidad y la toma rápida de decisiones, a partir de su necesidad de identificar qué equipos consumen más energía, evitar picos de consumo y recibir alertas claras desde su smartphone.

### 2.3.2. User Task Matrix

Matriz de tareas por User Persona, indicando frecuencia e importancia de cada tarea.

**Primer Segmento Objetivo (Responsables de operaciones y mantenimiento de cadenas de retail)**

*Figura 4 (User Task Matrix 1)*
<img src="assets/images/figures/04-u-task-matrix-1.png" alt="User Task Matrix 1" style="width: 100vw;">

**Segundo Segmento Objetivo (Propietarios y administradores de establecimientos independientes)**

*Figura 5 (User Task Matrix 2)*
<img src="assets/images/figures/05-u-task-matrix-2.png" alt="User Task Matrix 2" style="width: 100vw;">

**Análisis de la Matriz de Tareas (User Task Matrix)**
Ambos perfiles coinciden en la alta importancia de tareas enfocadas en el ahorro y resolución de alertas (revisar consumo diario y atender alertas de demanda), siendo estos los flujos críticos del negocio. Sin embargo, existen diferencias clave en la frecuencia de ciertas actividades operativas debido a su naturaleza y escala de operación. El **Persona #1 (Responsable de Operaciones de Cadena)** realiza con alta frecuencia tareas de análisis comparativo entre sedes y descarga de reportes para gerencia, ya que su rol exige la justificación de gastos corporativos. Por otro lado, el **Persona #2 (Propietario Independiente)** le da poca importancia y frecuencia a comparar locales y descargar reportes corporativos, pero revisa con altísima frecuencia su consumo diario, dado que está altamente preocupado por el día a día y el impacto en su bolsillo.

### 2.3.3. User Journey Mapping

El *User Journey Map* recorre la experiencia completa de cada User Persona a lo largo de un ciclo
de facturación, desde que empieza el mes hasta que recibe el recibo. A diferencia del *As-Is
Scenario Map*, que describe la secuencia de acciones, el *Journey Map* añade la dimensión
emocional y el nivel de conocimiento que la persona tiene en cada fase, que es lo que explica por
qué el problema persiste.

**Primer Segmento Objetivo (Responsables de operaciones y mantenimiento de cadenas de retail)**

*Figura 6 (User Journey Map 1)*
<img src="assets/images/figures/06-u-journey-map-1.png" alt="User Journey Map 1" style="width: 100vw;">

**Segundo Segmento Objetivo (Propietarios y administradores de establecimientos independientes)**

*Figura 7 (User Journey Map 2)*
<img src="assets/images/figures/07-u-journey-map-2.png" alt="User Journey Map 2" style="width: 100vw;">

### 2.3.4. Empathy Mapping

Elaborados en **UXPressia**, uno por User Persona, con los cuadrantes *Thinks and Feels*, *Sees*,
*Says and Does*, *Hears*, *Pains* y *Gains*.

**Primer Segmento Objetivo (Responsables de operaciones y mantenimiento de cadenas de retail)**

*Figura 8 (Empathy Map 1)*
<img src="assets/images/figures/08-empathy-map-1.png" alt="Empathy Map 1" style="width: 100vw;">

**Segundo Segmento Objetivo (Propietarios y administradores de establecimientos independientes)**

*Figura 9 (Empathy Map 2)*
<img src="assets/images/figures/09-empathy-map-2.png" alt="Empathy Map 2" style="width: 100vw;">

### 2.3.5. As-is Scenario Mapping

Elaborados en **Lucidchart**, uno por User Persona, con las filas *Phases*, *Doing*,
*Thinking* y *Feeling*, describiendo cómo el usuario afronta hoy la gestión del costo energético
de su establecimiento **sin** la solución.

**Primer Segmento Objetivo (Responsables de operaciones y mantenimiento de cadenas de retail)**

*Figura 10 (As-Is Scenario Map 1)*
<img src="assets/images/figures/10-as-is-scenario-map-1.png" alt="As Is Scenario Map 1" style="width: 100vw;">

> **Nota.** El mapa ilustra la falta de información antes de la llegada del recibo y la frustración que esto genera en el usuario durante el cierre del mes (**pain points**), así como la confianza que siente al delegar las tareas operativas (**happy moments**). También se identifican áreas por descubrir (**blank areas**), como la distribución exacta del consumo de las distintas áreas sin medidores. Elaboración propia en Lucidchart.

**Segundo Segmento Objetivo (Propietarios y administradores de establecimientos independientes)**

*Figura 11 (As-Is Scenario Map 2)*
<img src="assets/images/figures/11-as-is-scenario-map-2.png" alt="As Is Scenario Map 2" style="width: 100vw;">

> **Nota.** El mapa muestra la angustia del propietario al momento de la llegada del recibo mensual (**pain points**) y las acciones reactivas que toma sin conocimiento técnico. También destaca los momentos positivos derivados de la afluencia de clientes en las horas punta (**happy moments**) y áreas sobre las que no se tiene información (**blank areas**), como identificar qué equipos exactos son los que más consumen. Elaboración propia en Lucidchart.

## 2.4. Ubiquitous Language

Lenguaje común del dominio, compartido entre el equipo técnico y los expertos del negocio. Los
términos que se listan a continuación son los que se emplean de forma consistente en los
artefactos de diseño, en el código fuente y en la interfaz de los productos.

> **Nota sobre el idioma.** Según el enunciado del curso, el idioma por defecto de la interfaz de
> usuario, de los mensajes y de la documentación de todos los productos de la solución es el
> **inglés**. Por eso cada término se registra con su denominación en inglés, que es la que aparece
> en el código y en la API, junto con su equivalente en español empleado en este informe.

| Término (EN) | Término (ES) | Definición |
| :-- | :-- | :-- |
| **Organization** | Organización | Empresa que contrata el servicio, identificada por su RUC. Puede agrupar uno o varios locales. Es el nivel al que se asocia la suscripción. |
| **Site** | Local | Establecimiento físico con su propio suministro eléctrico, su medidor, su contrato con la distribuidora y su factura. Es la unidad sobre la que se predice el gasto y se comparan desempeños. |
| **Zone** | Zona | Subdivisión funcional de un local: sala de ventas, cámaras frigoríficas, almacén, cocina, oficinas. Determina si el consumo fuera del horario de atención es esperado o anómalo. |
| **Device / Meter** | Dispositivo / Medidor | Equipo de medición instalado en un local y, opcionalmente, asignado a una zona. Reporta lecturas de consumo. |
| **Membership** | Vínculo de acceso | Relación entre una persona y una organización, con un papel y un alcance. Determina qué locales puede ver o modificar. |
| **Contracted Power** | Potencia contratada | Potencia en kW pactada con la distribuidora para un local. Superarla no interrumpe el suministro: se factura como exceso. |
| **Maximum Demand** | Demanda máxima | Mayor potencia registrada en el periodo de facturación. Determina el cargo por potencia de todo el mes, aunque el pico haya durado minutos. |
| **Peak Hours** | Hora punta | Franja de 18:00 a 23:00 de cada día del año, con precio de energía más alto. |
| **Off-Peak Hours** | Fuera de punta | Resto de las horas, con precio de energía más bajo. |
| **Excludes Sundays From Peak** | Exclusión de domingos | Opción que un suministro puede tener concedida, a solicitud del cliente, para que sus domingos y feriados se facturen fuera de punta. No es la regla general. |
| **Tariff Category** | Categoría tarifaria | Clasificación del suministro según el pliego (BT5B, BT3, BT4, MT2, MT3). Determina si el suministro paga cargo por potencia. |
| **Power Charge** | Cargo por potencia | Concepto de la factura calculado sobre la demanda máxima, independiente de la energía consumida. |
| **Excess Power** | Exceso de potencia | Diferencia entre la demanda máxima y la potencia contratada, facturada con recargo. |
| **Demand Rule** | Regla de demanda | Regla de vigilancia asociada a un local que define a qué porcentaje de la potencia contratada se emite un aviso. |
| **Bill Estimate** | Factura estimada | Proyección del recibo del periodo, desglosada en energía de punta, energía fuera de punta, cargo por potencia y cargo fijo. |
| **Consumption Alert** | Alerta de consumo | Aviso generado cuando una lectura supera un umbral configurado para un dispositivo. |
| **Subscription Plan** | Plan de suscripción | Nivel de servicio contratado por la organización, definido por el número de locales y de medidores por local. |

# Capítulo III: Requirements Specification

En este capítulo se especifican los requisitos de los productos digitales de la solución a partir
del análisis realizado en el capítulo anterior. Se inicia con el To-Be Scenario Mapping, que
describe cómo cambia la experiencia del usuario al incorporar SEMS, y continúa con las User
Stories, el Impact Mapping y el Product Backlog priorizado.

## 3.1. To-Be Scenario Mapping

> Se elabora en **LucidChart o Miro**, uno por User Persona, una vez construidos los As-Is de la
> sección 2.3.4.

El proceso seguido por el equipo comprende las etapas de preparación, lluvia de ideas individual,
revisión conjunta, identificación de fases como columnas, denominación de las fases y comparación
con el As-Is correspondiente para hacer explícitos los cambios que introduce la solución.

**To-Be Scenario Map — User Persona #1: Responsable de operaciones de cadena**

`<Insertar imagen con las filas Phases, Doing, Thinking y Feeling>`

`<Explicación del mapa y comparación con el As-Is: qué fases desaparecen, cuáles se acortan y en
qué punto del recorrido el usuario pasa de reaccionar a anticipar.>`

**To-Be Scenario Map — User Persona #2: Propietario de establecimiento independiente**

`<Insertar imagen>`

`<Explicación y comparación con el As-Is.>`

## 3.2. User Stories

Las User Stories se redactan bajo el formato *Como \<rol\>, deseo \<objetivo\> para \<beneficio\>*,
con criterios de aceptación en estructura Gherkin (Given–When–Then). Los criterios se expresan en
tiempo presente y tercera persona, son comprobables y no hacen referencia a detalles de interfaz.

Se incluyen tres tipos de historia:

- **De usuario final**, para la aplicación web y móvil, con los roles derivados de los User Personas.
- **De visitante**, para el Landing Page, con el rol *visitante* o su subconjunto por segmento.
- **Technical Stories**, para los componentes sin interacción directa con el usuario final —los
  RESTful APIs—, redactadas con el rol *Developer* y con criterios expresados como escenarios de
  request/response.

### Epics

| Epic ID | Título | Descripción |
| :-- | :-- | :-- |
| **EP01** | Landing Page | Como visitante, deseo conocer la propuesta de valor de SEMS y acceder a la aplicación, para evaluar si resuelve el problema de costo energético de mi establecimiento. |
| **EP02** | Identidad y control de acceso | Como responsable de una organización, deseo gestionar quién accede a qué locales, para que cada persona vea únicamente lo que le corresponde. |
| **EP03** | Gestión de la organización y sus locales | Como administrador, deseo registrar mi cadena y sus locales con sus datos de suministro, para que el sistema calcule sobre la tarifa correcta de cada uno. |
| **EP04** | Gestión de zonas y medidores | Como supervisor, deseo organizar mi local en zonas y asignar medidores, para saber en qué parte del local se consume la energía. |
| **EP05** | Monitoreo de consumo | Como supervisor, deseo consultar el consumo de mi local en el tiempo, para detectar variaciones y entender el comportamiento de mis equipos. |
| **EP06** | Control de demanda y alertas | Como responsable, deseo ser avisado antes de superar la potencia contratada, para reducir carga a tiempo y evitar el recargo. |
| **EP07** | Analítica y proyección de factura | Como responsable, deseo conocer la factura estimada del periodo desglosada, para saber qué concepto pesa más y dónde actuar. |
| **EP08** | Suscripciones y pagos | Como administrador, deseo contratar y gestionar el plan que corresponde al tamaño de mi cadena, para acceder a las funcionalidades que necesito. |
| **EP09** | Plataforma y servicios (Technical) | Como developer, deseo disponer de un API RESTful documentado y seguro, para integrar los productos digitales de la solución. |

### User Stories

| Epic / User Story ID | Título | Descripción | Criterios de aceptación | Relacionado con (Epic ID) |
| :-- | :-- | :-- | :-- | :-- |
| **US01** | Sección hero del Landing Page | Como visitante, deseo comprender en la primera pantalla qué problema resuelve SEMS, para decidir en segundos si me interesa. | **Escenario:** el visitante llega al Landing Page.<br>**Given** el visitante accede a la página principal,<br>**When** la página termina de cargar,<br>**Then** se muestra la propuesta de valor centrada en el control del costo energético de establecimientos comerciales<br>**And** se muestra un call-to-action visible hacia el registro. | EP01 |
| **US02** | Explicación del cargo por potencia | Como visitante del segmento de establecimientos, deseo entender por qué un pico de minutos encarece mi recibo del mes, para reconocer el problema como propio. | **Given** el visitante se desplaza a la sección de problemática,<br>**When** visualiza el contenido,<br>**Then** se presenta con un ejemplo numérico la diferencia entre el costo de energía y el cargo por potencia. | EP01 |
| **US03** | Sección de planes en el Landing Page | Como visitante, deseo conocer los planes y sus límites, para estimar cuál corresponde a mi caso antes de registrarme. | **Given** el visitante accede a la sección de planes,<br>**When** visualiza el contenido,<br>**Then** se muestran los planes disponibles con su precio y su límite de locales<br>**And** cada plan presenta un call-to-action que redirige al registro de la aplicación web. | EP01 |
| **US04** | Navegación del Landing Page | Como visitante, deseo desplazarme entre las secciones del Landing Page, para revisar la información en el orden que me interesa. | **Given** el visitante se encuentra en cualquier sección,<br>**When** selecciona un elemento del menú de navegación,<br>**Then** la vista se desplaza a la sección correspondiente. | EP01 |
| **US05** | Selección de idioma en el Landing Page | Como visitante, deseo cambiar el idioma del Landing Page, para leer el contenido en el idioma que domino. | **Given** el visitante se encuentra en el Landing Page,<br>**When** selecciona un idioma disponible,<br>**Then** el contenido textual se presenta en el idioma seleccionado<br>**And** la selección persiste al navegar entre secciones. | EP01 |
| **US06** | Registro de cuenta | Como visitante, deseo crear una cuenta con mi correo y contraseña, para acceder a la aplicación. | **Escenario 1:** registro correcto.<br>**Given** el visitante proporciona un correo no registrado y una contraseña válida,<br>**When** confirma el registro,<br>**Then** la cuenta se crea y se emite un token de sesión.<br><br>**Escenario 2:** correo ya registrado.<br>**Given** el visitante proporciona un correo existente,<br>**When** confirma el registro,<br>**Then** el sistema informa que el correo ya está en uso y no crea una cuenta duplicada. | EP02 |
| **US07** | Inicio de sesión | Como usuario registrado, deseo iniciar sesión, para acceder a la información de mis locales. | **Escenario 1:** credenciales correctas.<br>**Given** el usuario proporciona credenciales válidas,<br>**When** confirma el inicio de sesión,<br>**Then** se emite un token de sesión y accede a la aplicación.<br><br>**Escenario 2:** credenciales incorrectas.<br>**Given** el usuario proporciona una contraseña incorrecta,<br>**When** confirma el inicio de sesión,<br>**Then** el acceso se rechaza sin revelar si el correo existe. | EP02 |
| **US08** | Recuperación de contraseña | Como usuario registrado, deseo restablecer mi contraseña, para recuperar el acceso si la olvido. | **Given** el usuario solicita el restablecimiento indicando su correo,<br>**When** confirma la solicitud,<br>**Then** el sistema responde de forma idéntica exista o no la cuenta<br>**And** si la cuenta existe, se envía un enlace de restablecimiento de un solo uso. | EP02 |
| **US09** | Cierre de sesión | Como usuario autenticado, deseo cerrar sesión, para impedir el acceso desde un equipo compartido del local. | **Given** el usuario tiene una sesión activa,<br>**When** cierra la sesión,<br>**Then** el token deja de ser válido para peticiones posteriores. | EP02 |
| **US10** | Asignación de acceso a una persona | Como administrador de la organización, deseo dar acceso a una persona indicando su papel y su alcance, para que gestione únicamente lo que le corresponde. | **Escenario 1:** supervisor con local asignado.<br>**Given** el administrador indica el papel *supervisor* y un local de su organización,<br>**When** confirma la asignación,<br>**Then** el vínculo se crea y la persona accede solo a ese local.<br><br>**Escenario 2:** supervisor sin local.<br>**Given** el administrador indica el papel *supervisor* sin local,<br>**When** confirma la asignación,<br>**Then** la operación se rechaza indicando que un supervisor requiere un local asignado. | EP02 |
| **US11** | Revocación de acceso | Como administrador, deseo revocar el acceso de una persona, para retirar permisos cuando deja el puesto. | **Escenario 1:** revocación válida.<br>**Given** existe más de un administrador en la organización,<br>**When** el administrador revoca un vínculo,<br>**Then** la persona pierde el acceso.<br><br>**Escenario 2:** último administrador.<br>**Given** queda un único administrador,<br>**When** se intenta revocar su vínculo,<br>**Then** la operación se rechaza para no dejar la organización sin gestión posible. | EP02 |
| **US12** | Registro de la organización | Como administrador, deseo registrar mi empresa con su RUC y tipo de negocio, para agrupar bajo ella todos mis locales. | **Escenario 1:** RUC válido.<br>**Given** el administrador proporciona una razón social y un RUC de once dígitos no registrado,<br>**When** confirma el registro,<br>**Then** la organización se crea y queda como administrador de ella.<br><br>**Escenario 2:** RUC con formato inválido.<br>**Given** el RUC no tiene once dígitos numéricos,<br>**When** confirma el registro,<br>**Then** la operación se rechaza indicando el formato esperado.<br><br>**Escenario 3:** RUC duplicado.<br>**Given** el RUC ya pertenece a otra organización,<br>**When** confirma el registro,<br>**Then** la operación se rechaza. | EP03 |
| **US13** | Registro de un local | Como administrador, deseo registrar un local con su potencia contratada y su categoría tarifaria, para que el sistema calcule sobre la tarifa que realmente le aplica. | **Escenario 1:** alta correcta.<br>**Given** el administrador proporciona código, nombre, potencia contratada mayor que cero y categoría tarifaria válida,<br>**When** confirma el alta,<br>**Then** el local queda registrado en la organización.<br><br>**Escenario 2:** código duplicado.<br>**Given** el código de local ya existe en esa organización,<br>**When** confirma el alta,<br>**Then** la operación se rechaza.<br><br>**Escenario 3:** potencia no válida.<br>**Given** la potencia contratada es cero o negativa,<br>**When** confirma el alta,<br>**Then** la operación se rechaza. | EP03 |
| **US14** | Consulta de los locales de la organización | Como responsable de operaciones, deseo ver la lista de mis locales vigentes, para acceder a cada uno desde un punto único. | **Given** el usuario está autenticado y pertenece a la organización,<br>**When** consulta los locales,<br>**Then** se listan los locales vigentes<br>**And** los locales archivados no aparecen en el listado. | EP03 |
| **US15** | Actualización de los datos de un local | Como supervisor, deseo actualizar los datos de mi local, para reflejar un cambio de potencia contratada o de categoría tarifaria. | **Given** el supervisor modifica la potencia contratada de su local por un valor mayor que cero,<br>**When** confirma el cambio,<br>**Then** los cálculos posteriores de factura estimada utilizan el nuevo valor. | EP03 |
| **US16** | Archivado de un local | Como administrador, deseo archivar un local que ha cerrado, para que deje de aparecer sin perder su histórico. | **Given** el administrador archiva un local,<br>**When** consulta el listado de locales,<br>**Then** el local no aparece<br>**And** su información histórica permanece almacenada. | EP03 |
| **US17** | Consulta de mis organizaciones | Como usuario, deseo ver a qué organizaciones pertenezco y con qué papel, para cambiar de contexto cuando trabajo para más de una. | **Given** el usuario tiene vínculos vigentes con una o más organizaciones,<br>**When** consulta sus organizaciones,<br>**Then** se listan con el papel y el alcance que tiene en cada una. | EP03 |
| **US18** | Registro de zonas de un local | Como supervisor, deseo dividir mi local en zonas, para saber en qué parte se consume la energía. | **Escenario 1:** alta de zona.<br>**Given** el supervisor indica un nombre y un tipo de zona válido,<br>**When** confirma el alta,<br>**Then** la zona queda registrada en el local.<br><br>**Escenario 2:** deducción del funcionamiento fuera de horario.<br>**Given** el supervisor registra una zona de tipo cámara frigorífica sin especificar si opera fuera del horario,<br>**When** confirma el alta,<br>**Then** la zona se marca como operativa fuera del horario de atención. | EP04 |
| **US19** | Registro de un medidor en un local | Como supervisor, deseo registrar un medidor indicando su local y su zona, para atribuir su consumo al suministro y al área correctos. | **Escenario 1:** alta correcta.<br>**Given** el supervisor indica un local vigente y una zona perteneciente a ese local,<br>**When** confirma el alta,<br>**Then** el medidor queda asociado a ese local y a esa zona.<br><br>**Escenario 2:** zona de otro local.<br>**Given** la zona indicada pertenece a un local distinto,<br>**When** confirma el alta,<br>**Then** la operación se rechaza.<br><br>**Escenario 3:** código de medidor duplicado.<br>**Given** el código externo del medidor ya está registrado,<br>**When** confirma el alta,<br>**Then** la operación se rechaza. | EP04 |
| **US20** | Consulta de medidores por local | Como supervisor, deseo ver los medidores instalados en mi local, para verificar la cobertura de la medición. | **Given** el supervisor consulta los medidores de su local,<br>**When** se obtiene el listado,<br>**Then** se muestran los medidores vigentes del local<br>**And** los medidores dados de baja no aparecen. | EP04 |
| **US21** | Consulta de medidores por zona | Como supervisor, deseo ver los medidores de una zona concreta, para revisar el consumo de esa área. | **Given** el supervisor consulta los medidores de una zona,<br>**When** se obtiene el listado,<br>**Then** se muestran únicamente los medidores asignados a esa zona. | EP04 |
| **US22** | Traslado de un medidor entre zonas | Como supervisor, deseo reasignar un medidor a otra zona del mismo local, para reflejar un traslado de equipo. | **Escenario 1:** zona del mismo local.<br>**Given** la zona destino pertenece al local del medidor,<br>**When** el supervisor confirma el cambio,<br>**Then** el medidor queda asignado a la nueva zona.<br><br>**Escenario 2:** zona de otro local.<br>**Given** la zona destino pertenece a otro local,<br>**When** el supervisor confirma el cambio,<br>**Then** la operación se rechaza. | EP04 |
| **US23** | Baja de un medidor | Como supervisor, deseo dar de baja un medidor retirado, para que deje de contar en mi cupo y en los listados. | **Given** el supervisor da de baja un medidor,<br>**When** consulta nuevamente los medidores del local,<br>**Then** el medidor no aparece<br>**And** el cupo de medidores del plan se libera<br>**And** las lecturas históricas del medidor se conservan. | EP04 |
| **US24** | Consulta del consumo actual | Como supervisor, deseo ver el consumo actual de mi local, para saber cómo está operando en este momento. | **Given** el local tiene al menos un medidor con lecturas,<br>**When** el supervisor consulta el consumo actual,<br>**Then** se presenta la última lectura registrada con su marca de tiempo. | EP05 |
| **US25** | Consulta del histórico de consumo | Como supervisor, deseo consultar el consumo histórico de un medidor, para comparar periodos. | **Given** el supervisor indica un medidor y un rango,<br>**When** consulta el histórico,<br>**Then** se presentan las lecturas del periodo ordenadas cronológicamente. | EP05 |
| **US26** | Consumo desglosado por zona | Como supervisor, deseo ver el consumo agrupado por zona, para identificar qué área concentra el gasto. | **Given** el local tiene zonas con medidores asignados,<br>**When** el supervisor consulta el consumo por zona,<br>**Then** se presenta el consumo agregado de cada zona en el periodo. | EP05 |
| **US27** | Consulta de la tarifa vigente | Como supervisor, deseo consultar la tarifa aplicable a mi local, para conocer los precios de energía y el cargo por potencia. | **Given** el local tiene una categoría tarifaria asignada,<br>**When** el supervisor consulta la tarifa,<br>**Then** se presentan el precio de energía en punta, el precio fuera de punta, el cargo por potencia y el horario de punta vigente. | EP05 |
| **US28** | Creación de una regla de demanda | Como responsable, deseo definir a qué porcentaje de mi potencia contratada quiero ser avisado, para tener margen de reacción. | **Escenario 1:** regla válida.<br>**Given** el responsable indica una potencia contratada mayor que cero y un porcentaje de aviso entre 1 y 100,<br>**When** confirma la creación,<br>**Then** la regla queda activa para el local.<br><br>**Escenario 2:** porcentaje fuera de rango.<br>**Given** el porcentaje indicado es cero o mayor que 100,<br>**When** confirma la creación,<br>**Then** la operación se rechaza. | EP06 |
| **US29** | Aviso de demanda con margen | Como responsable, deseo recibir un aviso cuando la demanda de mi local se acerca a la potencia contratada, para reducir carga antes del recargo. | **Given** existe una regla de demanda activa con umbral de aviso,<br>**When** la demanda registrada alcanza o supera el umbral sin superar la potencia contratada,<br>**Then** se genera una alerta de severidad *warning*<br>**And** la alerta indica cuántos kW de margen quedan. | EP06 |
| **US30** | Aviso de exceso de potencia | Como responsable, deseo saber cuándo he superado la potencia contratada, para dimensionar el recargo del periodo y evitar que se repita. | **Given** existe una regla de demanda activa,<br>**When** la demanda registrada supera la potencia contratada,<br>**Then** se genera una alerta de severidad *critical*<br>**And** la alerta indica cuántos kW se ha excedido. | EP06 |
| **US31** | Ausencia de aviso por debajo del umbral | Como responsable, deseo no recibir avisos cuando la operación es normal, para que la alerta conserve su valor. | **Given** existe una regla de demanda activa,<br>**When** la demanda registrada es inferior al umbral de aviso,<br>**Then** no se genera ninguna alerta. | EP06 |
| **US32** | Umbrales de consumo por dispositivo | Como supervisor, deseo definir umbrales de consumo para un equipo, para detectar comportamientos anómalos. | **Given** el supervisor define un umbral con un operador y un valor para un dispositivo,<br>**When** una lectura del dispositivo cumple la condición del umbral,<br>**Then** se genera una alerta de consumo asociada al dispositivo. | EP06 |
| **US33** | Consulta y resolución de alertas | Como supervisor, deseo revisar y marcar como resueltas las alertas de mi local, para llevar control de las atendidas. | **Given** existen alertas generadas para el usuario,<br>**When** consulta el listado,<br>**Then** se presentan con su severidad, mensaje y estado<br>**And** al marcar una alerta como resuelta, su estado cambia y deja de figurar como pendiente. | EP06 |
| **US34** | Preferencias de notificación | Como responsable, deseo configurar por qué canal y con qué severidad mínima recibo avisos, para no ser interrumpido por alertas menores. | **Given** el responsable define una severidad mínima y un canal,<br>**When** se genera una alerta de severidad inferior a la configurada,<br>**Then** la alerta se registra pero no se notifica por ese canal. | EP06 |
| **US35** | Proyección de factura del periodo | Como responsable, deseo conocer la factura estimada de mi local desglosada, para saber qué concepto pesa más. | **Given** el responsable indica el consumo previsto en punta y fuera de punta, la demanda máxima y la potencia contratada del local,<br>**When** solicita la proyección,<br>**Then** se presentan el costo de energía, el costo de potencia, el cargo fijo, el IGV y el total<br>**And** se indica si existe exceso sobre la potencia contratada. | EP07 |
| **US36** | Peso del cargo por potencia | Como responsable, deseo ver qué proporción de mi factura corresponde al cargo por potencia, para decidir si conviene actuar sobre el pico o sobre el consumo. | **Given** existe una proyección de factura calculada,<br>**When** el responsable la consulta,<br>**Then** se presenta la proporción del subtotal que corresponde al cargo por potencia. | EP07 |
| **US37** | Recomendaciones de ahorro | Como responsable, deseo recibir recomendaciones concretas para reducir mi costo, para saber por dónde empezar. | **Given** existen datos de consumo del local por franja horaria,<br>**When** el responsable consulta las recomendaciones,<br>**Then** se presentan recomendaciones con el ahorro estimado asociado a cada una. | EP07 |
| **US38** | Detección de anomalías de consumo | Como supervisor, deseo que el sistema señale consumos atípicos, para investigar posibles fallas o desperdicios. | **Given** existe un histórico de consumo del local,<br>**When** una lectura se desvía significativamente del patrón del periodo,<br>**Then** se registra una anomalía consultable por el usuario. | EP07 |
| **US39** | Comparación entre locales | Como responsable de operaciones, deseo comparar el desempeño energético de mis locales, para identificar los que están peor. | **Given** la organización tiene dos o más locales con datos de consumo,<br>**When** el responsable consulta la comparación,<br>**Then** se presentan los locales ordenados por un indicador comparable entre ellos. | EP07 |
| **US40** | Consulta de planes disponibles | Como administrador, deseo ver los planes con sus límites y precios, para elegir el que corresponde a mi cadena. | **Given** el administrador está autenticado,<br>**When** consulta los planes,<br>**Then** se listan los planes con su precio, su límite de locales y su límite de medidores por local. | EP08 |
| **US41** | Contratación de un plan | Como administrador, deseo contratar un plan, para habilitar las funcionalidades que necesita mi organización. | **Given** el administrador selecciona un plan y un método de pago válido,<br>**When** confirma la contratación,<br>**Then** la suscripción queda activa para la organización<br>**And** se habilitan los límites correspondientes al plan. | EP08 |
| **US42** | Límite de locales según el plan | Como administrador, deseo que el sistema respete el límite de locales de mi plan, para conocer cuándo necesito ampliarlo. | **Given** la organización alcanzó el límite de locales de su plan,<br>**When** intenta registrar un local adicional,<br>**Then** la operación se rechaza indicando el límite del plan vigente. | EP08 |
| **US43** | Registro de método de pago | Como administrador, deseo registrar un método de pago, para automatizar la renovación de la suscripción. | **Given** el administrador proporciona los datos de la tarjeta en el formulario de la pasarela,<br>**When** confirma el registro,<br>**Then** el método de pago queda asociado a la organización<br>**And** los datos de la tarjeta no son almacenados por la aplicación. | EP08 |
| **US44** | Consulta de comprobantes | Como administrador, deseo consultar mis comprobantes de pago, para llevar el control contable de la suscripción. | **Given** existen pagos registrados para la organización,<br>**When** el administrador consulta los comprobantes,<br>**Then** se listan con su fecha, importe y estado. | EP08 |
| **TS01** | API de autenticación | Como developer, deseo un endpoint de autenticación que emita tokens, para proteger el acceso a los recursos del API. | **Escenario 1:** credenciales válidas.<br>**Given** una petición `POST /api/v1/auth/login` con credenciales válidas,<br>**When** el servicio procesa la petición,<br>**Then** responde `200 OK` con un token de sesión.<br><br>**Escenario 2:** credenciales inválidas.<br>**Given** una petición con contraseña incorrecta,<br>**When** el servicio procesa la petición,<br>**Then** responde `401 Unauthorized` sin indicar si el correo existe. | EP09 |
| **TS02** | Protección por defecto de los endpoints | Como developer, deseo que todo endpoint exija sesión salvo los explícitamente públicos, para que un descuido no deje un recurso abierto. | **Escenario 1:** sin token.<br>**Given** una petición a un endpoint protegido sin cabecera de autorización,<br>**When** el servicio la procesa,<br>**Then** responde `401 Unauthorized`.<br><br>**Escenario 2:** token inválido.<br>**Given** una petición con un token mal formado,<br>**When** el servicio la procesa,<br>**Then** responde `401 Unauthorized`. | EP09 |
| **TS03** | API de organizaciones y locales | Como developer, deseo endpoints para gestionar organizaciones, locales y zonas, para que las aplicaciones cliente construyan la jerarquía del negocio. | **Escenario 1:** alta correcta.<br>**Given** una petición `POST /api/v1/organizations` con cuerpo válido y token,<br>**When** el servicio la procesa,<br>**Then** responde `201 Created` con el recurso creado.<br><br>**Escenario 2:** recurso inexistente.<br>**Given** una petición `GET /api/v1/organizations/{id}` con un identificador no registrado,<br>**When** el servicio la procesa,<br>**Then** responde `404 Not Found`.<br><br>**Escenario 3:** identificador mal formado.<br>**Given** una petición con un identificador que no es un UUID,<br>**When** el servicio la procesa,<br>**Then** responde `400 Bad Request`. | EP09 |
| **TS04** | API de cálculo de factura | Como developer, deseo un endpoint que calcule la factura estimada a partir del consumo y la demanda, para que las aplicaciones no repliquen la lógica tarifaria. | **Given** una petición `POST /api/v1/energy/bill-estimate` con categoría tarifaria, potencia contratada, consumo por franja y demanda máxima,<br>**When** el servicio la procesa,<br>**Then** responde `200 OK` con el desglose de energía, potencia, cargo fijo, IGV y total. | EP09 |
| **TS05** | API de evaluación de demanda | Como developer, deseo un endpoint que evalúe una demanda medida contra las reglas del local, para generar las alertas correspondientes. | **Given** una petición `POST /api/v1/sites/{siteId}/demand-evaluations` con la demanda medida,<br>**When** el servicio la procesa,<br>**Then** responde `200 OK` con las alertas generadas<br>**And** devuelve una lista vacía si ninguna regla resulta incumplida. | EP09 |
| **TS06** | Documentación OpenAPI | Como developer, deseo la especificación OpenAPI publicada, para conocer el contrato sin leer el código fuente. | **Given** una petición `GET /swagger/v1/swagger.json` o `GET /v3/api-docs`,<br>**When** el servicio la procesa,<br>**Then** responde `200 OK` con la especificación válida de todos los endpoints expuestos. | EP09 |
| **TS07** | Endpoints de salud del servicio | Como developer, deseo endpoints de salud diferenciados, para que el proveedor de hosting distinga un proceso caído de una base de datos inaccesible. | **Escenario 1:** proceso vivo.<br>**Given** una petición al endpoint de *liveness*,<br>**When** el proceso está en ejecución,<br>**Then** responde `200 OK` aunque la base de datos no esté disponible.<br><br>**Escenario 2:** dependencia caída.<br>**Given** una petición al endpoint de *readiness* con la base de datos inaccesible,<br>**When** el servicio la procesa,<br>**Then** responde `503 Service Unavailable`. | EP09 |
| **TS08** | Webhook de la pasarela de pagos | Como developer, deseo un endpoint de webhook autenticado por firma, para confirmar los pagos sin exponer un recurso abierto. | **Escenario 1:** firma ausente.<br>**Given** una petición al webhook sin cabecera de firma,<br>**When** el servicio la procesa,<br>**Then** responde `400 Bad Request`.<br><br>**Escenario 2:** firma válida.<br>**Given** una petición con firma válida,<br>**When** el servicio la procesa,<br>**Then** responde `200 OK` y actualiza el estado del pago. | EP09 |
| **TS09** | Configuración de CORS | Como developer, deseo restringir los orígenes que pueden consumir el API desde un navegador, para impedir el uso desde sitios no autorizados. | **Escenario 1:** origen permitido.<br>**Given** una petición de comprobación previa desde un origen registrado,<br>**When** el servicio la procesa,<br>**Then** responde con la cabecera de origen permitido.<br><br>**Escenario 2:** origen no permitido.<br>**Given** una petición desde un origen no registrado,<br>**When** el servicio la procesa,<br>**Then** la respuesta no incluye cabecera de origen permitido. | EP09 |

## 3.3. Product Backlog

El orden del Product Backlog lo determina el valor para el negocio. Se sitúan primero las
historias del Landing Page, por ser el punto de entrada del modelo de negocio y por requerirse
desde el primer sprint, seguidas de la construcción de la jerarquía de organización, local y zona,
que es la que habilita todo lo demás. Las historias de control de demanda —el diferencial del
producto— se priorizan por delante de la analítica avanzada y de los pagos.

**Herramienta:** `<Pivotal Tracker / Jira / Trello>`
**URL pública del Product Backlog:** `<...>`
`<Insertar captura del Product Backlog en la herramienta>`

| # Orden | User Story Id | Título | Descripción | Story Points |
| :-- | :-- | :-- | :-- | :-- |
| 1 | US01 | Sección hero del Landing Page | Como visitante, deseo comprender en la primera pantalla qué problema resuelve SEMS, para decidir en segundos si me interesa. | 3 |
| 2 | US02 | Explicación del cargo por potencia | Como visitante del segmento de establecimientos, deseo entender por qué un pico de minutos encarece mi recibo del mes, para reconocer el problema como propio. | 3 |
| 3 | US04 | Navegación del Landing Page | Como visitante, deseo desplazarme entre las secciones del Landing Page, para revisar la información en el orden que me interesa. | 2 |
| 4 | US03 | Sección de planes en el Landing Page | Como visitante, deseo conocer los planes y sus límites, para estimar cuál corresponde a mi caso antes de registrarme. | 3 |
| 5 | TS06 | Documentación OpenAPI | Como developer, deseo la especificación OpenAPI publicada, para conocer el contrato sin leer el código fuente. | 2 |
| 6 | US06 | Registro de cuenta | Como visitante, deseo crear una cuenta con mi correo y contraseña, para acceder a la aplicación. | 3 |
| 7 | US07 | Inicio de sesión | Como usuario registrado, deseo iniciar sesión, para acceder a la información de mis locales. | 3 |
| 8 | TS01 | API de autenticación | Como developer, deseo un endpoint de autenticación que emita tokens, para proteger el acceso a los recursos del API. | 3 |
| 9 | TS02 | Protección por defecto de los endpoints | Como developer, deseo que todo endpoint exija sesión salvo los explícitamente públicos, para que un descuido no deje un recurso abierto. | 3 |
| 10 | US12 | Registro de la organización | Como administrador, deseo registrar mi empresa con su RUC y tipo de negocio, para agrupar bajo ella todos mis locales. | 5 |
| 11 | US13 | Registro de un local | Como administrador, deseo registrar un local con su potencia contratada y su categoría tarifaria, para que el sistema calcule sobre la tarifa que realmente le aplica. | 5 |
| 12 | US14 | Consulta de los locales de la organización | Como responsable de operaciones, deseo ver la lista de mis locales vigentes, para acceder a cada uno desde un punto único. | 3 |
| 13 | TS03 | API de organizaciones y locales | Como developer, deseo endpoints para gestionar organizaciones, locales y zonas, para que las aplicaciones cliente construyan la jerarquía del negocio. | 5 |
| 14 | US18 | Registro de zonas de un local | Como supervisor, deseo dividir mi local en zonas, para saber en qué parte se consume la energía. | 3 |
| 15 | US19 | Registro de un medidor en un local | Como supervisor, deseo registrar un medidor indicando su local y su zona, para atribuir su consumo al suministro y al área correctos. | 5 |
| 16 | US20 | Consulta de medidores por local | Como supervisor, deseo ver los medidores instalados en mi local, para verificar la cobertura de la medición. | 2 |
| 17 | US27 | Consulta de la tarifa vigente | Como supervisor, deseo consultar la tarifa aplicable a mi local, para conocer los precios de energía y el cargo por potencia. | 3 |
| 18 | US24 | Consulta del consumo actual | Como supervisor, deseo ver el consumo actual de mi local, para saber cómo está operando en este momento. | 3 |
| 19 | US28 | Creación de una regla de demanda | Como responsable, deseo definir a qué porcentaje de mi potencia contratada quiero ser avisado, para tener margen de reacción. | 5 |
| 20 | US29 | Aviso de demanda con margen | Como responsable, deseo recibir un aviso cuando la demanda de mi local se acerca a la potencia contratada, para reducir carga antes del recargo. | 8 |
| 21 | US30 | Aviso de exceso de potencia | Como responsable, deseo saber cuándo he superado la potencia contratada, para dimensionar el recargo del periodo y evitar que se repita. | 3 |
| 22 | US31 | Ausencia de aviso por debajo del umbral | Como responsable, deseo no recibir avisos cuando la operación es normal, para que la alerta conserve su valor. | 2 |
| 23 | TS05 | API de evaluación de demanda | Como developer, deseo un endpoint que evalúe una demanda medida contra las reglas del local, para generar las alertas correspondientes. | 5 |
| 24 | US35 | Proyección de factura del periodo | Como responsable, deseo conocer la factura estimada de mi local desglosada, para saber qué concepto pesa más. | 8 |
| 25 | US36 | Peso del cargo por potencia | Como responsable, deseo ver qué proporción de mi factura corresponde al cargo por potencia, para decidir si conviene actuar sobre el pico o sobre el consumo. | 3 |
| 26 | TS04 | API de cálculo de factura | Como developer, deseo un endpoint que calcule la factura estimada a partir del consumo y la demanda, para que las aplicaciones no repliquen la lógica tarifaria. | 5 |
| 27 | US25 | Consulta del histórico de consumo | Como supervisor, deseo consultar el consumo histórico de un medidor, para comparar periodos. | 3 |
| 28 | US26 | Consumo desglosado por zona | Como supervisor, deseo ver el consumo agrupado por zona, para identificar qué área concentra el gasto. | 5 |
| 29 | US21 | Consulta de medidores por zona | Como supervisor, deseo ver los medidores de una zona concreta, para revisar el consumo de esa área. | 2 |
| 30 | US10 | Asignación de acceso a una persona | Como administrador de la organización, deseo dar acceso a una persona indicando su papel y su alcance, para que gestione únicamente lo que le corresponde. | 5 |
| 31 | US11 | Revocación de acceso | Como administrador, deseo revocar el acceso de una persona, para retirar permisos cuando deja el puesto. | 3 |
| 32 | US17 | Consulta de mis organizaciones | Como usuario, deseo ver a qué organizaciones pertenezco y con qué papel, para cambiar de contexto cuando trabajo para más de una. | 3 |
| 33 | US33 | Consulta y resolución de alertas | Como supervisor, deseo revisar y marcar como resueltas las alertas de mi local, para llevar control de las atendidas. | 3 |
| 34 | US32 | Umbrales de consumo por dispositivo | Como supervisor, deseo definir umbrales de consumo para un equipo, para detectar comportamientos anómalos. | 5 |
| 35 | US34 | Preferencias de notificación | Como responsable, deseo configurar por qué canal y con qué severidad mínima recibo avisos, para no ser interrumpido por alertas menores. | 3 |
| 36 | US15 | Actualización de los datos de un local | Como supervisor, deseo actualizar los datos de mi local, para reflejar un cambio de potencia contratada o de categoría tarifaria. | 2 |
| 37 | US22 | Traslado de un medidor entre zonas | Como supervisor, deseo reasignar un medidor a otra zona del mismo local, para reflejar un traslado de equipo. | 3 |
| 38 | US23 | Baja de un medidor | Como supervisor, deseo dar de baja un medidor retirado, para que deje de contar en mi cupo y en los listados. | 3 |
| 39 | US16 | Archivado de un local | Como administrador, deseo archivar un local que ha cerrado, para que deje de aparecer sin perder su histórico. | 2 |
| 40 | US39 | Comparación entre locales | Como responsable de operaciones, deseo comparar el desempeño energético de mis locales, para identificar los que están peor. | 8 |
| 41 | US37 | Recomendaciones de ahorro | Como responsable, deseo recibir recomendaciones concretas para reducir mi costo, para saber por dónde empezar. | 5 |
| 42 | US38 | Detección de anomalías de consumo | Como supervisor, deseo que el sistema señale consumos atípicos, para investigar posibles fallas o desperdicios. | 8 |
| 43 | US40 | Consulta de planes disponibles | Como administrador, deseo ver los planes con sus límites y precios, para elegir el que corresponde a mi cadena. | 2 |
| 44 | US42 | Límite de locales según el plan | Como administrador, deseo que el sistema respete el límite de locales de mi plan, para conocer cuándo necesito ampliarlo. | 3 |
| 45 | US43 | Registro de método de pago | Como administrador, deseo registrar un método de pago, para automatizar la renovación de la suscripción. | 5 |
| 46 | US41 | Contratación de un plan | Como administrador, deseo contratar un plan, para habilitar las funcionalidades que necesita mi organización. | 8 |
| 47 | TS08 | Webhook de la pasarela de pagos | Como developer, deseo un endpoint de webhook autenticado por firma, para confirmar los pagos sin exponer un recurso abierto. | 5 |
| 48 | US44 | Consulta de comprobantes | Como administrador, deseo consultar mis comprobantes de pago, para llevar el control contable de la suscripción. | 3 |
| 49 | US08 | Recuperación de contraseña | Como usuario registrado, deseo restablecer mi contraseña, para recuperar el acceso si la olvido. | 3 |
| 50 | US09 | Cierre de sesión | Como usuario autenticado, deseo cerrar sesión, para impedir el acceso desde un equipo compartido del local. | 2 |
| 51 | US05 | Selección de idioma en el Landing Page | Como visitante, deseo cambiar el idioma del Landing Page, para leer el contenido en el idioma que domino. | 3 |
| 52 | TS07 | Endpoints de salud del servicio | Como developer, deseo endpoints de salud diferenciados, para que el proveedor de hosting distinga un proceso caído de una base de datos inaccesible. | 2 |
| 53 | TS09 | Configuración de CORS | Como developer, deseo restringir los orígenes que pueden consumir el API desde un navegador, para impedir el uso desde sitios no autorizados. | 2 |

## 3.4. Impact Mapping

> Se elabora en **UXPressia**, a partir de las fichas de los User Personas de la sección 2.3.1.

**Business Goals (SMART)**

| ID | Business Goal |
| :-- | :-- |
| BG01 | Alcanzar 120 locales activos con suscripción de pago en un plazo de 12 meses desde el lanzamiento. |
| BG02 | Lograr que el 60% de las alertas de demanda de nivel *warning* vayan seguidas de una reducción de carga dentro de los 30 minutos siguientes, medido durante el segundo trimestre de operación. |
| BG03 | Alcanzar una tasa de renovación mensual del 85% entre las organizaciones suscritas, medida al sexto mes. |
| BG04 | Conseguir que 15 organizaciones con más de cinco locales adopten el plan *Enterprise* en los primeros 12 meses. |

**Estructura del Impact Map**

| Goal | Actor | Impact | Deliverable | User Stories |
| :-- | :-- | :-- | :-- | :-- |
| BG02 | Responsable de operaciones de cadena | Que reaccione ante el aviso reduciendo carga en lugar de ignorarlo | Alerta de demanda con margen expresado en kW y canal de notificación configurable | US28, US29, US30, US34 |
| BG02 | Propietario de establecimiento independiente | Que comprenda qué significa el aviso sin formación eléctrica | Mensaje de alerta redactado en términos de margen y de costo, no de magnitudes eléctricas | US29, US30 |
| BG01 | Propietario de establecimiento independiente | Que registre su local y su medidor sin apoyo técnico | Flujo de alta guiado de organización, local, zona y medidor | US12, US13, US18, US19 |
| BG01 | Visitante del Landing Page | Que reconozca el problema del cargo por potencia como propio | Sección del Landing Page con ejemplo numérico del impacto de un pico | US02, US03 |
| BG03 | Responsable de operaciones de cadena | Que use la plataforma de forma sostenida y no solo al inicio | Proyección de factura desglosada y comparación entre locales | US35, US36, US39 |
| BG04 | Responsable de operaciones de cadena | Que incorpore locales adicionales a la plataforma | Gestión multi-local con permisos por sede y límites por plan | US10, US14, US40, US42 |

`<Insertar imagen del Impact Map elaborado en UXPressia>`



# Capítulo IV: Product Design

Este capítulo recoge las decisiones de diseño del producto: el lenguaje visual común a los tres
artefactos de la solución, la arquitectura de la información, el diseño de interfaz del *Landing
Page* y de la aplicación web, la arquitectura de software y el diseño de datos.

## 4.1. Style Guidelines

### 4.1.1. General Style Guidelines

El lenguaje de diseño de toda la solución es **Material Design 3**. La decisión no es estética:
el enunciado del curso lo fija como restricción, y adoptarlo permite que el *Landing Page* y la
aplicación web compartan una misma gramática visual sin tener que mantener dos sistemas.

**Branding.** *Energix* es la startup; **SEMS** es el producto. En los artefactos digitales el
nombre visible es SEMS, y Energix aparece como responsable en el pie de página y en la sección
legal. La marca se apoya en un símbolo de rayo sobre un cuadrado de esquinas redondeadas, que
funciona a 32 px como favicon y a 36 px en la barra superior.

**Paleta.** Se usan los *color roles* de Material Design 3 en lugar de colores sueltos. Cada rol
tiene su pareja de contraste (`on-*`), lo que garantiza que ningún texto quede por debajo del
mínimo legible.

| Rol | Claro | Oscuro | Uso |
| :-- | :-- | :-- | :-- |
| `primary` | `#0b57d0` | `#adc6ff` | Acciones principales, enlaces, énfasis |
| `on-primary` | `#ffffff` | `#002e69` | Texto sobre `primary` |
| `primary-container` | `#d9e2ff` | `#00458f` | Fondos de realce, etiquetas |
| `tertiary` | `#146c2e` | `#a8d2b3` | Ahorro conseguido, estados favorables |
| `error` | `#b3261e` | `#f2b8b5` | Alerta de demanda, exceso de potencia |
| `surface` | `#fdfcff` | `#111318` | Fondo de página |
| `on-surface` | `#1a1c1e` | `#e2e2e6` | Texto principal |
| `on-surface-variant` | `#43474e` | `#c3c7cf` | Texto secundario |
| `outline-variant` | `#c3c7cf` | `#43474e` | Bordes y separadores |

El verde de `tertiary` se reserva para el ahorro y el rojo de `error` para la demanda por encima
de lo contratado. Esa asociación es constante en los tres artefactos: un número verde siempre
significa dinero que no se gastó, y un bloque rojo siempre significa un cargo que se va a aplicar.

**Tipografía.** *Roboto*, la familia tipográfica de Material Design, con la escala de tipos del
sistema. Se define una pila de reserva (`"Segoe UI", system-ui, -apple-system, sans-serif`) para
que la página siga siendo legible si la fuente remota no carga.

| Estilo | Tamaño | Peso | Uso |
| :-- | :-- | :-- | :-- |
| Display | `clamp(2.25rem, 1.4rem + 3.2vw, 3.5rem)` | 700 | Titular del *hero* |
| Headline | `clamp(1.75rem, 1.2rem + 2vw, 2.5rem)` | 700 | Títulos de sección |
| Title | 1.25 rem | 600 | Títulos de tarjeta |
| Body | 1 rem / 1.55 | 400 | Texto corrido |
| Label | 0.8125 rem | 600 | Etiquetas y *kickers* |

**Espaciado y forma.** Rejilla de 4 px. La escala de formas sigue la de Material Design: 4 px para
elementos pequeños, 12–16 px para tarjetas, 28 px para contenedores grandes y radio completo para
botones y *chips*.

**Movimiento.** Curva estándar `cubic-bezier(0.2, 0, 0, 1)` con duraciones de 150 ms (corta),
300 ms (media) y 500 ms (larga). Toda animación se desactiva bajo `prefers-reduced-motion`.

**Tono de voz.** Segunda persona, frases cortas y cifras concretas en soles. Se evita el
vocabulario técnico de ingeniería eléctrica en la interfaz de cara al cliente: se habla de
«consumo», «pico» y «potencia contratada», no de «factor de carga» ni de «demanda coincidente».

### 4.1.2. Web Style Guidelines

**Landing Page.** Implementado con HTML5, CSS3 y JavaScript sin framework. Los *color roles* y la
escala tipográfica se declaran como propiedades personalizadas de CSS sobre `:root`; el esquema
oscuro solo redefine esos tokens, de modo que no existe una segunda hoja de estilos que mantener.

Componentes de Material Design utilizados: botón relleno (*filled*), botón con contorno
(*outlined*), botón tonal, botón de icono, tarjeta con elevación, *chip* de asistencia y lista.
Los botones aplican el patrón de *state layer*: una capa translúcida del color actual al 8 % en
*hover* y al 12 % en foco y pulsación, en lugar de un cambio de color.

**Aplicación web.** Vue 3 con **PrimeVue** y su *preset* Material, tal como exige el enunciado
para el caso de Vue. La correspondencia entre ambos artefactos es directa: PrimeVue implementa los
mismos componentes de Material Design que el *Landing Page* construye a mano, por lo que un botón
principal se ve igual en los dos sitios.

| Elemento | Landing Page | Aplicación web |
| :-- | :-- | :-- |
| Botón principal | `.btn.btn-filled` | `<Button>` (*filled*) |
| Botón secundario | `.btn.btn-outlined` | `<Button outlined>` |
| Tarjeta | `.card` | `<Card>` |
| Tabla | `<table>` con estilos propios | `<DataTable>` |
| Aviso | `.mock-alert` | `<Message severity="error">` |

**Modo claro y oscuro.** Ambos artefactos ofrecen los dos temas. La preferencia se guarda en
`localStorage` y se aplica antes del primer pintado para evitar el parpadeo. Si no hay preferencia
guardada, se respeta `prefers-color-scheme`.

**Accesibilidad.** Se aplica **WCAG 2.1 nivel AA**:

- Contraste mínimo de 4.5:1 en texto normal, verificado en los dos temas.
- Objetivos táctiles de 48 × 48 px.
- Anillo de foco visible en todo elemento interactivo.
- Enlace de salto al contenido como primer elemento enfocable.
- Puntos de referencia semánticos (`header`, `nav`, `main`, `footer`) y un solo `h1` por página.
- Atributos ARIA en controles sin texto visible, en el acordeón de preguntas frecuentes
  (`aria-expanded` / `aria-controls`) y en el conmutador de tema (`aria-pressed`).

### 4.1.3. Mobile Style Guidelines

> Esta sección se completa cuando exista la aplicación nativa. La paleta, la tipografía y la
> escala de espaciado definidas en 4.1.1 son las que se trasladarán a ambas plataformas.

#### 4.1.3.1. iOS Mobile Style Guidelines

> `<Style guidelines para iOS.>`

#### 4.1.3.2. Android Mobile Style Guidelines

> `<Style guidelines para Android.>`

## 4.2. Information Architecture

### 4.2.1. Organization Systems

La solución organiza su contenido con tres esquemas distintos, cada uno donde corresponde:

| Esquema | Dónde se aplica | Ejemplo |
| :-- | :-- | :-- |
| **Secuencial** | *Landing Page* | El visitante recorre problema → funcionamiento → características → segmentos → planes → preguntas, en un orden pensado para construir el argumento |
| **Jerárquico** | Aplicación web | Organización → locales → zonas → medidores. Refleja la estructura real del cliente |
| **Matricial** | Analítica y reportes | El mismo consumo se puede ver por local, por zona, por periodo o por franja horaria |

La jerarquía de la aplicación web no es una decisión de interfaz sino del dominio: un medidor
pertenece a un local y opcionalmente a una zona, y esa relación es obligatoria en la API.

### 4.2.2. Labeling Systems

Las etiquetas visibles se toman del *Ubiquitous Language* de la sección 2.4, con su denominación
en inglés como forma canónica y su equivalente en español latinoamericano.

| Concepto | Etiqueta (en-US) | Etiqueta (es-419) | Nunca se usa |
| :-- | :-- | :-- | :-- |
| `Organization` | Organization | Organización | Empresa, cuenta |
| `Site` | Site | Local | Sucursal, tienda, hogar |
| `Zone` | Zone | Zona | Área, sección |
| `Meter` | Meter | Medidor | Sensor, dispositivo |
| `Peak hours` | Peak hours | Hora punta | Horario caro |
| `Contracted power` | Contracted power | Potencia contratada | Límite |
| `Maximum demand` | Maximum demand | Demanda máxima | Pico |
| `Power charge` | Power charge | Cargo por potencia | Cargo fijo |

La columna «nunca se usa» existe porque el producto viene de un segmento anterior de viviendas:
«hogar» y «sensor» son términos heredados que ya no corresponden al dominio comercial.

### 4.2.3. SEO Tags and Meta Tags

Etiquetas del *Landing Page*, en inglés por ser el idioma por defecto de la solución, con la
alternativa en español declarada:

| Etiqueta | Valor |
| :-- | :-- |
| `<title>` | SEMS — Stop paying for demand peaks you never saw |
| `<meta name="description">` | SEMS measures the electricity of supermarkets, stores and retail chains in real time, breaks consumption down by site and zone, and warns you before a demand peak raises your bill. A product by Energix. |
| `<html lang>` | `en-US`, conmutable a `es-419` |
| `og:type` | `website` |
| `og:title` | SEMS — Smart Energy Management System |
| `og:description` | Real-time electricity monitoring for commercial establishments in Peru. |
| `og:locale` | `en_US`, con `og:locale:alternate` = `es_419` |
| `twitter:card` | `summary_large_image` |
| `theme-color` | `#fdfcff` en claro y `#111318` en oscuro |

El título y la descripción también se traducen al cambiar de idioma, no solo el cuerpo de la
página: ambos llevan la marca `data-i18n` y el guion los sustituye junto al resto del contenido.

### 4.2.4. Searching Systems

El *Landing Page* no incorpora buscador: es una página única y la navegación por anclas cubre el
recorrido completo.

En la aplicación web la búsqueda es **filtrado dentro de cada vista**, no un buscador global:

| Vista | Filtro | Criterio |
| :-- | :-- | :-- |
| Dispositivos | Por local, por zona y por estado | Los dispositivos dados de baja no aparecen |
| Alertas | Por severidad y por estado de lectura | Las no leídas primero |
| Lecturas | Por rango de fechas y por dispositivo | Orden descendente por fecha |
| Analítica | Por periodo y por local | Comparación entre locales |

### 4.2.5. Navigation Systems

**Landing Page.** Barra superior fija con las cinco secciones y el llamado a la acción. En
pantallas menores de 860 px la barra se colapsa en un botón que despliega el menú, con
`aria-expanded` reflejando el estado. Los enlaces del pie repiten la navegación y añaden la
sección legal.

**Aplicación web.** Barra lateral persistente con las nueve vistas del producto, más una barra
superior con el título de la vista activa, el conmutador de idioma y el menú de la cuenta.

| Ruta | Vista | Acceso |
| :-- | :-- | :-- |
| `/login`, `/register` | Autenticación | Pública |
| `/forgot-password`, `/reset-password`, `/verify` | Recuperación y verificación | Pública |
| `/` | Resumen | Autenticada |
| `/devices` | Dispositivos | Autenticada |
| `/monitoring` | Monitoreo | Autenticada |
| `/analytics` | Analítica | Autenticada |
| `/alerts` | Alertas | Autenticada |
| `/reports` | Reportes | Autenticada |
| `/subscription` | Suscripción y pagos | Autenticada |
| `/settings` | Configuración | Autenticada |
| `/:pathMatch(.*)*` | No encontrado | Pública |

Un guardián de ruta comprueba la sesión antes de cada navegación y redirige a `/login` cuando no
hay token válido.

> **Deuda identificada.** La aplicación web conserva una vista `/household` («Mi hogar») heredada
> del segmento anterior de viviendas. No corresponde al dominio comercial y debe sustituirse por
> una vista de organización y locales. Queda registrada como deuda técnica en el capítulo V.

## 4.3. Landing Page UI Design

### 4.3.1. Landing Page Wireframe

![Landing](assets/landingWireframe.png) 

Estructura de bloques, de arriba abajo:

1. Barra superior con marca, navegación, idioma, tema y llamado a la acción.
2. *Hero* a dos columnas: propuesta de valor a la izquierda, vista previa del panel a la derecha.
3. Franja de cuatro cifras con su fuente citada.
4. Problema, en tres tarjetas.
5. Funcionamiento, en cuatro pasos numerados.
6. Características, en seis tarjetas.
7. Segmentos objetivo, en dos tarjetas con llamado a la acción propio.
8. Planes, en tres columnas con el plan intermedio destacado.
9. Preguntas frecuentes, en acordeón.
10. Llamado a la acción final.
11. Pie con navegación, enlaces legales y datos de contacto.

En navegador móvil las columnas colapsan a una sola y la navegación pasa al menú desplegable.

### 4.3.2. Landing Page Mock-up

![LandingMock](assets/landingMockup.png)

## 4.4. Mobile Applications UX/UI Design

En esta sección se presenta la propuesta de diseño UX/UI de la aplicación móvil de SEMS, describiendo la estructura visual, los elementos de interfaz y los patrones de interacción que orientan la experiencia del usuario tanto para coordinadores de cadenas como para propietarios independientes.

El diseño está enfocado en facilitar el monitoreo de energía y la gestión de alertas, priorizando una interacción clara, rápida y consistente. Asimismo, se mantiene la coherencia con los Style Guidelines y la Information Architecture establecidos.

### 4.4.1. Mobile Applications Wireframes

En esta sección se presentan los wireframes de fidelidad media para la aplicación móvil de SEMS, diseñada específicamente para los roles de Administrador de cadena (Segmento 1) y Propietario independiente (Segmento 2). La propuesta visual y funcional responde directamente a estándares de usabilidad móvil, estructuración de datos y accesibilidad.

<p align="center">
  <img src="assets/chapter4/wireframes/Screenshot_1.png" alt="wireframe 1" width="300"><br>
  Nota: Wireframe de Inicio de Sesión
</p>
<p align="center">
  <img src="assets/chapter4/wireframes/Screenshot_2.png" alt="wireframe 2" width="300"><br>
  Nota: Wireframe de Recuperación y Registro
</p>
<p align="center">
  <img src="assets/chapter4/wireframes/Screenshot_3.png" alt="wireframe 3" width="700"><br>
  Nota: Wireframe del Dashboard y Mis Dispositivos
</p>
<p align="center">
  <img src="assets/chapter4/wireframes/Screenshot_4.png" alt="wireframe 4" width="700"><br>
  Nota: Wireframe de Monitoreo y Escaneo de Medidores
</p>
<p align="center">
  <img src="assets/chapter4/wireframes/Screenshot_5.png" alt="wireframe 5" width="700"><br>
  Nota: Wireframe de Analíticas y Recomendaciones
</p>
<p align="center">
  <img src="assets/chapter4/wireframes/Screenshot_6.png" alt="wireframe 6" width="700"><br>
  Nota: Wireframe de Reportes, Suscripción y Organización
</p>
<p align="center">
  <img src="assets/chapter4/wireframes/Screenshot_7.png" alt="wireframe 7" width="500"><br>
  Nota: Wireframe de Configuración y Perfil
</p>
<p align="center">
  <img src="assets/chapter4/wireframes/Screenshot_8.png" alt="wireframe 8" width="500"><br>
  Nota: Wireframe de detalle de consumos
</p>
<p align="center">
  <img src="assets/chapter4/wireframes/Screenshot_9.png" alt="wireframe 9" width="300"><br>
  Nota: Wireframe de menús modales
</p>

### 4.4.2. Mobile Applications Wireflow Diagrams

**Segmento 1: Responsable de Operaciones de Cadena**

* User Goal: Como coordinador de cadena, quiero registrar un nuevo medidor inteligente escaneándolo con la cámara, para asignar en qué área del local está instalado y comenzar a monitorearlo.

Task Flow:
<p align="center"> 
<img src="assets/chapter4/wireflows/segmento%201/User%20goal-%20Administrar%20y%20vincular%20nuevos%20medidores%20inteligentes/taskflow.png" width="300">
<br> Nota: Diagrama de Task Flow para vincular nuevos medidores </p>

Wireflow:
<p align="center"> 
<img src="assets/chapter4/wireflows/segmento%201/User%20goal-%20Administrar%20y%20vincular%20nuevos%20medidores%20inteligentes/wireflow.png" width="700"> 
<br> Nota: Diagrama de Wireflow para el registro de nuevos dispositivos </p>

Descripción del flujo:
El usuario ingresa a la sección de "Mis Dispositivos" desde el menú lateral, selecciona la opción para agregar un nuevo equipo ("Vincular Dispositivo") y utiliza la cámara para escanear el código QR del medidor inteligente. Una vez detectado, asigna el tipo de dispositivo y la zona. Al confirmar, el dispositivo queda activo y vinculado a su red para comenzar la transmisión de datos.

* User Goal: Como coordinador de cadena, quiero atender una alerta de exceso de consumo en hora punta, para reconocerla a tiempo y evitar cargos extras en la facturación eléctrica.

Task Flow:
<p align="center"> 
<img src="assets/chapter4/wireflows/segmento%201/User%20goal-%20Atender%20y%20resolver%20alertas%20de%20exceso%20de%20consumo/taskflow.png" width="300">
<br> Nota: Diagrama de Task Flow para atención de alertas de consumo </p>

Wireflow:
<p align="center"> 
<img src="assets/chapter4/wireflows/segmento%201/User%20goal-%20Atender%20y%20resolver%20alertas%20de%20exceso%20de%20consumo/wireflow.png" width="700"> 
<br> Nota: Diagrama de Wireflow de resolución de alertas </p>

Descripción del flujo:
Desde el dashboard, el usuario visualiza notificaciones pendientes y navega a la vista de "Alertas". Allí filtra las activas, selecciona una alerta crítica de sobreconsumo (Cargo por Potencia), lee los detalles del incidente y presiona "Reconocer". Posteriormente, tras coordinar la reducción de carga, marca la alerta como "Resuelta", manteniendo un historial limpio.

* User Goal: Como coordinador de cadena, quiero configurar el costo por kWh y la meta global de consumo, para que el sistema me notifique si estoy por exceder el presupuesto del mes.

Task Flow:
<p align="center"> 
<img src="assets/chapter4/wireflows/segmento%201/User%20goal-%20Configurar%20metas%20corporativas%20y%20tarifas%20el%C3%A9ctricas/taskflow.png" width="300">
<br> Nota: Diagrama de Task Flow para configuración de tarifas y metas </p>

Wireflow:
<p align="center"> 
<img src="assets/chapter4/wireflows/segmento%201/User%20goal-%20Configurar%20metas%20corporativas%20y%20tarifas%20el%C3%A9ctricas/wireflow.png" width="700"> 
<br> Nota: Diagrama de Wireflow de actualización de metas y tarifas </p>

Descripción del flujo:
El usuario ingresa a "Mi Organización", donde visualiza los parámetros actuales de la sede. Modifica el campo de "Meta global (kWh/mes)" y luego actualiza el "Costo por kWh" en la sección de tarifa energética. Guarda ambos valores, los cuales recalcularán inmediatamente las proyecciones y costos estimados en todo el sistema.

* User Goal: Como coordinador de cadena, quiero generar un reporte energético mensual descargable, para presentarlo a gerencia y justificar los gastos de electricidad.

Task Flow:
<p align="center"> 
<img src="assets/chapter4/wireflows/segmento%201/User%20goal-%20Generar%20y%20exportar%20un%20reporte%20energ%C3%A9tico%20para%20gerencia/taskflow.png" width="300">
<br> Nota: Diagrama de Task Flow para generación de reportes </p>

Wireflow:
<p align="center"> 
<img src="assets/chapter4/wireflows/segmento%201/User%20goal-%20Generar%20y%20exportar%20un%20reporte%20energ%C3%A9tico%20para%20gerencia/wireflow.png" width="700"> 
<br> Nota: Diagrama de Wireflow de exportación de reportes PDF </p>

Descripción del flujo:
El usuario se dirige a la sección de "Reportes PDF". Selecciona el rango de tiempo deseado (por ejemplo, "Mes Pasado") a través del menú desplegable y presiona "Descargar PDF". El sistema procesa la información de todos los dispositivos y genera un documento con las métricas consolidadas, listo para ser guardado o compartido.


**Segmento 2: Propietario de Establecimiento Independiente**

* User Goal: Como dueño de local, quiero iniciar sesión de forma segura y poder recuperar mi cuenta si olvido la contraseña, para no perder el acceso a los datos de mi negocio.

Task Flow:
<p align="center"> 
<img src="assets/chapter4/wireflows/segmento%202/User%20goal-%20Autenticaci%C3%B3n%20y%20recuperaci%C3%B3n%20segura%20en%20la%20plataforma/taskflow.png" width="300">
<br> Nota: Diagrama de Task Flow de inicio de sesión y recuperación </p>

Wireflow:
<p align="center"> 
<img src="assets/chapter4/wireflows/segmento%202/User%20goal-%20Autenticaci%C3%B3n%20y%20recuperaci%C3%B3n%20segura%20en%20la%20plataforma/wireflow.png" width="700"> 
<br> Nota: Diagrama de Wireflow de autenticación de usuario </p>

Descripción del flujo:
El propietario abre la app e intenta iniciar sesión, pero al fallar las credenciales selecciona "¿Olvidaste tu contraseña?". Ingresa su correo electrónico y el sistema le envía un enlace de recuperación. Tras restablecer sus credenciales, accede exitosamente al Dashboard.

* User Goal: Como dueño de local, quiero revisar el resumen rápido de mi consumo actual, para saber de un vistazo cuánto he gastado hasta el momento en el mes.

Task Flow:
<p align="center"> 
<img src="assets/chapter4/wireflows/segmento%202/User%20goal-%20Revisar%20el%20resumen%20r%C3%A1pido%20de%20consumo%20diario/taskflow.png" width="300">
<br> Nota: Diagrama de Task Flow de revisión de consumo diario </p>

Wireflow:
<p align="center"> 
<img src="assets/chapter4/wireflows/segmento%202/User%20goal-%20Revisar%20el%20resumen%20r%C3%A1pido%20de%20consumo%20diario/wireflow.png" width="700"> 
<br> Nota: Diagrama de Wireflow de consulta rápida de resumen </p>

Descripción del flujo:
Al iniciar sesión, el usuario aterriza directamente en el Dashboard Principal. Allí visualiza su consumo actual en soles (S/) y kilovatios-hora (kWh), además de un gráfico de barras con la tendencia de los últimos 14 días. Para más detalle, entra a "Monitoreo de Energía" donde ve un desglose simplificado por dispositivo activo.

* User Goal: Como dueño de local, quiero aplicar sugerencias automáticas de la IA, para reducir mi factura de luz sin tener que analizar gráficos complejos.

Task Flow:
<p align="center"> 
<img src="assets/chapter4/wireflows/segmento%202/User%20goal-%20Aplicar%20recomendaciones%20de%20IA%20para%20reducir%20la%20factura/taskflow.png" width="300">
<br> Nota: Diagrama de Task Flow para aplicación de recomendaciones de ahorro </p>

Wireflow:
<p align="center"> 
<img src="assets/chapter4/wireflows/segmento%202/User%20goal-%20Aplicar%20recomendaciones%20de%20IA%20para%20reducir%20la%20factura/wireflow.png" width="700"> 
<br> Nota: Diagrama de Wireflow de implementación de sugerencias de IA </p>

Descripción del flujo:
El usuario ingresa a "Analíticas" y revisa la sección "Recomendaciones de IA". Identifica una sugerencia útil (ej. "Apaga el Aire Acondicionado a las 3 AM" que promete un ahorro de S/ 35.50). Selecciona aplicar recomendación, y la IA ajusta automáticamente el cronograma del enchufe inteligente. El estado de la recomendación cambia a "Aplicada", reflejando un impacto positivo en la proyección de su factura mensual.


### 4.4.3. Mobile Applications Mock-ups

Esta sección reúne la interfaz gráfica de alta fidelidad para la aplicación móvil de SEMS, diseñada para ofrecer una experiencia fluida e intuitiva tanto para los administradores corporativos como para los dueños de locales independientes. El diseño aplica la identidad visual completa del proyecto: modo oscuro predeterminado por eficiencia energética (OLED), paleta con acentos azules, e indicadores claros en verde/rojo para estados financieros y de alerta.

<p align="center">
  <img src="assets/chapter4/mockups/Screenshot_1.png" alt="mockup 1" width="500"><br>
  Nota: Mockup de Inicio de Sesión
</p>
<p align="center">
  <img src="assets/chapter4/mockups/Screenshot_2.png" alt="mockup 2" width="500"><br>
  Nota: Mockup de Recuperación y Registro
</p>
<p align="center">
  <img src="assets/chapter4/mockups/Screenshot_3.png" alt="mockup 3" width="900"><br>
  Nota: Mockup del Dashboard y Mis Dispositivos
</p>
<p align="center">
  <img src="assets/chapter4/mockups/Screenshot_4.png" alt="mockup 4" width="900"><br>
  Nota: Mockup de Monitoreo y Escaneo de Medidores
</p>
<p align="center">
  <img src="assets/chapter4/mockups/Screenshot_5.png" alt="mockup 5" width="900"><br>
  Nota: Mockup de Analíticas y Recomendaciones
</p>
<p align="center">
  <img src="assets/chapter4/mockups/Screenshot_6.png" alt="mockup 6" width="900"><br>
  Nota: Mockup de Reportes, Suscripción y Organización
</p>
<p align="center">
  <img src="assets/chapter4/mockups/Screenshot_7.png" alt="mockup 7" width="500"><br>
  Nota: Mockup de Configuración y Perfil
</p>
<p align="center">
  <img src="assets/chapter4/mockups/Screenshot_8.png" alt="mockup 8" width="500"><br>
  Nota: Mockup de detalle de consumos
</p>
<p align="center">
  <img src="assets/chapter4/mockups/Screenshot_9.png" alt="mockup 9" width="300"><br>
  Nota: Mockup de menús modales
</p>

### 4.4.4. Mobile Applications User Flow Diagrams

**Segmento 1: Responsable de Operaciones de Cadena**

* User Goal: Como coordinador de cadena, quiero registrar un nuevo medidor inteligente escaneándolo con la cámara, para asignar en qué área del local está instalado y comenzar a monitorearlo.

User Flow:
<p align="center"> 
<img src="assets/chapter4/userflows/segmento%201/User%20goal-%20Administrar%20y%20vincular%20nuevos%20medidores%20inteligentes/userflow.png" width="700"> 
<br> Nota: Diagrama de User Flow para el registro de nuevos dispositivos en alta fidelidad </p>

* User Goal: Como coordinador de cadena, quiero atender una alerta de exceso de consumo en hora punta, para reconocerla a tiempo y evitar cargos extras en la facturación eléctrica.

User Flow:
<p align="center"> 
<img src="assets/chapter4/userflows/segmento%201/User%20goal-%20Atender%20y%20resolver%20alertas%20de%20exceso%20de%20consumo/userflow.png" width="700"> 
<br> Nota: Diagrama de User Flow de resolución de alertas en alta fidelidad </p>

* User Goal: Como coordinador de cadena, quiero configurar el costo por kWh y la meta global de consumo, para que el sistema me notifique si estoy por exceder el presupuesto del mes.

User Flow:
<p align="center"> 
<img src="assets/chapter4/userflows/segmento%201/User%20goal-%20Configurar%20metas%20corporativas%20y%20tarifas%20el%C3%A9ctricas/userflow.png" width="700"> 
<br> Nota: Diagrama de User Flow de actualización de metas y tarifas en alta fidelidad </p>

* User Goal: Como coordinador de cadena, quiero generar un reporte energético mensual descargable, para presentarlo a gerencia y justificar los gastos de electricidad.

User Flow:
<p align="center"> 
<img src="assets/chapter4/userflows/segmento%201/User%20goal-%20Generar%20y%20exportar%20un%20reporte%20energ%C3%A9tico%20para%20gerencia/userflow.png" width="700"> 
<br> Nota: Diagrama de User Flow de exportación de reportes PDF en alta fidelidad </p>


**Segmento 2: Propietario de Establecimiento Independiente**

* User Goal: Como dueño de local, quiero iniciar sesión de forma segura y poder recuperar mi cuenta si olvido la contraseña, para no perder el acceso a los datos de mi negocio.

User Flow:
<p align="center"> 
<img src="assets/chapter4/userflows/segmento%202/User%20goal-%20Autenticaci%C3%B3n%20y%20recuperaci%C3%B3n%20segura%20en%20la%20plataforma/userflow.png" width="700"> 
<br> Nota: Diagrama de User Flow de autenticación de usuario en alta fidelidad </p>

* User Goal: Como dueño de local, quiero revisar el resumen rápido de mi consumo actual, para saber de un vistazo cuánto he gastado hasta el momento en el mes.

User Flow:
<p align="center"> 
<img src="assets/chapter4/userflows/segmento%202/User%20goal-%20Revisar%20el%20resumen%20r%C3%A1pido%20de%20consumo%20diario/userflow.png" width="700"> 
<br> Nota: Diagrama de User Flow de consulta rápida de resumen en alta fidelidad </p>

* User Goal: Como dueño de local, quiero aplicar sugerencias automáticas de la IA, para reducir mi factura de luz sin tener que analizar gráficos complejos.

User Flow:
<p align="center"> 
<img src="assets/chapter4/userflows/segmento%202/User%20goal-%20Aplicar%20recomendaciones%20de%20IA%20para%20reducir%20la%20factura/userflow.png" width="700"> 
<br> Nota: Diagrama de User Flow de implementación de sugerencias de IA en alta fidelidad </p>

## 4.5. Mobile Applications Prototyping

### 4.5.1. Android Mobile Applications Prototyping

> `<Enlace al prototipo de Android.>`

### 4.5.2. iOS Mobile Applications Prototyping

> `<Enlace al prototipo de iOS.>`

## 4.6. Web Applications UX/UI Design

### 4.6.1. Web Applications Wireframes

![Login](assets/WireLogin.png)


![Login](assets/WireCreate.png)


![Login](assets/WireRestore.png)


![Login](assets/WireChange.png)


![Login](assets/WireVerify.png)


![Login](assets/WireDashboard.png)


![Login](assets/WireDevices.png)


![Login](assets/WireMonitor.png)


![Login](assets/WireAnalytics.png)


![Login](assets/WireAelrts.png)


![Login](assets/WireReports.png)


![Login](assets/WireSubs.png)


![Login](assets/WireLocals.png)


![Login](assets/WireConfig.png)


![Login](assets/WireNotFound.png)

Distribución común a todas las vistas autenticadas: barra lateral fija a la izquierda con la
navegación, barra superior con el título de la vista y los controles de cuenta, y área de
contenido con una rejilla de tarjetas.

### 4.6.2. Web Applications Wireflow Diagrams

![WireFlow1](assets/Wireflow1.png)

![WireFlow2](assets/Wireflow2.png)

![WireFlow3](assets/Wireflow3.png)

![WireFlow4](assets/Wireflow4.png)

![WireFlow5](assets/Wireflow5.png)


Flujos que deben representarse:

- Registro → verificación de correo → primer inicio de sesión → alta de organización.
- Alta de local → definición de zonas → registro de medidores.
- Recepción de alerta de demanda → consulta del detalle → acción sobre la zona responsable.
- Consulta de planes → sesión de pago → confirmación de la suscripción.

### 4.6.3. Web Applications Mock-ups

![MockWeb](assets/MockLogin.png)


![MockWeb](assets/MockCreate.png)


![MockWeb](assets/MockRestore.png)


![MockWeb](assets/MockChange.png)


![MockWeb](assets/MockVerify.png)


![MockWeb](assets/MockDashboard.png)


![MockWeb](assets/MockDevices.png)


![MockWeb](assets/MockMonitor.png)


![MockWeb](assets/MockAnalytics.png)


![MockWeb](assets/MockAlerts.png)


![MockWeb](assets/MockReports.png)


![MockWeb](assets/MockSubs.png)


![MockWeb](assets/MockLocals.png)


![MockWeb](assets/MockConfig.png)


![MockWeb](assets/MockNotFound.png)

### 4.6.4. Web Applications User Flow Diagrams

![UserFlows](assets/UserFlow1.png)


![UserFlows](assets/UserFlow2.png)


![UserFlows](assets/UserFlow3.png)


![UserFlows](assets/UserFlow4.png)

## 4.7. Web Applications Prototyping

https://www.figma.com/design/O4iOfbaAggqazFr6Y5aNeR/SEMS-%E2%80%94-UI-UX-Design--4.3-%C2%B7-4.6-%C2%B7-4.7-?node-id=4-8&t=bT9hE9gbEQIG2Cls-1 

## 4.8. Domain-Driven Software Architecture

La arquitectura se representa con el **C4 Model**. El *backend* es un **monolito modular**: un
único proceso desplegable con ocho módulos, cada uno con su propio modelo de dominio y sus tablas
prefijadas, comunicándose entre sí por puertos explícitos y por eventos de dominio.

### 4.8.1. Software Architecture Context Diagram

![Context](assets/Context.png)

| Elemento | Tipo | Descripción |
| :-- | :-- | :-- |
| Administrador de organización | Persona | Gestiona la cadena, los locales y los permisos |
| Supervisor de local | Persona | Opera un local concreto |
| Operario | Persona | Consulta el estado de los equipos de su local |
| **SEMS** | Sistema | Mide, analiza y alerta sobre el consumo eléctrico comercial |
| Pasarela de pagos | Sistema externo | Procesa cobros y devuelve eventos de confirmación |
| Proveedor de correo | Sistema externo | Entrega verificaciones, recuperaciones y alertas |
| Proveedor de tarifas | Sistema externo | Suministra el precio vigente de la energía |

### 4.8.2. Software Architecture Container Diagrams

![Container](assets/Container.png)

| Contenedor | Tecnología | Responsabilidad |
| :-- | :-- | :-- |
| Landing Page | HTML5, CSS3, JavaScript | Presentar la propuesta de valor y dirigir al registro |
| Aplicación web | Vue 3, PrimeVue, Vite | Interfaz de operación del producto |
| API REST | ASP.NET Core 8, C# | Lógica de negocio y persistencia |
| Base de datos | PostgreSQL | Almacén único con tablas prefijadas por módulo |

### 4.8.3. Software Architecture Components Diagrams

![Components](assets/Components.png)

Los ocho módulos del monolito y su prefijo de tablas:

| Módulo | Prefijo | Responsabilidad |
| :-- | :-- | :-- |
| Identity & Access Management | `iam_` | Cuentas, autenticación, papeles y tokens |
| Organizations | `og_` | Organizaciones, locales, zonas y permisos |
| Device Management | `dm_` | Alta, vinculación, configuración y eventos de dispositivos |
| Energy Monitoring | `em_` | Medidores, lecturas, tarifa comercial y factura estimada |
| Analytics | `an_` | Proyecciones, recomendaciones, anomalías y comparaciones |
| Alerts | `al_` | Umbrales, reglas de demanda e inactividad, notificaciones |
| Subscriptions | `sb_` | Planes, límites y suscripciones |
| Payments | `pm_` | Cobros, comprobantes y eventos de la pasarela |

**Puertos entre módulos.** Ningún módulo accede a las tablas de otro. Las tres dependencias que
existen se resuelven por interfaces declaradas en el dominio del consumidor:

| Consumidor | Puerto | Proveedor | Qué pregunta |
| :-- | :-- | :-- | :-- |
| Device Management | `ISiteDirectory` | Organizations | Si un local está vigente y si una zona le pertenece |
| Analytics | `IBillCalculator` | Energy Monitoring | Cuánto costaría un consumo previsto |
| Energy Monitoring | `IEnergyPricingProvider` | Externo | El precio vigente de la energía |

**Eventos de dominio.** Trece eventos publicados en un bus interno, con entrega posterior al
*commit* de la transacción:

`UserRegistered`, `UserLoggedIn`, `VerificationRequested`, `PasswordResetRequested`,
`RoleAssigned`, `DeviceRegistered`, `DeviceStatusUpdated`, `DeviceLinked`, `DeviceUnlinked`,
`ReadingProcessed`, `AlertTriggered`, `SubscriptionChanged`, `PaymentProcessed`.

## 4.9. Software Object-Oriented Design

### 4.9.1. Class Diagrams

#Alerts

![alerts](assets/alertsCL.png)

#Analytics

![analytics](assets/analyticsCL.png)

#Energy

![energy](assets/energyCL.png)

#iam

![iam](assets/iamCL.png)

#organizatoins

![organizations](assets/organizationsCL.png)

#payments

![payments](assets/paymentsCL.png)

#subscriptions

![subscriptions](assets/subscriptionsCL.png)

### 4.9.2. Class Dictionary

**Módulo Identity & Access Management**

| Clase | Tipo | Descripción |
| :-- | :-- | :-- |
| `User` | Agregado | Cuenta del sistema. Guarda el resumen de la contraseña, nunca el valor en claro |
| `EmailAddress` | Objeto de valor | Correo validado en su construcción |
| `RefreshToken` | Entidad | Token de refresco, almacenado como resumen y revocable |
| `UserAuthToken` | Entidad | Token de verificación o de recuperación, de un solo uso |
| `RoleName` | Enumeración | `ADMIN`, `STAFF` |

**Módulo Organizations**

| Clase | Tipo | Descripción |
| :-- | :-- | :-- |
| `Organization` | Agregado | Cadena o empresa propietaria de los locales |
| `Site` | Entidad | Local con su categoría tarifaria, su potencia contratada y si tiene concedida la exclusión de domingos |
| `Zone` | Entidad | División interna del local; indica si sigue consumiendo con el local cerrado |
| `Membership` | Entidad | Permiso de una persona sobre la organización o sobre un local concreto |
| `TariffCategory` | Enumeración | `BT5B`, `BT3`, `BT4`, `MT2`, `MT3` |
| `BusinessType` | Enumeración | `SUPERMARKET`, `CONVENIENCE_STORE`, `DEPARTMENT_STORE`, `RESTAURANT`, `WAREHOUSE`, `OTHER` |
| `ZoneType` | Enumeración | `SALES_FLOOR`, `COLD_STORAGE`, `WAREHOUSE`, `KITCHEN`, `OFFICES`, `HVAC`, `PARKING`, `OTHER` |
| `MembershipRole` | Enumeración | `ORG_ADMIN`, `SUPERVISOR`, `OPERATOR` |

**Módulo Device Management**

| Clase | Tipo | Descripción |
| :-- | :-- | :-- |
| `Device` | Agregado | Equipo medido. Pertenece obligatoriamente a un local y opcionalmente a una zona |
| `DeviceBinding` | Entidad | Vínculo entre un dispositivo y la persona que lo opera |
| `DeviceConfiguration` | Entidad | Ajuste con nombre asociado a un dispositivo |
| `DeviceEvent` | Entidad | Registro histórico de lo ocurrido al dispositivo |
| `DeviceStatus` | Enumeración | `ACTIVE`, `INACTIVE`, `REMOVED` |
| `ConnectionProtocol` | Enumeración | `WIFI`, `BLUETOOTH` |

**Módulo Energy Monitoring**

| Clase | Tipo | Descripción |
| :-- | :-- | :-- |
| `EnergyMeter` | Agregado | Medidor inteligente asociado a un local |
| `EnergyReading` | Entidad | Medición individual con marca temporal |
| `DeviceConsumption` | Entidad | Consumo agregado por dispositivo y periodo |
| `ConsumptionAlert` | Entidad | Aviso generado por el propio módulo de medición |
| `CommercialTariff` | Objeto de valor | Precios por franja y cargos por potencia de una categoría del pliego |
| `BillBreakdown` | Objeto de valor | Desglose: energía, cargo por potencia, exceso, IGV y total |
| `PowerReading` | Objeto de valor | Lectura instantánea de potencia |
| `FranjaHoraria` | Enumeración | `PUNTA`, `FUERA_DE_PUNTA` |

**Módulo Alerts**

| Clase | Tipo | Descripción |
| :-- | :-- | :-- |
| `Alert` | Agregado | Aviso levantado por un umbral, una inactividad o una regla de demanda |
| `AlertThreshold` | Entidad | Umbral configurable sobre una métrica |
| `DemandRule` | Entidad | Vigilancia de la demanda de un local frente a su potencia contratada |
| `InactivityRule` | Entidad | Detección de un dispositivo sin reportar |
| `NotificationPreference` | Entidad | Canal preferido de la persona |
| `NotificationLog` | Entidad | Registro de lo enviado |
| `DemandLevel` | Enumeración | `OK`, `WARNING`, `CRITICAL` |

**Módulos Analytics, Subscriptions y Payments**

| Clase | Tipo | Descripción |
| :-- | :-- | :-- |
| `BillPrediction` | Entidad | Proyección del recibo del periodo |
| `Recommendation` | Entidad | Consejo de ahorro con su impacto estimado |
| `Anomaly` | Entidad | Desviación detectada respecto del patrón habitual |
| `ConsumptionRanking` | Entidad | Ordenación de locales o dispositivos por consumo |
| `SubscriptionPlan` | Agregado | Plan con su precio y sus límites |
| `PlanFeature` | Entidad | Característica o límite concreto del plan |
| `Subscription` | Agregado | Suscripción vigente de una organización |
| `Payment` | Agregado | Cobro realizado |
| `Invoice` | Entidad | Comprobante emitido por un cobro |
| `PaymentMethodEntity` | Entidad | Identificador del medio de pago guardado en la pasarela |
| `PaymentWebhookEvent` | Entidad | Evento recibido de la pasarela, con control de duplicados |
| `Money` | Objeto de valor | Importe con su moneda |

### 4.9.3. Reglas de dominio relevantes

| Regla | Dónde vive | Enunciado |
| :-- | :-- | :-- |
| Hora punta | `HorarioPunta` (Energy) | De 18:00 a 23:00 de **todos los días del año**. La exclusión de domingos existe pero solo se aplica si el cliente la solicitó a la distribuidora, y se registra por local en `Site.ExcludesSundaysFromPeak` |
| Cargo por potencia | `CommercialTariff` (Energy) | Se calcula sobre la demanda máxima del periodo, con independencia de la energía consumida |
| Exceso de potencia | `CommercialTariff` (Energy) | Se aplica cuando la demanda máxima supera la potencia contratada, y afecta a todo el mes |
| Aviso de demanda | `DemandRule` (Alerts) | Emite `WARNING` con margen antes de alcanzar la potencia contratada y `CRITICAL` al superarla |
| Baja de dispositivo | `Device` (Devices) | Es lógica: el dispositivo pasa a `REMOVED` y deja de aparecer en los listados del usuario y de contar para el límite del plan |
| Límite del plan | `SubscriptionPlan` (Subscriptions) | Se mide en locales, no en dispositivos: un supermercado tiene decenas de medidores en un solo edificio |

## 4.10. Database Design

### 4.10.1. Relational Database Diagram


Una única base **PostgreSQL** para todo el monolito. El aislamiento entre módulos se consigue por
prefijo de tabla: cada módulo solo escribe sobre las suyas, y las relaciones entre módulos se
guardan como identificadores sin restricción de clave foránea cruzada, para que la frontera sea
real y no solo una convención.

**33 tablas**, distribuidas así:

| Prefijo | Tablas |
| :-- | :-- |
| `iam_` (3) | `iam_users`, `iam_refresh_tokens`, `iam_user_auth_tokens` |
| `og_` (4) | `og_organizations`, `og_sites`, `og_zones`, `og_memberships` |
| `dm_` (4) | `dm_devices`, `dm_device_bindings`, `dm_device_configurations`, `dm_device_events` |
| `em_` (4) | `em_energy_meters`, `em_energy_readings`, `em_device_consumptions`, `em_consumption_alerts` |
| `an_` (5) | `an_bill_predictions`, `an_recommendations`, `an_anomalies`, `an_device_identifications`, `an_consumption_rankings` |
| `al_` (6) | `al_alerts`, `al_thresholds`, `al_demand_rules`, `al_inactivity_rules`, `al_notification_preferences`, `al_notification_logs` |
| `sb_` (3) | `sb_subscription_plans`, `sb_plan_features`, `sb_subscriptions` |
| `pm_` (4) | `pm_payments`, `pm_payment_methods`, `pm_invoices`, `pm_webhook_events` |

**IAM
![IAM](assets/iam.png)


**Organizations
![ORG](assets/organizations.png)


**Devices
![Devices](assets/devices.png)


**Energy
![Energy](assets/energy.png)


**Analytics
![Analytics](assets/analytics.png)


**Alerts
![Alerts](assets/alerts.png)


**Subscriptions
![Subscriptions](assets/subscriptions.png)


**Payments
![Payments](assets/payments.png)
**Restricciones de unicidad relevantes**

| Tabla | Restricción | Por qué |
| :-- | :-- | :-- |
| `iam_users` | `email_address` única | Evita cuentas duplicadas aunque falle la comprobación en la aplicación |
| `og_organizations` | `tax_id` única | Un RUC identifica a una sola organización |
| `og_sites` | `site_code` única por organización | El código de local es propio de cada cadena |
| `dm_devices` | `external_device_code` única | Un equipo físico no puede registrarse dos veces |
| `pm_webhook_events` | `(provider, event_id)` única | Impide procesar dos veces el mismo aviso de la pasarela |

**Gestión del esquema.** El esquema se crea y evoluciona con **migraciones de Entity Framework
Core**, no con generación automática. La decisión se tomó tras comprobar que `EnsureCreated()` no
crea nada si la base ya contiene alguna tabla, lo que ocurre en la base gestionada de producción,
que trae esquemas propios del proveedor. Cada cambio de modelo genera una migración versionada que
se aplica al arrancar.

**Almacenamiento de series temporales.** Las lecturas (`em_energy_readings`) son la tabla de mayor
crecimiento. Para el alcance actual se mantienen en PostgreSQL con índice por dispositivo y fecha.
Si el volumen lo exige, la ruta prevista es particionar por rango de fecha antes que introducir un
segundo motor.



# Capítulo V: Product Implementation

## 5.1. Software Configuration Management

### 5.1.1. Software Development Environment Configuration

| Propósito | Herramienta | Versión | Enlace |
| :-- | :-- | :-- | :-- |
| Control de versiones | Git | 2.4x | <https://git-scm.com> |
| Alojamiento y colaboración | GitHub | — | <https://github.com> |
| Gestión del producto | `<Pivotal Tracker / Jira / Trello>` | — | `<URL del tablero>` |
| Editor de código | Visual Studio Code | 1.9x | <https://code.visualstudio.com> |
| Entorno del backend | .NET SDK | 8.0 | <https://dotnet.microsoft.com> |
| Entorno de la web | Node.js | 20 LTS | <https://nodejs.org> |
| Empaquetador de la web | Vite | 7 | <https://vite.dev> |
| Base de datos local | PostgreSQL | 16 | <https://www.postgresql.org> |
| Cliente de base de datos | pgAdmin / DBeaver | — | — |
| Pruebas de la API | Swagger UI, cURL | — | — |
| Diagramas C4 | Structurizr | — | <https://structurizr.com> |
| Diagramas UML y ER | LucidChart | — | <https://lucidchart.com> |
| Artefactos UX | UXPressia | — | <https://uxpressia.com> |
| Diseño de interfaz | Figma | — | <https://figma.com> |

**Puesta en marcha del backend**

```bash
git clone https://github.com/SEMS-Diseno-de-Experimentos/SEMS-Backend.git
cd SEMS-Backend
cp .env.example .env      # completar DATABASE_URL, JWT_SECRET y el resto
dotnet restore
dotnet test               # 68 pruebas
dotnet run --project src/Sems.Api
```

**Puesta en marcha de la aplicación web**

```bash
git clone https://github.com/SEMS-Diseno-de-Experimentos/SEMS-Web-Application.git
cd SEMS-Web-Application/semswebapp
npm install
npm run dev
```

> El proyecto vive en la subcarpeta `semswebapp/`. Todos los comandos de `npm` se ejecutan ahí.

**Puesta en marcha del Landing Page**

No requiere instalación ni compilación: se abre `index.html` en el navegador, o se sirve la
carpeta con cualquier servidor estático.

**Variables de entorno.** Ninguna credencial se versiona. Cada repositorio incluye un
`.env.example` con todas las claves y sus valores vacíos, y `.env` está en `.gitignore`. Las
variables con prefijo `VITE_` quedan incrustadas en el paquete que descarga el navegador, de modo
que **nunca contienen secretos**: solo la URL pública de la API y la clave publicable de la
pasarela de pagos.

### 5.1.2. Source Code Management

El proyecto usa **GitFlow**.

| Rama | Propósito | Origen | Destino |
| :-- | :-- | :-- | :-- |
| `main` | Código en producción | `develop` | — |
| `develop` | Integración del trabajo en curso | `main` | `main` |
| `feature/<nombre>` | Una funcionalidad o tarea | `develop` | `develop` |
| `release/<versión>` | Preparación de una entrega | `develop` | `main` y `develop` |
| `hotfix/<nombre>` | Corrección urgente en producción | `main` | `main` y `develop` |

Nunca se hace *push* directo a `main` ni a `develop`: todo entra por *Pull Request*.

**Repositorios de la organización**

| Repositorio | Contenido |
| :-- | :-- |
| [SEMS-Backend](https://github.com/SEMS-Diseno-de-Experimentos/SEMS-Backend) | API REST en ASP.NET Core |
| [SEMS-Web-Application](https://github.com/SEMS-Diseno-de-Experimentos/SEMS-Web-Application) | Aplicación web en Vue 3 |
| [SEMS-Landing-Page](https://github.com/SEMS-Diseno-de-Experimentos/SEMS-Landing-Page) | Sitio estático en HTML5, CSS3 y JavaScript |
| [SEMS-Mobile-App](https://github.com/SEMS-Diseno-de-Experimentos/SEMS-Mobile-App) | Aplicación móvil nativa |
| [SEMS-Report](https://github.com/SEMS-Diseno-de-Experimentos/SEMS-Report) | Este informe |

**Convención de commits.** Se aplica **Conventional Commits**, con el formato
`<tipo>(<alcance>): <descripción en imperativo>`.

| Prefijo | Cuándo se usa |
| :-- | :-- |
| `feat:` | Funcionalidad nueva visible para el usuario |
| `fix:` | Corrección de un defecto |
| `test:` | Pruebas nuevas o modificadas |
| `ci:` | Cambios en pipelines o automatización |
| `refactor:` | Reorganización sin cambio de comportamiento |
| `docs:` | Documentación |
| `chore:` | Mantenimiento y configuración |
| `style:` | Formato, sin efecto sobre el comportamiento |

**Versionado.** Se sigue **Semantic Versioning** (`MAJOR.MINOR.PATCH`) con etiquetas anotadas en
`main` por cada entrega.

### 5.1.3. Source Code Style Guide & Conventions

| Artefacto | Guía | Herramienta |
| :-- | :-- | :-- |
| Backend (C#) | Convenciones de nomenclatura de .NET | Analizadores de .NET, `dotnet format` |
| Aplicación web (JavaScript, Vue) | Guía de estilo de Vue 3 | ESLint con `eslint-plugin-vue` |
| Landing Page (HTML, CSS, JS) | HTML5 semántico, BEM ligero en CSS | Revisión en *Pull Request* |
| Markdown | — | Revisión en *Pull Request* |

**Convenciones del backend**

- `PascalCase` para clases, registros, propiedades y métodos públicos; `_camelCase` para campos
  privados; `camelCase` para variables locales y parámetros.
- Un archivo por agregado o por conjunto cohesionado de tipos del mismo módulo.
- Los tipos del dominio no llevan anotaciones de persistencia ni de serialización: el mapeo vive
  en la capa de infraestructura y el contrato JSON en la capa de interfaces.
- Los comentarios explican **por qué**, no **qué**. La documentación XML de cada acción del
  controlador se publica en la interfaz de documentación de la API.

**Convenciones de la aplicación web**

- Componentes en `PascalCase`, uno por archivo, con `<script setup>`.
- Vistas en `views/`, componentes reutilizables en `components/`, llamadas a la API en `services/`.
- El estado del servidor se gestiona con TanStack Query; el estado propio de la interfaz, con Pinia.

**Contrato de la API.** El estilo de nomenclatura del JSON no es uniforme entre módulos, y esto es
deliberado: los módulos migrados desde el servicio original conservan el estilo que ya consumían
los clientes existentes, para no romperlos. La regla se documenta aquí para que sea una decisión
registrada y no una inconsistencia accidental.

| Módulo | Estilo del JSON |
| :-- | :-- |
| Identity & Access Management, Device Management | `camelCase` |
| Energy, Analytics, Alerts, Organizations, Payments | `snake_case` |
| Subscriptions | Peticiones en `snake_case`, respuestas en `PascalCase` |

**Idioma.** El idioma por defecto de los mensajes, de la interfaz y de la documentación de todos
los productos es el **inglés**, con español latinoamericano disponible en los artefactos de cara
al usuario.

### 5.1.4. Software Deployment Configuration

| Artefacto | Plataforma | Estrategia |
| :-- | :-- | :-- |
| Landing Page | GitHub Pages | Publicación del repositorio tal cual, sin compilación, al hacer *push* a `main` |
| Aplicación web | Vercel | Compilación con Vite y publicación automática por rama |
| API REST | Render | Servicio web con despliegue automático desde `main` |
| Base de datos | PostgreSQL gestionado | Instancia única con migraciones aplicadas al arrancar |

**Configuración del backend en el proveedor**

| Variable | Contenido |
| :-- | :-- |
| `DATABASE_URL` | Cadena de conexión completa de Npgsql, en **una sola** variable |
| `PORT` | Lo inyecta la plataforma; la aplicación lo lee y escucha en él |
| `ALLOWED_ORIGINS` | Los orígenes de la aplicación web y del entorno local, separados por comas |
| `JWT_SECRET` | Mínimo 32 caracteres, generado aleatoriamente |
| `MAIL_*` | Servidor de correo saliente |
| `STRIPE_SECRET_KEY`, `STRIPE_WEBHOOK_SECRET` | Credenciales de la pasarela |

**Comprobaciones de salud.** La API expone dos rutas distintas, y la diferencia importa:

| Ruta | Qué responde | Para qué sirve |
| :-- | :-- | :-- |
| `/health` | Que el proceso está vivo | Comprobación de vida de la plataforma |
| `/health/ready` | Que además la base de datos acepta consultas | Comprobación de disponibilidad real |

Separarlas evita el fallo más común de esta clase de despliegues: un servicio que responde
«correcto» mientras su base de datos está caída.

## 5.2. Product Implementation & Deployment

### 5.2.1. Sprint Backlogs

**Sprint 1**

| Sprint | Objetivo | Fecha inicio | Fecha fin |
| :-- | :-- | :-- | :-- |
| 1 | Publicar el Landing Page y la API con el registro, la gestión de organizaciones y locales, y el cálculo de la factura comercial | `<dd/mm/aaaa>` | `<dd/mm/aaaa>` |

| ID | User Story | Tarea | Responsable | Estimación (h) | Estado |
| :-- | :-- | :-- | :-- | --: | :-- |
| US01 | Sección hero del Landing Page | Maquetar el *hero* con la propuesta de valor | `<Integrante>` | 4 | `<Estado>` |
| US03 | Sección de planes | Maquetar los tres planes con sus límites | `<Integrante>` | 4 | `<Estado>` |
| US04 | Navegación del Landing Page | Barra superior, menú móvil y anclas | `<Integrante>` | 3 | `<Estado>` |
| US05 | Selección de idioma | Diccionarios en-US y es-419, y conmutador | `<Integrante>` | 5 | `<Estado>` |
| — | Infraestructura | Publicación automática en GitHub Pages | `<Integrante>` | 2 | `<Estado>` |
| — | Infraestructura | Despliegue de la API y de la base de datos | `<Integrante>` | 4 | `<Estado>` |

> Se amplía con un cuadro por sprint en cada entrega.

### 5.2.2. Implemented Landing Page Evidence

| Dato | Valor |
| :-- | :-- |
| Repositorio | <https://github.com/SEMS-Diseno-de-Experimentos/SEMS-Landing-Page> |
| Desplegado en | <https://sems-diseno-de-experimentos.github.io/SEMS-Landing-Page/> |
| Tecnología | HTML5, CSS3 y JavaScript, sin framework ni paso de compilación |
| Páginas | `index.html` y `terms.html` |

**Características implementadas**

- Diseño Material Design 3 con tema claro y oscuro.
- Internacionalización en inglés (por defecto) y español latinoamericano, con 211 claves y
  persistencia de la elección.
- Accesibilidad: enlace de salto, puntos de referencia semánticos, atributos ARIA en todos los
  controles sin texto visible, acordeón operable por teclado y contraste verificado en ambos temas.
- Llamados a la acción por segmento que redirigen a las vistas correspondientes de la aplicación web.
- Sección de Términos y Condiciones con la política de privacidad y el acuerdo de nivel de servicio.

![landingDeploy](assets/landingDeploy.png)

### 5.2.3. Implemented Frontend-Web Application Evidence

| Dato | Valor |
| :-- | :-- |
| Repositorio | <https://github.com/SEMS-Diseno-de-Experimentos/SEMS-Web-Application> |
| Desplegado en | <https://sems-web-application-fyld.vercel.app/> |
| Tecnología | Vue 3, Vite, PrimeVue con *preset* Material, Pinia, TanStack Query |

![WebDeploy](assets/webDeploy.png)


### 5.2.4. Implemented Native-Mobile Application Evidence

> `<Evidencia de la aplicación móvil.>`

### 5.2.5. Implemented RESTful API Evidence

| Dato | Valor |
| :-- | :-- |
| Repositorio | <https://github.com/SEMS-Diseno-de-Experimentos/SEMS-Backend> |
| Desplegado en | <https://sems-backend-diseno.onrender.com/swagger>  |
| Tecnología | ASP.NET Core 8, C#, Entity Framework Core, PostgreSQL |
| Endpoints | 111 |
| Módulos | 8 |
| Tablas | 33 |
| Pruebas | 68, todas en verde |

**Estado de la implementación por módulo**

| Módulo | Estado | Endpoints |
| :-- | :-- | --: |
| Identity & Access Management | Implementado | 8 |
| Organizations | Implementado | 16 |
| Device Management | Implementado | 18 |
| Energy Monitoring | Implementado | 23 |
| Analytics | Implementado | 13 |
| Alerts | Implementado | 14 |
| Subscriptions | Implementado | 7 |
| Payments | Implementado | 12 |
| **Total** | | **111** |

**Seguridad implementada**

- Autenticación por JWT con token de acceso de vida corta y token de refresco de vida larga.
- Política de autorización global: toda ruta exige autenticación salvo las declaradas públicas.
- Contraseñas almacenadas con BCrypt; los tokens se guardan como resumen SHA-256, nunca en claro.
- CORS restringido a la lista de orígenes configurada.
- El *webhook* de la pasarela se autentica por la firma del cuerpo, no por JWT, y controla
  duplicados para no procesar dos veces el mismo cobro.
- `forgot-password` responde exactamente lo mismo exista o no la cuenta, para no convertirse en un
  verificador de correos registrados.
- Los datos de la tarjeta nunca llegan al servidor: se introducen en la página de la pasarela y la
  aplicación solo recibe un identificador del medio de pago.

![BackDeploy](assets/backDeploy.png)

### 5.2.6. RESTful API Documentation

La API se documenta con **OpenAPI 3**, generada con Swashbuckle a partir de la documentación XML
del propio código, de modo que documentación e implementación no pueden divergir.

| Dato | Valor |
| :-- | :-- |
| Interfaz de documentación | `<URL del servicio>/swagger` |
| Documento OpenAPI | `<URL del servicio>/swagger/v1/swagger.json` |
| Título | SEMS API |
| Descripción | Smart Energy Management System. Modular monolith: one bounded context per module. |
| Idioma | Inglés |
| Autenticación | Esquema `Bearer` declarado; el token se pega en el diálogo *Authorize* |

**Ejemplo — estimación de la factura de un local**

```http
POST /api/v1/energy/bill-estimate
Authorization: Bearer <token>
Content-Type: application/json

{
  "tariff_category": "MT2",
  "contracted_power_kw": 250,
  "kwh_peak": 12000,
  "kwh_off_peak": 48000,
  "max_demand_kw": 280
}
```

```json
{
  "kwh_peak": 12000,
  "kwh_off_peak": 48000,
  "max_demand_kw": 280,
  "contracted_power_kw": 250,
  "subtotal": 32108.80,
  "igv": 5779.58,
  "total": 37888.38
}
```

> `<Insertar capturas de la interfaz de documentación desplegada.>`

### 5.2.7. Team Collaboration Insights

| Dato | Valor |
| :-- | :-- |
| Organización | <https://github.com/SEMS-Diseno-de-Experimentos> |
| Flujo de trabajo | GitFlow |
| Convención de commits | Conventional Commits |

> `<Insertar la gráfica de contribuciones de cada repositorio (pestaña Insights → Contributors) y
> una tabla que relacione cada integrante con sus commits y Pull Requests del sprint.>`

| Integrante | Commits | Pull Requests | Revisiones | Artefactos principales |
| :-- | --: | --: | --: | :-- |
| `<Integrante>` | `<n>` | `<n>` | `<n>` | `<Artefactos>` |
| `<Integrante>` | `<n>` | `<n>` | `<n>` | `<Artefactos>` |
| `<Integrante>` | `<n>` | `<n>` | `<n>` | `<Artefactos>` |
| `<Integrante>` | `<n>` | `<n>` | `<n>` | `<Artefactos>` |
| `<Integrante>` | `<n>` | `<n>` | `<n>` | `<Artefactos>` |

## 5.3. Video About-the-Product

| Dato | Valor |
| :-- | :-- |
| Enlace | `<URL privado de Microsoft Stream>` |
| Duración | `<mm:ss>` |

## 5.4. Deuda técnica identificada

Se registra de forma explícita lo que hoy no cumple con el diseño descrito, para que el estado del
producto quede documentado con honestidad y sea verificable en la siguiente entrega.

| # | Deuda | Dónde | Impacto | Prevista para |
| :-- | :-- | :-- | :-- | :-- |
| DT01 | La aplicación web conserva la vista `/household` («Mi hogar») del segmento anterior de viviendas | Aplicación web | Incoherencia con el dominio comercial | Sprint 2 |
| DT02 | El formulario de alta de dispositivo no envía `siteId`, que la API exige como obligatorio | Aplicación web | El alta de dispositivos falla contra la API actual | Sprint 2 |
| DT03 | La aplicación web muestra la interfaz en español por defecto | Aplicación web | Incumple la restricción de idioma por defecto en inglés | Sprint 2 |
| DT04 | No existe suite de pruebas automatizadas en la aplicación web | Aplicación web | Sin red de seguridad ante regresiones | Sprint 2 |
| DT05 | No existe pipeline de integración continua | Los tres repositorios | Las pruebas del backend se ejecutan a mano | Sprint 2 |
| DT06 | La aplicación móvil no está iniciada | SEMS-Mobile-App | Alcance pendiente | `<Sprint>` |


# Conclusiones, Bibliografía y Anexos

## Conclusiones

**Sobre el segmento y el problema.** El sector comercial concentra 9 157,3 GWh anuales, el 17,18 %
de la venta nacional de energía eléctrica a cliente final. A diferencia del residencial, enfrenta
una tarifa con cargo por potencia calculado sobre la demanda máxima del mes: un único pico de
quince minutos fija el cargo de todo el periodo. Ese desajuste entre la complejidad de la tarifa y
la capacidad instalada del cliente —miles de establecimientos sin área de energía propia— es lo
que justifica el producto.

**Sobre el diseño del producto.** Adoptar Material Design como lenguaje común permitió que el
*Landing Page*, construido a mano con HTML5, CSS3 y JavaScript, y la aplicación web, construida
con PrimeVue, presenten la misma gramática visual sin mantener dos sistemas de diseño. La
accesibilidad y la internacionalización se incorporaron desde el primer sprint, no como una capa
posterior.

**Sobre la arquitectura.** El monolito modular con ocho módulos, tablas prefijadas y puertos
explícitos ofrece la separación conceptual del diseño dirigido por el dominio sin el costo
operativo de una arquitectura distribuida. Las tres dependencias entre módulos se resuelven por
interfaces reducidas, de modo que la frontera es verificable y no una convención.

**Sobre el proceso.** El valor del curso está en la evidencia de que el producto se construye con
un proceso riguroso. En este primer hito se establecieron el control de versiones con GitFlow, la
convención de commits, la separación de entornos por variables sin credenciales versionadas, las
comprobaciones de vida y de disponibilidad diferenciadas y una suite de 68 pruebas del núcleo del
dominio. Queda registrada de forma explícita la deuda pendiente: la automatización del pipeline,
las pruebas de la aplicación web y las correcciones heredadas del segmento anterior.

**Sobre las decisiones que exigieron un juicio informado.** Dos merecen mención. La primera, haber
corregido la regla de hora punta al contrastarla con el pliego tarifario oficial, aun cuando el
error producía facturas estimadas favorables al cliente y nadie lo habría notado. La segunda,
haber verificado en la fuente primaria la cifra de participación del sector comercial en lugar de
aceptar un dato de circulación frecuente que resultó no coincidir con el anuario oficial.

> Las conclusiones se amplían en cada entrega.

## Recomendaciones

- Cerrar la deuda técnica DT01 a DT05 antes del segundo hito, empezando por el envío de `siteId`
  desde la aplicación web, que hoy impide dar de alta dispositivos contra la API.
- Automatizar la ejecución de las 68 pruebas en cada *Pull Request*.
- Incorporar pruebas de la aplicación web, hoy inexistentes.
- Instrumentar el producto para poder medir los objetivos declarados en el capítulo III.

## Bibliografía

> Referencias en formato APA. Se amplía en cada entrega.

- Bass, L., Clements, P., & Kazman, R. (2021). *Software architecture in practice* (4th ed.). Addison-Wesley.
- Evans, E. (2003). *Domain-driven design: Tackling complexity in the heart of software*. Addison-Wesley.
- Vernon, V. (2013). *Implementing domain-driven design*. Addison-Wesley.
- Brown, S. (2023). *The C4 model for visualising software architecture*. https://c4model.com
- Gothelf, J., & Seiden, J. (2021). *Lean UX: Designing great products with agile teams* (3rd ed.). O'Reilly Media.
- Google. (2024). *Material Design 3*. https://m3.material.io
- World Wide Web Consortium. (2018). *Web Content Accessibility Guidelines (WCAG) 2.1*. https://www.w3.org/TR/WCAG21/
- Driessen, V. (2010). *A successful Git branching model*. https://nvie.com/posts/a-successful-git-branching-model/
- Conventional Commits. (2023). *Conventional Commits 1.0.0*. https://www.conventionalcommits.org
- Ministerio de Energía y Minas. (2025). *Anuario estadístico de electricidad 2024. Capítulo 5: Distribución de energía eléctrica* [cuadro 5.3.3.1, venta mensual de energía eléctrica por sector económico]. MINEM. https://www.gob.pe/institucion/minem/informes-publicaciones/7324144-anuario-estadistico-de-electricidad-2024
- Organismo Supervisor de la Inversión en Energía y Minería. (s. f.). *Anexo B: Opciones tarifarias y condiciones de aplicación de las tarifas a usuario final*. OSINERGMIN. https://www.osinergmin.gob.pe/Resoluciones/pdf/ANEXO_B_Resolucion_1908.pdf
- Organismo Supervisor de la Inversión en Energía y Minería. (s. f.). *Pliegos tarifarios aplicables al cliente final*. OSINERGMIN. https://www.osinergmin.gob.pe/seccion/institucional/regulacion-tarifaria/pliegos-tarifarios/electricidad/pliegos-tarifiarios-cliente-final

## Anexos

**Anexo A. Estructura para la sección Objetivo del Estudiante (Student Outcome)**

Ver [Student Outcome](00-student-outcome.md).

**Anexo B. Informe de participación**

El *Final Project Individual Member Performance Report* lo elabora el Team Leader en un documento
aparte, con el nombre de archivo
`upc-pre-202620-1asi0732-<NRC>-energix-performance-<avn/tbn>` en `.docx` y `.pdf`, y se adjunta en
cada entrega.

| Ítem | Estudiante | Responsabilidades | Cumplimiento | Calificación |
| :-- | :-- | :-- | :-- | :-- |
| 1 | `<Apellidos, Nombres>` | `<Responsabilidades>` | `<A tiempo / A destiempo / Parcialmente / No cumplió>` | `<20/16/13/07/00>` |
| 2 | `<Apellidos, Nombres>` | `<Responsabilidades>` | `<...>` | `<...>` |
| 3 | `<Apellidos, Nombres>` | `<Responsabilidades>` | `<...>` | `<...>` |
| 4 | `<Apellidos, Nombres>` | `<Responsabilidades>` | `<...>` | `<...>` |
| 5 | `<Apellidos, Nombres>` | `<Responsabilidades>` | `<...>` | `<...>` |

**Anexo C. Videos**

| Entrega | Video | URL | Duración |
| :-- | :-- | :-- | :-- |
| TB1 | Exposición | `<URL privado de Microsoft Stream>` | `<mm:ss>` |
| TB1 | About-the-Product | `<URL>` | `<mm:ss>` |
| TB1 | About-the-Team | `<URL>` | `<mm:ss>` |
| TB1 | Evidencia de entrevistas | `<URL>` | `<mm:ss>` |

**Anexo D. Enlaces del proyecto**

| Recurso | URL |
| :-- | :-- |
| Organización | <https://github.com/SEMS-Diseno-de-Experimentos> |
| Repositorio del informe | <https://github.com/SEMS-Diseno-de-Experimentos/SEMS-Report> |
| Repositorio del Landing Page | <https://github.com/SEMS-Diseno-de-Experimentos/SEMS-Landing-Page> |
| Repositorio de la aplicación web | <https://github.com/SEMS-Diseno-de-Experimentos/SEMS-Web-Application> |
| Repositorio de la API | <https://github.com/SEMS-Diseno-de-Experimentos/SEMS-Backend> |
| Repositorio de la aplicación móvil | <https://github.com/SEMS-Diseno-de-Experimentos/SEMS-Mobile-App> |
| Landing Page desplegado | <https://sems-diseno-de-experimentos.github.io/SEMS-Landing-Page/> |
| Aplicación web desplegada | `<URL de Vercel>` |
| API desplegada | `<URL del servicio>` |
| Documentación de la API | `<URL del servicio>/swagger` |
| Tablero de gestión | `<URL del tablero>` |





