# Instalación y configuración inicial del servidor

## Contexto
En este laboratorio se configuró un servidor basado en Debian con el objetivo de practicar administración de sistemas Linux y hardening básico.

## Objetivo
Configurar un servidor Debian con OMV como base para un laboratorio de ciberseguridad y uso como NAS personal, priorizando buenas prácticas de administración y seguridad.

## Acciones realizadas
Se habilitó el acceso remoto mediante SSH y se creó un usuario no privilegiado, otorgándole privilegios administrativos controlados mediante sudo, con el fin de evitar el uso directo del usuario root.

## Acciones realizadas
- Instalación de Debian y OpenMediaVault
- Creación de usuario no privilegiado
- Habilitación de acceso remoto mediante SSH

## Problemas encontrados
- Fallo de acceso SSH para el usuario no root

## Diagnóstico
- Revisión de logs del servicio SSH (`journalctl -u ssh`)
- Identificación de restricción en la directiva `AllowGroups`

## Solución aplicada
- Corrección de la directiva para incluir el grupo del usuario
- Validación de acceso remoto exitoso

## Resultado
- Acceso SSH funcional y endurecido
- Configuración documentada y reproducible

## Notas adicionales
- `PermitRootLogin no`
- `PasswordAuthentication yes`
- Cambio de puerto SSH 22 → 90
- VS Code configurado como editor por defecto
