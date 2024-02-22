## Materiales necesarios:

- 1 Arduino Uno o similar.
- 1 Display LCD 16x2 con interfaz I2C.
- Cables de conexión.
- (Opcional) 1 sensor de temperatura como el TMP36 para mostrar valores de sensores.
## Objetivo:

El objetivo de este taller es enseñar a los participantes cómo comunicarse con un display LCD a través de la interfaz I2C para mostrar mensajes estáticos y valores dinámicos de sensores. Los participantes aprenderán a utilizar librerías específicas para manejar el display LCD y entenderán los conceptos básicos de la comunicación I2C.
## Esquema de conexión:

1. **Display LCD a Arduino**:
   - **VCC** del LCD a **5V** del Arduino.
   - **GND** del LCD a **GND** del Arduino.
   - **SDA** del LCD a **SDA** del Arduino (A4 en Uno, 20 en Mega, o el pin marcado SDA en otros modelos).
   - **SCL** del LCD a **SCL** del Arduino (A5 en Uno, 21 en Mega, o el pin marcado SCL en otros modelos).
2. **Sensor TMP36** (opcional):
   - **VCC** al **5V** del Arduino.
   - **GND** al **GND** del Arduino.
   - **Signal** al pin analógico **A0** del Arduino.
## Diagrama: 

![[Pasted image 20240220130012.png]]
## Instrucciones:

1. **Monta el Circuito**: Conecta el display LCD y, si decides incluirlo, el sensor de temperatura al Arduino siguiendo el esquema de conexión.
2. **Instala las Librerías Necesarias**: Asegúrate de tener instalada la librería para manejar el LCD con I2C. Puedes encontrarla en el Gestor de Librerías del IDE de Arduino buscando "LiquidCrystal I2C" y seleccionando la versión más reciente. En el simulador están en la sección de "Library Management". "Wire.h" no la tienen que añadir en el  "Library Management". Al finalizar lo verán de esta manera: ![[Pasted image 20240220130955.png]]
1. **Programa el Arduino**: Utiliza la plantilla de código proporcionada para escribir el programa que mostrará mensajes en el display LCD. Si incluyes el sensor de temperatura, modifica el programa para leer y mostrar estos valores.
2. **Observa el Comportamiento**: Una vez cargado el programa, deberías ver el mensaje estático o los valores del sensor mostrados en el display LCD.
## Plantilla del Código:

```cpp
#include <Wire.h> 
#include <LiquidCrystal_I2C.h>

// Inicializar el display LCD (dirección I2C, columnas, filas)
LiquidCrystal_I2C lcd(0x27, 16, 2);

// Coeficiente Beta del termistor
const float BETA = 3950;

void setup() {
  // LCDs pueden ser algo confusas asi que les deje algo de codigo comentado 
  // que pueden usar. igual que en los otros talleres, la explicacion esta mas abajo.
  
  // Iniciar el LCD
  //lcd.init();   
  // Encender la retroiluminación                   
  //lcd.backlight();        
           
  // Mostrar un mensaje estático
  // Establecer el cursor en la primera columna, 
  // primera fila
  //lcd.setCursor(0, 0);
  // Escribir el primer mensaje             
  //lcd.print("Hola Mundo!");  
  // Mover el cursor a la primera columna, segunda fila      
  //lcd.setCursor(0, 1);
  // Escribir el segundo mensaje             
  //lcd.print("Arduino LCD I2C");    
}

void loop() {
  // Aquí puedes agregar código para leer un sensor y mostrar sus valores
  // Por ejemplo, para un sensor de temperatura conectado al pin A0:
  // float temperatura = leerTemperatura();
  // lcd.setCursor(0, 1);
  // lcd.print("Temp: ");
  // lcd.print(temperatura);
  // lcd.print(" C");
  // delay(1000); // Actualizar el valor cada segundo
}

// Función para leer la temperatura (si se incluye el sensor)
// float leerTemperatura() {
	// Pueden crearlas en base a el taller 2 
// }
```

## Guía del Código:

### Inclusión de Librerías

```cpp
#include <Wire.h> 
#include <LiquidCrystal_I2C.h>
```

- `#include <Wire.h>`: Esta línea incluye la librería Wire, que permite la comunicación I2C entre el Arduino y otros dispositivos, como el display LCD. I2C es un protocolo de comunicación que utiliza dos líneas: SDA (datos) y SCL (reloj).
- `#include <LiquidCrystal_I2C.h>`: Incluye la librería LiquidCrystal_I2C, específicamente diseñada para controlar displays LCD que utilizan un módulo de interfaz I2C. Esta librería simplifica la tarea de enviar datos al LCD.
### Inicialización del Display LCD

