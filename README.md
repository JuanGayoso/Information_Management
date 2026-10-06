# Information Management — Plantillas modulares IPR e IPP

Plantillas para gestionar la información de proyectos de edificación privada bajo ISO 19650 y ISO 7817-1 (LOIN), con enfoque **Lean / VDC / IPD** y formatos **openBIM** (IFC, BCF, IDS, bSDD).

| Plantilla | Quién la redacta | Para qué sirve | Archivo |
|---|---|---|---|
| **IPR** — Information Product/Purpose Requirements (≡ **EIR**) | Appointing Party (cliente), con apoyo del Information Manager | Declara **qué** información necesita el cliente y **para qué** | [`plantillas/IPR_Modular_v2.0.docx`](plantillas/IPR_Modular_v2.0.docx) |
| **IPP** — Information Production Plan (≡ **BEP**) | Lead Appointed Party, con el Information Manager | Responde al IPR: **cómo, quién y cuándo** se produce esa información | [`plantillas/IPP_Modular_v2.0.docx`](plantillas/IPP_Modular_v2.0.docx) |

> **Estado normativo.** Los nombres IPR e IPP vienen del Draft International Standard de la revisión de ISO 19650 (consulta pública desde el 10 de marzo de 2026; publicación definitiva proyectada para 2027). **Esa revisión aún no es norma vigente.** Bajo el marco contractual aplicable hoy (ISO 19650-2:2018 y -3:2020) los mismos documentos se llaman **EIR** y **BEP**: su contenido y función son equivalentes y pueden presentarse como tales sin modificación. La especificación de niveles de información sigue ISO 7817-1:2024.

---

## 1. Principio de uso

**Un objetivo activa módulos; un módulo nunca se activa solo.**

Cada requisito de información se traza a una cadena única. Si un contenedor de información no llega hasta un objetivo del cliente, no se produce (principio *pull* de Lean Construction).

```mermaid
flowchart LR
    A["1. Objetivo de negocio<br/>¿para qué?"] --> B["2. Propósito de uso<br/>¿quién lo consume y<br/>qué decide?"]
    B --> C["3. LOIN<br/>geometría, datos y<br/>documentos por objeto y hito"]
    C --> D["4. Contenedor<br/>TIDP / MIDP"]
    D --> E["5. Verificación<br/>y validación"]
    E --> F["6. Lección aprendida<br/>mejora del estándar"]
    F -.->|"PDCA"| A
```

---

## 2. Flujo general: primero el IPR, luego el IPP

El IPR se llena **primero** y es la fuente de la que el IPP deriva su configuración. Los objetivos marcados en el IPR (sección 1.1) determinan qué módulos del IPP se activan.

```mermaid
flowchart TD
    subgraph FASE1["FASE 1 — IPR (cliente / Information Manager)"]
        direction TB
        I1["Portada y datos del proyecto"] --> I2["1.1 Marcar objetivos del cliente O1–O12"]
        I2 --> I3["2.3 Plan de Usos:<br/>activar propósitos P1–P7"]
        I3 --> I4["2.4 Configuración del IPP exigida<br/>módulos Núcleo / Propósito / Soporte"]
        I4 --> I5["3 Gobernanza · 4 LOIN · 5 CDE y formatos<br/>6 Hitos H1–H5 · 7 Criterios de evaluación"]
        I5 --> I6["8 Entrega al AIM<br/>solo si O6 u O7"]
        I6 --> I7["Anexos A–C: matrices LOIN<br/>D: metrados · E: espacios"]
        I7 --> I8["Anexo F: trazabilidad IPR → IPP<br/>y aprobación"]
    end

    I8 ==>|"IPR aprobado y emitido"| P1

    subgraph FASE2["FASE 2 — IPP (Lead Appointed Party / Information Manager)"]
        direction TB
        P1["Paso 1 · Leer el IPR<br/>(si no hay: Anexo D del IPP, IPR mínimo)"] --> P2["Paso 2 · N1 y N2<br/>copiar y confirmar objetivos y Plan de Usos"]
        P2 --> P3["Paso 3 · Parte 0<br/>matriz objetivo→módulos (0.5), perfil (0.6)<br/>y Registro de configuración (0.9)"]
        P3 --> P4["Paso 4 · N3 + Anexo A (+ S2)<br/>LOIN por objeto × propósito × hito,<br/>antes de modelar"]
        P4 --> P5["Paso 5 · N4 + Anexo B<br/>hitos, TIDP y MIDP<br/>solo contenedores trazables"]
        P5 --> P6["Paso 6 · N5 y N6, luego módulos P activos,<br/>luego módulos S activos"]
        P6 --> P7["Paso 7 · N7 y movilización<br/>firmar configuración y publicar en el CDE"]
    end

    P7 -.->|"cambios por adenda al IPR"| I4
```

