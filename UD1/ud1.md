[Volver al índice general](../README.md)

# UD1 – Análisis del entorno y detección de necesidades tecnológicas

## Índice de apartados

- [ ] **1. Análisis del sector tecnológico**
- [ ] **2. Selección de la empresa o contexto de trabajo**
- [ ] **3. Identificación de necesidades tecnológicas**
- [ ] **4. Oportunidades y viabilidad del proyecto**
- [ ] **5. Obligaciones legales y normativas**
- [ ] **6. Guion inicial del proyecto**

## Enlaces a recursos de la unidad

- [Documentos de la unidad (Estudios de mercado y Normativa)](./documentos/)
- [Diagramas e imágenes (Mapa de red y DAFO)](./img/)

---

### 1. Análisis del sector tecnológico

El proyecto se sitúa geográficamente en el **Parque Científico y Tecnológico Cartuja (Sevilla TechPark)**, el principal motor tecnológico de Andalucía con una facturación agregada superior a los 4.000 millones de euros. El análisis del sector TIC en esta zona muestra una transición del modelo tradicional de "Outsourcing" hacia el desarrollo de producto propio y servicios de alto valor añadido (IA, Big Data y Ciberseguridad).

Sin embargo, los informes del sector (como el del *Círculo de Empresarios de Cartuja*) señalan un reto común: muchas empresas consolidadas crecieron rápidamente con infraestructuras "on-premise" que ahora resultan rígidas e inseguras frente a las nuevas amenazas de ransomware. Existe, por tanto, una demanda real y urgente de perfiles de administración de sistemas capaces de modernizar estas arquitecturas heredadas, garantizando la seguridad perimetral y la alta disponibilidad que exigen los clientes internacionales.

### 2. Selección de la empresa o contexto de trabajo

Para contextualizar el proyecto en un entorno real, se ha seleccionado el perfil de una **Consultora de Desarrollo de Software (Software Factory)** de tamaño mediano, con sede en el edificio *Centris* o *Pabellón de Italia* del PCT Cartuja. Este tipo de empresa (comparable a firmas reales de la zona como *Soltel* o *Guadaltech*) maneja datos sensibles de terceros y cuenta con equipos de desarrollo que requieren acceso remoto constante.

El escenario de trabajo parte de una situación habitual en el sector: la empresa ha sufrido micro-cortes en sus servicios y dificultades para gestionar el teletrabajo seguro de sus empleados. El proyecto no consiste en crear la empresa desde cero, sino en actuar como el **Departamento de Sistemas (IT)** que debe diseñar una nueva infraestructura interna (Intranet, Servidores de Pruebas y Almacenamiento) para solucionar la deuda técnica acumulada y profesionalizar el despliegue de sus aplicaciones.

### 3. Identificación de necesidades tecnológicas (Mapeo Curricular)

La auditoría técnica ha desglosado las necesidades del proyecto vinculándolas directamente a las competencias requeridas para la modernización de la infraestructura:

* **[ASGBD] Gestión de Datos Críticos:** La empresa no puede depender de bases de datos por defecto. Se requiere desplegar un servidor **MariaDB/MySQL** optimizado. No basta con la instalación; es imperativo configurar **políticas de usuarios (GRANTS)** para separar los permisos de la aplicación Nextcloud de los del administrador, así como programar **scripts de exportación lógica (mysqldump)** automatizados para evitar la pérdida de datos.
* **[ASO] Administración de Sistemas:** Se necesita estandarizar los servidores (Linux Ubuntu Server). El reto principal es la **gestión de identidades centralizada**: implementación de scripts en *Bash* y configuración de **OpenLDAP** para que los usuarios tengan *roaming profile* (su /home les sigue) y cuotas de disco asignadas.
* **[SRI] Interconexión Híbrida:** La red local debe conectarse con la nube. Se requiere configurar un **Servidor VPN (WireGuard)** que actúe de túnel transparente. Además, se debe implementar un servidor **DNS interno (Bind9 o Unbound)** para que las direcciones internas (`intranet.empresa.lan`) se resuelvan correctamente tanto en la oficina como a través de la VPN.
* **[IAW] Despliegue de Aplicaciones:** Abandonar las instalaciones monolíticas. Se requiere "dockerizar" la intranet corporativa (**Nextcloud** y Wiki). Esto implica configurar un **Proxy Inverso (Nginx/Traefik)** en la nube (AWS) que gestione los certificados SSL (HTTPS) y enrute el tráfico hacia los contenedores locales de forma segura.
* **[SAD] Seguridad y Monitorización:** La alta disponibilidad se simulará mediante la capacidad de recuperación rápida. Se necesita un sistema de **monitorización activa (Prometheus + Grafana)** que vigile el estado de los discos y la carga de la CPU. La seguridad perimetral se reforzará con **Fail2Ban** en el nodo expuesto a internet para mitigar ataques de fuerza bruta.
* **[IPE II] Enfoque Profesional:** El proyecto debe simular un entorno de producción real, priorizando el uso de herramientas demandadas en el mercado laboral (Docker, AWS, n8n) y generando documentación técnica que justifique la toma de decisiones (Soft Skills).

