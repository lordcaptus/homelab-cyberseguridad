# Acceso SSH y Hardening básico

## Contexto
El acceso remoto mediante SSH es un vector crítico en servidores expuestos a red. Por esta razón, se decidió aplicar un hardening básico desde la etapa inicial del laboratorio, priorizando la reducción de superficie de ataque sin comprometer la operatividad.

## Objetivo
Configurar un acceso SSH funcional y seguro, evitando el uso de root, restringiendo usuarios autorizados y aplicando configuraciones mínimas de endurecimiento.

## Configuración aplicada

### Usuario y privilegios
- Creación de usuario no privilegiado
- Asignación controlada de privilegios mediante sudo
- Deshabilitación de acceso remoto directo para root

### Endurecimiento del servicio SSH
- Cambio del puerto por defecto (22 → 90)
- Restricción de usuarios/grupos autorizados (`AllowGroups`)
- Configuración explícita de parámetros de autenticación

### Parámetros relevantes

(bash)
PermitRootLogin no
PasswordAuthentication yes
Port 90
AllowGroups ...

## Problema encontrado

Tras aplicar las restricciones de acceso, el usuario creado no pudo autenticarse vía SSH, a pesar de contar con permisos sudo.

## Diagnóstico

Se analizaron los logs del servicio SSH utilizando journalctl -u ssh, lo que permitió identificar que la directiva AllowGroups limitaba el acceso únicamente al grupo configurado inicialmente.

## Solución

Se corrigió la directiva AllowGroups para incluir el grupo correspondiente al usuario, restableciendo el acceso remoto de forma controlada.

## Resultado

- Acceso SSH funcional para usuario autorizado
- Root inaccesible remotamente
- Configuración endurecida y documentada

## Lecciones aprendidas

- La importancia de validar configuraciones restrictivas antes de cerrar sesiones activas
- El rol de los logs como fuente primaria de diagnóstico
- Diferencia entre control de privilegios y control de acceso