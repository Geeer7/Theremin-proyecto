# Theremin-proyecto
Es un repositorio de como crear un Theremin sencillo

Para este proyecto se necesita Pure Data y Arduino 
El código de Arduino es realmente corto y muy sencillo, de inicio tiene un Serial Begin en 9600
y como solamente una foto resistencia es el material principal utilizaremos AnalogRead en A0 que esel lugar en donde se conectará la foto resistencia.

Yo utilicé una protoboard para la conexión de el circuito. 
Tiene también SensorValue para que lea la fotoresistencia en cuánto a sus valores y eso sería todo por parte de Arduino

En el caso De Pure Data Utilizo 3 Cajas de mensaje, la primera Es Devices, la segunda es Open 5 y la tercera es Close 5.
Devices es para poder ver que puerto esta abierto, por lo general te pone 2 puertos a los cuales te puedes conectar.
en mi caso es el puerto 5, por eso Open y Close llevan el número 5. Ese número lo puedes cambiar dependiendo el puerto que tu eligas.
Open es para que empiece a generar sonido y Close es para estancar el sonido, para dejarlo sonando en la ultima frecuencia que escuchamos.
Estas 3 cajas van conectadas a una caja llamada Objeto en la cual tendrá por nombre "comport 9600".
Se necesita descargar un libreria externa para poder utilizar el código comport. Este código es el que nos permite vincular Arduino con Pure Data
por medio de Puerto Serial.
Conectamos comport 9600 a una caja de número. Sus valores son 0 como mínimo y en mi caso 110 com máximo. A esta caja de número vamos a conectar un Toggle
para que una vez que pongamos Close 5, podamos apagar el sonido.
Vamos a conectar un VSlider a nuestra caja de número. Los valore de VSlider son 0 como mínimo y 247 como máximo.
Casi para terminar tenemos ponemos una caja de mensaje y en ella escribimos "* 15" y conectada a esta, otra caja de mensaje. En esta vamos a escribir "osc~ 220"
Abajo de estas cajas vamos a poner una penúltima caja en la cual escribiremos "*~ 1" este código de señal lo dejé en uno ya que si no escribes un valor suena 
demasiado fuerte y con ese valor de 1 se puede regular el volumen de salida. A esta penúltima caja camos a conectarle un HSlider con valores de 0 como 
mínimo y 1 como máximo. Con el HSlider vamos a poder controlar el volumen.
Por último conectaremos un caja de objeto en la cual escribiremos "dac~" que será nuestra señal de salida.
