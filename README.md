# Pre-entrega-170226-
Proyecto de verificación de clima para activación de riego automático

# Caso: Sistema de Monitoreo Climático y Alerta de Riego
# Trigger (Disparador):
Se utiliza el nodo Schedule, configurado para ejecutarse de forma automática cada 3 horas. Esto asegura que el monitoreo sea constante sin intervención humana.

# Descripción de los Nodos:

Schedule: Inicia el flujo automáticamente en intervalos de tiempo definidos.

HTTP Request: Realiza una llamada GET a la API pública de Open-Meteo para obtener datos meteorológicos en tiempo real (temperatura actual) sin necesidad de autenticación compleja.

Edit Fields (Set): Recibe los datos de la API y crea una variable limpia llamada temperatura_actual, facilitando el mapeo de expresiones en los nodos siguientes.

IF (Condicional): Evalúa si la temperatura recibida es mayor a 24°C. Se eligió este valor para decidir si el clima amerita una notificación de alerta para riego o cuidado térmico.

Gmail: Nodo de notificación que envía un correo electrónico automático utilizando credenciales OAuth2. Se activa solo si el condicional es verdadero (True).

# Buenas Prácticas Aplicadas:

Seguridad: Uso de la gestión de credenciales nativa de n8n (OAuth2) para Gmail, evitando exponer contraseñas en el flujo.

Persistencia: Los datos se normalizan en un nodo específico para mantener el orden del flujo.

Mantenimiento: Uso de una API pública y estable que no requiere rotación de tokens.
