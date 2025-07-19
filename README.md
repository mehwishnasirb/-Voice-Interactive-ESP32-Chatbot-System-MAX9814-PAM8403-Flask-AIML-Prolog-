# 🎙️ Voice-Interactive ESP32 Chatbot System (MAX9814 + PAM8403 + Flask + AIML)

This project builds a **real-time, voice-controlled AI chatbot** using:
- **ESP32** microcontroller
- **MAX9814** microphone (voice input)
- **PAM8403** amplifier (audio output)
- **Flask** + **AIML + Prolog** AI server (intelligence)

It mimics Alexa/Google Assistant behavior on low-cost hardware. Voice queries are captured, sent to a server, processed for meaning and logic, then converted to speech and played through a speaker.

---

## 🚀 Key Features

### 📱 Hardware Integration
- 🎤 Voice Input via **MAX9814 Analog Microphone**
- 📡 Audio transfer from **ESP32 to Flask Server** (HTTP POST)
- 🔊 Audio Output using **I2S DAC** and **PAM8403 Amplifier**
- 🔁 Serial Monitor logs for debugging

### 🧠 AI & Logic
- 💬 AIML Chatbot Brain (`.aiml`)
- 🧠 Prolog Inference Engine (`relations_prolog.pl`)
- 🔊 Text-to-Speech using **gTTS**
- 🧬 Multi-type Memory: Semantic, Sensory, PAM (Procedural/Autobiographical)
- ⚙️ Flask APIs handle audio/text exchange with ESP32

---

## 📂 Project Structure
VoiceChatbot/
├── app.py # Flask Web Server
├── server.py # Audio processing & routing
├── chatbot_module.py # AIML + Prolog chatbot logic
├── bot_brain.brn # AIML compiled brain
├── pam_memory.aiml # Procedural memory
├── semantic_memory.aiml # Factual memory
├── sensory_memory.aiml # Perception layer
├── prolog.aiml # Prolog interface
├── relations_prolog.pl # Prolog logic rules

---

## 🎛 ESP32 Firmware

### Functions:
- Records voice via MAX9814 (analog input)
- Sends audio to Flask server as POST request
- Receives Base64 WAV audio in response
- Plays audio using DAC (GPIO 25) or I2S + MAX98357 → PAM8403
- Logs actions in Serial Monitor

---

## 🧰 Requirements

### 🔌 Hardware
| Component         | Purpose                      |
|------------------|------------------------------|
| ESP32-WROOM      | Main microcontroller         |
| MAX9814          | Analog mic for voice input   |
| PAM8403 / MAX98357| Audio amplifier/I2S DAC     |
| 4Ω 3W Speaker     | Voice output                 |
| Breadboard + Wires| Circuit wiring              |

### 🖥 Software
- Arduino IDE + ESP32 Board
- Python 3.8+
- Flask, gTTS, aiml libraries


## 🔌 Wiring Diagrams

### 2A. ESP32 → MAX98357A (I2S DAC Output) → PAM8403 → Speaker

If you're using the MAX98357A DAC to convert digital audio to analog before amplification:

| MAX98357A Pin | ESP32 Pin | Description        |
|---------------|-----------|--------------------|
| VIN           | 5V        | Power              |
| GND           | GND       | Ground             |
| DIN           | GPIO 25   | I2S Data Line      |
| BCLK          | GPIO 26   | Bit Clock          |
| LRC           | GPIO 22   | Word Select (WS)   |

➡️ Connect **MAX98357A output (L/R)** to **PAM8403 input**, then to the speaker:

| PAM8403 Pin | Connection            |
|-------------|------------------------|
| IN+         | MAX98357A L or R out   |
| IN–         | GND                    |
| OUT+ / OUT– | Speaker (4Ω 3W)        |

---

### 2B. ESP32 → PAM8403 Direct (Analog DAC Output)

If you're skipping I2S and using ESP32's built-in DAC to output analog audio directly:

| ESP32 Pin  | PAM8403 Pin | Description               |
|------------|-------------|---------------------------|
| GPIO 25    | IN+         | DAC1 analog audio out     |
| GND        | IN–         | Ground (audio reference)  |
| 5V         | VCC         | Power supply to amplifier |
| GND        | GND         | Common ground             |
| OUT+ / OUT–| Speaker     | Audio output terminals     |

🛑 **Important:** Only GPIO 25 and GPIO 26 support DAC on the ESP32.

---

### 🧰 Summary of Required Components

| Component         | Purpose                               |
|------------------|----------------------------------------|
| ESP32 Dev Board   | Core microcontroller                  |
| MAX9814 Microphone| Captures voice                        |
| MAX98357A (Optional)| I2S DAC for better audio output    |
| PAM8403 Amplifier | Amplifies analog audio signal         |
| 4Ω 3W Speaker     | Plays AI-generated responses          |
| Jumper Wires      | Circuit wiring                        |
| Breadboard        | Prototype circuit layout              |