### 2.1 Fase 1 — Cómo llenar el IPR

Orden recomendado. Las decisiones de los primeros pasos condicionan los siguientes.

| Paso | Sección del IPR | Qué se decide | Quién |
|---|---|---|---|
| 1 | Portada | Proyecto, tipo de activo, fase, disciplinas, Appointing Party, estado del documento | Information Manager |
| 2 | **1.1** Objetivos del cliente | **Marcar O1–O12.** Es el selector principal de todo el sistema | Cliente |
| 3 | **2.3** Plan de Usos | Activar propósitos P1–P7 con consumidor, decisión que habilitan e hitos. Un propósito sin consumidor no se activa | Cliente + IM |
| 4 | **2.4** Configuración del IPP exigida | Módulos mínimos que exige el cliente (Núcleo, Propósito, Soporte). Se deriva de 1.1 | IM |
| 5 | 3 · 4 · 5 | Gobernanza y escala de criticidad · marco LOIN (3 pilares, 5 aspectos) · CDE, formatos abiertos, nomenclatura | IM |
| 6 | 6 | Hitos H1–H5, TIDP/MIDP y test *pull* de existencia de contenedores | IM + cliente |
| 7 | 7 | Criterios con que se evaluará el IPP | Cliente |
| 8 | 8 | Requisitos de entrega al AIM. **Solo si O6 u O7** | Cliente |
| 9 | Anexos A, B, C | Matrices LOIN de Arquitectura, Estructuras y MEP por objeto × propósito × hito. «No aplicable» es respuesta válida | IM + disciplinas |
| 10 | Anexos D, E | Metrados (si P2) y espacios (si P3) | IM |
| 11 | Anexo F | Trazabilidad IPR → IPP y firma de aprobación | Cliente + IM |

### 2.2 Fase 2 — Cómo llenar el IPP

El IPP **no se completa de la página 1 a la última**. Se ensambla en siete pasos (Parte 0, sección 0.4); cada paso consume decisiones del anterior y así se evita el retrabajo.

| Paso | Módulos | Qué se hace | Salida |
|---|---|---|---|
| 1 | Anexo D | Leer el IPR. Si el cliente no emitió uno, redactar el IPR mínimo con él | IPR (o IPR mínimo) firmado |
| 2 | **N1, N2** | Identificar el proyecto y confirmar los **objetivos del cliente**; de ahí salen propósitos y condiciones | Objetivos y Plan de Usos |
| 3 | **Parte 0** | Aplicar la matriz objetivo → módulos (0.5) y el perfil de partida (0.6); firmar el Registro de configuración (0.9) | Registro de configuración |
| 4 | **N3, Anexo A**, S2 | Definir el LOIN por objeto × propósito × hito **antes de modelar** | Matriz LOIN aprobada |
| 5 | **N4, Anexo B** | Hitos, TIDP y MIDP, solo con contenedores trazables a un propósito activo | MIDP consolidado |
| 6 | N5, N6 → P activos → S activos | Primero CDE y roles; luego los módulos de propósito (orden P3 → P2 → P1 → P4 → P5 → P6 → P7); luego soporte (S1, S3, S6, S5, S4) | Módulos completos |
| 7 | **N7**, N5-8 | Cerrar KPIs con lo que realmente quedó activo, movilizar al equipo y **publicar** el IPP en el CDE | IPP en estado *Published* |

**Por qué ese orden:** P3 (espacios) va primero porque P2, P4 y P7 lo consumen; P1 necesita la georreferenciación de N5; P7 depende de P3 y S2; S4 (auditoría) va último porque audita contra lo definido en N3 y S2.

---

## 3. Estructura del IPP: tres capas de módulos

