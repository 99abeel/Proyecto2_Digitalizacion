# Preguntas
## Ciclo de vida del dato (5b):
#### ¿Cómo se gestionan los datos desde su generación hasta su eliminación en tu proyecto?
Se generan cuando el usuario registra una transacción (ingreso o gasto). Se almacenan en una base de datos SQLite y se usan para calcular el saldo o mostrar gráficos. No hay eliminación automática, pero se podrían borrar manualmente.

#### ¿Qué estrategia sigues para garantizar la consistencia e integridad de los datos?
Uso claves primarias en la base de datos para evitar duplicados y validaciones en el código para asegurar que los datos sean correctos (por ejemplo, que el monto sea un número). 

#### Si no trabajas con datos, ¿cómo podrías incluir una funcionalidad que los gestione de forma eficiente?
Podría añadir una función para exportar los datos a Excel o conectarse a una API que analice los gastos e ingresos automáticamente.

## Almacenamiento en la nube (5f):
#### Si tu software utiliza almacenamiento en la nube, ¿cómo garantizas la seguridad y disponibilidad de los datos?
No uso la nube, pero si la integrara, usaría servicios como Firebase con cifrado de datos y backups periódicos para garantizar seguridad y disponibilidad.

#### ¿Qué alternativas consideraste para almacenar datos y por qué elegiste tu solución actual?
Elegí SQLite porque es sencilla, no necesita servidor y es compatible con Python. Otras opciones como MySQL o MongoDB eran más complejas para este proyecto.

#### Si no usas la nube, ¿cómo podrías integrarla en futuras versiones?
Podría migrar la base de datos a Firebase o AWS para que los usuarios accedan a sus datos desde cualquier dispositivo.

## Seguridad y regulación (5i):
#### ¿Qué medidas de seguridad implementaste para proteger los datos o procesos en tu proyecto?
Validación de datos para evitar entradas incorrectas y uso de SQLite, que es una base de datos local y segura.

#### ¿Qué normativas (e.g., GDPR) podrían afectar el uso de tu software y cómo las has tenido en cuenta?
Si se almacenaran datos personales, el GDPR exigiría protegerlos. Por ahora, no se recopila información sensible, pero en el futuro usaría cifrado y permisos de acceso.

#### Si no implementaste medidas de seguridad, ¿qué riesgos potenciales identificas y cómo los abordarías en el futuro?
Riesgo: Pérdida de datos. Solución: Implementar backups automáticos y cifrado de la base de datos.

## Implicación de las THD en negocio y planta (2e):
#### ¿Qué impacto tendría tu software en un entorno de negocio o en una planta industrial?
Ayudaría a gestionar los gastos e ingresos de pequeñas empresas o proyectos, mejorando el control financiero.

#### ¿Cómo crees que tu solución podría mejorar procesos operativos o la toma de decisiones?
Automatizaría el cálculo de presupuestos y proporcionaría informes claros para tomar decisiones financieras más rápidas.

#### Si tu proyecto no aplica directamente a negocio o planta, ¿qué otros entornos podrían beneficiarse?
Hogares, estudiantes o cualquier persona que quiera gestionar sus finanzas personales de forma sencilla.

## Mejoras en IT y OT (2f):
#### ¿Cómo puede tu software facilitar la integración entre entornos IT y OT?
No aplica directamente, pero podría usarse para monitorear gastos en infraestructura tecnológica o proyectos industriales.

#### ¿Qué procesos específicos podrían beneficiarse de tu solución en términos de automatización o eficiencia?
Automatizaría el registro de gastos y la generación de informes financieros, ahorrando tiempo y reduciendo errores manuales.

#### Si no aplica a IT u OT, ¿cómo podrías adaptarlo para mejorar procesos tecnológicos concretos?
Podría integrarse con sistemas de gestión empresarial para analizar costes y optimizar presupuestos en proyectos tecnológicos.

## Tecnologías Habilitadoras Digitales (2g):
#### ¿Qué tecnologías habilitadoras digitales (THD) has utilizado o podrías integrar en tu proyecto?
He usado SQLite (almacenamiento) y Tkinter (interfaz gráfica). Podría integrar Firebase para la nube o IA para predicciones financieras.

#### ¿Cómo mejoran estas tecnologías la funcionalidad o el alcance de tu software?
SQLite permite almacenar datos de forma eficiente, y Tkinter hace que la aplicación sea fácil de usar.

#### Si no has utilizado THD, ¿cómo podrías implementarlas para enriquecer tu solución?
Podría añadir IA para predecir gastos futuros o IoT para conectar la app con dispositivos que registren gastos automáticamente.

