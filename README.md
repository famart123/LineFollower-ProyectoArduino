# 🤖 Proyecto Arduino: Robot Seguidor de Línea (Line Follower)

Este es el proyecto para la Asignatura de **Programación Informática en Arduino**, realizado por:
* **Fernando Andrés Martínez Ekame**
* **Thiago Damian Rios Garcete**

> **Estado del Proyecto:** 🟡 En desarrollo (Sprint 3)

---

## 🛠️ Lista de Materiales

Componentes necesarios para el prototipo completo (basado en el diseño de [Luis Llamas](https://www.luisllamas.es/curso-arduino-intermedio/)).

### 1. Control
* 1x Placa Arduino UNO R3

### 2. Sensores
* 2x Módulos Sensores Infrarrojos (TCRT5000) o Módulo de 3 sensores.

### 3. Chasis y Movimiento
* 1x Kit de Chasis 2WD (Motores DC + Ruedas)
* 1x Rueda loca (Caster wheel)
* 1x Controlador de Motores: **Driver L293D** (Simulación) / **L298N** (Montaje real).

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
* [cite_start]**Objetivo:** Control de actuadores, modularización, uso de funciones y arrays.
* **Logros Técnicos:**
    * Implementación de **funciones propias** para el movimiento: `avanzar()`, `retroceder()`, `parar()`.
    * Control de motores mediante **Driver L293D** en simulación Tinkercad.
    * Separación de la lógica de movimiento del bucle principal (`loop`).
* **📂 Código:** [Ver Código del Sprint 2](./Sprint_2/sprint2_motores.ino)

**📸 Evidencia del Circuito (Tinkercad):**
*(Aquí va tu captura de pantalla mostrando el Arduino conectado al chip L293D y los motores)*
<img width="742" alt="Simulación Sprint 2" src="https://github.com/user-attachments/assets/8e418a30-8ad8-41d3-93da-62f8fa905dcc" />

---

### ⏳ Sprint 3: Integración Final
* **Fecha límite:** 12 de Diciembre.
* [cite_start]**Objetivo:** Integración hardware-software, optimización y eficiencia energética[cite: 16].
* **Estado:** Pendiente.
