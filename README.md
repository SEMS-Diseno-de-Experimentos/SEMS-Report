
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

`<Insertar imagen del logo de Energix>`

### 1.1.2. Perfiles de integrantes del equipo

| Integrante | Código | Carrera | Perfil |
| :-- | :-- | :-- | :-- |
| `<Apellidos, Nombres>` **(Team Leader)** | `<Código>` | Ingeniería de Software | `<Foto. Párrafo de resumen con los principales conocimientos técnicos y habilidades que aporta al equipo.>` |
| `<Apellidos, Nombres>` | `<Código>` | Ingeniería de Software | `<Foto. Párrafo de resumen con los principales conocimientos técnicos y habilidades que aporta al equipo.>` |
| `<Apellidos, Nombres>` | `<Código>` | Ingeniería de Software | `<Foto. Párrafo de resumen con los principales conocimientos técnicos y habilidades que aporta al equipo.>` |
| `<Apellidos, Nombres>` | `<Código>` | Ingeniería de Software | `<Foto. Párrafo de resumen con los principales conocimientos técnicos y habilidades que aporta al equipo.>` |
| `<Apellidos, Nombres>` | `<Código>` | Ingeniería de Software | `<Foto. Párrafo de resumen con los principales conocimientos técnicos y habilidades que aporta al equipo.>` |

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
determina por el **pico más alto registrado**, aunque ese pico haya durado quince minutos. En un
supermercado, el arranque simultáneo de los compresores de las cámaras frigoríficas tras un
corte, una jornada de alta afluencia o la puesta en marcha del aire acondicionado a primera hora
bastan para producirlo. El administrador del local no dispone de ninguna señal en el momento en
que ocurre: se entera treinta días después, cuando llega el recibo, y para entonces el recargo ya
está aplicado a todo el periodo.

A esa ceguera se añade una segunda: el recibo llega agregado por suministro. No indica qué zona
del local ni qué equipo originó el consumo, de modo que aunque el responsable quiera actuar, no
sabe **dónde** actuar. En una cadena con varias sedes el problema se multiplica, porque tampoco
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

`<Insertar imagen del Lean UX Canvas elaborado por el equipo, con los ocho cuadrantes:
1. Business Problem · 2. Business Outcomes · 3. Users · 4. User Outcomes & Benefits ·
5. Solutions · 6. Hypotheses · 7. What's the most important thing we need to learn first? ·
8. What's the least amount of work we need to do to learn the next most important thing?>`

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

