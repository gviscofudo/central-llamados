# Central de llamados – Fudo CS

Panel del equipo de CS para la campaña de retención sobre cuentas de Argentina bloqueadas en Dash con estado comercial activo, más cuentas sumadas a mano con etiqueta (por ejemplo «Riesgo alto»).

## Qué hay en este repo
- `index.html`: la aplicación completa (página estática publicada con GitHub Pages).

## Backend (Supabase, proyecto «Central de llamados CS»)
- Tablas: `cuentas`, `gestiones`, `llamados`, `equipo`, `cuentas_extra`, `mensajes_enviados`, `sync_log` y el histórico de campañas cerradas (`llamados_historico`, `gestiones_historico`).
- Edge Functions:
  - `sync-cuentas`: trae las cuentas de HubSpot cada hora.
  - `sync-llamadas-intercom`: trae las llamadas de Intercom cada 10 minutos (último llamado por cuenta).
  - `contactos`: contactos de la cuenta en HubSpot e Intercom.
  - `hubspot-llamado`: nota, tarea y solicitud de baja en HubSpot.
  - `planilla-activacion`: activaciones inmediatas en la planilla de Administración.
  - `enviar-mensaje`: marca en el negocio la propiedad que dispara el workflow de WhatsApp (hoy: `hsm_llamados_cs_promocion`).
  - `usuarios`: alta de usuarios y cambio de contraseñas (solo líderes).
- Acceso con mail y contraseña. Los usuarios los crea un líder desde «Equipo y usuarios».

La clave que aparece en `index.html` es la clave pública (publishable) de Supabase: está pensada para estar en el navegador. Los tokens de HubSpot e Intercom viven solo como secretos de Supabase, nunca en este repo.
