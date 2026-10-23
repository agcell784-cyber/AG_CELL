# AG_CELL Servicio Técnico V9

Aplicación web instalable (PWA) para gestión de reparación y servicio técnico de celulares.

## Incluye
- Recepción y gestión de equipos.
- Órdenes de servicio.
- Caja e ingresos/gastos.
- Inventario de repuestos y accesorios.
- Perfil del negocio.
- Fotos de equipos (máximo 8 por equipo, 3 MB por foto).
- Inicio de sesión con Supabase Auth y sincronización entre dispositivos.
- PIN local de bloqueo.
- Cifrado de accesos de equipos en el navegador.
- Mensajes preparados para WhatsApp (el usuario revisa y envía el mensaje).
- Patrón de desbloqueo dibujable en una cuadrícula 3×3.
- Relación de abonos automáticos con el equipo para poder eliminar los movimientos asociados al borrar equipos.

## Primer uso
1. Publica los archivos de esta carpeta en el directorio raíz del sitio estático.
2. En Supabase, confirma que el proyecto sea `cqggmnbjueomoeulcpqx`.
3. Si aún no ejecutaste `CONFIGURAR_SUPABASE.sql` en ese proyecto, abre **SQL Editor**, pega el contenido y ejecuta una vez.
4. Abre la aplicación publicada, crea una cuenta o inicia sesión y prueba primero con datos ficticios.
5. Para usarla en otro dispositivo, inicia sesión con la misma cuenta.

## Seguridad
- `index.html` usa una clave **publishable** de Supabase. Nunca sustituyas esa clave por una `service_role` o una clave `secret`.
- Las tablas expuestas deben tener Row Level Security (RLS) y políticas que limiten los registros al usuario autenticado.
- Registra patrones, PIN o contraseñas de equipos solo con autorización del cliente y elimina esos datos cuando ya no sean necesarios.
- Si se cambia la contraseña de la cuenta, los accesos cifrados con la contraseña anterior podrían no poder descifrarse.
- WhatsApp abre un mensaje preparado; no envía mensajes automáticamente.

## Notas
- `CONFIGURAR_SUPABASE.sql` crea la tabla de inventario si falta y añade `device_id` a `cash_entries` para relacionar los abonos automáticos con los equipos.
- El código de eliminación borra primero movimientos de caja, órdenes y registros de fotos asociados al equipo. Las fotos almacenadas pueden requerir limpieza adicional del almacenamiento si ya se habían subido.
- Prueba los flujos principales antes de usar la aplicación con datos reales.
