NetCom 2.0 - Sistema de Gestión de Contratos

NetCom 2.0 es una aplicación web progresiva (PWA) de una sola página (SPA) diseñada para Mobilenet Solutions. Su objetivo principal es automatizar y estandarizar la generación de contratos de servicios de telecomunicaciones (Internet Fibra, Pack Dúo y Enlaces Dedicados) para Entel Empresas.

El sistema gestiona el flujo completo desde la captura de datos del cliente (con integración de APIs de consulta) hasta la exportación de documentos PDF listos para la firma digital o física.

🚀 Características Principales

Generador de Contratos (Wizard): Flujo guiado de 5 pasos con validación de datos en tiempo real (Oportunidad, Representante Legal, Instalación, Planes, Cierre).

Integración con RENIEC/SUNAT: Consultas automáticas de RUC y DNI mediante API externa para autocompletar datos.

Motor de PDF (Client-Side): Generación de documentos PDF (Contrato de Arrendamiento, Servicios Suplementarios, Tarifas) directamente en el navegador utilizando pdf-lib.

Nota: Incluye un sistema de "Fallback" que genera un documento resumen si no se encuentran las plantillas base.

Constructor de Direcciones: Modal interactivo para estandarizar el formato de direcciones (Vía, Número, Manzana, Lote, Urbanización, Distrito).

Gestión de Planes: Módulo administrativo para crear, editar y eliminar planes de servicio (velocidades, tarifas, cargos fijos).

Control de Acceso:

Gestión de Usuarios y Roles (Administrador / Operador).

Restricción por IP: Seguridad lógica que permite limitar el acceso de operadores a direcciones IP específicas (ej. solo desde la oficina).

Interfaz UI/UX: Diseño moderno "Clean & Sharp" basado en Tailwind CSS, con feedback visual mediante notificaciones "Toast".

🛠️ Stack Tecnológico

El sistema es monolítico y client-side. No requiere instalación de servidor backend (Node.js, PHP, etc.) para funcionar, ya que toda la lógica reside en el navegador del cliente.

Core: HTML5, JavaScript (ES6+).

Estilos: Tailwind CSS (vía CDN) + Fuentes Google (Plus Jakarta Sans / Inter).

Librerías:

pdf-lib: Manipulación de PDFs.

lucide: Iconografía vectorial.

Persistencia: LocalStorage del navegador (para usuarios, catálogo de planes e historial de logs).

APIs Externas:

apisperu.com: Consulta de datos de personas y empresas.

ipify.org: Detección de IP pública para seguridad.

🔑 Credenciales de Acceso (Por Defecto)

El sistema se inicializa con los siguientes usuarios.

Administradores (Acceso Total)

Tienen acceso a la pestaña de "Configuración" para gestionar usuarios y planes.

Usuario

Contraseña

Rol

mob_hmedinab

adminMobilenet2025

Admin

mob_dcarrasco

adminMobilenet2025

Admin

Operadores (Acceso Limitado)

Solo pueden generar contratos y ver el historial. Tienen restricción de IP activada por defecto (pueden requerir desactivación en modo local).

Usuario

Contraseña

Rol

MOB_JAQPAREDES

Mob_2025-17553

Normal

MOB_WALSALCEDO

Mob_2025-63354

Normal

Nota de Debug: En la pantalla de login existe un botón "Restablecer Usuarios" que reinicia la base de datos local a estos valores predeterminados.

📦 Instalación y Despliegue

Requisitos

Un navegador web moderno (Chrome, Edge, Firefox, Safari).

Conexión a internet (para cargar librerías CDN y consultar APIs).

Pasos

Código Fuente: Guarde el código proporcionado como index.html.

Plantillas PDF (Recomendado): Para que el sistema rellene los PDFs oficiales de Entel, debe colocar los siguientes archivos en la misma carpeta que el index.html:

Arrendamiento.pdf (o con el prefijo "Pack " según corresponda)

Servicios Suplementarios.pdf

Tarifas y Servicios.pdf

Si no se colocan, el sistema generará un PDF genérico con los datos.

Ejecución: Simplemente abra el archivo index.html con su navegador.

⚠️ Configuración Avanzada

Token de API (RUC/DNI)

El sistema utiliza un token de demostración para apisperu.com. Si las consultas dejan de funcionar, busque la constante en el código y reemplácela:

const APISPERU_TOKEN = "SU_NUEVO_TOKEN_AQUI";


IPs Permitidas

Para modificar las IPs de oficina permitidas para los operadores, edite el array en el código:

const ALLOWED_IPS = ['148.102.51.78', '190.8.133.125', 'SU_NUEVA_IP'];
