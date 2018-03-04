## Proyecto Arduino

Esta página ha sido creada con el propósito de recoger la información que nos conduzca al éxito de manejar las diferentes herramientas de desarrollo a la hora de llevar a cabo un proyecto Arduino.

## Introducción

El _board_ Arduino, no es más que un procesador al que le conectamos algunas entradas (desde teclado, ratón, cámara). 
El procesador utiliza la información de las entradas para generar salidas (a un monitor, por ejemplo).

A través de sensores o captadores de datos, obtendremos magnitudes físicas (velocidad, aceleración, temperatura, fuerza, presión, inclinación) que se pueden convertir en electricidad que Arduino puede medir.

## Características de los pines

En el _board_ nos encontramos dos filas de pines diferentes.

<img src="imagenes/board.png" height="300" width="450"/>

Arriba, los pines digitales, numerados de 0 al 13. Solo pueden tener 2 estados y pueden ser tanto entradas como salidas. 

Abajo, los pines analógicos, de 0 a 5. Están pensados para *captar* aquello que varía en su voltaje y solo pueden ser entradas. 

A la izquierda de los pines analógicos, las salidas de voltaje 5V, 3.3V, GRD (tierra).

## Conectando el _board_

Desde la IDE de Arduino, en el menú superior:

Elegimos nuestro modelo
```
Tools > Board > 
```
Elegimos el puerto COM al que está conectado el dispositivo
```
Tools > Serials Port >
```
## Funciones básicas de Arduino

### La función setup()

La utilizamos para configurar salidas y entradas.

```
void setup() {

}
```

### La función loop()

Utilizada para el código que está en constante ejecución.

```
void setup() {

}
```
Más, en la [Wiki de Funciones](https://github.com/nicorl/effinno/wiki/Manual-de-funciones)

## Proyecto 0

**Objetivo**: hacer parpadear el LED que trae la placa por defecto.

Información necesaria: Arduino UNO trae un LED integrado en el pin digital 13.

Ya que los pines digitales pueden ser E/S, hay que decir que queremos utilizar el pin 13 como salida.

```javascript
void setup() { // Código que se ejecuta una única vez.
  pinMode(13, OUTPUT); // Declaración del pin 13 como salida. // LED_BUILTIN
}

void loop(){ // Código que se ejecuta constantemente.
  digitalWrite(13, HIGH); // Se enciende el LED // LED_BUILTIN
  delay(1000); // Espera 1 segundo
  digitalWrite(13, LOW); // Se apaga el LED // LED_BUILTIN
  delay(1000); // Espera 1 segundo
}
```
Descarga este código [aquí](https://create.arduino.cc/editor/nicorl/479d5c08-82a6-4aa8-a39e-5da9fe516b02/preview)

### Webs de interés

Desde [Arduino](https://www.arduino.cc/en/Main/Software) podemos descargar el IDE de desarrollo con el que trabajaremos.

Todo el código del proyecto [Effinno](https://github.com/nicorl/effinno).
