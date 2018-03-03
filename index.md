## Proyecto Arduino

Esta página ha sido creada con el propósito de recoger la información que nos conduzca al éxito de manejar las diferentes herramientas de desarrollo a la hora de llevar a cabo un proyecto Arduino.

## Introducción

El _board_ Arduino, no es más que un procesador al que le conectamos algunas entradas (desde teclado, ratón, cámara). 
El procesador utiliza la información de las entradas para generar salidas (a un monitor, por ejemplo).

A través de sensores o captadores de datos, obtendremos magnitudes físicas (velocidad, aceleración, temperatura, fuerza, presión, inclinación) que se pueden convertir en electricidad que Arduino puede medir.

## Características de los pines

En el _board_ nos encontramos dos filas de pines diferentes.

<div style="text-align:center"><img src="imagenes/board.png" height="300" width="450"/></div>

Arriba, los pines digitales, numerados de 0 al 13. Solo pueden tener 2 estados y pueden ser tanto entradas como salidas. 

Abajo, los pines analógicos, de 0 a 5. Están pensados para *captar* aquello que varía en su voltaje y solo pueden ser entradas. 


### Webs de interés

Desde [Arduino](https://www.arduino.cc/en/Main/Software) podemos descargar el IDE de desarrollo con el que trabajaremos.

Todo el código del proyecto [Effinno](https://github.com/nicorl/effinno).
