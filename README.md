# NMEA2000-TempPressure
This repository shows how to  measure temperature and barometric pressure with a BMP280 sensor and send it to NME2000 network.

![Schematics](https://github.com/AK-Homberger/NMEA2000-TempPressure/blob/master/NMEA2000%20Barometer.png)

The BMP280 measures temperature and barometric pressure. Small PCBs can be bought from Adafruit or AZ-Delivery for example.

The data is sent to NMEA2000 network with PGN130310 (Outside Environmental Parameters)

The wiring is detailled in the schematics avove. 

The project requires the NMEA2000 and the NMEA2000_esp32 libraries from Timo Lappalainen: https://github.com/ttlappalainen. Both libraries have to be downloaded and installed.

For the BMP280 the Adafruit BMP280 library has to be installed via the library manager.

The ESP32 in this project is an ESP32 NODE MCU from AzDelivery. Pin layout for other ESP32 devices might differ.

For the ESP32 CAN bus, I used the "Waveshare SN65HVD230 Can Board" as transceiver. It works well with the ESP32. The correct GPIO ports are defined in the main sketch. For this project, I use the pins GPIO4 for CAN RX and GPIO5 for CAN TX.

The 12 Volt is reduced to 5 Volt with a DC Step-Down_Converter (D24V10F5, https://www.pololu.com/product/2831).

