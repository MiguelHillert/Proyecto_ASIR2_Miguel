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

### 3. Identificación de necesidades tecnológicas

Tras simular una auditoría técnica basada en los estándares del sector, se detectan las siguientes necesidades críticas para la operatividad de la consultora:

* **Servicios de Red (SRI):** La red actual es plana. Se requiere segmentación mediante VLANs (Desarrollo, Administración, Invitados), un servicio DHCP/DNS robusto y acceso remoto vía VPN para los desarrolladores.
* **Sistemas Operativos (ASO):** Estandarización de servidores. Se necesita un Directorio Activo (o LDAP en Linux) para centralizar la gestión de los 50+ usuarios y equipos, aplicando políticas de grupo (GPO) restrictivas.
* **Aplicaciones Web (IAW):** Despliegue de herramientas internas de productividad. Específicamente, una nube privada (*Nextcloud*) para eliminar el uso de "Shadow IT" (Dropbox personal) y un servidor web para alojar la Wiki interna de documentación.
* **Bases de Datos (ASGBD):** Implementación de un servidor de bases de datos dedicado (MySQL/MariaDB) que soporte los entornos de "Staging" (pruebas) de los desarrolladores, separado del entorno de producción.
* **Seguridad y Alta Disponibilidad (SAD):** Dado que la empresa ofrece servicios 24/7, es imperativo implementar un clúster de Alta Disponibilidad para la web corporativa y un cortafuegos perimetral (Pfsense/Opnsense) con detección de intrusos (IDS).

### 4. Oportunidades y viabilidad del proyecto

Este proyecto es altamente viable tanto técnica como económicamente. Al utilizar tecnologías *Open Source* (Linux, Apache, KVM), el coste de licencias se minimiza, permitiendo destinar el presupuesto a hardware y formación. Para la empresa, esta modernización supone una ventaja competitiva directa: poder certificar ante sus clientes que cumplen con estándares de seguridad ISO 27001, algo cada vez más exigido en licitaciones públicas y grandes contratos.

Desde la perspectiva del alumno (**IPE II**), este escenario permite entrenar competencias transversales de "DevOps" y "SysAdmin". Resolver problemas de integración entre la base de datos, el servidor web y la seguridad perimetral simula fielmente los desafíos diarios de un administrador de sistemas en el mercado laboral sevillano actual.

### 5. Obligaciones legales y normativas

El proyecto se regirá estrictamente por el **RGPD (Reglamento General de Protección de Datos)**. Al gestionar una base de datos de empleados y clientes, se implementarán medidas de *Privacy by Design*: cifrado de discos, políticas de contraseñas fuertes y logs de acceso inalterables.

Adicionalmente, se considerará la **Ley de Propiedad Intelectual**, asegurando que todo el software desplegado tenga licencias compatibles (GPL, Apache, MIT) para uso comercial. En el ámbito de la seguridad de la información, se seguirán las guías del **Esquema Nacional de Seguridad (ENS)** en nivel básico, como buena práctica recomendada para proveedores tecnológicos de la administración pública.

### 6. Guion inicial del proyecto

El despliegue técnico se estructurará en las siguientes fases:

* **Fase 1: Infraestructura Base (ASO + SRI).** Instalación de hipervisores, configuración de red, segmentación (VLANs), servicios DHCP/DNS y configuración del Firewall perimetral.
* **Fase 2: Despliegue de Servicios (IAW + ASGBD).** Instalación y bastionado del servidor de Base de Datos. Despliegue de la aplicación "Nextcloud" y la Intranet corporativa sobre pila LAMP.
* **Fase 3: Aseguramiento (SAD).** Configuración de clúster HA (Alta Disponibilidad) para el servidor web, implementación de RAID software y programación de scripts de Backup automáticos (locales y remotos).
* **Fase 4: Documentación y Entrega.** Elaboración de manuales de explotación, plan de recuperación ante desastres y documentación técnica final.
