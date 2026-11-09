# trabajo_project_sodimac
Sistema de gestión y trazabilidad de activos tecnológicos dados de baja - Sodimac Chile (EPE3)

1. Introducción y Contextualización
El presente documento recopila toda la información técnica, registros de avance y código fuente desarrollados para la evaluación final EPE3 de la asignatura Taller de Diseño de Sistemas Informáticos II. El proyecto responde a la necesidad de Sodimac Chile de gestionar de forma transparente, auditable y centralizada la trazabilidad de sus activos tecnológicos dados de baja (notebooks, monitores, impresoras y servidores).
A lo largo del trabajo se construyeron los incrementos de software, las consultas de base de datos relacional, las evidencias de pruebas de calidad y la documentación estructurada en la plataforma ProjectFlow para su posterior integración en GitHub.
2. Registros para Plataforma ProjectFlow
Modulo 1: Planificación de la Construcción
Metodología de desarrollo y división en fases	Trabajamos con un enfoque iterativo por sprints cortos. Dividimos el proyecto en cuatro etapas: primero levantamos la arquitectura y la base de datos; luego armamos el Hito 1 con el CRUD principal y el registro de bajas; después avanzamos con el Hito 2 para las consultas y reportes; y cerramos con las pruebas integrales y el despliegue del sistema.
Cronograma: Gantt o PERT	• Semanas 1 y 2: Modelamiento del esquema relacional y configuración inicial del repositorio en Git.
• Semanas 3 y 4: Desarrollo del Hito 1 (gestión de usuarios, inventario y módulo de bajas de equipos).
• Semanas 5 y 6: Desarrollo del Hito 2 (filtros avanzados, historial y trazabilidad completa).
• Semana 7: Pruebas de integración, corrección de bugs y subida al entorno de prueba.
Actividades, fases, responsables y dependencias	• Fase de Base de Datos: A cargo del modelado y la estructura SQL. Sin dependencias previas.
• Fase Hito 1: Encargado de programar la lógica del backend y las vistas principales. Depende de tener la base de datos lista.
• Fase Hito 2: A cargo de integrar los reportes y las consultas de historial. Depende de que el Hito 1 funcione de manera estable.
• Fase de QA y Despliegue: Revisión grupal de errores y subida de la versión final. Depende de terminar ambos hitos.
Enlace al cronograma / repositorio	https://github.com/pedro145antonio/trabajo_project_sodimac
Observaciones y riesgos	• Riesgo 1: Que los estados de los equipos queden desincronizados al dar de baja un activo. Solución: Pusimos validaciones estrictas directo en la lógica del backend y restricciones en la base de datos.
• Riesgo 2: Problemas al fusionar los códigos de ambos hitos. Solución: Hicimos commits diarios y revisamos los cambios en equipo para evitar conflictos grandes.

Modulo 2: Desarrollo — Hito 1 (Módulo Core)
Funcionalidades desarrolladas	Construimos la base operativa del sistema permitiendo la autenticación de usuarios, la gestión de inventario activo y la primera versión del módulo de baja. Se implementó el registro de nuevos equipos (código, marca, modelo, número de serie y ubicación) y el cambio de estado a 'Dado de baja' indicando el motivo y fecha de retiro.
Responsables	Equipo de desarrollo completo (modelado de base de datos SQL, backend y vistas del módulo de alta/baja).
Evidencias, enlace a código o commit	• Repositorio: https://github.com/pedro145antonio/trabajo_project_sodimac
• Commit Hito 1: feat: estructura inicial de base de datos y modulo de alta/baja de activos.
• Capturas: Vistas del listado de inventario y formulario de registro.
Dificultades y trabajo pendiente	• Dificultad: Validar que el número de serie fuera único a nivel de base de datos para evitar registros duplicados.
• Pendiente: Integrar el buscador avanzado e historial completo (programado para el Hito 2).

Modulo 3: Desarrollo — Hito 2 (Trazabilidad e Historial)
Funcionalidades desarrolladas	Implementamos el módulo del segundo incremento centrado en la trazabilidad y consulta de activos. Construimos el buscador por código de serie e identificador interno, los filtros por estado y fecha de retiro, la vista de la línea de tiempo histórica del activo (alta, traslados y baja definitiva) y la generación de reportes resumidos.
Responsables	Equipo de desarrollo completo (programación de lógica de negocio en backend, integración de la vista de historial en frontend y consultas a la base de datos).
Evidencias, enlace a código o commit	• Repositorio: https://github.com/pedro145antonio/trabajo_project_sodimac
• Commit Hito 2: feat: modulo de trazabilidad e historial de activos dados de baja
• Pruebas: Capturas de pantalla adjuntas en el informe mostrando la búsqueda de un equipo dado de baja y su historial completo.
Dificultades y trabajo pendiente	• Dificultad resuelta: Optimizar las consultas SQL para que el historial mostrara los datos ordenados cronológicamente sin ralentizar la interfaz.
• Trabajo pendiente: Queda pendiente integrar la exportación automática de reportes a PDF/Excel y el envío de alertas por correo electrónico ante una nueva baja.

