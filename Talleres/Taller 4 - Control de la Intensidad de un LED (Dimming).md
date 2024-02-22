## Materiales necesarios:

- 1 Arduino Uno o similar.
- 1 LED.
- 1 resistencia de 220 ohmios.
- Cables de conexión.
- 1 Protoboard.
## Objetivo:
El objetivo de este taller es enseñar a los participantes cómo controlar la intensidad de un LED utilizando la modulación por ancho de pulso (PWM) y bucles `for` en Arduino. Los participantes aprenderán a variar la luminosidad de un LED de forma gradual, aumentándola y disminuyéndola sucesivamente.
## Esquema de conexión:
1. **LED**: Conectar el ánodo (lado largo) del LED a uno de los pines que soportan PWM en el Arduino (por ejemplo, pin 9) a través de una resistencia de 220 ohmios. El cátodo (lado corto) se conecta a GND.
## Diagrama de conexión:

```
LED:
Pin PWM (9)   --- Resistor 220Ω --- Ánodo (LED)
GND (Arduino) --- Cátodo (LED)
```
## Diagrama:
![[Pasted image 20240220124200.png]]
## Instrucciones:

1. **Monta el Circuito**: Siguiendo el esquema de conexión, conecta el LED en el protoboard y enlázalo con el pin correspondiente en el Arduino.
2. **Programa el Arduino**: Utiliza la plantilla de código proporcionada para escribir el programa que controlará la intensidad del LED.
3. **Observa el Comportamiento**: Una vez cargado el programa, el LED debería aumentar gradualmente su brillo hasta alcanzar el máximo, para luego disminuir su brillo hasta apagarse, repitiendo este ciclo continuamente.
## Plantilla del Código:

```cpp
// Definir el pin del LED que soporta PWM
const int ledPin = 9;

void setup() {
  // Configurar el pin del LED como salida
  pinMode(ledPin, OUTPUT);
}

void loop() {
  // Aumentar gradualmente la intensidad del LED de 0 a 255
  // Utilizar un bucle for para incrementar el valor de intensidad del LED
  // Dentro del bucle, usar analogWrite para establecer la intensidad del LED con el valor del contador del bucle
  // Agregar un delay para ralentizar el aumento de la intensidad, haciendo el cambio visible
  
  // Disminuir gradualmente la intensidad del LED de 255 a 0
  // Utilizar otro bucle for para decrementar el valor de intensidad del LED
  // Dentro del bucle, usar analogWrite para establecer la intensidad del LED con el valor del contador del bucle
  // Agregar un delay para ralentizar la disminución de la intensidad, haciendo el cambio visible
  
  // Notas:
  // - analogWrite(pin, valor) permite controlar la intensidad de un LED conectado al pin especificado.
  //   'valor' debe estar entre 0 (completamente apagado) y 255 (brillo máximo).
  // - delay(tiempo) pausa el programa por el 'tiempo' especificado en milisegundos. Usar esto para ver el efecto de dimming.
}
```
## Guía del Código:

### Definición de Variables Globales

```cpp
const int ledPin = 9;
```

- `const int ledPin = 9;`: Esta línea declara una variable constante de tipo `int` llamada `ledPin` y le asigna el valor `9`. Esto indica que el LED está conectado al pin 9 del Arduino, que es capaz de salida PWM (Modulación por Ancho de Pulso). La palabra clave `const` asegura que el valor de `ledPin` no cambie durante la ejecución del programa.

### Función `setup()`

```cpp
void setup() {
  pinMode(ledPin, OUTPUT);
}
```

- `void setup() { ... }`: Esta función se ejecuta una sola vez cuando el programa comienza. Se utiliza para configurar ciertos parámetros iniciales.
- `pinMode(ledPin, OUTPUT);`: Establece el pin conectado al LED (definido por `ledPin`) como un pin de salida (`OUTPUT`). Esto es necesario para controlar el LED, permitiendo que el pin proporcione un voltaje alto o bajo.
### Función `loop()`

```cpp
void loop() {
  for(int i = 0; i <= 255; i++) {
    analogWrite(ledPin, i);
    delay(10);
  }

  for(int i = 255; i >= 0; i--) {
    analogWrite(ledPin, i);
    delay(10);
  }
}
```

- `void loop() { ... }`: Esta función se ejecuta en un bucle infinito después de `setup()`. En este caso, se utiliza para variar la intensidad del LED de forma continua.
#### Aumentar la Intensidad del LED

- `for(int i = 0; i <= 255; i++) { ... }`: Este bucle `for` incrementa gradualmente el valor de `i` de 0 a 255. Cada iteración del bucle incrementa `i` en 1. El rango de 0 a 255 corresponde a la gama completa de intensidad que se puede aplicar al LED mediante PWM, donde 0 es completamente apagado y 255 es el brillo máximo.
- `analogWrite(ledPin, i);`: Envía una señal PWM al pin del LED, estableciendo su intensidad al valor actual de `i`. La función `analogWrite()` es capaz de simular una salida analógica utilizando PWM, permitiendo variar la intensidad del LED.
- `delay(10);`: Pausa la ejecución del programa durante 10 milisegundos después de cada ajuste de intensidad. Esto ralentiza el aumento de la intensidad del LED, haciendo el cambio visible y suave.
#### Disminuir la Intensidad del LED

- `for(int i = 255; i >= 0; i--) { ... }`: Después de alcanzar el brillo máximo, este bucle `for` reduce gradualmente el valor de `i` de 255 a 0. Cada iteración del bucle decrementa `i` en 1, disminuyendo la intensidad del LED hasta que se apaga completamente.
- `analogWrite(ledPin, i);`: Similar al bucle anterior, ajusta la intensidad del LED al valor actual de `i`, pero esta vez disminuyendo la intensidad.
- `delay(10);`: Igual que en el bucle anterior, pausa la ejecución del programa durante 10 milisegundos después de cada ajuste de intensidad para hacer el cambio visible y suave.
## Código completo:
link en wokwi: https://wokwi.com/projects/390271884243807233

```cpp
// Definir el pin del LED que soporta PWM
const int ledPin = 9;

void setup() {
  // Configurar el pin del LED como salida
  pinMode(ledPin, OUTPUT);
}

void loop() {
  // Aumentar gradualmente la intensidad del LED
  for(int i = 0; i <= 255; i++) {
    // Establecer la intensidad del LED (0 a 255)
    analogWrite(ledPin, i);
    // Esperar un poco para ver el cambio de intensidad
    delay(10);
  }

  // Disminuir gradualmente la intensidad del LED
  for(int i = 255; i >= 0; i--) {
    // Establecer la intensidad del LED (255 a 0)
    analogWrite(ledPin, i);
    // Esperar un poco para ver el cambio de intensidad
    delay(10);
  }
}
```