| Competitive Analysis Landscape | | **Energix — SEMS** | **Schneider EcoStruxure** | **Portal de la distribuidora** | **Medidores tipo Refoss / Shelly** |
| :-- | :-- | :-- | :-- | :-- | :-- |
| **¿Por qué llevar a cabo este análisis?** | | Determinar qué necesidad del segmento de establecimientos comerciales no está siendo atendida por la oferta actual, y sobre qué base construir la ventaja competitiva de SEMS. | | | |
| **Perfil** | Overview | Plataforma web de gestión energética para establecimientos comerciales. Mide por local y por zona, calcula con la tarifa comercial peruana y avisa antes de superar la potencia contratada. | Suite empresarial de gestión de energía y automatización para industria y edificios corporativos. | Portal de consulta de consumo y facturación que la distribuidora ofrece a sus clientes. | Dispositivos de medición de consumo con aplicación móvil, orientados al mercado doméstico. |
| | Ventaja competitiva | Modela la estructura tarifaria comercial peruana completa (punta, fuera de punta y demanda máxima) y alerta con margen antes del exceso. | Profundidad técnica, calidad de energía, integración con control industrial y respaldo de marca global. | El dato proviene de la misma empresa que emite la factura. | Precio bajo e instalación sencilla. |
| **Perfil de Marketing** | Mercado objetivo | Establecimientos comerciales de 200 a 2.000 m² y cadenas de retail pequeñas y medianas. | Industria, minería, edificios corporativos y grandes superficies. | Todos los clientes de la concesionaria. | Consumidor doméstico y pequeño negocio. |
| | Estrategias de marketing | Venta directa a cadenas, alianzas con gremios de comerciantes y prueba piloto gratuita en un local. | Red de integradores certificados y venta consultiva de alto ticket. | Canal propio incluido en el servicio. | Comercio electrónico y retail de tecnología. |
| **Perfil de Producto** | Productos y servicios | Landing page, aplicación web, API RESTful y aplicación móvil. Alertas de demanda, factura estimada desglosada, consumo por zona y comparación entre locales. | Medidores, software de supervisión, servicios de ingeniería y analítica avanzada. | Consulta de recibos, histórico de consumo y demanda facturada. | Medidor con aplicación de consumo y automatizaciones básicas. |
| | Precios y costos | Suscripción mensual escalonada por número de locales. Plan de entrada gratuito para un local. | Licenciamiento e implementación de alto costo, con proyecto de integración. | Sin costo adicional, incluido en el servicio eléctrico. | Pago único por dispositivo. |
| | Canales de distribución | Web y móvil. | Integradores y fuerza de ventas directa. | Web y aplicación de la distribuidora. | Comercio electrónico. |
| **Análisis SWOT** | Fortalezas | Modela la tarifa comercial peruana; alerta preventiva de demanda; desglose por zona; equipo con conocimiento del contexto regulatorio local. | Marca consolidada, robustez técnica, catálogo completo de hardware y software. | Acceso directo al dato oficial de facturación. | Costo bajo, gran base instalada y facilidad de uso. |
| | Debilidades | Startup sin trayectoria ni base instalada; depende de hardware de medición de terceros; sin histórico de casos de éxito. | Costo y complejidad desproporcionados para el segmento; ciclo de venta largo. | Dato diferido y agregado; sin desglose por zona; sin capacidad de alerta preventiva. | No modela franja horaria ni demanda máxima; orientado al hogar; sin gestión multi-local. |
| | Oportunidades | Segmento desatendido entre el medidor doméstico y la suite industrial; presión creciente sobre los costos operativos del retail. | Expansión hacia edificios comerciales medianos. | Ampliar los servicios digitales al cliente comercial. | Adaptar su producto al segmento comercial. |
| | Amenazas | Que la distribuidora o un fabricante de medidores incorporen alertas de demanda en su propia oferta. | Competidores especializados más ágiles en nichos concretos. | Regulación y competencia en la comercialización eléctrica. | Saturación del mercado y competencia por precio. |

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

`<Resumen descriptivo de las respuestas del entrevistado a las preguntas realizadas, incluyendo
características objetivas y subjetivas.>`

> Repetir esta ficha para cada entrevista: **3 a 5 por segmento**.

### 2.2.3. Análisis de entrevistas

> **Pendiente de ejecución por el equipo.** Se completa una vez registradas las entrevistas.

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

> Los artefactos de esta sección **derivan de las entrevistas** y deben elaborarse una vez
> registradas y analizadas. Se incluye aquí la estructura y las herramientas indicadas por el
> enunciado. Construirlos antes de entrevistar invalidaría el proceso: los arquetipos dejarían de
> representar a personas reales y pasarían a ser suposiciones del equipo.

### 2.3.1. User Personas

Elaborados en **UXPressia**, uno por segmento objetivo. Cada User Persona debe incluir datos
demográficos, rasgos de personalidad, motivaciones, frustraciones, objetivos, marcas e
influencias, canales digitales y dispositivos, **todos derivados del análisis de la sección 2.2.3**.

**User Persona — Segmento #1: Responsable de operaciones de cadena**

`<Insertar imagen del User Persona elaborado en UXPressia>`

`<Párrafo explicativo del arquetipo, indicando de qué hallazgos de las entrevistas proviene cada
característica.>`

**User Persona — Segmento #2: Propietario de establecimiento independiente**

`<Insertar imagen del User Persona elaborado en UXPressia>`

`<Párrafo explicativo.>`

### 2.3.2. User Task Matrix

Matriz de tareas por User Persona, indicando frecuencia e importancia de cada tarea.

| Tarea | Persona #1 — Frecuencia | Persona #1 — Importancia | Persona #2 — Frecuencia | Persona #2 — Importancia |
| :-- | :-- | :-- | :-- | :-- |
| Revisar el consumo del día | `<Alta/Media/Baja>` | `<Alta/Media/Baja>` | `<...>` | `<...>` |
| Revisar el recibo mensual | | | | |
| Identificar la causa de una variación en el recibo | | | | |
| Atender un aviso de consumo anómalo | | | | |
| Comparar el desempeño entre locales | | | | |
| Configurar umbrales y avisos | | | | |
| Dar acceso a personal del local | | | | |
| Registrar un equipo o medidor nuevo | | | | |
| Descargar un reporte para la gerencia | | | | |

