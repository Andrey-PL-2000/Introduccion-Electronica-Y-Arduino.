# Introduccion a la electronica y Arduino.

*Este conjunto de prácticas te llevará a un emocionante viaje introductorio en el mundo de la electrónica y la programación utilizando la plataforma Arduino. A través de una serie de proyectos prácticos, aprenderás los conceptos fundamentales de la electrónica.Estas prácticas están diseñadas para proporcionarte una sólida base que te permitirá explorar áreas avanzadas como la robótica y la automatización. No importa si eres un principiante o tienes experiencia previa, este conjunto de prácticas te ayudará a desarrollar habilidades esenciales y te inspirará a crear tus propios proyectos electrónicos emocionantes.*

## P1 "Conexión de Múltiples LEDs en una Configuración Paralela"

*[Practica 1] (https://www.tinkercad.com/things/0f3lZS00tbI)*
![p1](https://github.com/Andrey-PL-2000/Introduccion-Electronica-Y-Arduino./assets/117885708/922f1d1b-7c51-4fc2-9087-0672257ed194)

### P2 "Introducción al Control de LEDs con Arduino"

*[Practica 2] (https://www.tinkercad.com/things/iXVpzXA2myD?sharecode=Ip5qbnyeI1pzkY4eQukolvZUtlrNtMeBfQDv5V6LxM4)*


```
 // C++
int led_rojo = 13;//Define el pin 13 (salida)
void setup()
{
pinMode(led_rojo,OUTPUT);// se configura el led como salida
}

void loop()
{
 digitalWrite(led_rojo, HIGH); // Enciende el LED
  delay(1000); // Espera 500 milisegundos (medio segundo)
  digitalWrite(led_rojo, LOW); // Apaga el LED
  delay(500); // Espera otros 500 milisegundos
} 
```
![p2](https://github.com/Andrey-PL-2000/Introduccion-Electronica-Y-Arduino./assets/117885708/395c3924-f9db-4407-b13c-d952b90c82ac)

### P3 "Práctica de Control de LED con Botón"

*[Practica 3] (https://www.tinkercad.com/things/7wAPwiLjgVs?sharecode=5WOTgd3oejP7bqgTMrp-5uVhVkyoAzwpDFV4Ufxl408)*

```
int LED = 13;
int pulsador = 5; 
int estado;
void setup() {
pinMode(LED,OUTPUT);
pinMode(pulsador,INPUT_PULLUP);
estado=0;
}
void loop() {
while(digitalRead(pulsador)==HIGH);
estado = digitalRead(LED);
digitalWrite(LED,!estado);
while(digitalRead(pulsador)==LOW);
}
```
![p3](https://github.com/Andrey-PL-2000/Introduccion-Electronica-Y-Arduino./assets/117885708/bc87b677-35cc-440d-9f8b-accce234203d)

### P4 "Control de LED con Fotorresistencia"

*[Practica 4] (https://www.tinkercad.com/things/j9FfVZSQBsC?sharecode=vsvlUePTB3CUElDBPNM6mLMmr5pK3KdAtCu2BcHLihE)*

```
int sensor_luz =0;  //Pin análogo en donde va conectada la fotocelda
int led =4;
int valor_luz = 0;  


void setup() {  
  pinMode(sensor_luz,INPUT); 
  Serial.begin(9600);
}

void loop() {
    
  valor_luz =analogRead(sensor_luz); //Mapeo inverso de los valores que toma la fotocelda
  Serial.println(valor_luz);
  if(valor_luz < 300){
    digitalWrite(led,HIGH);
  }else{(led,LOW);
       }
}
```

![P4](https://github.com/Andrey-PL-2000/Introduccion-Electronica-Y-Arduino./assets/117885708/caf2b609-6267-40e8-936f-c9f7aabbb9f3)


### P5 Control de Intensidad de un LED con Potenciómetro"

*[Practica 5] (https://www.tinkercad.com/things/3WoCbK5HBvv?sharecode=sn7dlxo0nPF18-PbblmJcZE5q1mQf-BBiqFX9pqd6Dk)*

```
const int potPin = A0; // Pin analógico donde se conecta el potenciómetro
const int ledPin = 13; // Pin digital donde se conecta el LED

void setup() {
  pinMode(ledPin, OUTPUT);
  digitalWrite(ledPin, LOW); // Apaga el LED al inicio
  Serial.begin(9600);
}

void loop() {
  int potValue = analogRead(potPin); // Lee el valor del potenciómetro
  int brightness = map(potValue, 0, 1023, 0, 255); // Mapea el valor a un rango adecuado para el brillo del LED
  analogWrite(ledPin, brightness); // Controla la intensidad del LED con PWM
  Serial.println(brightness); // Imprime el valor en el monitor serie (opcional)
}
```
![p5](https://github.com/Andrey-PL-2000/Introduccion-Electronica-Y-Arduino./assets/117885708/6d8e07f7-4045-420c-be68-0b1d6fc6dfc4)


### P6 "Contador 0-9 con visualizador anodo"
*[Practica 6] (https://www.tinkercad.com/things/7WBg3qqee35?sharecode=AWXyCKbbH0CNPJ6kh2EmUE090Zeawo5YLbgKWG0svgo)*

```
// Definiciones de pines para el visualizador de 7 segmentos
const int segA = 2;
const int segB = 3;
const int segC = 4;
const int segD = 5;
const int segE = 6;
const int segF = 7;
const int segG = 8;
const int segDP = 9;

// Definiciones de los dígitos 0 al 9 en binario
byte numeros[] = {
 0b1000000,     //0
 0b1111001,          //1
 0b0100100,          //2
 0b0110000,          //3
 0b0011001,          //4
 0b0010010,          //5
 0b0000010,          //6
 0b1111000,          //7
 0b0000000,          //8
 0b0010000};         //9

void setup() {
  // Configura los pines del visualizador de 7 segmentos como salida
  pinMode(segA, OUTPUT);
  pinMode(segB, OUTPUT);
  pinMode(segC, OUTPUT);
  pinMode(segD, OUTPUT);
  pinMode(segE, OUTPUT);
  pinMode(segF, OUTPUT);
  pinMode(segG, OUTPUT);
  pinMode(segDP, OUTPUT);
}

void loop() {
  for (int numero = 0; numero < 10; numero++) {
    mostrarNumero(numero);
    delay(1000); // Espera un segundo antes de mostrar el siguiente número
  }
}

void mostrarNumero(int numero) {
  if (numero >= 0 && numero <= 9) {
    byte segmentos = numeros[numero];
    digitalWrite(segA, bitRead(segmentos, 0));
    digitalWrite(segB, bitRead(segmentos, 1));
    digitalWrite(segC, bitRead(segmentos, 2));
    digitalWrite(segD, bitRead(segmentos, 3));
    digitalWrite(segE, bitRead(segmentos, 4));
    digitalWrite(segF, bitRead(segmentos, 5));
    digitalWrite(segG, bitRead(segmentos, 6));
    digitalWrite(segDP, bitRead(segmentos, 7));
  }
}
```

![p6](https://github.com/Andrey-PL-2000/Introduccion-Electronica-Y-Arduino./assets/117885708/e1d4abc6-5b37-4d8d-9023-1422338493d5)

### P7 "Efecto de Cambio de Colores en LED RGB de Cátodo Común"

*[Practica 7] (https://www.tinkercad.com/things/gYlSJp2Vhqb?sharecode=mqcoybqFwzGe6GDJAexR_OtOE5gKFgcDxZTnMG0m0Zg)*

```
int redPin = 9;    // Pin para el color rojo
int greenPin = 10;  // Pin para el color verde
int bluePin = 11;   // Pin para el color azul
int delayTime = 50; // Tiempo de espera entre cambios de color en milisegundos

void setup() {
  pinMode(redPin, OUTPUT);
  pinMode(greenPin, OUTPUT);
  pinMode(bluePin, OUTPUT);
}

void loop() {
  for (int i = 0; i < 256; i++) {
    setColor(255 - i, i, 255 - i); // Cambia gradualmente de morado a amarillo
    delay(delayTime);
  }

  for (int i = 0; i < 256; i++) {
    setColor(i, 255 - i, 255 - i); // Cambia gradualmente de amarillo a rojo
    delay(delayTime);
  }

  for (int i = 0; i < 256; i++) {
    setColor(255 - i, 255 - i, i); // Cambia gradualmente de rojo a azul
    delay(delayTime);
  }
}

void setColor(int red, int green, int blue) {
  analogWrite(redPin, red);
  analogWrite(greenPin, green);
  analogWrite(bluePin, blue);
}
```

![p7](https://github.com/Andrey-PL-2000/Introduccion-Electronica-Y-Arduino./assets/117885708/2549fa86-1f02-4d8c-83ef-5521c5816934)


### P8 "Pantalla LCD 16x2 con Mensajes Deslizantes"

*[Practica 8] (https://www.tinkercad.com/things/goBmtyIXrSC?sharecode=HJlcy81kuRgV0OHijT7erfT2HLc1UXt74kI-XqSaCpc)*

```
#include <LiquidCrystal.h>

LiquidCrystal lcd(12, 11, 5, 4, 3, 2); // Configura los pines RS, E, D4, D5, D6 y D7

void setup() {
  lcd.begin(16, 2); // Inicializa la pantalla LCD (16 columnas x 2 filas)
  lcd.setCursor(0, 0); // Establece la posición del cursor en la fila 1, columna 0
  lcd.print("Mensaje deslizante: ");
  delay(500);
  lcd.setCursor(0, 1); // Establece la posición del cursor en la fila 2, columna 0
  lcd.print("Este es un ejemplo");
}

void loop() {
  String mensaje = "Este es un ejemplo de desplazamiento de mensajes en una pantalla LCD 16x2.";

  for (int i = 0; i < mensaje.length(); i++) {
    lcd.setCursor(0, 1); // Fila 2, columna 0
    lcd.print(mensaje.substring(i));
    delay(400); // Ajusta la velocidad del desplazamiento
    lcd.clear();
  }
}
```

![p8](https://github.com/Andrey-PL-2000/Introduccion-Electronica-Y-Arduino./assets/117885708/a8276eb5-eb8c-4730-a0c0-bc2d7fd472c9)



### P10 catodo comun

*[Practica 10] (https://www.tinkercad.com/things/cta7P7Vdrx1?sharecode=0GeBfTaG8GZI-tm2NhHcmvaaR1a21hYWcAyaq8Q2oGE)*

```
// Definiciones de pines para el visualizador de 7 segmentos
const int segA = 2;
const int segB = 3;
const int segC = 4;
const int segD = 5;
const int segE = 6;
const int segF = 7;
const int segG = 8;
const int segDP = 9;

// Definiciones de los dígitos 0 al 9 en binario
byte numeros[] = {
  B00111111, // 0
  B00000110, // 1
  B01011011, // 2
  B01001111, // 3
  B01100110, // 4
  B01101101, // 5
  B01111101, // 6
  B00000111, // 7
  B01111111, // 8
  B01101111  // 9
};

void setup() {
  // Configura los pines del visualizador de 7 segmentos como salida
  pinMode(segA, OUTPUT);
  pinMode(segB, OUTPUT);
  pinMode(segC, OUTPUT);
  pinMode(segD, OUTPUT);
  pinMode(segE, OUTPUT);
  pinMode(segF, OUTPUT);
  pinMode(segG, OUTPUT);
  pinMode(segDP, OUTPUT);
}

void loop() {
  for (int numero = 0; numero < 10; numero++) {
    mostrarNumero(numero);
    delay(1000); // Espera un segundo antes de mostrar el siguiente número
  }
}

void mostrarNumero(int numero) {
  if (numero >= 0 && numero <= 9) {
    byte segmentos = numeros[numero];
    digitalWrite(segA, bitRead(segmentos, 0));
    digitalWrite(segB, bitRead(segmentos, 1));
    digitalWrite(segC, bitRead(segmentos, 2));
    digitalWrite(segD, bitRead(segmentos, 3));
    digitalWrite(segE, bitRead(segmentos, 4));
    digitalWrite(segF, bitRead(segmentos, 5));
    digitalWrite(segG, bitRead(segmentos, 6));
    digitalWrite(segDP, bitRead(segmentos, 7));
  }
}

```

![p10](https://github.com/Andrey-PL-2000/Introduccion-Electronica-Y-Arduino./assets/117885708/8336da29-f811-446f-9c6e-4bf952d80240)

## *Trabajando...*

