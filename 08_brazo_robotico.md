---
layout: default
title: Brazo robótico
nav_order: 9
---
# Brazo robótico
 Durante esta actividad trabajamos en el diseño y construcción de un brazo robótico, utilizando diferentes herramientas de diseño, simulación y electrónica. El proyecto nos permitió integrar conocimientos de diseño asistido por computadora, programación y control mediante componentes electrónicos.

Para la estructura del brazo utilizamos MDF, mientras que para el control empleamos un Arduino Uno y varios potenciómetros. Los potenciómetros permiten modificar los valores de entrada y controlar el movimiento del brazo de acuerdo con la programación realizada.


## Código

```cpp
#include <Servo.h>

Servo servo1;
Servo servo2;
Servo servo3;
Servo servo4;

int pos1 = 90;
int pos2 = 90;
int pos3 = 90;
int pos4 = 90;

void setup() {
  servo1.attach(6);
  servo2.attach(7);
  servo3.attach(8);
  servo4.attach(9);

  servo1.write(90);
  servo2.write(90);
  servo3.write(90);
  servo4.write(90);
}

void loop() {

  int lectura1 = analogRead(A0);
  int lectura2 = analogRead(A1);
  int lectura3 = analogRead(A2);
  int lectura4 = analogRead(A3);

  int nuevo1 = map(lectura1, 0, 1023, 0, 180);
  int nuevo2 = map(lectura2, 0, 1023, 0, 180);
  int nuevo3 = map(lectura3, 0, 1023, 0, 180);
  int nuevo4 = map(lectura4, 0, 1023, 0, 180);

  if (abs(nuevo1 - pos1) >= 2) {
    pos1 = nuevo1;
    servo1.write(pos1);
  }

  if (abs(nuevo2 - pos2) >= 2) {
    pos2 = nuevo2;
    servo2.write(pos2);
  }

  if (abs(nuevo3 - pos3) >= 2) {
    pos3 = nuevo3;
    servo3.write(pos3);
  }

  if (abs(nuevo4 - pos4) >= 2) {
    pos4 = nuevo4;
    servo4.write(pos4);
  }

  delay(20);
}
```
