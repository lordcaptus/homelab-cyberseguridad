1. Contexto
En este laboratorio se configuró un servidor basado en Debian con el objetivo de practicar administración de sistemas Linux y hardening básico.

Se eligió OpenMediaVault (OMV), que se ejecuta sobre Debian, ya que permite combinar un entorno de laboratorio de ciberseguridad con un servidor personal tipo NAS. Este enfoque facilita realizar pruebas de configuración y seguridad sin perder la funcionalidad práctica de un servidor doméstico.

2. Acción
Se habilitó el acceso remoto mediante SSH y se creó un usuario no privilegiado, otorgándole privilegios administrativos controlados mediante sudo, con el fin de evitar el uso directo del usuario root.

3. Problemas
Tras aplicar configuraciones de endurecimiento en SSH, el acceso remoto falló para el usuario creado. El problema se evidenció durante los intentos de conexión por SSH.

4. Diágnostico
El análisis de los logs del servicio SSH, utilizando journalctl, permitió identificar una restricción en la directiva AllowGroups, la cual impedía el acceso del usuario al servicio.

5. Solución
Se modificó la directiva AllowGroups para incluir el grupo del usuario creado, lo que permitió restablecer el acceso remoto de forma controlada.

6. Resultado
El sistema quedó accesible de forma segura y documentado para futuras reproducciones.

7. Observaciones Técnicas adicionales
Se validaron las directivas PermitRootLogin no y PasswordAuthentication yes en el archivo de configuración de SSH.

Se configuró Visual Studio Code como editor principal y se añadió al PATH del sistema, evitando el uso de editores por consola como Vim durante la administración.

Se creó un usuario con privilegios administrativos controlados mediante sudo, deshabilitando el acceso directo de root por buenas prácticas de seguridad.

Se modificó el puerto SSH por defecto (22) a un puerto alternativo (90) como medida básica de reducción de superficie de ataque.

