# Proyecto Integrador
Documentación del proyecto integrador:  Replicación de movimientos con robot 3D y visión por computadora.
## Introducción
<div align="justify">
 El presente proyecto se centra en el diseño y la implementación de un esqueleto humanoide robótico en 3D, equipado con servomotores que permiten la imitación de movimientos 
 humanos. A pesar de que la replicación de estos movimientos no es completamente precisa y se enfrenta a un ligero retraso en la respuesta, el sistema demuestra una notable 
 capacidad para emular la dinámica del cuerpo humano. Para lograr esta imitación, se ha integrado un sistema de visión por computadora que permite al robot detectar puntos 
 clave del cuerpo, como muñecas, codos y hombros, facilitando así la sincronización de los movimientos.<br>
 La comunicación entre el sistema de visión y los actuadores del robot se realiza a través de una conexión Wi-Fi y Bluetooth, lo que permite una transmisión de datos 
 eficiente, aunque con ciertas limitaciones en la sincronización. Además, se ha incorporado un módulo ESP32 y una pantalla LCD, que mejoran la interacción y el control del 
 sistema, ofreciendo una interfaz más amigable para el usuario. Este proyecto no solo busca avanzar en la robótica humanoide, sino también explorar las posibilidades de 
 interacción entre humanos y máquinas, abriendo nuevas vías para el desarrollo de tecnologías asistivas y de entretenimiento.
</div>

## Objetivo 
<div align="justify">
 Desarrollar un robot que replique los movimientos humanos mediante visión por computadora y control de servomotores, ejecutando los movimientos de forma secuencial.
</div>

## Desarrollo 

###  Implementación de prototipo: esqueleto robótico

<div align="justify">
 En el desarrollo del proyecto, se empleó un prototipo de esqueleto robótico impreso en 3D, diseñado para la integración de servomotores en sus articulaciones.
 Además, se implementó visión por computadora para la detección y análisis de los movimientos humanos, permitiendo la replicación de estos en el robot mediante el control de 
 los actuadores(servomotores).
</div>
<br>
 
<div align="center">
  <img src="https://github.com/cbmeli/Proyecto_Integrador/raw/main/prototipo2.jpg" alt="Prototipo del robot" width="500">
  <p><em>Figura 1. Prototipo robótico impreso en 3D con servomotores integrados.</em></p>
</div>

###  Interconexión entre Arduino (ESP32) y Python mediante Wi-Fi y Bluethooth.
#### Importación de librerías en Python

Para el procesamiento de imágenes y videos en tiempo real, se instalaron y configuraron las siguientes herramientas en el entorno de Python:
* OpenCV: Se integró la biblioteca OpenCV para disponer de la herramienta cv2, que permite el análisis y procesamiento eficiente de imágenes
 y videos en tiempo real.
* MediaPipe: Se implementó MediaPipe para facilitar el análisis de secuencias de video en tiempo real. Esta herramienta proporciona funciones
 avanzadas como el reconocimiento de gestos, el seguimiento facial y corporal, así como la detección de objetos, lo que optimiza la interpretación
 de movimientos.
* Time: Se usa para calcular la velocidad de movimiento del rostro detectado.
>[!NOTE]
>
>Para establecer la comunicación Wi-Fi entre Arduino (ESP32) y Python, se utilizó el protocolo de sockets, que permite el intercambio de datos
 a través de una red.

En Python, los sockets se implementan en el módulo socket. Para crear un socket en Python se siguieron los siguientes pasos:

1) Importar el módulo socket: ***import socket***
1) Crear un objeto socket:<br>
 ***sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)*** <br>
 Donde: el primer argumento indica que se usará el protocolo IP versión
 4 y el segundo argumento indica que se utiliza el protocolo de transporte
 TCP.
1) Conectar el socket con la ESP32: <br>
 ***sock.connect(( dirección IP, Puerto))*** <br>
 En este caso se especificó la dirección ip de la ESP32 y el puerto 80.
1) Para enviar datos con el socket se programó la siguiente línea de código: <br>
 **sock.sendall(dato.encode())**
1)  Finalmente, se cierra el socket: ***sock.close()***

>[!IMPORTANT]
>
>El socket actúa como cliente, iniciando la conexión con la ESP32. Es decir, establece ese canal de comunicación, vinculándose a una dirección IP y a un puerto especifico.

###  Reconocimiento eficiente usando MediaPipe y OpenCV.

<div align="justify">
La visión por computadora es un campo que permite a los equipos informáticos interpretar y comprender su entorno. A través del uso de algoritmos avanzados y técnicas de aprendizaje automático, estos sistemas son capaces de analizar imágenes y videos para llevar a cabo tareas complejas, como la detección de rostros y cuerpos humanos. En el desarrollo de este proyecto, se empleó la biblioteca OpenCV debido a su eficiencia en el procesamiento de video. <br>
La función ***cv2.VideoCapture()*** es esencial para capturar un vídeo desde una cámara, basta con crear un objeto que contenga dicha función y pasar como argumento el índice de cámara (0 para la cámara predeterminada). <br>

La estimación de la postura humana es el proceso de detección y seguimiento de puntos de referencia del cuerpo humano en imágenes y vídeos, para esta técnica de visión artificial se utilizó **MediaPipe**. Los puntos clave detectados suelen incluir articulaciones como codos, rodillas, hombros y tobillos. <br>
MediaPipe es un marco de aprendizaje automático multiplataforma y de código abierto. Uno de sus modelos, MediaPipe Stance, es capaz de identificar hasta 33 puntos de referencia en 3D del cuerpo humano, como la cabeza, los hombros, los codos, las muñecas, las manos y las caderas, lo que permite estimar con precisión la postura de una persona.
</div> 

<div align="center">
  <img src="https://github.com/cbmeli/Proyecto_Integrador/raw/main/puntos.png" alt="Puntos de referencia" width="500">
  <p><em>Figura 2. Puntos de referencia 3D predefinidos para la estimación de la postura humana.</em></p>
</div>

## Conclusión

<div align="justify">
En conclusión, la contribución de este proyecto no solo radica en el desarrollo de un esqueleto humanoide robótico, sino también en su potencial para influir en múltiples áreas, desde la investigación y la educación hasta diversas aplicaciones prácticas en la vida cotidiana. Al abordar los desafíos actuales en la robótica humanoide, este proyecto puede facilitar el camino para innovaciones futuras que mejoren la interacción entre humanos y robots. Además, la integración de tecnologías como la comunicación inalámbrica, visión por computadora y el procesamiento en tiempo real refuerza la versatilidad del sistema. </div>
<br>

**Link reporte final**: [Documentación oficial](https://github.com/cbmeli/Proyecto_Integrador/raw/main/Reporte.pdf)




