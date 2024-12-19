# DHT22-CON-LCD

# Practica ESP32 con DHT22 y LCD
Este repositorio muestra como podemos programar una ESP32 con el sensor DHT22 y una pantalla LCD que nos muestre la información recibida por el sensor ESP32.

## Introducción

### Descripción

La ```ESP32``` la utilizamos en un entorno de adquisición de datos, en esta práctica ocuparemos un sensor (```DTH22```) para adquirir los datos de temperatura y humedad del entorno y una pantalla LCD para poder visualizar los datos leídos por dicho sensor.  Cabe aclarar que esta practica se usara un simulador llamado [WOKWI](https://https://wokwi.com/).


## Material Necesario

Para realizar esta practica necesitas lo siguiente

- [WOKWI](https://https://wokwi.com/)
- Tarjeta ESP 32
- Sensor DHT22
- Pantalla LCD 16x2 ILC



## Instrucciones

### Requisitos previos

Para poder usar este repositorio necesitas entrar a la plataforma [WOKWI](https://https://wokwi.com/).


### Instrucciones de preparación de entorno 

1. Abrir la terminal de programación y colocar la siguente programación:

```
#include "DHTesp.h"
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR   0x27
#define LCD_COLUMNS 20
#define LCD_LINES  4

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
lcd.print("  Humidity: " + String(data.humidity, 1) + "% ");
lcd.print("wokwi Online IoT");

  delay(1000);
}

```
2. Instalar las librerías:
-  **DHT sensor library for ESPx**
- **LiquidCrystal I2C**

![](https://github.com/Ricardoramosdelapaz/DHT22-CON-LCD/blob/main/Captura%20lib.PNG?raw=true).

3. Hacer la conexion de **DHT2** con la **ESP32** y la pantalla LCD como se muestra en la siguiente imagen.

![](https://github.com/Ricardoramosdelapaz/DHT22-CON-LCD/blob/main/Captura%20con.PNG?raw=true).

### Instrucciónes de operación

1. Iniciar simulador.
2. Visualizar los datos en el monitor serial.
3. Colocar la temperatura y humedad dando *doble click* al sensor **DHT22** 

## Resultados

Al iniciar la simulacion, verás los valores dentro del monitor serial y la pantalla LCD como se muestra en la siguente imagen.

![](https://github.com/Ricardoramosdelapaz/DHT22-CON-LCD/blob/main/res.PNG?raw=true).



# Créditos

Desarrollado por Ing. Ricardo Ramos De la paz

- https://github.com/Ricardoramosdelapaz
