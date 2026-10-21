# Central de llamados – Fudo CS

Panel para la campaña de retención sobre cuentas de Argentina bloqueadas en Dash con estado comercial activo.

- Frontend: `index.html` (página estática, se publica con GitHub Pages).
- Backend: Supabase, proyecto «Central de llamados CS» (`rgbnwwppkrcbyolegnpi`).
  - Tablas: `cuentas`, `gestiones`, `llamados`, `equipo`, `sync_log`.
  - Edge Functions: `sync-cuentas` (trae las cuentas de HubSpot, corre cada hora de 8 a 21 hs), `contactos` (contactos de HubSpot + Intercom), `hubspot-llamado` (crea nota y tarea en HubSpot).
- El acceso se controla con la tabla `equipo`: solo entran mails @fu.do activos en esa lista. Los líderes los gestionan desde el botón «Equipo».

La clave que aparece en `index.html` es la clave pública (publishable) de Supabase: está pensada para estar en el navegador. Los tokens de HubSpot e Intercom viven solo como secretos de Supabase, nunca en este repo.

Para cambiar las propuestas comerciales o los motivos de baja, editá las listas `PROPUESTAS` y `MOTIVOS` al principio del script en `index.html`.