```cpp
LiquidCrystal_I2C lcd(0x27, 16, 2);
```

- `LiquidCrystal_I2C lcd(0x27, 16, 2);`: Crea un objeto `lcd` de la clase `LiquidCrystal_I2C`. Este objeto se utilizará para interactuar con el display LCD. Los parámetros son:
  - `0x27`: La dirección I2C del módulo LCD. Esta dirección puede variar (comúnmente `0x27` o `0x3F`), y se puede encontrar utilizando un escáner I2C.
  - `16, 2`: El tamaño del display, indicando que tiene 16 columnas y 2 filas.
### Configuración Inicial

```cpp
void setup() {
  lcd.init();                      // Iniciar el LCD
  lcd.backlight();                 // Encender la retroiluminación
  lcd.setCursor(0, 0);             // Establecer el cursor
  lcd.print("Hola Mundo!");        // Escribir mensaje
  lcd.setCursor(0, 1);             // Mover el cursor
  lcd.print("Arduino LCD I2C");    // Escribir segundo mensaje
}
```

- `lcd.init();`: Inicializa el display LCD.
- `lcd.backlight();`: Enciende la retroiluminación del LCD para que el texto sea visible.
- `lcd.setCursor(0, 0);`: Mueve el cursor a la primera columna de la primera fila.
- `lcd.print("Hola Mundo!");`: Muestra el mensaje "Hola Mundo!" en la primera fila.
- `lcd.setCursor(0, 1);`: Mueve el cursor a la primera columna de la segunda fila.
- `lcd.print("Arduino LCD I2C");`: Muestra el mensaje "Arduino LCD I2C" en la segunda fila.
### Bucle Principal

```cpp
void loop() {
  float temperatura = leerTemperatura();
  lcd.setCursor(0, 1);
  lcd.print("Temp: ");
  lcd.print(temperatura);
  lcd.print(" C");
  delay(1000); // Actualizar cada segundo
}
```

- Dentro del bucle `loop`, se lee continuamente la temperatura utilizando la función `leerTemperatura`, se actualiza el display LCD con el valor de la temperatura, y se espera un segundo (`delay(1000)`) antes de repetir el proceso.
### Lectura de la Temperatura

```cpp
float leerTemperatura() {
  int analogValue = analogRead(A0);
  float temperatura = 1 / (log(1 / (1023. / analogValue - 1)) / BETA + 1.0 / 298.15) - 273.15;
  return temperatura;
}
```

- `float leerTemperatura()`: Esta función lee el valor analógico del sensor de temperatura conectado al pin A0, calcula la temperatura en grados Celsius utilizando la ecuación de Steinhart-Hart (una forma de la ecuación de resistencia-temperatura para termistores), y devuelve este valor.
- `int analogValue = analogRead(A0);`: Lee el valor analógico del sensor de temperatura.
- La ecuación utilizada convierte el valor leído en una temperatura en grados Celsius. La constante `BETA` y los valores numéricos específicos en la fórmula dependen de las características del sensor de temperatura utilizado.
## Código completo: 
Link de wokwi: https://wokwi.com/projects/390273830791061505
```cpp
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

// Inicializar el display LCD (dirección I2C, columnas, filas)
LiquidCrystal_I2C lcd(0x27, 16, 2);
// Coeficiente Beta del termistor
const float BETA = 3950;

void setup() {
  lcd.init();                      // Iniciar el LCD
  lcd.backlight();                 // Encender la retroiluminación
  
  // Mostrar un mensaje estático:
  lcd.setCursor(0, 0);             // Establecer el cursor en la primera columna, primera fila
  lcd.print("Hola Mundo!");        // Escribir el primer mensaje
  lcd.setCursor(0, 1);             // Mover el cursor a la primera columna, segunda fila
  lcd.print("Arduino LCD I2C");    // Escribir el segundo mensaje
}

void loop() {
  float temperatura = leerTemperatura();
  lcd.setCursor(0, 1);
  lcd.print("Temp: ");
  lcd.print(temperatura);
  lcd.print(" C");
  delay(1000); // Actualizar el valor cada segundo
}

// Función para leer la temperatura (si se incluye el sensor)
float leerTemperatura() {
  int analogValue = analogRead(A0);
  float temperatura = 1 / (log(1 / (1023. / analogValue - 1)) / BETA + 1.0 / 298.15) - 273.15;
  return temperatura;
}
```