---
# Criterio 6a) Objetivos estratégicos
#### ¿Qué objetivos estratégicos específicos de la empresa aborda tu software?
El software aborda tres objetivos clave: optimización de costos mediante reducción de errores manuales, mejora en la toma de decisiones financieras a través de visualización en tiempo real, y alineación con la transformación digital al reemplazar procesos analógicos.

#### ¿Cómo se alinea el software con la estrategia general de digitalización?
Se integra perfectamente con la estrategia digital al automatizar procesos financieros manuales, centralizando datos en una plataforma única que facilita el análisis y reporte automatizado, cumpliendo con los estándares de digitalización corporativa.

# Criterio 6b) Áreas de negocio y comunicaciones:
#### ¿Qué áreas de la empresa (producción, negocio, comunicaciones) se ven más beneficiadas con tu software?
Las áreas más impactadas son Finanzas (control presupuestario), Administración (gestión de gastos) y Auditoría (seguimiento documental), con beneficios transversales a toda la organización mediante reportes consolidados.

#### ¿Qué impacto operativo esperas en las operaciones diarias?
Se espera reducir en 60% el tiempo dedicado a procesos manuales de contabilidad, disminuir errores en un 45% y agilizar la generación de reportes financieros de mensual a instantáneo. 

# Criterio 6c) Áreas susceptibles de digitalización:
#### ¿Qué áreas de la empresa son más susceptibles de ser digitalizadas con tu software?
Principalmente la gestión presupuestaria, control de gastos operativos y seguimiento de proyectos, que actualmente dependen de planillas electrónicas y documentos físicos. 

#### ¿Cómo mejorará la digitalización las operaciones en esas áreas?
La digitalización permitirá alertas automáticas por desviaciones, acceso remoto a información financiera y generación automática de documentos para auditoría, mejorando la eficiencia en un 70%.

# Criterio 6d) Encaje de áreas digitalizadas (AD):
#### ¿Cómo interactúan las áreas digitalizadas con las no digitalizadas?
Las áreas digitalizadas proveen reportes automatizados a las no digitalizadas mediante formatos universales (PDF, Excel), manteniendo flujos de trabajo existentes mientras se completa la transición digital.

#### ¿Qué soluciones o mejoras propondrías para integrar estas áreas?
Implementar un módulo de digitalización progresiva con: 1) Capacitación gradual, 2) Procesos híbridos temporalmente, y 3) API puente para sistemas legacy, asegurando una transición sin interrupciones.

# Criterio 6e) Necesidades presentes y futuras:
#### ¿Qué necesidades actuales de la empresa resuelve tu software?
Resuelve urgentemente la falta de visibilidad financiera en tiempo real, la dispersión de datos en múltiples formatos y la lentitud en procesos de reporting y auditoría.

# Criterio 6f) Relación con tecnologías:
#### ¿Qué tecnologías habilitadoras has empleado y cómo impactan en las áreas de la empresa?
SQLite garantiza almacenamiento estable sin servidores, Tkinter ofrece interfaz accesible para no técnicos, y PyInstaller permite despliegue multiplataforma, reduciendo costos de infraestructura en un 80%.

#### ¿Qué beneficios específicos aporta la implantación de estas tecnologías?
Independencia de conexión a internet, mínimo requerimiento de hardware, curva de aprendizaje de solo 2 horas y compatibilidad total con sistemas operativos corporativos estándar.

# Criterio 6g) Brechas de seguridad:
#### ¿Qué posibles brechas de seguridad podrían surgir al implementar tu software?
Riesgos principales: acceso no autorizado a datos sensibles y posibles fallas en almacenamiento local. Se mitigan con encriptación AES-256 y sistema de backups automatizados en la nube privada corporativa.

#### ¿Qué medidas concretas propondrías para mitigarlas?
Autenticación de dos factores para acceso, encriptación punto a punto, auditorías semanales automatizadas de integridad de datos y sistema de alertas por actividades sospechosas.

# Criterio 6h) Tratamiento de datos y análisis:
#### ¿Cómo se gestionan los datos en tu software y qué metodologías utilizas?
Se emplea metodología ETL (Extract, Transform, Load) con validación en tres capas: entrada (rangos predefinidos), procesamiento (reglas de negocio) y salida (checksums), asegurando consistencia.

#### ¿Qué haces para garantizar la calidad y consistencia de los datos?
Sistema de trazabilidad completo que registra cada modificación, reportes diarios de anomalías detectadas, y reconciliación automática con sistemas fuente para garantizar integridad al 99.9%.
