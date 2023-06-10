# Practica ESP32 con DHT22 CON PANTALLA LCD 16x2 (I2C).
Este repositorio muestra como podemos programar una ESP32 con el sensor DHT22 y mostrar los resultados en una pantalla 16x2 (I2C).

## Introducción

### Descripción

La Esp32 la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor DTH22 para adquirir temperatura y humedad del entorno que se vera reflejado en una pantalla lcd 16x2 (I2C), ademas mostrara el nombre completo del creador del programa; Cabe aclarar que esta practica se usara un simulador llamado [WOKWI](https://https://wokwi.com/).


## Material Necesario

Para realizar esta practica necesitas lo siguiente

- [WOKWI](https://https://wokwi.com/)
- Tarjeta ESP 32
- Sensor DHT22
- Pantalla lcd 16x2 (I2C)



## Instrucciones

### Requisitos previos

Para poder usar este repositorio necesitas entrar a la plataforma [WOKWI](https://https://wokwi.com/).


### Instrucciones de preparación de entorno 

1. Abrir la terminal de programación y colocar la siguente programación:


#include "DHTesp.h"
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4

const int DHT_PIN = 15;

DHTesp dhtSensor;

LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {

  Serial.begin(115200);
  dhtSensor.setup(DHT_PIN, DHTesp::DHT22);
  lcd.init();
  lcd.backlight();

}

void loop() {

  TempAndHumidity  data = dhtSensor.getTempAndHumidity();
  Serial.println("Temp: " + String(data.temperature, 1) + "°C");
  Serial.println("Humidity: " + String(data.humidity, 1) + "%");
  Serial.println("---");
  
  lcd.setCursor(0, 0);
  lcd.print("  Temp: " + String(data.temperature, 1) + "\xDF"+"C  ");
  lcd.setCursor(0, 1);
  lcd.print(" Humidity: " + String(data.humidity, 1) + "% ");
  lcd.print("Wokwi Online IoT");

  delay(1000);

lcd.setCursor(0,0);
lcd.print("Jorge Alberto    ");

lcd.setCursor(0,1);
lcd.print("Roldan Aponte    ");
delay(1000);

}


2. Instalar la libreria de *DHT sensor library for ESPx* como se muestra en la siguente imagen.

![](https://github.com/jroldanap/DHT22CONPANTALLA/blob/main/LIBRERIA.png?raw=true)

3. Hacer la conexion de *DHT22*, pantalla *lcd16x2(I2C)* con la *ESP32* como se muestra en la siguente imagen.

![](https://github.com/jroldanap/DHT22CONPANTALLA/blob/main/CONEXION%202.png?raw=true)

### Instrucciónes de operación

1. Iniciar simulador dando click en el boton verde de play.
2. Visualizar los datos en el monitor serial y lcd16x2(I2C) .
3. Colocar la temperatura y humedad dando doble click al sensor *DHT22* 

## Resultados

Cuando haya funcionado, verás los valores dentro del monitor serial y lcd16x2(I2C) como se muestra en la siguente imagen.

![](https://github.com/jroldanap/DHT22CONPANTALLA/blob/main/programa%202%20corriendo.png?raw=true)

![](https://github.com/jroldanap/DHT22CONPANTALLA/blob/main/programa%202%20corr.png?raw=true)




## Evidencias de programa corriendo

![](https://github.com/jroldanap/DHT22CONPANTALLA/blob/main/programa%202%20corriendo.png?raw=true)

![](https://github.com/jroldanap/DHT22CONPANTALLA/blob/main/programa%202%20corr.png?raw=true)


# Créditos

Desarrollado por Jorge Alberto Roldan Aponte

- [GitHub](https://github.com/jroldanap)