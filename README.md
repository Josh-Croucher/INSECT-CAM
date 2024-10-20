# Project Description
This project aims to create a wireless camera streaming system that can attach the back of an insect. It will use an ESP32 and WiFi to stream the video to a computer connected to the same network.

# Instructions
In it's current state, the system is quite easy to use. There are 3 components that are required.
- Pololu 5V Step-Up Voltage Regulator U1V10F5
- Esp32 CAM
- A small 1S lipo with dupont connectors soldered onto it

NOTE: The ESP32 CAM used has the breakout pins flipped so that they point out the same side as the camera connector. **As a result, do not directly plug the board into the programmer!**
To wire everything up, the Battery positive is plugged into the **VIN** on the regulator, and the negative plugged into a **GND** Pin on the ESP32. The **VOUT** of the regulator must then be plugged into the **5V** on the ESP32, and the **GND** of the regulator connected to a **GND** on the ESP32.

## Programming
As mentioned above, the board cannot be plugged directly into the programmer. Instead, the **GND/R**, **U0R**, **U0T**, **I01** and **5V** pins must be connected to the programmer using jumper wires.
When programming the board, it must be put into programming mode. To do this, hold in the **I01** button down, and then press the **RST** one, this will change the mode. Once programmed, the **RST** button can be hit again to switch back.

## Streaming video
Once the board is connected, it will act as an access point and create a network named *ESP-CAM-NETWORK*. Connect to this and go to *192.169.4.1* in a browser, where the video will be streaming.
NOTE: The board normally chooses 192.168.4.1, however, this is not a hard coded value, and it will output it's IP Address over the Serial Monitor upon start up. Hence, if there are issues with the stream not loading at the address, but you are successfully connected to the network, check this.

# Known Issues
As the current system exists as a proof of concept, there exists many bugs and irregularities. These are:
## Visual artifacts in the stream
There may be lines that appear on the stream, these do not significantly effect the quality of the stream but are notable and will be fixed in later iterations.
## Stream droppping out
Sometimes the stream can drop out, this is normally fixed by reloading the web page.
