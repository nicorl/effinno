# Basicos

## Lectura analógica de un potenciómetro

Un potenciómetro es una unidad mecánica que permite variar la cantidad de resistencia cuando se gira la ruleta.
El voltaje atraviesa el potenciómetro y se transforma a un valor analógico de entrada hacia el _board_. 
Es posible medir la resistencia producida por el potenciómetro como valor analógico.

El objetivo de este _básico_ es monitorizar el estado del potenciómetro después de establecer comunicación entre Arduino y el IDE.

### Circuito

La conexión del potenciómetro al circuito se debe hacer atendiendo al esquema de la imagen.

Girando el eje del potenciómetro cambia la cantidad de resistencia, cambiando el voltaje al pin central del potenciómetro.
Cuando la resistencia entre el pin central y el pin conectado a 5 voltios es cercano a cero + la resistencia en el otro lado es cercana a 10 kOhm, el voltaje en el pin central es de 5 voltios.

Cuando las resistencias se invierten, la tensión en el pin central es próximo a 0. Este voltaje es el valor analógico que vamos a leer como entrada.

Arduino tiene un circuito ADC (Analog to Digital Converter) que lee el valor del voltaje y lo convierte en un valor entre 0-1023. La función _analogRead()_ devolverá el valor entre 0-1023 que es proporcional a la cantidad de tensión aplicado al pin.

### Esquemas

<img src="imagenes/AnalogReadSerial_BB.png" height="300" width="200"/>

<img src="imagenes/AnalogReadSerial_sch.png" height="300" width="200"/>

### Código

En la parte del ```setup``` se establecerá el _serial_ de comunicación.

En la parte del ```loop``` se define una variable para guardar el valor recogido y un comando para enviar la variable hasta el ordenador.

```javascript
void setup() {
  Serial.begin(9600);
}

void loop() {
  int sensorValue = analogRead(A0);
  Serial.println(sensorValue);
  delay(1);
}
```
## Lectura digital de un potenciómetro

Los botones permiten conectar dos puntos en un circuito cuando se presionan. 
Cuando el botón está abierto, no hay conexión entre las patillas del botón, por lo que el _pin_ está conectado a tierra a través de la resistencia _pull-down_ y lee LOW o 0. Cuando el botón está cerrado, hace una conexión entre sus dos patas, conectando el pin a 5 voltios, por lo que devuelve HIGH o 1.

https://paletosdelaelectronica.wordpress.com/2015/01/25/resistencias-pull-up-y-pull-down/

### Esquemas

<img src="imagenes/button_basics.png" height="300" width="200"/>

<img src="imagenes/button_sch.png" height="300" width="200"/>

### Código

En la parte de ```setup``` definimos el _serial_ de comunicación. Además, inicializamos el pin 2, como pin de lectura del botón como entrada (INPUT).

En la parte de ```loop``` se configura para que cuando el botón sea pulsado, 5 voltios fluyan a través del circuito, y cuando el botón no es pulsado, esté conectado a tierra a través de una resistencia de 10 kOhm. La entrada digital solo podrá ser 0 o 1, sin valores intermedios.

```javascript
int pushButton = 2;

void setup() {
  Serial.begin(9600);
  pinMode(pushButton, INPUT);
}

void loop() {
  int buttonState = digitalRead(pushButton);
  Serial.println(buttonState);
  delay(1);       
}
```
