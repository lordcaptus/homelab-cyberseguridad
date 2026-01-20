# Reconocimiento de Redes

## Contexto
Laboratorio para analisis de una red domestica segmentada en entorno controlado, para fines educativos y de aprendizaje, compuesta por un servidor fisico(OMOV sobre Debian) y maquinas virtuales Debian en Virtualbox.
El analisis se realiza desde una VM dedicada, sin afectar la red productiva del hogar.

## Objetivo
Identificar hosts activos, puertos expuestos y servicios accesibles dentro del segmento del laboratorio, como base para evaluaciones de seguridad posteriores.

## Alcance
El alcance de esta práctica se limita al reconocimiento pasivo y activo de la red del laboratorio.
No se realizan ataques de denegación, explotación, modificación de configuraciones ni pruebas sobre redes externas o productivas.

## Herramientas
Se utilizan herramientas nativas de Linux (ip, ss) para identificar interfaces y servicios locales, y nmap para el escaneo controlado de hosts y puertos en la red del laboratorio.