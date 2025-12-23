# Camera-shutter-measuring-device
This device is dedicated to verifying the proper functioning of the shutters of film cameras.
This MicroPython program is designed for the **Raspberry Pi Pico** (specifically using the Pimoroni Pico Display) to function as a **Digital Shutter Speed Tester**. It allows photographers and camera collectors to verify the accuracy of analog camera shutters using a photodiode.

Hardware need
 Raspebry Pico
 Pico Display
 Photo resistor GL5528
 Resistor 10kHom
 
---

## Technical Overview

The program utilizes a photodiode connected to the Pico's **ADC0 (GP26)** to detect light. It measures the time elapsed between the moment the light intensity exceeds a user-defined threshold and the moment it falls back below it.

### Key Technical Features:

* **High-Precision Timing:** Uses `time.ticks_us()` to capture shutter speeds with microsecond accuracy.
* **Persistent Storage:** Automatically saves and loads your preferred **backlight brightness** and **light threshold** settings to the Pico's internal flash memory (`.txt` files).
* **Real-time Feedback:** Displays the current light level, the set threshold, and the last measured speed in seconds.
* **Optimized Rendering:** Uses the `PicoGraphics` library with a 4-bit palette to minimize RAM usage and ensure smooth UI updates.

---

## User Manual

### 1. Hardware Setup

1. Connect a **photodiode** to the Raspberry Pi Pico (Signal to **GP26**, and appropriate VCC/GND).
2. Mount the photodiode behind the camera's film plane.
3. Position a bright light source (like a torch or lamp) in front of the camera lens.

### 2. Controls & Navigation

The program uses the four buttons (A, B, X, Y) found on the Pimoroni Pico Display:

| Button | Main Screen Function | Settings Menu Function |
| --- | --- | --- |
| **A** | None | Increase Value (+) |
| **B** | Enter **Backlight Settings** | Decrease Value (-) |
| **X** | **Refresh** Screen | **Exit** & Save |
| **Y** | Enter **Threshold Settings** | N/A |

### 3. How to Measure a Shutter Speed

1. **Start:** Power on the device. Press any button on the "Home Page" to enter the main measurement screen.
2. **Calibrate:** Check the "Lumiere" (Current Light) value. It should be low when the shutter is closed and high when a light is shone through the lens.
3. **Set Threshold:** Press **Y**. Adjust the threshold until it is roughly halfway between the "Dark" and "Light" values you observed. Press **X** to save.
4. **Fire Shutter:** Trigger your camera's shutter.
5. **Read Results:** The screen will update "Vitesse" (Speed) showing the duration in seconds (e.g., `0.0020 s` for 1/500th).

### 4. Adjusting Display Brightness

If the screen is too bright or too dim:

1. Press **B** on the main screen.
2. Use **A (+)** or **B (-)** to change the backlight level.
3. Press **X** to save and return.

### 5. Troubleshooting

* **"Attente..." stays on screen:** The light did not cross the threshold. Ensure your light source is bright enough or lower the threshold.
* **Screen seems frozen:** Press **X** on the main screen to force a manual refresh of the display buffer.
* **Values not saving:** Ensure your Pico has enough free space for the small `.txt` configuration files.

Would you like me to explain how to convert the decimal results (like 0.008s) into standard photographic fractions (like 1/125)?
