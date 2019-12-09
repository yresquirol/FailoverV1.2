Este código te permitirá configurar en un Mikrotik (licencia de nivel >=4 requerida y preferentemente versión internacional) múltiples interfaces para conectarlas a una zona pública de internet en Cuba ofreciendo la posibilidad de que varios usuarios puedan conectarse simultáneamente con su cuenta Nauta y al mismo tiempo aplicar para una lista de IPs un balanceo usando el parámetro NTH el cual permitirá que se distribuyan las conexiones de esta lista entre todas las interfaces con Internet.

HAY DOS ARCHIVOS DE CONFIGURACION, UNO USA LA HERRAMIENTA NETWATCH PARA CHEQUEAR CUANDO HAY INTERNET Y EL OTRO HACE USO DE SCRIPTS.
TOMEN EN CUENTA QUE EL CÓDIGO HA SIDO ESCRITO PARA EJECUTARSE EN UN EQUIPO SIN CONFIGURACIÓN ALGUNA (No Default Configuration)
LOS AJUSTES PARA CONECTARSE A WIFI-ETECSA DE LA INTERFAZ INALÁMBRICA FÍSICA DEBE REALIZARLOS MANUALMENTE

Si estás viendo este código en GitHub.... Para descargar use el botón verde de arriba a la derecha (Clone or download)

Como usar el código:
1. Descargar el código y modificar los valores de las variables según se requiera (Si el archivo que usted está modificando carece de alguna de las variables de abajo es porque no la necesita).
    - ifaces >>> es la cantidad de interfaces inalámbricas que deseamos tener en nuestro equipo (modificar el número según la cantidad deseada).
    - prefix >>> es el prefijo que tendrán las interfaces o sea la parte 'de alante' común entre ellas. Ejemplo para wlan1, wlan2, wlan3, wlan4 el prefijo es wlan. Escribir el valor dentro de las comillas.
    - ssid >>> es el nombre de la red WIFI a la que queremos conectarnos. Escribir el nombre entre las comillas.
    - gw >>> es el IP que asigna ETECSA como puerta de enlace
    - lanInterface >>> es la interfaz que va a actuar como LAN en nuestro equipo. Si el equipo tiene una sola interfaz ethernet este valor no hay que cambiarlo
    - lanAddress >>> es el IP que tendrá el Mikrotik en la interfaz LAN que hayamos escogido con la variable de arriba. Escribir el IP de manera que siempre sea el .1
    - hostToPing >>> es el IP al que se le hará ping para comprobar si una interfaz tiene o no Internet

2. Copiar todo el código, pegarlo en el Terminal del Mikrotik y esperar a que se ejecuten todas las operaciones.
3. Si usó el archivo de configuración que usa netwatch para chequear si hay Internet salte directamente al paso 4, si no, modifica el código de abajo manteniendo el esquema según el nombre y la cantidad de interfaces inalámbricas que tengas. El valor entre las comillas es el nombre de las interfaces inalámbricas:

    :global before { "wlan1"=0 ; "wlan2"=0 ; "wlan3"=0 ; "wlan4"=0 };
    - Ir a: System -> Scheduler, abrir el script "Init" y pegar el código ya adaptado a su configuración en la primera línea de manera que quede de primero.
    
4. Reinicar el equipo para que el proceso comience con normalidad desde cero.

Te recomiendo ver el video y usarlo como guía: https://youtu.be/XOtVFpJb-xw
