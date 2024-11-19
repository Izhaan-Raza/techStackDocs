

## **AI Thinker NodeMCU Ai-WB2-13: Documentation**

The **AI-WB2-13** module by AI Thinker is a compact, high-performance NodeMCU development board powered by the Bouffalo Lab's **BL602 chip**. It supports **Wi-Fi** and **Bluetooth LE (BLE)**, making it suitable for IoT and AI-enabled applications.

---

### **1. Board Overview**
#### **Key Features**
- **Microcontroller:** BL602 (32-bit RISC-V CPU, 384KB RAM)
- **Wireless Communication:**
  - Wi-Fi: IEEE 802.11b/g/n
  - Bluetooth 5.0 LE
- **GPIO Pins:** 11 GPIOs with multiple functions
- **Interfaces:**
  - UART, SPI, I2C, PWM, ADC
  - I2S for audio processing
- **AI Features:**
  - Lightweight AI support for edge ML models (e.g., TensorFlow Lite Micro).
- **Operating Voltage:** 3.3V

#### **Pinout Diagram**
[Insert a pinout diagram here, showcasing GPIOs, power pins, UART, SPI, etc.]

---

### **2. Initial Setup**
#### **Hardware Requirements**
- AI-WB2-13 NodeMCU Board
- Micro USB cable (data-capable)
- Computer with USB drivers installed
- Breadboard and jumper wires (optional for external components)

#### **Software Requirements**
- Python (3.7 or higher)
- BL602 SDK or Arduino IDE
- UART Debug Tool (e.g., **PuTTY** or **TeraTerm**)
- Firmware flashing tool (e.g., **BLFlash**)

---

#### **Step 1: Install Drivers**
1. **Windows/Linux:**
   - Download and install the CH340 USB-to-serial driver (if required).
2. **macOS:**
   - Use built-in drivers or install them via Homebrew if needed.

#### **Step 2: Set Up SDK/IDE**
- **Option 1: BL602 SDK (Recommended)**
  - Clone the BL602 SDK:  
    ```bash
    git clone https://github.com/bouffalolab/bl_iot_sdk.git
    cd bl_iot_sdk
    ./tools/setup.sh
    ```
  - Build and flash example firmware:
    ```bash
    cd customer_app/bl602_demo
    make
    make flash
    ```

- **Option 2: Arduino IDE**
  1. Install the **BL602 board support** in Arduino IDE.
  2. Open Arduino IDE, go to **File > Preferences**, and add this URL:  
     `https://github.com/bouffalolab/bl_iot_sdk/releases/download/board-support/package_bl602_index.json`
  3. Install the board from the Board Manager.

#### **Step 3: Connect and Test**
1. Connect the board via USB.
2. Open a serial monitor at `115200 baud rate`.
3. Test with a "Hello World" example:
   ```cpp
   void setup() {
       Serial.begin(115200);
       Serial.println("Hello, AI-WB2-13!");
   }
   void loop() {}
   ```

---

### **3. Flashing Firmware**
1. Enter bootloader mode:
   - Press and hold the **BOOT** button while powering the device.
2. Use **BLFlash** or similar tools:
   ```bash
   ./blflash flash -p /dev/ttyUSB0 -f firmware.bin
   ```

---

### **4. AI Applications**
#### **Edge AI Frameworks**
- **TensorFlow Lite Micro (TFLM):**
  - Run small ML models directly on the device for tasks like gesture recognition or audio classification.

#### **Example: ML Inference**
1. Install TFLM on your BL602 device using the SDK.
2. Create and train a TensorFlow model (e.g., MNIST digit recognition).
3. Convert it to a `.tflite` model and load it onto the device:
   ```cpp
   // Pseudo-code for inference
   tflite::MicroInterpreter model(...);
   model.AllocateTensors();
   model.Invoke();
   int result = model.output(0);
   ```

#### **Voice Commands with AI-WB2-13**
- Integrate **speech-to-text** modules for simple command recognition.
- Connect an external microphone to the I2S interface for audio input.

#### **IoT with AI**
- Use AI-based anomaly detection models to monitor sensor data (e.g., temperature, motion, etc.).
- Implement real-time predictions on data streams with Wi-Fi-enabled cloud connectivity.

---

### **5. Troubleshooting**
#### **Common Issues**
1. **Serial Port Not Detected:**
   - Ensure drivers are installed and use a working USB cable.
2. **Flashing Errors:**
   - Check BOOT mode and ensure the correct firmware.
3. **Wi-Fi/Bluetooth Connection Fails:**
   - Verify the SSID/password or BLE pairing setup.

---

### **6. Additional Resources**
- **Datasheet and Documentation:**  
  [AI Thinker Ai-WB2-13 Datasheet](https://docs.ai-thinker.com)
- **BL602 SDK:**  
  [GitHub Repo](https://github.com/bouffalolab/bl_iot_sdk)
- **Arduino IDE Support:**  
  [Board Installation Guide](https://www.arduino.cc)

---

This documentation provides a strong foundation for getting started with the AI-WB2-13 board and exploring AI and IoT applications. Let me know if you need additional resources!