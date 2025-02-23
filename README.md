# RGB LED Animation with Arduino 🎨💡

An **Arduino** project to control an **RGB LED** with smooth color transitions using **PWM (Pulse Width Modulation)**.


## 📜 Description
This project demonstrates how to control an **RGB LED** using **Arduino Uno**, smoothly transitioning between colors. The project explores:
- **PWM control for LED brightness**
- **Common Anode vs. Common Cathode LED configurations**
- **Hue-to-RGB conversion for dynamic colors**

## 🚀 Getting Started
### 🔧 Components Required
- ✅ Arduino Uno
- ✅ RGB LED
- ✅ 330Ω Resistors (x3)
- ✅ Jumper Wires & Breadboard
- ✅ USB Cable

### 🔌 Circuit Diagram
![Circuit Diagram](Circuit_Diagram.png)

### 💻 Code
The Arduino sketch controls the RGB LED colors using **hue-based color mixing**.

```cpp
// Define RGB LED Pins
int rpin = 11;
int gpin = 10;
int bpin = 9;
float h = 0;
int r = 0, g = 0, b = 0;

void setup() {
    pinMode(rpin, OUTPUT);
    pinMode(gpin, OUTPUT);
    pinMode(bpin, OUTPUT);
}

void loop() {
    h = h + 0.005;
    if (h >= 1.0) h = 0;
    h2rgb(h, r, g, b);

    // Common Anode Adjustment
    analogWrite(rpin, 255 - r);
    analogWrite(gpin, 255 - g);
    analogWrite(bpin, 255 - b);

    delay(20);
}
