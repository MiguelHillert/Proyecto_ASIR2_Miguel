[Volver al índice general](../README.md)



-----

# UD1 – Análisis del entorno y detección de necesidades tecnológicas

## Índice de apartados
- [ ] **1. [Análisis del sector tecnológico](#1-análisis-del-sector-tecnológico)**
- [ ] **2. Selección de la empresa o contexto de trabajo**
- [ ] **3. Identificación de necesidades tecnológicas**
- [ ] **4. Oportunidades y viabilidad del proyecto**
- [ ] **5. Obligaciones legales y normativas**
- [ ] **6. Guion inicial del proyecto**

-----

### 1\. Análisis del sector tecnológico

Voy a centrar mi análisis en el eje **Cartuja - Vega del Rey**, considerado el verdadero pulmón tecnológico de Andalucía. Aunque el PCT Cartuja es el núcleo histórico, el Parque Empresarial Vega del Rey (Camas) funciona como su extensión natural de "alto rendimiento", albergando sedes corporativas que requieren una infraestructura de sistemas crítica.

Antes de entrar en detalle, es vital contextualizar la situación con datos oficiales. Según el **Informe del Mercado de Trabajo de Sevilla 2024 (Datos 2023) del SEPE**:

  * [cite_start]**Estabilidad y Demanda:** Existe una dificultad real para cubrir vacantes técnicas debido a la falta de candidatos cualificados y competencias técnicas específicas, especialmente en roles de gestión de datos y sistemas[cite: 2476, 2481, 2491].
  * **Calidad del Empleo:** El sector tecnológico presenta una estabilidad superior a la media y es uno de los motores de contratación indefinida, siendo un refugio seguro frente a la temporalidad que afecta a otros sectores.

En este entorno de Vega del Rey, no hablamos de micro-pymes, sino de grandes jugadores:

  * **Ayesa:** Gigante de ingeniería y tecnología.
  * **Vueling Innovation Lab:** Centro de desarrollo digital de la aerolínea.
  * **OGA (oga.ai):** La empresa en la que centraré mi proyecto.

### 2\. Selección de la empresa

**Empresa seleccionada -\> OGA (oga.ai)**

Ubicada en el Edificio Vega del Rey 1, **OGA** no es una consultora tradicional; es una "boutique" de **Inteligencia Artificial y Optimización de Procesos**. Trabajan con datos críticos para optimizar logística, industria y retail para clientes de gran calibre.

He elegido esta empresa porque su dependencia de la infraestructura es total. Si sus servidores de cálculo fallan, los algoritmos de IA no entrenan y el cliente pierde dinero. Esto eleva el nivel del proyecto: no se trata solo de mantener una red de oficina, sino de sostener una infraestructura de **Datos y Alto Rendimiento**.

### 3\. Identificación de necesidades tecnológicas

En el entorno de la Inteligencia Artificial aplicada, existe una brecha operativa importante: los científicos de datos desarrollan algoritmos complejos, pero a menudo carecen de la infraestructura robusta necesaria para ejecutarlos de forma segura y eficiente en producción.

Basándonos en la realidad del mercado laboral de Sevilla descrita en el informe del SEPE, el proyecto se centrará en cubrir tres necesidades críticas que las empresas tienen dificultades para resolver:

  * **Profesionalización y Gobierno del Dato:**
    [cite_start]El informe del SEPE destaca explícitamente en su Tabla 32 la dificultad para cubrir vacantes de **"Diseñadores y administradores de bases de datos"** por falta de candidatos[cite: 2491, 2500]. En OGA, el dato es el activo más valioso. La necesidad es migrar de sistemas de almacenamiento dispersos a un servidor de base de datos centralizado (**MariaDB**), configurado con políticas de usuarios estrictas y copias de seguridad automatizadas para garantizar que la información crítica nunca se pierda.

  * **Continuidad Operativa y Monitorización:**
    Los procesos de entrenamiento de IA son intensivos y costosos. Una caída del sistema no detectada a tiempo implica grandes pérdidas. Se requiere implementar un sistema de **observabilidad en tiempo real** (utilizando stacks como Grafana) que actúe como un "signo vital" del servidor, alertando preventivamente sobre saturación de recursos antes de que ocurra un fallo crítico. Esto responde a la demanda de perfiles capaces de mantener la alta disponibilidad de los sistemas.

  * **Acceso Remoto Seguro (Perímetro Híbrido):**
    La flexibilidad laboral es clave, pero exponer servidores de cálculo a internet es un riesgo inasumible. La solución técnica requerida es el despliegue de un túnel **VPN (WireGuard)**. Esto permite a los ingenieros acceder a la potencia de cálculo de la oficina desde cualquier ubicación de forma transparente y cifrada, sin comprometer la seguridad perimetral de la empresa.

### 4\. Oportunidades y viabilidad del proyecto

La viabilidad técnica es total y el coste de licencias es nulo. La propuesta se basa en sustituir procesos manuales por un stack tecnológico *Open Source* robusto: **Linux (Ubuntu Server), Docker y Python**.

Para OGA, la rentabilidad es inmediata:

1.  **Ahorro de tiempo:** Un despliegue automatizado libera a los desarrolladores senior de tareas repetitivas.
2.  **Seguridad:** Al usar contenedores aislados, se reduce el riesgo de que un error en una librería rompa el servidor entero.
3.  **Escalabilidad:** Si el proyecto crece, replicar un contenedor Docker es instantáneo.

### 5\. Obligaciones legales y normativas

Al tratar con Inteligencia Artificial y datos masivos, el cumplimiento normativo es el pilar del proyecto:

  * **RGPD (Reglamento General de Protección de Datos):** OGA trata datos que pueden ser personales o sensibles de sus clientes. Los backups deben estar cifrados y los accesos auditados (Logs inmutables).
  * **AI Act (Reglamento Europeo de IA):** Aunque es una normativa reciente, exige trazabilidad y transparencia en los sistemas de IA. Nuestra infraestructura debe permitir saber *quién* desplegó *qué* versión del modelo y *cuándo*.
  * **ENS (Esquema Nacional de Seguridad):** Necesario para garantizar la integridad y disponibilidad de los servicios, especialmente si colaboran con entidades públicas.

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
