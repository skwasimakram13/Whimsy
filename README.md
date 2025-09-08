<img align="center" src="https://i.ibb.co/JRQH7Dg2/Whimsy.gif" width="200" />

# Whimsy
A cute 2-wheeled dancing robot that plays music and delivers a personalized voice message.
---

## 📌 Project Overview
This project builds a **small, affordable robot** (under ₹5K INR) that:  
- Moves on **2 wheels + 1 caster wheel**.  
- Plays a **cute song** when powered on.  
- Dances by moving forward, backward, left, and right.  
- Speaks a **personalized recorded message**:  
  👉 *“This is your personal robot, built with love by Wassu.”*  

A perfect **DIY gift robot** for fun, learning, or surprising loved ones ❤️.  

---

## 🛠 Hardware Requirements
| Component | Qty | Approx Price (INR) |
|-----------|-----|--------------------|
| Arduino Uno / Nano | 1 | ₹500–800 |
| L298N Motor Driver | 1 | ₹300 |
| DC Gear Motors + Wheels | 2 | ₹500–600 |
| Caster Wheel | 1 | ₹100 |
| DFPlayer Mini MP3 Module | 1 | ₹250 |
| MicroSD Card (8GB) | 1 | ₹300 |
| Speaker (3W/5W) | 1 | ₹200 |
| Li-ion Battery Pack (7.4V) + Switch | 1 | ₹500–700 |
| Robot Chassis Kit (or DIY) | 1 | ₹500 |
| Jumper Wires & Screws | — | ₹200 |
| (Optional) RGB LEDs | — | ₹100 |

**💰 Total Cost:** ~ ₹3K–4K INR  

---

## 🧑‍💻 Software Requirements
- **Arduino IDE** (latest version)  
- **Arduino Libraries**:
  - `SoftwareSerial.h`  
  - `DFRobotDFPlayerMini.h`  

---

## 📂 Project Structure
```
Whimsy/
│
├── code/
│   └── dancing_robot.ino       # Arduino sketch
│
├── hardware/
│   ├── wiring_diagram.png      # Circuit connections
│   ├── chassis_design.png      # Robot body design (optional)
│
├── sounds/
│   ├── 0001.mp3                # Cute song
│   └── 0002.mp3                # Voice message: "This is your personal robot, built with love by Wassu."
│
├── docs/
│   ├── README.md               # Full project description
│   └── roadmap.md              # Step-by-step roadmap
│
└── LICENSE
```

---

## ⚡ Wiring Diagram
| Module | Arduino Pins | Notes |
|--------|-------------|-------|
| L298N Motor IN1, IN2 | D5, D6 | Motor A control |
| L298N Motor IN3, IN4 | D9, D10 | Motor B control |
| L298N VCC, GND | +7.4V, GND | Battery power |
| DFPlayer Mini RX/TX | D10, D11 (via SoftwareSerial) | Audio control |
| DFPlayer Mini VCC, GND | +5V, GND | Power |
| DFPlayer Mini Speaker L/R | Speaker +/– | Audio output |

*(See `hardware/wiring_diagram.png` for visual guide.)*  

---

## 🎵 Audio Setup
1. Record your **voice message** on phone:  
   👉 *“This is your personal robot, built with love by Wassu.”*  
2. Save as `0002.mp3`.  
3. Save your chosen **cute song** as `0001.mp3`.  
4. Copy both files to **microSD card**.  
5. Insert card into **DFPlayer Mini**.  

---

## 🧑‍💻 Example Arduino Code
```cpp
#include <SoftwareSerial.h>
#include <DFRobotDFPlayerMini.h>

SoftwareSerial mySerial(10, 11); // RX, TX
DFRobotDFPlayerMini myDFPlayer;

int motor1A = 5, motor1B = 6;
int motor2A = 9, motor2B = 10;

void setup() {
  pinMode(motor1A, OUTPUT);
  pinMode(motor1B, OUTPUT);
  pinMode(motor2A, OUTPUT);
  pinMode(motor2B, OUTPUT);

  mySerial.begin(9600);
  myDFPlayer.begin(mySerial);
  myDFPlayer.volume(25);

  delay(1000);
  myDFPlayer.play(1); // Play cute_song.mp3
}

void loop() {
  // Dancing pattern
  forward(); delay(500);
  back(); delay(500);
  left(); delay(500);
  right(); delay(500);

  static unsigned long lastTime = millis();
  if (millis() - lastTime > 10000) { // after 10 sec
    myDFPlayer.play(2); // Play voice_message.mp3
    while(true); // stop further movement
  }
}

void forward() { digitalWrite(motor1A, HIGH); digitalWrite(motor1B, LOW); digitalWrite(motor2A, HIGH); digitalWrite(motor2B, LOW); }
void back()    { digitalWrite(motor1A, LOW); digitalWrite(motor1B, HIGH); digitalWrite(motor2A, LOW); digitalWrite(motor2B, HIGH); }
void left()    { digitalWrite(motor1A, LOW); digitalWrite(motor1B, HIGH); digitalWrite(motor2A, HIGH); digitalWrite(motor2B, LOW); }
void right()   { digitalWrite(motor1A, HIGH); digitalWrite(motor1B, LOW); digitalWrite(motor2A, LOW); digitalWrite(motor2B, HIGH); }
```

---

## 🚦 Roadmap
### Phase 1 – Hardware Setup
- Buy all components.  
- Assemble chassis (2 wheels + caster).  
- Mount Arduino, motor driver, speaker, battery.  

### Phase 2 – Wiring
- Connect **DC motors** → L298N → Arduino.  
- Connect **DFPlayer Mini** → Arduino TX/RX + speaker.  
- Connect **Battery** → Arduino & motor driver.  

### Phase 3 – Programming
- Upload Arduino code:
  - Play `0001.mp3` (song).  
  - Move motors in a dance sequence.  
  - After 10s, play `0002.mp3` (voice message).  

### Phase 4 – Testing
- Test motors individually.  
- Test DFPlayer separately.  
- Test combined code.  

### Phase 5 – Personalization
- Record your voice message.  
- Decorate robot with colors, stickers, LEDs.  

### Phase 6 – Delivery
- Gift-wrap it 🎁  
- Switch ON → Dancing robot surprise ❤️  

---

## 🎀 Future Improvements
- Bluetooth control (via HC-05).  
- Mic + voice commands (mini Jarvis).  
- Add servos for waving hands.  
- Add small OLED screen for robot “eyes.”  

---

## Badges
[![trophy](https://github-profile-trophy.vercel.app/?username=ryo-ma)](https://github.com/ryo-ma/github-profile-trophy)

---

## Author
**Develope By** - [Sk Wasim Akram](https://github.com/skwasimakram13)

- 👨‍💻 All of my projects are available at [https://skwasimakram.com](https://skwasimakram.com)

- 📝 I regularly write articles on [https://blog.skwasimakram.com](https://blog.skwasimakram.com)

- 📫 How to reach me **hello@skwasimakram.com**

- 🧑‍💻 Google Developer Profile [https://g.dev/skwasimakram](https://g.dev/skwasimakram)

- 📲 LinkedIn [https://www.linkedin.com/in/sk-wasim-akram](https://www.linkedin.com/in/sk-wasim-akram)

---

## 🤝 Contribution

Pull requests, feature suggestions, and bug reports are welcome.

---

## 📜 License
This project is open-source under the **MIT License**.  

---

💡 *Built with ❤️ and creativity by Wassu.*
