# Funcionamiento

HC-SR04 es un sensor ultrasónico que utiliza sonar para determinar a la distanca a la que un objeto está y su rango puede llegar hasta 4 metros.

## Caracteristicas

Alimentación:+5V DC

Corriente en reposo : <2mA

Corriente de trabajo: 15mA

Ángulo efectivo: <15°

Rango de medida : 2cm – 400 cm

Resolución : 0.3 cm

Ángulo de medida: 30 degree

Ancho de pulso: 10uS

Dimensiones: 45mm x 20mm x 15mm

## Funcionamiento

El transmisor envia una señal, un sonido de alta frecuencia, la señal rebota en el objeto y la onda reflejada vuelve al transmisor, captándola.

## Esquema del sensor

<img src="imagenes/HC-SR04.png" height="200" width="300"/>

VCC: Conexión de +5VDC

Trig: Trigger (entrada)

Echo: Echo (salida)

GND: Tierra

<img src="imagenes/EsquemaHC-SR04.jpg" height="377" width="809"/>

## Codigo

```javascript

int trigPin = 11;    //Trig - emisor
int echoPin = 12;    //Echo - receptor
long duration, cm, inches;
 
void setup() {
  //Puerto para comunicaciones
  Serial.begin (9600);
  //Definir entradas y salidas
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
}
 
void loop()
{
 
 
  // The sensor is triggered by a HIGH pulse of 10 or more microseconds.
  // Give a short LOW pulse beforehand to ensure a clean HIGH pulse:
  digitalWrite(trigPin, LOW);
  delayMicroseconds(5);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
 
  // Read the signal from the sensor: a HIGH pulse whose
  // duration is the time (in microseconds) from the sending
  // of the ping to the reception of its echo off of an object.
  pinMode(echoPin, INPUT);
  duration = pulseIn(echoPin, HIGH);
 
  // convert the time into a distance
  cm = (duration/2) / 29.1;
  inches = (duration/2) / 74; 
  
  Serial.print(inches);
  Serial.print("in, ");
  Serial.print(cm);
  Serial.print("cm");
  Serial.println();
  
  delay(250);
}

```

Descarga este código [aquí](https://create.arduino.cc/editor/nicorl/94ffe2d2-c62c-44ed-80a4-4234415c8a1f/preview)

## Utilizando LiquidCrystal para mostrar el resultado

```javascript
#include <LiquidCrystal.h> //Importamos la librería LiquidCrystal
 
LiquidCrystal lcd(12, 11, 5, 4, 3, 2); //Creamos la variable y establecemos los pins del display
 
int PinEnvio = 9;    //Trig - emisor
int PinVuelta = 10;    //Echo - receptor
long duracion, cm; 


void setup()
{
  lcd.begin(16, 2); //Inicializamos el display configurando 16 columnas por 2 filas
  lcd.setCursor(0,0); //Ponemos el cursor en la primera fila a la izquierda
  lcd.print("Inicializando..."); //Imprimimos un mensaje inicial
  delay(2000); //Esperamos 2 segundos
  lcd.clear(); //Borramos lo que pone a la pantalla
  
  //Puerto para comunicaciones
  Serial.begin (9600);
  //Definir entradas y salidas
  pinMode(PinEnvio, OUTPUT);
  pinMode(PinVuelta, INPUT);
}
 
void loop()
{
  //Primera fila
  lcd.setCursor(0, 0);
  lcd.print("DISTANCIA MEDIDA");
 
   // The sensor is triggered by a HIGH pulse of 10 or more microseconds.
  // Give a short LOW pulse beforehand to ensure a clean HIGH pulse:
  digitalWrite(PinEnvio, LOW);
  delayMicroseconds(5);
  digitalWrite(PinEnvio, HIGH);
  delayMicroseconds(10);
  digitalWrite(PinEnvio, LOW);
 
  // Lee la señal del sensor: un pulso HIGH cuya
  // duración es el tiempo (en microsegundos) desde el envio
  // del PING hasta su recepción.
  pinMode(PinVuelta, INPUT);
  duracion = pulseIn(PinVuelta, HIGH);
 
  // Convertir el tiempo en distancia
  cm = (duracion/2) / 29.1;

 
  //Segunda fila
  lcd.setCursor(0, 1);
  lcd.print(cm);
  delay(200);
 
  lcd.clear(); //Borramos lo que pone a la pantalla
}
```
Descarga este código [aquí](https://create.arduino.cc/editor/nicorl/5b8ef3ea-9018-4403-8c43-020ba1069a1e/preview)