```mermaid
flowchart LR
    subgraph NUCLEO["NÚCLEO — siempre activo"]
        N["N1 Identificación y partes<br/>N2 Propósitos y Plan de Usos<br/>N3 LOIN (ISO 7817-1)<br/>N4 Hitos, TIDP y MIDP<br/>N5 CDE, nomenclatura, formatos<br/>N6 Roles y conducta<br/>N7 Verificación, KPIs y mejora"]
    end
    subgraph PROP["PROPÓSITO — por objetivo del cliente"]
        P["P1 Coordinación e interferencias<br/>P2 Cuantificación y metrados<br/>P3 Espacios<br/>P4 Cumplimiento normativo<br/>P5 Documentación y comunicación 3D<br/>P6 Extensiones 4D / 6D<br/>P7 Activos y AIM / gemelo digital"]
    end
    subgraph SOP["SOPORTE — por condición del proyecto"]
        S["S1 Colaboración ICE / Big Room<br/>S2 Propiedades, clasificación, IDS<br/>S3 Seguridad (ISO 19650-5)<br/>S4 Calidad formal y auditoría<br/>S5 Riesgos del proceso<br/>S6 Planificación VDC / Last Planner"]
    end
    subgraph ANX["ANEXOS"]
        A["A Matriz LOIN · B TIDP/MIDP y catálogo<br/>C Diccionario de propiedades<br/>D IPR mínimo · E Registro de revisiones<br/>F Glosario"]
    end
    NUCLEO --> PROP --> SOP --> ANX
```

---

## 4. Qué módulos activar según el objetivo

Los módulos **N1–N7 se activan siempre.** Esta matriz (IPP, sección 0.5) indica qué módulos adicionales activa cada objetivo marcado en el IPR 1.1.

**●** activar (necesario para cumplir el objetivo) · **○** recomendado (activar salvo razón documentada)

| ID | Objetivo del cliente | Propósito | Soporte |
|---|---|---|---|
| **O1** | Coordinación multidisciplinar y constructibilidad | **P1** | **S1** · ○ S2, S4, S5 |
| **O2** | Certeza de costo: metrados desde el modelo (5D) | **P2** · ○ P3 | **S2** · ○ S4 |
| **O3** | Cumplimiento normativo y licenciamiento | **P3, P4** · ○ P5 | **S2** |
| **O4** | Documentación de construcción desde el modelo | **P5** | ○ S4 |
| **O5** | Validación del diseño con cliente y usuarios | **P5** | ○ S1 |
| **O6** | Continuidad hacia la operación (AIM / FM) | **P3, P7** | **S2** · ○ S3, S4 |
| **O7** | Gemelo digital | **P3, P7** | **S2, S3** |
| **O8** | Control de producción de diseño (VDC / Last Planner) | — | **S1, S6** · ○ S5 |
| **O9** | Secuenciación 4D o análisis energético 6D (por adenda) | **P6** · ○ P3 | ○ S2 |
| **O10** | Gestión de riesgos del proceso (proyecto complejo) | — | **S5** · ○ S4, S6 |
| **O11** | Información sensible o confidencial | — | **S3** |
| **O12** | Auditoría o QA formal exigido por contrato | — | **S4** · ○ S2 |

**Dependencias en cascada:** si se activa P2, P3 o P7, **S2 pasa a obligatorio** aunque no figure en la fila del objetivo. Otras dependencias: P1 requiere N3 y N5 (georreferencia); P4 requiere P3 y S2; P6 requiere P3 (6D); S6 requiere N4 y S1; S4 requiere N7 y S2.

```mermaid
flowchart LR
    O1["O1 Coordinación"] --> P1["P1"]
    O1 --> S1["S1"]
    O2["O2 Metrados 5D"] --> P2["P2"]
    O3["O3 Normativo"] --> P3["P3"]
    O3 --> P4["P4"]
    O6["O6 AIM / FM"] --> P3
    O6 --> P7["P7"]
    O7["O7 Gemelo digital"] --> P7
    O7 --> S3["S3"]
    O4["O4 Documentación"] --> P5["P5"]
    O5["O5 Validación 3D"] --> P5
    O9["O9 4D / 6D"] --> P6["P6"]
    O8["O8 VDC / LPS"] --> S6["S6"]
    O10["O10 Riesgos"] --> S5["S5"]
    O11["O11 Confidencial"] --> S3
    O12["O12 QA formal"] --> S4["S4"]
    P2 -.->|"cascada"| S2["S2"]
    P3 -.->|"cascada"| S2
    P7 -.->|"cascada"| S2
```

