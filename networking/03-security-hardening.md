## ufw hardening

“Tras el escaneo con nmap y la reducción de servicios expuestos, se implementó un firewall restrictivo con ufw para controlar tráfico entrante y saliente.”

## Preliminares
- Sudo ufw status verbose sin respuesta, no instalado
- No existencia en repositorios. grep -R ^deb /etc/apt/sources.list /etc/apt/sources.list.d/
* Adicionado en sources.list sudo nano /etc/apt/sources.list
- deb http://deb.debian.org/debian bookworm main
- deb http://security.debian.org/debian-security bookworm-security main
- deb http://deb.debian.org/debian bookworm-updates main

## Estado inicial:
- Firewall inexistente o con salida libre
- Riesgo de exfiltración y abuso de servicios

## Acciones realizadas (con comandos):
- Instalación y activación de ufw
- Reglas IN (80, 90)
- Cambio de política OUT a deny
- Habilitación explícita de DNS, HTTP, HTTPS, loopback
* solo permitir salidas a DNS, actualizaciones y OMV necesita para sus servicios
- sudo ufw status verbose
- sudo ufw default deny outgoing
- sudo ufw allow out 53/udp
- sudo ufw allow out 53/tcp
- sudo ufw allow out 80/tcp
- sudo ufw allow out 443/tcp
- sudo ufw allow out on lo
- sudo ufw allow in on lo
- sudo ufw reload
- sudo ufw status numbered
* Validaciones funcionales
- ping google.com
- apt update
- ss -tulpen
- Vm atacante nmap -p 1-1000 <IP_DEL_SERVIDOR>

## Validación:
- ufw status numbered
- nmap desde VM atacante
- Confirmación de funcionamiento del sistema

## Resultado:
“Servidor con política de mínimo privilegio y superficie de ataque reducida.”

## Actualizaciones despues de validaciones
- sudo apt update
- sudo apt upgrade
* Servidor parchado a versiones recientes 05/02/2026
- Actualización de seguridad y paquetes críticos:
- gnupg2: corrección de vulnerabilidades y mejora en la verificación de firmas.
- libxml2: mitigación de vulnerabilidad de denegación de servicio (XPath).
- vim: ajuste de pruebas problemáticas en compilación.
