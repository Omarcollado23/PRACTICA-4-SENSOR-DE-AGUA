# Practica de ESP32 con Sensor de Distancia HC-SR04 y LED´S
Este repositorio muestra como podemos programar una ESP32 con el sensor de distancia HC-SR04  con un LCD.


### Descripción

La ```Esp32``` la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (```HC-SR04```) para medir el rango de nivel de agua y 4 Led´s que nos indicaran como sube y baja el nivel. Cabe aclarar que esta practica se usara en el simulador llamado [WOKWI](https://https://wokwi.com/).


## Material Necesario

Para realizar esta practica necesitas lo siguiente

- [WOKWI](https://https://wokwi.com/)
- Tarjeta ESP 32
- Sensor HC-SR04
- 4 Led´s
- 4 Resistencias


## Instrucciones


### Requisitos previos

Para poder usar este repositorio necesitas entrar a la plataforma [WOKWI](https://https://wokwi.com/).


### Instrucciones de preparación de entorno 

1. Abrir la terminal de programación y colocar la siguente programación:

```
// defines pins numbers
const int trigPin = 26;
const int echoPin = 25;
const int led1 = 22;
const int led2 = 21;
const int led3 = 19;
const int led4 = 18;


// defines variables
long duration;
int distance;
int safetyDistance;


void setup() {
pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
pinMode(echoPin, INPUT); // Sets the echoPin as an Input
pinMode(led1, OUTPUT);
pinMode(led2, OUTPUT);
pinMode(led3, OUTPUT);
pinMode(led4, OUTPUT);
Serial.begin(9600); // Starts the serial communication
}


void loop() {
// Clears the trigPin
digitalWrite(trigPin, LOW);
delayMicroseconds(2);

// Sets the trigPin on HIGH state for 10 micro seconds
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);

// Reads the echoPin, returns the sound wave travel time in microseconds
duration = pulseIn(echoPin, HIGH);

// Calculating the distance
distance= duration*0.034/2;

safetyDistance = distance;
if(safetyDistance>=2 && safetyDistance<=10)
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=10 && safetyDistance<=21) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=22 && safetyDistance<=32) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=32 && safetyDistance<=50) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, HIGH);
}
else
{
  digitalWrite(led1, LOW);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}

// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);
delay(1000);
}
```

2. Conectamos el **HC-SR04** con la **ESP32**, los Led´s y las reistencias como se muestra en la siguente imagen.
led1-pin22
led2-pin21
led3-pin19
led4-pin18

![](https://github.com/Omarcollado23/PRACTICA-4-SENSOR-DE-AGUA/blob/main/conexiones.jpg?raw=true)

### Instrucciónes de operación

1. Iniciamos el simulador.
2. Visualizar los datos en el monitor serial.
3. Colocar la distancia dando *doble click* al sensor **HC-SR04** 

  

## Resultados

Cuando haya funcionado, la información obtenida se arrojara en el LCD como se muestra en la siguente imagen.

![](https://github.com/Omarcollado23/PRACTICA-4-SENSOR-DE-AGUA/blob/main/led1.jpg?raw=true)
![](https://github.com/Omarcollado23/PRACTICA-4-SENSOR-DE-AGUA/blob/main/led2.jpg?raw=true)
![](https://github.com/Omarcollado23/PRACTICA-4-SENSOR-DE-AGUA/blob/main/led3.jpg?raw=true)
![](https://github.com/Omarcollado23/PRACTICA-4-SENSOR-DE-AGUA/blob/main/led4.jpg?raw=true)
![](https://github.com/Omarcollado23/PRACTICA-4-SENSOR-DE-AGUA/blob/main/leds%20apagados.jpg?raw=true)


# Créditos

Desarrollado por Ing. Omar Alejandro Collado Carriola

- [GitHub](https://github.com/Omarcollado23)