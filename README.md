# 🤖 Proyecto Arduino: Robot Seguidor de Línea (Line Follower)

Este es el proyecto para la Asignatura de **Programación Informática en Arduino**, realizado por:
* **Fernando Andrés Martínez Ekame**
* **Thiago Damian Rios Garcete**

> **Estado del Proyecto:** 🟢 Finalizado (Sprint 3 Completado)

---

## 🛠️ Lista de Materiales

Componentes necesarios para el prototipo completo.
**⚠️ Nota de actualización:** Para la versión final del robot, hemos sustituido el driver estándar por uno I2C para optimizar el cableado.

### 1. Control
* 1x Placa Arduino UNO R3

### 2. Sensores
* 1x Módulo de 3 sensores Infrarrojos (o 3x TCRT5000 independientes).

### 3. Chasis y Movimiento
* 1x Kit de Chasis 2WD (Motores DC + Ruedas)
* 1x Rueda loca (Caster wheel)
* **1x Controlador de Motores: Grove I2C Motor Driver** (Hardware Final).

### 4. Alimentación
* 1x Portapilas (4x AA) para los motores.
* 4x Pilas AA.

---

## 📈 Progreso y Sprints

Seguimos la metodología Agile con entregas quincenales.

### ✅ Sprint 1: Lectura de Sensores
* **Fecha límite:** 14 de Noviembre.
* [cite_start]**Objetivo:** Lectura de sensores, uso de variables, estructuras condicionales y depuración[cite: 10].
* **Entregable:** Código capaz de distinguir entre blanco y negro usando el Monitor Serie.
* **📂 Código:** [Ver Código del Sprint 1](./Sprint_1/sprint1_sensores.ino)

---

### ✅ Sprint 2: Control de Actuadores (Modularización)
* **Fecha límite:** 28 de Noviembre.
* [cite_start]**Objetivo:** Control de actuadores, modularización, uso de funciones y arrays[cite: 13].
* **Logros Técnicos:**
    * Implementación de **funciones propias** para el movimiento: `avanzar()`, `retroceder()`, `parar()`.
    * Simulación realizada con Driver L293D en Tinkercad.
    * Separación de la lógica de movimiento del bucle principal (`loop`).
* **📂 Código:** [Ver Código del Sprint 2](./Sprint_2/sprint2_motores.ino)

**📸 Evidencia del Circuito (Simulación):**
<img width="742" alt="Simulación Sprint 2" src="https://github.com/user-attachments/assets/8e418a30-8ad8-41d3-93da-62f8fa905dcc" />

---

### ✅ Sprint 3: Integración Final
* **Fecha límite:** 12 de Diciembre.
* [cite_start]**Objetivo:** Integración hardware-software, optimización del código, eficiencia energética y presentación profesional[cite: 16].
* **Cambios y Optimizaciones:**
    * **Migración a I2C:** Cambio del driver L298N por **Grove I2C Motor Driver** para reducir el uso de pines digitales y usar la librería `Grove_I2C_Motor_Driver.h`.
    * **Lógica de Prioridad:** Implementación de un algoritmo de control robusto con `else if` y `else` final de seguridad.
    * **Gestión de Hardware:** Uso de pines 11, 12 y 13 para los sensores.

#### 📂 Código Final del Proyecto
<details>
<summary><b>Haz clic aquí para ver el código completo del Sprint 3</b></summary>

```cpp
#include "Grove_I2C_Motor_Driver.h"

#define I2C_ADDRESS 0x0f
#define PinSI 13
#define PinSD 12
#define PinSC 11

#define MOTOR_IZQ MOTOR1
#define MOTOR_DER MOTOR2

#define LINEA LOW
#define SUELO HIGH

void avanzar() {
 Motor.speed(MOTOR_IZQ, 200);
 Motor.speed(MOTOR_DER, -200);
}

void girarIzquierda() {
 Motor.speed(MOTOR_IZQ, 100);
 Motor.speed(MOTOR_DER, -200);
}

void girarDerecha() {
 Motor.speed(MOTOR_IZQ, 200);
 Motor.speed(MOTOR_DER, -100);
}

void parar() {
 Motor.stop(MOTOR_IZQ);
 Motor.stop(MOTOR_DER);
}

void setup() {
  
  Motor.begin(I2C_ADDRESS);
  pinMode(PinSI, INPUT);
  pinMode(PinSC, INPUT);
  pinMode(PinSD, INPUT);

/*
  pinMode(MOTOR_IZQ, OUTPUT);
  pinMode(MOTOR_DER, OUTPUT);
*/

  Serial.begin(9600);
}

void loop() {

  int izq = digitalRead(PinSI);
  int cen = digitalRead(PinSC);
  int der = digitalRead(PinSD);
  
  if (cen == LINEA) {
    avanzar();
  }
  else if (izq == LINEA) {
    girarIzquierda();
  }
  else if (der == LINEA) {
    girarDerecha();
  }
  else{
    parar();
  }
}
