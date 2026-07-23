# Sistema de Gestión Bidireccional (Sheets ↔ Tasks)

Sistema bidireccional (Sheets ↔ Tasks) en Apps Script. Automatiza asignación, sincronización de estatus y recordatorios por correo HTML. Incluye mapeo dinámico de columnas anti-errores, archivado por roles (ejecutivos/superusuarios) y un carril exclusivo automatizado para usuarios remotos con auditoría silenciosa (Log_Bot).

## 🚀 Características Principales

* **Sincronización Bidireccional:** Crea tareas desde Sheets a Google Tasks y lee los estatus de vuelta para actualizar el Excel automáticamente.
* **Mapeo Dinámico de Columnas:** Código inmune a la inserción, eliminación o reordenamiento de columnas gracias al escaneo dinámico de encabezados.
* **Carril Remoto Exclusivo:** Flujo de trabajo 100% independiente para usuarios remotos con reglas de negocio y estatus predeterminados personalizados (ej. *Por confirmar*).
* **Archivado Inteligente:** Permisos basados en roles. Usuarios estándar solo archivan sus propias tareas; Súper Usuarios ejecutan limpiezas globales.
* **Bot de Recordatorios:** Evaluación diaria de tareas estancadas y envío de resúmenes por correo (HTML) con enlaces directos a la bitácora.
* **Auditoría Silenciosa:** Registro automático de cada asignación, cierre y re-apertura en una pestaña oculta (`Log_Bot`).

## 🛠️ Stack Tecnológico

* **Google Apps Script** (V8)
* **Google Sheets API**
* **Google Tasks API** 

## ⚙️ Configuración Rápida (Deploy)

1. Habilitar la API de **Google Tasks** en los Servicios Avanzados del editor de Apps Script.
2. Actualizar el archivo `appsscript.json` con los `oauthScopes` requeridos (`/tasks`, `/spreadsheets`, `/script.send_mail`).
3. Configurar la pestaña **Config** en Sheets con los directorios de correos, estatus permitidos y el correo oficial del Usuario Remoto.
4. Configurar **Activadores (Triggers)** basados en tiempo para las funciones:
   * `sincronizarTasksASheets` (Lectura)
   * `sincronizarTareasManualmente` (Escritura)
   * `enviarRecordatoriosDiarios` (Cronjob)
