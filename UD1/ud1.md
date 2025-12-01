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

### 3. Identificación de necesidades tecnológicas (Enfoque Innovador)

La auditoría de seguridad revela que la empresa tiene servidores antiguos en la oficina que deben ser accesibles desde internet, pero la conexión a internet de la sede carece de IP fija y seguridad perimetral moderna. Para solucionar esto sin migrar todos los datos (costoso) ni exponer la red local (peligroso), se propone una arquitectura de **"Nube Híbrida con Túnel Inverso"**.

Las necesidades técnicas se han elevado para superar los estándares básicos:

* **Conectividad y Seguridad (SRI):** En lugar de las VPNs tradicionales (lentas y pesadas), se requiere implementar **WireGuard**, un protocolo de nueva generación más rápido y auditable. Se necesita un **VPS en la nube (AWS)** que actúe de "cara pública", limpiando el tráfico malicioso antes de que llegue a la oficina mediante un **Proxy Inverso**.
* **Gestión de Identidad (ASO):** Centralización de usuarios con **OpenLDAP**, pero integrando una gestión moderna. Se requiere que los servicios web lean estos usuarios para evitar duplicidad de contraseñas.
* **Despliegue de Aplicaciones (IAW):** Para maximizar los recursos del hardware limitado, se abandonará la virtualización tradicional por servidor en favor de la **Containerización (Docker)**. Se desplegará **Nextcloud** y una Wiki interna utilizando *Docker Compose*, facilitando las copias de seguridad y la actualización.
* **Monitorización Inteligente (SAD):** Se sustituye la revisión manual de logs por un stack de observabilidad: **Prometheus** (métricas) + **Grafana** (visualización). El elemento diferenciador será la **automatización de respuesta con n8n**: si un servicio cae, n8n recibirá la alerta y notificará automáticamente al equipo de guardia vía Telegram/Email, cerrando el ciclo de incidente.

### 4. Oportunidades y viabilidad del proyecto

Este proyecto es altamente viable tanto técnica como económicamente. Al utilizar tecnologías *Open Source* (Linux, Apache, KVM), el coste de licencias se minimiza, permitiendo destinar el presupuesto a hardware y formación. Para la empresa, esta modernización supone una ventaja competitiva directa: poder certificar ante sus clientes que cumplen con estándares de seguridad ISO 27001, algo cada vez más exigido en licitaciones públicas y grandes contratos.

Desde la perspectiva del alumno (**IPE II**), este escenario permite entrenar competencias transversales de "DevOps" y "SysAdmin". Resolver problemas de integración entre la base de datos, el servidor web y la seguridad perimetral simula fielmente los desafíos diarios de un administrador de sistemas en el mercado laboral sevillano actual.

### 5. Obligaciones legales y normativas

El proyecto se regirá estrictamente por el **RGPD (Reglamento General de Protección de Datos)**. Al gestionar una base de datos de empleados y clientes, se implementarán medidas de *Privacy by Design*: cifrado de discos, políticas de contraseñas fuertes y logs de acceso inalterables.

Adicionalmente, se considerará la **Ley de Propiedad Intelectual**, asegurando que todo el software desplegado tenga licencias compatibles (GPL, Apache, MIT) para uso comercial. En el ámbito de la seguridad de la información, se seguirán las guías del **Esquema Nacional de Seguridad (ENS)** en nivel básico, como buena práctica recomendada para proveedores tecnológicos de la administración pública.

### 6. Guion inicial del proyecto

El proyecto implementará un esquema de "Servicios Ocultos" protegidos por la nube:

* **Fase 1: El Bastión Local (SRI + ASO).**
    * Despliegue de **OPNsense** (o servidor Linux endurecido) en VirtualBox como Gateway.
    * Segmentación de red: DMZ interna y Red de Servicios.
    * Configuración de políticas de Firewall estrictas (Deny All por defecto).

* **Fase 2: Containerización de Servicios (IAW + ASGBD).**
    * Instalación de **Docker Engine** en el Servidor de Aplicaciones.
    * Despliegue del stack `docker-compose.yml`:
        * **OpenLDAP** + **phpLDAPadmin** (Gestión visual de usuarios).
        * **Nextcloud** + **MariaDB** (Almacenamiento y BBDD).
    * Vinculación de Nextcloud con LDAP para login único.

* **Fase 3: Hibridación y Exposición Segura (AWS).**
    * Despliegue de instancia EC2 en AWS (Capa Gratuita).
    * Configuración de **WireGuard Site-to-Site**: AWS y la oficina se ven como si estuvieran en el mismo cable.
    * Configuración de **Nginx Proxy Manager** (o Caddy) en AWS: Recibe el tráfico web público (HTTPS con Let's Encrypt automático) y lo deriva por el túnel VPN hasta el Docker local. *Resultado: La IP de la oficina nunca se expone.*

* **Fase 4: Observabilidad y Automatización (SAD).**
    * Despliegue de **Prometheus** y **Grafana** en contenedores.
    * Configuración de "Exporters" en los nodos para medir CPU/RAM.
    * **Workflow de n8n**: Webhook de alerta -> Proceso de lógica (¿Es crítico?) -> Envío de mensaje a Telegram del SysAdmin.

---