### Perfiles de configuración (punto de partida, IPP 0.6)

| Perfil | Cuándo usarlo | Módulos además del núcleo |
|---|---|---|
| **A — Esencial** | 1–2 disciplinas, un solo propósito | Un módulo P (+ S2 si es P2, P3 o P7) |
| **B — Coordinado** | Diseño multidisciplinar (ARQ + EST + MEP) con coordinación y presupuesto de control | P1, P2, S1, S2 |
| **C — Integrado Lean / IPD** | Proyecto complejo, producción de diseño planificada y medida | B + S4, S5, S6 (+ P5) |
| **D — Ciclo de vida (AIM)** | El cliente operará el activo y exige datos para FM o gemelo digital | C + P3, P7, S3 (+ P4) |

Se parte del perfil más cercano y se ajusta con la matriz anterior. Los perfiles no son obligatorios.

---

## 5. Hitos de entrega (comunes a IPR e IPP)

| Hito | Descripción | Estado CDE al cierre |
|---|---|---|
| **H1** Cabida | Estudio de factibilidad volumétrica | Shared |
| **H2** Anteproyecto | Anteproyecto arquitectónico y de ingenierías | Shared |
| **H3** Proyecto para revisión | Revisión del cliente y entidades | Shared → Published |
| **H4** Proyecto detallado / obra | Expediente técnico para construcción | Published |
| **H5** As-built *(opcional)* | Modelo verificado y datos de activos | Published |

Los hitos se definen **una sola vez** (IPR 6.1 / IPP N4-1); los demás módulos los citan y no redefinen fechas.

---

## 6. Principios que rigen ambos documentos

- **LOIN, no LOD.** Cada objeto se especifica con tres pilares (geométrico, alfanumérico, documentación) y, dentro del geométrico, cinco aspectos independientes: detalle, dimensionalidad, ubicación, apariencia y comportamiento paramétrico (ISO 7817-1:2024). Se pregunta siempre: ¿por qué (propósito)?, ¿cuándo (hito)?, ¿quién (actor)?, ¿qué (objeto)?
- **«No aplicable» es una respuesta válida** y es la herramienta principal contra la sobreentrega de información.
- **Fuente única de cada dato.** Cada dato vive en un solo lugar (IPP 0.8) y los demás módulos lo citan por código, sin copiarlo.
- **Test *pull* de existencia.** Un contenedor entra al MIDP solo si responde a: ¿a qué propósito sirve?, ¿quién lo consume?, ¿qué decisión habilita y cuándo?, ¿qué LOIN lo define?, ¿quién lo produce y en qué hito?
- **Reporte temprano sin estigma.** Una sola escala de criticidad (GRAVE / MEDIA / LEVE) con plazos de respuesta definidos.
- **Mejora continua.** Cada sesión ICE revisa también el proceso; las lecciones aprendidas se registran de forma estructurada y alimentan el estándar.
- **openBIM primero.** IFC 4.x para intercambio, BCF para incidencias, IDS para validación automatizada, bSDD para clasificación.

---

## 7. Cómo extender la plantilla

Para añadir un propósito nuevo (adquisiciones, fabricación digital, sostenibilidad), siga IPP 0.10:

1. Registrar el objetivo del cliente (N2-1) y el propósito (N2-2), con consumidor y decisión que habilita.
2. Crear el módulo con la ficha estándar.
3. Añadir al Anexo A las filas LOIN del nuevo propósito.
4. Añadir al Anexo B los contenedores trazables y actualizar el MIDP.
5. Actualizar las matrices 0.3, 0.5, 0.7 y 0.8 y el registro de configuración.
6. Si el IPR cambia, tramitar primero la **adenda al IPR**.

---

## Estructura del repositorio

```
Information_Management/
├── README.md
├── LICENSE
└── plantillas/
    ├── IPR_Modular_v2.0.docx   # Fase 1: requisitos del cliente
    └── IPP_Modular_v2.0.docx   # Fase 2: plan de producción (respuesta al IPR)
```

Versión de las plantillas: **2.0 — Octubre 2026 (borrador para revisión)**. Licencia: ver [`LICENSE`](LICENSE).
