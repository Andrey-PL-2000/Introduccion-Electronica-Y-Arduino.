# Introduccion a la electronica y Arduino.

*Este conjunto de prácticas te llevará a un emocionante viaje introductorio en el mundo de la electrónica y la programación utilizando la plataforma Arduino. A través de una serie de proyectos prácticos, aprenderás los conceptos fundamentales de la electrónica.Estas prácticas están diseñadas para proporcionarte una sólida base que te permitirá explorar áreas avanzadas como la robótica y la automatización. No importa si eres un principiante o tienes experiencia previa, este conjunto de prácticas te ayudará a desarrollar habilidades esenciales y te inspirará a crear tus propios proyectos electrónicos emocionantes.*

## P1 "Conexión de Múltiples LEDs en una Configuración Paralela"

### [Practica 1] (https://www.tinkercad.com/things/0f3lZS00tbI)
![p1](https://github.com/Andrey-PL-2000/Introduccion-Electronica-Y-Arduino./assets/117885708/922f1d1b-7c51-4fc2-9087-0672257ed194)

### P2 "Introducción al Control de LEDs con Arduino"

###[Practica 2] (https://www.tinkercad.com/things/iXVpzXA2myD)


``` // C++
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
} ```

![p2](https://github.com/Andrey-PL-2000/Introduccion-Electronica-Y-Arduino./assets/117885708/395c3924-f9db-4407-b13c-d952b90c82ac)

