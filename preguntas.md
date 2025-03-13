# Preguntas
### Ciclo de vida del dato (5b):
#### ¿Cómo se gestionan los datos desde su generación hasta su eliminación en tu proyecto?
Se generan cuando el usuario registra una transacción (ingreso o gasto). Se almacenan en una base de datos SQLite y se usan para calcular el saldo o mostrar gráficos. No hay eliminación automática, pero se podrían borrar manualmente.

#### ¿Qué estrategia sigues para garantizar la consistencia e integridad de los datos?
Uso claves primarias en la base de datos para evitar duplicados y validaciones en el código para asegurar que los datos sean correctos (por ejemplo, que el monto sea un número). 

#### Si no trabajas con datos, ¿cómo podrías incluir una funcionalidad que los gestione de forma eficiente?
Podría añadir una función para exportar los datos a Excel o conectarse a una API que analice los gastos e ingresos automáticamente.

### Almacenamiento en la nube (5f):
#### Si tu software utiliza almacenamiento en la nube, ¿cómo garantizas la seguridad y disponibilidad de los datos?
No uso la nube, pero si la integrara, usaría servicios como Firebase con cifrado de datos y backups periódicos para garantizar seguridad y disponibilidad.

#### ¿Qué alternativas consideraste para almacenar datos y por qué elegiste tu solución actual?
Elegí SQLite porque es sencilla, no necesita servidor y es compatible con Python. Otras opciones como MySQL o MongoDB eran más complejas para este proyecto.

#### Si no usas la nube, ¿cómo podrías integrarla en futuras versiones?
Podría migrar la base de datos a Firebase o AWS para que los usuarios accedan a sus datos desde cualquier dispositivo.

### Seguridad y regulación (5i):
#### ¿Qué medidas de seguridad implementaste para proteger los datos o procesos en tu proyecto?
Validación de datos para evitar entradas incorrectas y uso de SQLite, que es una base de datos local y segura.

#### ¿Qué normativas (e.g., GDPR) podrían afectar el uso de tu software y cómo las has tenido en cuenta?
Si se almacenaran datos personales, el GDPR exigiría protegerlos. Por ahora, no se recopila información sensible, pero en el futuro usaría cifrado y permisos de acceso.

#### Si no implementaste medidas de seguridad, ¿qué riesgos potenciales identificas y cómo los abordarías en el futuro?
Riesgo: Pérdida de datos. Solución: Implementar backups automáticos y cifrado de la base de datos.

### Implicación de las THD en negocio y planta (2e):
#### ¿Qué impacto tendría tu software en un entorno de negocio o en una planta industrial?
Ayudaría a gestionar los gastos e ingresos de pequeñas empresas o proyectos, mejorando el control financiero.

#### ¿Cómo crees que tu solución podría mejorar procesos operativos o la toma de decisiones?
Automatizaría el cálculo de presupuestos y proporcionaría informes claros para tomar decisiones financieras más rápidas.

#### Si tu proyecto no aplica directamente a negocio o planta, ¿qué otros entornos podrían beneficiarse?
Hogares, estudiantes o cualquier persona que quiera gestionar sus finanzas personales de forma sencilla.

### Mejoras en IT y OT (2f):
#### ¿Cómo puede tu software facilitar la integración entre entornos IT y OT?
No aplica directamente, pero podría usarse para monitorear gastos en infraestructura tecnológica o proyectos industriales.

#### ¿Qué procesos específicos podrían beneficiarse de tu solución en términos de automatización o eficiencia?
Automatizaría el registro de gastos y la generación de informes financieros, ahorrando tiempo y reduciendo errores manuales.

#### Si no aplica a IT u OT, ¿cómo podrías adaptarlo para mejorar procesos tecnológicos concretos?
Podría integrarse con sistemas de gestión empresarial para analizar costes y optimizar presupuestos en proyectos tecnológicos.

### Tecnologías Habilitadoras Digitales (2g):
#### ¿Qué tecnologías habilitadoras digitales (THD) has utilizado o podrías integrar en tu proyecto?
He usado SQLite (almacenamiento) y Tkinter (interfaz gráfica). Podría integrar Firebase para la nube o IA para predicciones financieras.

#### ¿Cómo mejoran estas tecnologías la funcionalidad o el alcance de tu software?
SQLite permite almacenar datos de forma eficiente, y Tkinter hace que la aplicación sea fácil de usar.

#### Si no has utilizado THD, ¿cómo podrías implementarlas para enriquecer tu solución?
Podría añadir IA para predecir gastos futuros o IoT para conectar la app con dispositivos que registren gastos automáticamente.
