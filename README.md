# Módulo Formativo: Gestión de Infraestructura de Redes y Sistemas Informáticos

Este repositorio académico funciona como el sistema centralizado de control docente, planificaciones, recursos didácticos y registro de temas impartidos para el desarrollo de las competencias profesionales del título **INCO03-3**.

---

## 🗺️ Mapa Curricular: 9 Resultados de Aprendizaje (RA)

Para facilitar el seguimiento de las clases, las prácticas de laboratorio (en entornos físicos y emulados como GNS3/Ubuntu y Packet Tracer) y la documentación técnica, el módulo se encuentra estructurado en los siguientes **9 Resultados de Aprendizaje**:

### 🏗️ Bloque I: Arquitectura, Cableado Estructurado e Interconexión (Fase Física y Lógica Inicial)
* **📂 RA01: Instalación y Configuración de Nodos de Red**
    * *Enfoque:* Fundamentos de redes locales (LAN), modelos de referencia, topologías, cálculo/diseño de cableado estructurado según normativas y despliegue del software de comunicación interna.
* **📂 RA02: Parámetros Operativos de Dispositivos de Interconexión**
    * *Enfoque:* Revisión de conmutadores (Switches) y hardware core, metodologías de verificación de conectividad y análisis de parámetros técnicos en dispositivos de distribución.
* **📂 RA03: Montaje de Equipos y Centros de Datos (Data Centers)**
    * *Enfoque:* Planificación y ejecución física en racks/gabinetes, direccionamiento IP estructurado (Subnetting VLSM), paneles de conexión (Patch Panels) y certificación/documentación del cableado.

### ⚙️ Bloque II: Configuración Avanzada y Redes Inalámbricas (Fase Lógica y Conectividad)
* **📂 RA04: Medios de Transmisión Inalámbricos (WLAN)**
    * *Enfoque:* Estándares de la industria (IEEE 802.11), ensamblaje, mitigación de vulnerabilidades/debilidades de seguridad inalámbrica y optimización de cobertura de los Access Points.
* **📂 RA05: Configuración de Dispositivos de Red bajo Plan Técnico**
    * *Enfoque:* Integración segura y eficiente de equipos a la infraestructura perimetral, mapeo en los modelos OSI y TCP/IP, ejecución de comandos CLI, pruebas de conectividad y documentación técnica.

### 🛡️ Bloque III: Soporte, Gestión de Incidencias y Monitoreo (Fase de Continuidad del Negocio)
* **📂 RA06: Soporte Técnico al Cableado Estructurado**
    * *Enfoque:* Ciclo de órdenes de servicio, mantenimiento preventivo/correctivo y aislamiento de anomalías físicas y lógicas en la infraestructura de transmisión.
* **📂 RA07: Resolución Avanzada de Incidencias en Dispositivos Locales**
    * *Enfoque:* Diagnóstico autónomo y avanzado en entornos de alta disponibilidad, aislamiento sistemático de fallos operacionales y análisis de protocolos de comunicación.
* **📂 RA08: Investigación de Fallos en Líneas de Transmisión y Equipos**
    * *Enfoque:* Monitoreo efectivo del desempeño de la red, interpretación avanzada de esquemas e investigación profunda de interoperabilidad y rutas de transmisión de datos.
* **📂 RA09: Seguimiento y Gestión de Incidencias en Servicios de Comunicación**
    * *Enfoque:* Configuración y uso de herramientas especializadas en la gestión de incidentes (Sistemas de Ticketing / Monitoreo), métricas de tiempos de respuesta, atención al usuario y documentación de simulación de crisis multiproblema.

---

## 📂 Propuesta de Estructura de Directorios para este Repositorio

Para mantener la concordancia exacta con la documentación del Ministerio, los recursos se almacenan bajo la siguiente jerarquía de carpetas:

```text
├── 📁 RA01_Instalacion_Nodos/        # Teoría LAN, Topologías, Normas de Cableado
├── 📁 RA02_Dispositivos_Interconex/  # Laboratorios de Switches, CLI Inicial, Verificación
├── 📁 RA03_Montaje_DataCenter/       # Prácticas de Subnetting VLSM, Patch Panels, Racks
├── 📁 RA04_Redes_Inalambricas/       # Configuración de APs, Seguridad WLAN (WPA3/WPA2)
├── 📁 RA05_Configuracion_Core/       # Enrutamiento, Modelos OSI/TCPIP, Scripts CLI
├── 📁 RA06_Soporte_Cableado/         # Plantillas de Órdenes de Servicio, Mantenimiento
├── 📁 RA07_Resolucion_Incidencias/   # Prácticas avanzadas de aislamiento de fallos lógicos
├── 📁 RA08_Investigacion_Lineas/     # Esquemas complejos, captura de tráfico, análisis
└── 📁 RA09_Gestion_Seguimiento/      # Bitácoras de incidentes, Simulación de fallos múltiples
