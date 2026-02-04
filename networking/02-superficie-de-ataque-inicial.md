# Revision y analisis de puertos posterior a actualizacion 

## Contexto
- Analisis de protocolos
- Puertos expuestos
- Validacion de escucha local y red completa
- Servicios / procesos que lo expone

## Comando utilizado
- ss -tulpen

## Observaciones iniciales
### SSH - correcto y esperado
- No se exponen puertos por defecto o estandar
- Escucha IPv4 e IPv6
- ssh.service

### HTTP(nginx) - conscientemente expuesto
- escucha puerto tcp en puerto 80
- OMV expone su interfaz web.
- Accesible desde toda la red
- Analizar posible restriccion por firewall, mover o proteger mejor.

### systemd-resolved (DNS local)
- 5355 tcp/udp normal Debian actual
- Resolver local
- Multicast DNS (mDNS)

### chrony (NTP)
-loopback correcto

## Servicios que requieren revisión futura
### avahi-daemon (mDNS)
- visible para descubrimiento de servicios en red local
- udp 5353/5355 entornos domesticos es util, innecesario en servidor endurecido. 

### rpcbind (PUERTO 111)
- Requiere atencion tcp/udp 111
- utilizado para NFS y servicios RPC antiguos
- vulnerable a ataques
- No exponer si no se usa NFS

## Incidente durante prueba de escaneo 
### Observaciones operativas durante cambio de modo de red (VirtualBox)
- Contexto: cambio de red en VM atacante durante pruebas de escaneo.
- Síntomas observados: pérdida de conectividad, NO-CARRIER, Destination Host Unreachable.
- Hipótesis inicial (incorrecta): cambio de IP / fallo lógico.
- Causa real: desconexión física del cable Ethernet.
- Lección técnica: validar capas 1–3 antes de asumir fallos de configuración