Modulo 4: Integración y Calidad
Casos de prueba, resultados y criterios de aceptación	• CP-01 (Registro): Ingresar un nuevo equipo con número de serie. Resultado esperado: se almacena y lista en inventario. Resultado obtenido: guardado exitoso y visible en pantalla (Aprobado).
• CP-02 (Baja): Seleccionar un equipo activo y confirmar su baja con motivo. Resultado obtenido: cambió de estado correctamente, aunque se ajustó un detalle de bloqueo de edición (Aprobado con corrección).
• CP-03 (Trazabilidad): Buscar el historial de un equipo dado de baja. Resultado obtenido: despliega la línea de tiempo completa de forma ordenada (Aprobado).
Integración de componentes y defectos corregidos	Conectamos los módulos del Hito 1 (alta y baja de equipos) con los componentes de consulta del Hito 2. El principal defecto corregido fue un desfase visual en la interfaz, ya que la tabla de activos no se actualizaba automáticamente tras confirmar una baja; se solucionó recargando la vista desde el controlador.
Responsables de pruebas	Equipo de desarrollo e integración (encargados de la ejecución de las pruebas unitarias, validación de flujos y verificación de datos en la base de datos).
Evidencias de ejecución y reportes	• Repositorio: https://github.com/pedro145antonio/trabajo_project_sodimac
• Evidencias: Capturas de pantalla adjuntas en el informe que demuestran el flujo completo de prueba (desde el registro del activo hasta la consulta de su historial y foto de baja).
Defectos pendientes y riesgos	No quedaron defectos críticos abiertos para la versión demostrativa. Como riesgo menor proyectado se identificó la necesidad de implementar más adelante restricciones por roles de usuario (administrador vs. auditor), lo cual quedó fuera del alcance acotado de este trabajo.

Modulo 5: Puesta en Producción
Entorno de despliegue y procedimiento	La versión demostrativa se publicó en un entorno local simulado. El procedimiento consistió en clonar la rama principal del repositorio, configurar la conexión a la base de datos relacional y ejecutar el servidor de la aplicación para validar el funcionamiento en el navegador.
Verificación de funcionamiento y resultado	Se realizaron pruebas de sanidad comprobando que la aplicación permite registrar con éxito nuevos activos tecnológicos, procesar su baja con el motivo y la ruta de la evidencia fotográfica, y consultar correctamente el historial de trazabilidad.
Responsables del despliegue	Equipo de desarrollo completo (encargados de la configuración del entorno, validación de la base de datos y pruebas finales de ejecución).
URL, capturas o evidencias del despliegue	• Repositorio: https://github.com/pedro145antonio/trabajo_project_sodimac
• Evidencias: Capturas de pantalla adjuntas en el informe técnico que muestran la ejecución de los flujos principales del sistema.
Observaciones, limitaciones y mantenimiento	El sistema cumple de manera íntegra con el alcance acotado de la evaluación demostrativa. Como limitaciones declaradas, no incluye pasarelas de pago ni integraciones con sistemas ERP externos corporativos, quedando como mantenimiento futuro la automatización de respaldos de la base de datos.

3. Código Base de Datos SQL
A continuación se detallan las sentencias SQL ejecutadas para la creación de las tablas principales (`activos` y `bajas`) y la inserción de datos de prueba demostrativos:
-- 1. Estructura de la tabla de Activos
CREATE TABLE activos (
    id INT PRIMARY KEY,
    nombre VARCHAR(50),
    estado VARCHAR(20)
);

-- 2. Estructura de la tabla de Bajas (incluye ruta de la foto de evidencia)
CREATE TABLE bajas (
    id INT PRIMARY KEY,
    activo_id INT,
    motivo VARCHAR(100),
    foto VARCHAR(255)
);

-- 3. Inserción de datos demostrativos en Activos
INSERT INTO activos (id, nombre, estado) VALUES (1, 'Notebook HP ProBook', 'Activo');
INSERT INTO activos (id, nombre, estado) VALUES (2, 'Monitor Dell 24"', 'Activo');
INSERT INTO activos (id, nombre, estado) VALUES (3, 'Impresora LaserJet', 'Activo');

-- 4. Inserción de registros de baja con evidencia fotográfica
INSERT INTO bajas (id, activo_id, motivo, foto) VALUES (1, 1, 'Obsolescencia técnica y falla de placa', 'uploads/baja_notebook_1.png');
INSERT INTO bajas (id, activo_id, motivo, foto) VALUES (2, 3, 'Daño físico irreparable en pantalla y carcasa', 'uploads/baja_impresora_3.png');


4. Documentación para el Repositorio GitHub (README.md)
Texto estructurado recomendado para incorporar directamente en el archivo README.md del repositorio oficial `trabajo_project_sodimac`:
# Sistema de Trazabilidad de Activos Tecnológicos Dados de Baja - Sodimac Chile

Proyecto desarrollado para la asignatura **Taller de Diseño de Sistemas Informáticos II (EPE3)** en **IPCHILE**.

## 📌 Descripción del Proyecto
La aplicación busca dar solución a la problemática de gestión e inventario de hardware tecnológico en proceso de obsolescencia o retiro operativo en Sodimac Chile. Permite registrar activos, procesar su baja formal adjuntando evidencia fotográfica y consultar el historial auditable de cada equipo.

## 🚀 Tecnologías Utilizadas
* **Base de Datos:** SQL (Gestión de tablas `activos` y `bajas`).
* **Control de Versiones:** Git & GitHub.
* **Gestión de Proyecto:** Plataforma ProjectFlow IPCHILE.

## 🗂️ Estructura de la Base de Datos
* `activos`: Almacena el identificador, nombre y estado operativo del equipo.
* `bajas`: Registra el motivo de retiro, la relación con el activo y la ruta de la imagen adjunta como evidencia.

## 📋 Instrucciones de Ejecución
1. Clonar el repositorio: `git clone https://github.com/pedro145antonio/trabajo_project_sodimac.git`
2. Importar los scripts SQL ubicados en la sección de base de datos.
3. Ejecutar las consultas `INSERT` para cargar los registros de prueba.



