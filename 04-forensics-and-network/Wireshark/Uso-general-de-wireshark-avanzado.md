This documents contain my answers of [Uso de Wireshark Avanzado](https://www.apuntesinformaticafp.com/actividades/usar_wireshark_avanzado.html)

# Uso general del software y la interfaz
## ¿Tienes instalada la última versión de Wireshark?
Barra de wireshark > Ayuda > Acerca de Wireshark.
## ¿En qué interfaces de red puedes hacer una captura?
Puede capturar en cualquier interfaz de red, mientras este tenga permisos.
## ¿Sabes cómo hacer una captura de 1.000 paquetes?
Barra de wireshark > Captura > Opciones > Opciones --> Donde pone "Detener captura despues de..." Introducir 1000 en paquetes.
## ¿Sabes cómo hacer una captura de tráfico de 5 segundos?
Lo mismo pero aplicamos los 5 segundos en la opción que corresponde
## ¿Sabes cómo capturar sólo tráfico udp?
Barra de wireshark > Captura > Opciones --> En la pestaña "Entrada" --> Filtro de captura para interfaces --> Añadimos UDP
## ¿Puedes hacer una captura de 1.000 paquetes, con tráfico TCP?
Sí. Filtro de captura o visualización: tcp y detener al llegar a 1000 paquetes.
## ¿Sabes cual es la IP origen de un paquete?
Campo Source.
## ¿Sabes cual es la IP destino?
Campo Destination.
## ¿Cual fue la fecha de captura de ese paquete?
En Frame → Arrival Time.
## ¿Cual es el tamaño total de ese paquete?
En Length o Frame Length.
## ¿Y qué medio de transmisión utiliza y que tipo de interfaz de red es?
En Frame → Interface y Encapsulation (Ethernet, Wi-Fi).
## ¿Sabes qué protocolo de capa 2 utiliza?
Normalmente Ethernet II
## ¿Sabes qué protocolo de capa 3 utiliza?
IPv4 o IPv6
## ¿Sabes qué protocolo de capa 4 utiliza?
TCP o UDP
## ¿Hay algún paquete que tenga la cadena de texto “pass” (en su contenido)?
frame contains "pass"
## ¿Hay algún paquete que tenga la cadena de texto “content” (en su contenido)?
frame contains "content"
## ¿Hay algún paquete que tenga la cadena de texto “content” (en la información del paquete)?
frame matches "content"
