# Actualizacion servidor 21/01/26

## Contexto: Debian 12 + OMV
Simulacion apt list --upgradeble antes de sudo apt update muestra que paquetes se van a instalar y si alguno tiene incidencias o paquetes criticos que afecten el servicio.

## Problema: repo público inválido
404 Not Found
El repositorio «https://packages.openmediavault.org/public bookworm Release» 
APT intenta usar repositorio de OpenMediaVault que no existe o no corresponde a version actual de Debian, bloqueado por seguridad.

## Diagnóstico: apt-secure + ausencia de Release
Posiblemente OMV no soporte Debian 12 (Bookworm) en version actual.
Tambien puso tratarse de mal configuracion del repo de OMV tras la instalacion manual o actualizaciones incompletas.
No se fuerza actualizaciones inseguras.
Separacion entre actualizacion del sistema base y servicios OMV
Analisis con grep -R openmediavault /etc/apt/sources.list /etc/apt/sources.list.d/ 

## Decisión: deshabilitar repo para preservar estabilidad
- Existencia de repo local, usado como cache local de paquetes sin riesgo.
- Existencia de repo publico, APT intenta acceder a endpoint y el repo no existe para Bookworm o inexistencia de publicacion.
- Se deshabilita (comentado) repo sin ser borrado evitando que se intente actualizar OMV desde dicho repositorio. sudo nano /etc/apt/sources.list.d/openmediavault.list

## Resultado: sistema actualizado sin romper OMV
- SSh se mantiene estable
- Servidor actualizado sin romper capa de servicios (OMV)
- Debian 12 como base no se vio afectado
- Se respeto modelo de seguridad de APT

## Hallazgos y novedades
Durante la actualización del repositorio se presentó un error HTTP 403 al intentar realizar git push.
El problema se debió a la creación de un Personal Access Token sin el scope repo, lo que impedía operaciones de escritura.
Tras regenerar el token con los permisos correctos y actualizar las credenciales locales, la operación se completó exitosamente.