### 2.3.3. User Journey Mapping

El *User Journey Map* recorre la experiencia completa de cada User Persona a lo largo de un ciclo
de facturación, desde que empieza el mes hasta que recibe el recibo. A diferencia del *As-Is
Scenario Map*, que describe la secuencia de acciones, el *Journey Map* añade la dimensión
emocional y el nivel de conocimiento que la persona tiene en cada fase, que es lo que explica por
qué el problema persiste.

> `<Insertar los User Journey Maps elaborados en UXPressia, uno por cada User Persona.>`

**User Journey Map — User Persona #1 (responsable de operaciones de cadena)**

| Fase | Acción | Punto de contacto | Qué piensa | Emoción | Oportunidad |
| :-- | :-- | :-- | :-- | :-- | :-- |
| Inicio del mes | Recibe el presupuesto energético del trimestre | Hoja de cálculo interna | «Tengo que cerrar por debajo de lo presupuestado» | Confianza | Fijar un objetivo por local y medirlo desde el día 1 |
| Operación diaria | Delega la operación en cada jefe de tienda | Llamadas y mensajería | «Confío en que avisen si algo pasa» | Neutral | Dar a cada sede su propia vista con permisos acotados |
| Ocurre el pico | Nadie lo percibe: la operación continúa con normalidad | Ninguno | — | Ignorancia | **Alerta con margen antes de superar la potencia contratada** |
| Llega el recibo | Detecta un cargo por potencia superior al previsto | Recibo de la distribuidora | «¿De dónde salió esto?» | Frustración | Desglose por local y por zona del periodo facturado |
| Investigación | Pide explicaciones a la sede y no obtiene evidencia | Correo, reuniones | «Nadie sabe qué pasó» | Impotencia | Historial de demanda con marca temporal del pico |
| Cierre | Justifica la desviación ante gerencia sin causa raíz | Informe mensual | «El mes que viene puede repetirse» | Resignación | Comparación entre locales para aislar la sede desviada |

**User Journey Map — User Persona #2 (propietario de establecimiento independiente)**

| Fase | Acción | Punto de contacto | Qué piensa | Emoción | Oportunidad |
| :-- | :-- | :-- | :-- | :-- | :-- |
| Inicio del mes | Opera el local sin ninguna referencia de consumo | Local | «La luz es lo que es» | Indiferencia | Panel simple con el consumo del día en soles |
| Operación diaria | Enciende todo al abrir y apaga al cerrar | Tablero eléctrico | «Siempre lo hemos hecho así» | Rutina | Señalar el arranque simultáneo como causa de pico |
| Ocurre el pico | No lo percibe | Ninguno | — | Ignorancia | **Aviso inmediato en el móvil con qué hacer** |
| Llega el recibo | Ve un importe mayor sin explicación | Recibo | «¿Por qué subió si trabajé igual?» | Ansiedad | Comparación contra los tres meses anteriores |
| Reacción | Apaga equipos al azar para ahorrar | Local | «Algo tengo que hacer» | Angustia | Recomendación concreta priorizada por impacto |
| Cierre | Asume el costo como inevitable | — | «Es parte del negocio» | Resignación | Evidencia del ahorro conseguido mes a mes |

### 2.3.4. Empathy Mapping

Elaborados en **UXPressia**, uno por User Persona, con los cuadrantes *Thinks and Feels*, *Sees*,
*Says and Does*, *Hears*, *Pains* y *Gains*.

`<Insertar imagen del Empathy Map del User Persona #1 y su explicación>`

`<Insertar imagen del Empathy Map del User Persona #2 y su explicación>`

### 2.3.5. As-is Scenario Mapping

Elaborados en **LucidChart o Miro**, uno por User Persona, con las filas *Phases*, *Doing*,
*Thinking* y *Feeling*, describiendo cómo el usuario afronta hoy la gestión del costo energético
de su establecimiento **sin** la solución.

`<Insertar imagen del As-is Scenario Map del User Persona #1 y su explicación>`

`<Insertar imagen del As-is Scenario Map del User Persona #2 y su explicación>`

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