### 4. Oportunidades y viabilidad del proyecto

Este proyecto es altamente viable tanto técnica como económicamente. Al utilizar tecnologías *Open Source* (Linux, Apache, KVM), el coste de licencias se minimiza, permitiendo destinar el presupuesto a hardware y formación. Para la empresa, esta modernización supone una ventaja competitiva directa: poder certificar ante sus clientes que cumplen con estándares de seguridad ISO 27001, algo cada vez más exigido en licitaciones públicas y grandes contratos.

Desde la perspectiva del alumno (**IPE II**), este escenario permite entrenar competencias transversales de "DevOps" y "SysAdmin". Resolver problemas de integración entre la base de datos, el servidor web y la seguridad perimetral simula fielmente los desafíos diarios de un administrador de sistemas en el mercado laboral sevillano actual.

### 5. Obligaciones legales y normativas

El proyecto se regirá estrictamente por el **RGPD (Reglamento General de Protección de Datos)**. Al gestionar una base de datos de empleados y clientes, se implementarán medidas de *Privacy by Design*: cifrado de discos, políticas de contraseñas fuertes y logs de acceso inalterables.

Adicionalmente, se considerará la **Ley de Propiedad Intelectual**, asegurando que todo el software desplegado tenga licencias compatibles (GPL, Apache, MIT) para uso comercial. En el ámbito de la seguridad de la información, se seguirán las guías del **Esquema Nacional de Seguridad (ENS)** en nivel básico, como buena práctica recomendada para proveedores tecnológicos de la administración pública.

### 6. Guion inicial del proyecto

El cronograma de trabajo se organiza para cubrir todas las áreas técnicas de forma secuencial:

* **Fase 1: Cimientos de Red y Sistema (SRI + ASO).**
    * Despliegue de máquinas virtuales y configuración de interfaces de red.
    * Instalación del **Gateway OPNsense/Linux** con reglas de *iptables* y NAT.
    * Configuración de servicios básicos: **DHCP** para clientes y **DNS Split** (diferente resolución dentro y fuera).
    * Levantamiento del túnel **WireGuard** entre Local y AWS.

* **Fase 2: Persistencia y Datos (ASGBD).**
    * Despliegue del contenedor de Base de Datos (MariaDB).
    * **Tarea clave:** Creación de usuarios específicos (`nextcloud_user`, `admin_backup`) con privilegios mínimos.
    * Implementación de un script cron para **Backups diarios** de la BBDD hacia un volumen externo.

* **Fase 3: Aplicaciones y Web (IAW).**
    * Orquestación de contenedores con **Docker Compose**.
    * Despliegue de **Nextcloud** conectado a la BBDD de la Fase 2.
    * Configuración del **Proxy Inverso en AWS** para dar salida pública a los servicios internos bajo dominio seguro (HTTPS).

* **Fase 4: Seguridad y Observabilidad (SAD).**
    * Hardening del servidor expuesto en AWS (SSH por llaves, cierre de puertos).
    * Despliegue del stack **Prometheus + Grafana**.
    * Configuración de **n8n** para recibir alertas del sistema (ej: "Espacio en disco > 90%").

* **Fase 5: Documentación y Entrega (IPE II).**
    * Redacción del manual de contingencia.
    * Presentación del diagrama final de arquitectura.

---
