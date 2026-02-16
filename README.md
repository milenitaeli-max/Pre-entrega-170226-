
# Caso: Sistema de Monitoreo Climático y Alerta de Riego
 Pre-entrega: Sistema de Monitoreo Climático con n8n

## Descripción del Proyecto
Este workflow automatiza el monitoreo de temperatura ambiental utilizando datos en tiempo real de una API externa y notificando vía Gmail si se superan ciertos umbrales térmicos.

## Estructura del Workflow
El flujo se compone de los siguientes nodos:
* **Schedule (Trigger):** Activa el flujo automáticamente cada 3 horas.
* **HTTP Request (API):** Consulta a Open-Meteo API para obtener la temperatura actual de Buenos Aires.
* **Edit Fields (Manejo de datos):** Normaliza la respuesta de la API en la variable `temperatura_actual`.
* **IF (Condicional):** Evalúa si el dato es mayor a 24°C.
* **Gmail (Notificación):** Envía un correo de alerta mediante OAuth2.

## Buenas Prácticas
* **Seguridad:** No se incluyen credenciales en el archivo JSON. Se utiliza el gestor de credenciales nativo de n8n.
* **Documentación:** Cada nodo tiene una función clara y específica dentro del proceso de negocio.
