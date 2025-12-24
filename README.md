# Homelab de Ciberseguridad

Este repositorio documenta el diseño, construcción y explotación controlada de un laboratorio personal de ciberseguridad, orientado a desarrollar competencias prácticas en administración Linux, redes, hardening, seguridad ofensiva y defensiva.

El enfoque del laboratorio es **práctico y reproducible**, simulando escenarios reales de infraestructura y seguridad utilizados en entornos profesionales.

---

## Objetivo del laboratorio

- Construir una base sólida en sistemas Linux y redes.
- Practicar hardening y análisis de configuraciones inseguras.
- Realizar pruebas de seguridad ofensiva en entornos controlados.
- Documentar errores reales, hallazgos y mitigaciones.
- Generar evidencia técnica demostrable para portafolio profesional.

---

## Infraestructura

### Servidor físico
- Sistema base: Debian + OpenMediaVault (OMV)
- Acceso remoto mediante SSH endurecido
- Uso: servicios, almacenamiento, laboratorio defensivo

### Virtualización
- Host: Windows
- Hypervisor: VirtualBox
- VM principal: Debian 12 (Bookworm)
- Uso: prácticas de Linux, redes, scripting y pruebas de seguridad

---

## Tecnologías y herramientas

- Linux (Debian)
- SSH, systemd, journald
- Networking: TCP/IP, escaneo y análisis de tráfico
- Git & GitHub para control de versiones
- Python para automatización y recon
- Herramientas de seguridad (nmap, Wireshark, Burp, Metasploit – progresivamente)

---

## Metodología

- Aprendizaje basado en problemas reales.
- Documentación de errores y soluciones.
- Versionado de todo el proceso.
- Enfoque en reproducibilidad y evidencia técnica.

---

## Estructura del repositorio

- `lab-setup/`: instalación y configuración del laboratorio.
- `networking/`: prácticas de escaneo, análisis y segmentación.
- `scripts/`: automatización en Python y Bash.
- `writeups/`: reportes técnicos de prácticas y mini-proyectos.
- `roadmap.md`: plan de aprendizaje y evolución del laboratorio.

---

## Estado actual

- Laboratorio operativo.
- Acceso SSH funcional y endurecido.
- Repositorio inicializado y documentado.
- Próximo paso: documentación detallada del setup y primeros ejercicios de red.

---

## Autor

Proyecto desarrollado como parte de un proceso de transición profesional hacia el área de ciberseguridad.

