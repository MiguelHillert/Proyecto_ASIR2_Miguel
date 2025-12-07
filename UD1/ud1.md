[Volver al índice general](../README.md)



-----

# UD1 – Análisis del entorno y detección de necesidades tecnológicas

## Índice de apartados
- [ ] **[1. Análisis del sector tecnológico](#1-análisis-del-sector-tecnológico)**
- [ ] **[2. Selección de la empresa o contexto de trabajo](#2-selección-de-la-empresa-o-contexto-de-trabajo)**
- [ ] **[3. Identificación de necesidades tecnológicas](#3-identificación-de-necesidades-tecnológicas)**
- [ ] **[4. Oportunidades y viabilidad del proyecto](#4-oportunidades-y-viabilidad-del-proyecto)**
- [ ] **[5. Obligaciones legales y normativas](#5-obligaciones-legales-y-normativas)**
- [ ] **[6. Guion inicial del proyecto](#6-guion-inicial-del-proyecto)**





-----

### 1\. Análisis del sector tecnológico

Voy a centrar mi análisis en el eje **Cartuja - Vega del Rey**, considerado el verdadero pulmón tecnológico de Andalucía. Aunque el PCT Cartuja es el núcleo histórico, el Parque Empresarial Vega del Rey (Camas) funciona como su extensión natural de "alto rendimiento", albergando sedes corporativas que requieren una infraestructura de sistemas crítica.

[cite_start]La relevancia de este entorno se confirma con los datos más recientes del **Informe de Evaluación y Desarrollo Tecnológico de Sevilla TechPark 2024** (ver [📄 Informe de Resultados](documentos/Informe-Resultados_Sevilla-TechPark_DEF.pdf)), que destaca una facturación agregada de **5.513 millones de euros** (un 13,7% más que el año anterior) y un ecosistema de **575 entidades** tecnológicas[cite: 3520].

Antes de entrar en detalle, es vital contextualizar la situación laboral con datos oficiales. Según el **Informe del Mercado de Trabajo de Sevilla 2024 (Datos 2023)** del SEPE (ver [📄 Informe Mercado Trabajo](documentos/Mercado_de_Trabajo_2024_Sevilla_(Datos_2023).pdf)):

  * **Estabilidad y Demanda:** Existe una dificultad real para cubrir vacantes técnicas. [cite_start]La **Tabla 32** del informe destaca explícitamente la escasez de candidatos para el perfil de **"Diseñadores y administradores de bases de datos"** y ocupaciones técnicas relacionadas con la informática[cite: 3222].
  * **Calidad del Empleo:** El informe señala el crecimiento sostenido de la contratación indefinida en el sector TIC, justificando la viabilidad laboral de la especialización propuesta en este proyecto.

### 2\. Selección de la empresa o contexto de trabajo

**Empresa seleccionada -\> OGA (oga.ai)**

Ubicada en el entorno de innovación de Sevilla, **OGA** no es una consultora tradicional; es una "boutique" especializada en **Inteligencia Artificial e Investigación Operativa** para eficientar procesos críticos en sectores como energía, logística y defensa.

He elegido esta empresa por su relevancia y proyección, tal como se detalla en su dossier de prensa (ver [📄 Noticia OGA Info](https://www.google.com/search?q=./documentos/oga_noticia_info.pdf)):

  * [cite_start]**Reconocimiento:** Ha sido galardonada en los **Premios de RSE y Sostenibilidad 2024** en la categoría PYME, destacando su compromiso con la innovación y la sostenibilidad[cite: 715].
  * [cite_start]**Innovación:** Cuenta con el apoyo del Grupo CÁTEDRA y lidera la Cátedra URJC-OGA en IA y Desarrollo Sostenible[cite: 731].
  * **Dependencia de la Infraestructura:** Al trabajar con modelos complejos de IA para grandes corporaciones, su dependencia de una infraestructura de sistemas robusta, segura y de alta disponibilidad es total.

### 3\. Identificación de necesidades tecnológicas

En el entorno de la Inteligencia Artificial aplicada, existe una brecha operativa importante: los científicos de datos desarrollan algoritmos complejos, pero a menudo carecen de la infraestructura robusta necesaria para ejecutarlos de forma segura y eficiente en producción.

Basándonos en la realidad del mercado laboral descrita en el informe del SEPE (ver [📄 Informe SEPE pág. 83](https://www.google.com/search?q=./documentos/Mercado%2520de%2520Trabajo%25202024%2520Sevilla%2520\(Datos%25202023\).pdf)) y la naturaleza crítica de OGA, el proyecto cubrirá tres necesidades clave:

  * **Profesionalización y Gobierno del Dato:**
    Dado que el informe del SEPE alerta sobre la falta de candidatos para administración de bases de datos (Tabla 32), este proyecto implementará un servidor de base de datos centralizado (**MariaDB**). El objetivo es pasar de datos dispersos a un sistema con políticas de usuarios estrictas y copias de seguridad automatizadas, protegiendo el activo más valioso de OGA.

  * **Continuidad Operativa y Monitorización:**
    Los procesos de IA son intensivos. Una caída del sistema implica pérdidas directas. Se requiere un sistema de **observabilidad en tiempo real** (con Grafana/Prometheus) que actúe como "signo vital" del servidor, alertando sobre saturación de recursos antes de que ocurra un fallo crítico.

  * **Acceso Remoto Seguro (Perímetro Híbrido):**
    La flexibilidad laboral es clave, pero exponer servidores de cálculo a internet es un riesgo. La solución técnica será un túnel **VPN (WireGuard)**, permitiendo a los ingenieros acceder a la potencia de cálculo de la oficina de forma cifrada y transparente.

### 4\. Oportunidades y viabilidad del proyecto

La viabilidad técnica es total y el coste de licencias nulo al basarse en **Software Libre** (Linux, Docker, Python). [cite_start]Además, el proyecto se alinea con la **I Estrategia Cloud de Andalucía 2030** (ver [📄 Estrategia Cloud Junta Andalucía](https://www.google.com/search?q=./documentos/Estrategia_Cloud_v.Publica.5r1.pdf)), que fomenta explícitamente la adopción de modelos de **nube híbrida**, la soberanía del dato y la ciberseguridad en el tejido productivo andaluz[cite: 35].

Para OGA, la rentabilidad es inmediata:

1.  **Ahorro de tiempo:** Automatización de despliegues para liberar a los desarrolladores.
2.  **Seguridad:** Contenerización de aplicaciones para reducir riesgos.
3.  **Escalabilidad:** Capacidad de replicar entornos de IA instantáneamente.

### 5\. Obligaciones legales y normativas

Al tratar con Inteligencia Artificial y datos masivos, el cumplimiento normativo es el pilar del proyecto. Aunque OGA sea una empresa privada, al proveer servicios críticos que pueden afectar a terceros, nos alineamos con las mejores prácticas del sector:

  * [cite_start]**Esquema Nacional de Seguridad (ENS):** Seguiremos las guías del ENS (Nivel Básico/Medio) para el bastionado de servidores, tal como se recomienda en la Estrategia Cloud de Andalucía para garantizar la integridad y disponibilidad de los sistemas[cite: 34].
  * **Reglamento Europeo de IA (AI Act):** El proyecto contempla desde el diseño la trazabilidad de los datos y la seguridad de los modelos, requisitos previos fundamentales para cumplir con la futura Ley de IA europea (DOUE L 2024/81079).
  * **RGPD:** Se implementarán medidas técnicas como cifrado de backups y logs inmutables para proteger los datos personales.

### 6\. Guion inicial del proyecto

```text
┌─────────────────────────────────────────────────────────────────────────────┐
│                       PROYECTO INFRAESTRUCTURA OGA.AI                       │
└─────────────────────────────────┬───────────────────────────────────────────┘
                                  │
                                  ▼
        ┌─────────────────────────────────────────────────────────┐
        │           FASE 1: Cimientos y Contenedorización         │
        │                                                         │
        ├─────────────────────────────────────────────────────────┤
        │                                                         │
        │  1. Host / Entorno Base                                 │
        │     ┌─────────────────────────────────────┐             │
        │     │ • Linux Server (Ubuntu)             │             │
        │     │ • Hardening SSH & Usuarios          │             │
        │     │ • Docker Engine & Compose           │             │
        │     └─────────────────────────────────────┘             │
        │                     │                                   │
        │                     ▼                                   │
        │  2. Empaquetado de Servicios                            │
        │     ┌─────────────────────────────────────┐             │
        │     │ • Dockerfile App (Python/API)       │             │
        │     │ • Dockerfile BBDD (MariaDB)         │             │
        │     └─────────────────────────────────────┘             │
        │                     │                                   │
        │                     ▼                                   │
        │  3. Automatización (Scripting)                          │
        │     ┌─────────────────────────────────────┐             │
        │     │ • Script Bash/Python "Deploy"       │             │
        │     │ • Gestión de variables de entorno   │             │
        │     └─────────────────────────────────────┘             │
        └─────────────────────────┬───────────────────────────────┘
                                  │
                                  ▼
        ┌─────────────────────────────────────────────────────────┐
        │           FASE 2: Seguridad y Datos Críticos            │
        │                                                         │
        ├─────────────────────────────────────────────────────────┤
        │                                                         │
        │  1. Red Segura y Acceso Remoto                          │
        │     ┌─────────────────────────────────────┐             │
        │     │ • WireGuard VPN (Acceso seguro)     │             │
        │     │ • Firewall (UFW/Iptables)           │             │
        │     │ • Segmentación de red Docker        │             │
        │     └─────────────────────────────────────┘             │
        │                     │                                   │
        │                     ▼                                   │
        │  2. Gestión de Datos (ASGBD)                            │
        │     ┌─────────────────────────────────────┐             │
        │     │ • Usuarios BBDD (Privilegios mín)   │             │
        │     │ • Backups Automáticos Cifrados      │             │
        │     │ • Volúmenes Persistentes            │             │
        │     └─────────────────────────────────────┘             │
        └─────────────────────────┬───────────────────────────────┘
                                  │
                                  ▼
        ┌─────────────────────────────────────────────────────────┐
        │          FASE 3: Observabilidad y Entrega               │
        │                                                         │
        ├─────────────────────────────────────────────────────────┤
        │                                                         │
        │  1. Monitorización Activa                               │
        │     ┌─────────────────────────────────────┐             │
        │     │ • Prometheus (Métricas)             │             │
        │     │ • Node Exporter (Hardware)          │             │
        │     └─────────────────────────────────────┘             │
        │                     │                                   │
        │                     ▼                                   │
        │  2. Visualización                                       │
        │     ┌─────────────────────────────────────┐             │
        │     │ • Grafana Dashboard                 │             │
        │     │ • Alertas (Telegram/Email)          │             │
        │     └─────────────────────────────────────┘             │
        │                     │                                   │
        │                     ▼                                   │
        │  3. Documentación Final                                 │
        │     ┌─────────────────────────────────────┐             │
        │     │ • Manual de Despliegue              │             │
        │     │ • Plan de Contingencia (DRP)        │             │
        │     │ • Diagrama de Arquitectura          │             │
        │     └─────────────────────────────────────┘             │
        └─────────────────────────┬───────────────────────────────┘
                                  │
                                  ▼
                    ┌─────────────────────────────┐
                    │     PROYECTO COMPLETADO     │
                    └─────────────────────────────┘
```

#### Descripción de Fases

**Fase 1: Cimientos y Contenedorización**

  * **Host:** Preparación del servidor Linux con medidas de seguridad básicas.
  * **Docker:** Creación de imágenes ligeras para la API de IA y la base de datos, asegurando que el entorno de desarrollo sea idéntico al de producción.
  * **Automatización:** Creación de un script en Bash/Python que levante todo el entorno con un solo comando (`./deploy.sh`).

**Fase 2: Seguridad y Datos Críticos**

  * **Acceso:** Implementación de **WireGuard** para que los desarrolladores accedan de forma segura desde casa.
  * **Datos:** Configuración experta de **MariaDB**, creando usuarios específicos y programando copias de seguridad automáticas para evitar pérdidas de datasets valiosos.

**Fase 3: Observabilidad y Entrega**

  * **Monitorización:** Despliegue del stack Prometheus + Grafana para ver en tiempo real si el servidor está saturado.
  * **Documentación:** Entrega del repositorio GitHub con el código, manuales y el Plan de Recuperación ante Desastres.

-----

### Enlaces y Recursos

  * **Informe Mercado Trabajo Sevilla 2024:** [📂 Ver documento local](https://www.google.com/search?q=./documentos/08_Informe_SEPE_Mercado_IT.pdf) (Referencia a la dificultad de cobertura de vacantes técnicas en Tabla 32).
  * **Web Corporativa OGA:** [🔗 oga.ai](https://oga.ai)
  * **Parque Vega del Rey:** [🔗 Información del Parque](https://www.google.com/search?q=parque+empresarial+vega+del+rey)
  * **PCT Cartuja:** [🔗 Informe de Actividad](https://www.pctcartuja.es/)

-----

  * **[Mercado Laboral]** `Mercado de Trabajo 2024 Sevilla (Datos 2023).pdf`: Informe del SEPE que justifica la demanda de perfiles ASGBD y SysAdmin.
  * **[Contexto Empresa]** `oga_noticia_info.pdf`: Información corporativa sobre OGA, sus premios y actividad en IA.
  * **[Ecosistema]** `Informe-Resultados_Sevilla-TechPark_DEF.pdf`: Datos sobre el impacto económico y tecnológico de Cartuja/Sevilla.
  * **[Estrategia Regional]** `Estrategia_Cloud_v.Publica.5r1.pdf`: Marco de referencia de la Junta de Andalucía para la adopción de Cloud y seguridad.
  * **[Normativa]** `enlacesBOEyreferenciamercadosevilla.pdf`: Referencias legales al ENS y normativa europea.




