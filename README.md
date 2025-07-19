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

```bash
pip install flask gtts aiml

🔧 Wiring Diagram
1. MAX9814 → ESP32
MAX9814 Pin	ESP32 Pin	Function
VCC	3.3V	Power supply
GND	GND	Ground
OUT	GPIO 34	Analog mic input
