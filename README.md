# Edifier-MR4-Remote-Control
This project turns Edifier MR4 studio monitors into smart speakers by adding remote control via Home Assistant using the ESP32-C6 and ESPHome. (Thread)

Features
Since the MR4 is controlled by a single physical knob (encoder and button), this controller simulates key presses and monitors the device's status via LEDs:

• Remote On/Off: Simulates a long press (2 seconds).

• Mute Control: Simulates a short press.

• Mode Switching (Music/Monitor): Automatic double scroll/tap to select an equalizer preset.

• State Feedback: The controller accurately knows whether the speakers are on and which mode is active by reading signals from the built-in LEDs via optocouplers.

• Thread Support: Using the ESP32-C6 allows integration into the modern Thread network.

**Features**

Since the MR4 is controlled by a single physical knob (encoder and button), this controller simulates key presses and monitors the device's 
status via LEDs:

• Remote On/Off: Simulates a long press (2 seconds).

• Mute Control: Simulates by a short press.

• Mode Switching (Music/Monitor): Automatic double scroll/mtap to select an equalizer preset.

• State Feedback: The controller accurately knows whether the speakers are on and which mode is active by reading signals from the built-in LEDs via optocouplers.

• Thread Support: Using the ESP32-C6 allows integration into the modern Thread network.

**Hardware**

• The project is based on the ESP32-C6-DevKitC-1.

• Optocouplers are used to interface with the speaker electronics without risk of damage.

Connection diagram (logic):
• Output: GPIO20 controls the optocoupler, which "presses" the encoder button.

• Inputs: GPIO19 and GPIO18 read the state of the red and green front panel LEDs (via optocoupler).

**Software**
The configuration implements complex signal filtering logic:

• delayed_off / delayed_on: Used to stabilize the status so that the LED "blinking" during switching does not cause false triggers in Home Assistant.

• Template Switch: Separate switches for power and mute mode.

• Template Select: Convenient drop-down menu for choosing between "Monitoring" and "Music" modes.
