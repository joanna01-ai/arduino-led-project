# 💡 Arduino LED Blink Project

> Documented with the aid of Claude | Learning Arduino from scratch using Wokwi simulator

---

## 📋 Project Overview

My first Arduino project! Making an LED light blink using an Arduino Uno and the Wokwi browser simulator.

**Simulator used:** [Wokwi](https://wokwi.com) (browser-based, no hardware needed)

---

## 🔧 Components

| Component | Value | Purpose |
|---|---|---|
| Arduino Uno | — | The microcontroller brain |
| LED | Red | The light that blinks |
| Resistor | 220Ω | Protects the LED from too much electricity |

---

## 🔌 Wiring

| From | To |
|---|---|
| Arduino Pin 13 | One leg of the resistor |
| Other leg of resistor | Long leg (+) of LED |
| Short leg (–) of LED | Arduino GND |

> ⚠️ Always connect the resistor between Pin 13 and the LED — it protects the LED from burning out!

---

## 💻 Code

```cpp
void setup() {
  pinMode(13, OUTPUT);  // Set pin 13 as output
}

void loop() {
  digitalWrite(13, HIGH);  // Turn LED ON
  delay(1000);              // Wait 1 second
  digitalWrite(13, LOW);   // Turn LED OFF
  delay(1000);              // Wait 1 second
}
```

---

## 🧠 What Does the Code Mean?

### `void setup()`
Runs **once** when the Arduino turns on. Think of it as the "preparation" phase.

```cpp
pinMode(13, OUTPUT);
```
Tells the Arduino: *"Pin 13 is going to SEND electricity out"* — that's what OUTPUT means.

---

### `void loop()`
Runs **forever**, over and over, as long as the Arduino is on.

```cpp
digitalWrite(13, HIGH);  // Sends electricity to Pin 13 → LED turns ON
delay(1000);             // Waits 1000 milliseconds = 1 second
digitalWrite(13, LOW);   // Stops electricity to Pin 13 → LED turns OFF
delay(1000);             // Waits 1 second, then loops back
```

---

## 🧠 Simple Way to Remember It

| Term | Think of it as... |
|---|---|
| `setup()` | Getting dressed in the morning — done once |
| `loop()` | Your heartbeat — repeats forever |
| `HIGH` | Switch ON |
| `LOW` | Switch OFF |
| `delay(1000)` | Pause for 1 second |

---

## 📓 Project Logs

### log1 — [06/05/2026]
➡️ I made an LED light blink! The code above is the first working version with a 1 second blink delay.

### log2 — [06/05/2026]
➡️ Trying to make the LED blink faster. Changed both `delay(1000)` values to `delay(100)`. Now it blinks 10x faster!

## log3 — [07/05/2026]
➡️ Changed delay from 1000 to 100 — LED now blinks 
10x faster! Confirmed it works in Wokwi simulator.

```cpp
void loop() {
  digitalWrite(13, HIGH);
  delay(100);   // changed from 1000 → 100 for faster blink
  digitalWrite(13, LOW);
  delay(100);   // same as the other one
}
```

---

## 🚀 Installation (Wokwi for VS Code)

1. Install the **Wokwi for VS Code** extension
2. Press `F1` and select **"Wokwi: Request a new License"**
3. VS Code will ask you to confirm opening the Wokwi website — click **Open**
4. Click **"GET YOUR LICENSE"** (create a free account if needed)
5. Confirm sending the license back to VS Code
6. You'll see: *"License activated for [your name]"* — you're ready! 🎉

---

## 📈 Next Steps

- [ -] Make LED blink super fast (`delay(100)`)
- [- ] Add a button to control the LED
- [ ] Make the LED fade in and out
- [ ] Build a traffic light with multiple LEDs

---

log4 — [07/05/2026]
➡️ Added a pushbutton to control the LED.
Now the LED only turns ON when the button
is clicked and held. Learned about:

```cpp
digitalRead()
```

```cpp
int variables
```

```cpp
if/else statements
```

```cpp
INPUT_PULLUP
```

## **CODE:**

```arduino
void setup() {
  pinMode(13, OUTPUT);  // LED pin
  pinMode(2, INPUT_PULLUP);  // Button pin
}

void loop() {
  int buttonState = digitalRead(2);  // Read the button

  if (buttonState == LOW) {
    digitalWrite(13, HIGH);  // Button pressed → LED ON
  } else {
    digitalWrite(13, LOW);   // Button not pressed → LED OFF
  }
}
```

### 🧠 The Code Explained Line by Line

```cpp
void setup() section:
```

```cpp
cpp
```

```cpp
pinMode(13, OUTPUT);  // LED pin
```

```cpp
Same as before — tells Arduino that **Pin 13 sends electricity out** to the LED
```

```cpp
cpp
```

```cpp
pinMode(2, INPUT_PULLUP);  // Button pin
```

```cpp
**Pin 2** is where the button is connected
```

```cpp
**INPUT_PULLUP** means *"Pin 2 will RECEIVE information"* (from the button)
```

```cpp
The **PULLUP** part means the pin starts as HIGH by default and goes LOW when pressed — more on this below! 👇
```

---

```cpp
void loop() section:
```

```cpp
cpp
```

```cpp
int buttonState = digitalRead(2);
```

```cpp
**int** — creates a box to store a number (short for integer)
```

```cpp
**buttonState** — the name of that box
```

```cpp
**digitalRead(2)** — checks Pin 2 and asks *"is the button pressed or not?"*
```

```cpp
The answer gets stored in the buttonState box — either **HIGH** or **LOW**
```

---

```cpp
cpp
```

```cpp
if (buttonState == LOW) {
    digitalWrite(13, HIGH);  // Button pressed → LED ON
```

```cpp
**if** — means *"only do this IF something is true"*
```

```cpp
**buttonState == LOW** — checks if the button is being pressed
```

```cpp
If YES → turn the LED ON
```

```cpp
💡 Why LOW means pressed? Because of INPUT_PULLUP — it's a bit backwards! When button is NOT pressed = HIGH. When button IS pressed = LOW.
```

---

```cpp
cpp
```

```cpp
} else {
    digitalWrite(13, LOW);   // Button not pressed → LED OFF
}
```

```cpp
**else** — means *"if the above was NOT true, do THIS instead"*
```

```cpp
So if button is NOT pressed → turn LED OFF
```

---

### 🔄 The whole flow in plain English:

1. Setup — *"Pin 13 sends power, Pin 2 receives button info"*
2. Loop forever:
    - *"Check if button is pressed"*
    - *"If yes → turn LED on"*
    - *"If no → turn LED off"*
    - *"Repeat forever"*

---

*Built by a complete beginner ✨ | Started 06/05/2026*
