# AG_CELL Servicio Técnico V8

Versión conectada al proyecto Supabase `AG_CELL`.

## Qué incluye
- Equipos / recepción
- Órdenes de servicio
- Caja
- Perfil del negocio
- Fotos de equipos (máx. 8 por equipo, 3 MB por foto)
- Login con Supabase Auth para sincronizar celular y computador
- PIN local de bloqueo
- Acceso del teléfono cifrado en el navegador antes de guardarse
- Storage privado para fotos
- RLS en las tablas
- Caché local básica para conservar la interfaz si falla Internet

## Primer uso
1. Sirve esta carpeta desde un servidor web/hosting (no abras `index.html` con `file://` si el navegador bloquea módulos/Storage).
2. Abre la app.
3. Crea tu cuenta con correo y contraseña.
4. Inicia sesión en los demás dispositivos con la misma cuenta.
5. Define el PIN del dispositivo.

## Importante
La clave incluida en `index.html` es la publishable key de Supabase; no es una service_role key.
Nunca sustituyas esa clave por una service_role/secret key.

El campo de acceso de los teléfonos se cifra con una clave derivada de la contraseña de la cuenta mientras se usa la aplicación. Si se pierde la contraseña, esos accesos cifrados no pueden recuperarse desde la aplicación.

## Nota sobre fotos
El bucket `agcell-photos` es privado. La V8 usa URLs firmadas con duración limitada para mostrar las fotos.

## Próximo endurecimiento recomendado
- URLs firmadas para fotos
- política de recuperación de cuenta
- auditoría de accesos a credenciales
- sincronización offline con cola de cambios/conflictos
- exportación/importación de respaldo
- empaquetado Android/desktop
