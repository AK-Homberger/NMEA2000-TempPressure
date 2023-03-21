# NMEA2000 Temperature and Pressure
This repository shows how to  measure temperature and barometric pressure with a BMP280 sensor and send it to NMEA2000 network.

![Schematics](https://github.com/AK-Homberger/NMEA2000-TempPressure/blob/master/NMEA2000%20Barometer.png)

The BMP280 measures temperature and barometric pressure. Small PCBs can be bought from Adafruit or AZ-Delivery for example.

The data is sent to NMEA2000 network with PGN130310 (Outside Environmental Parameters)

The wiring is detailled in the schematics avove. 

The project requires the NMEA2000 and the NMEA2000_esp32 libraries from Timo Lappalainen: https://github.com/ttlappalainen. Both libraries have to be downloaded and installed.

For the BMP280 the Adafruit BMP280 library has to be installed via the library manager.

The ESP32 in this project is an ESP32 NODE MCU from AzDelivery. Pin layout for other ESP32 devices might differ.

For the ESP32 CAN bus, I used the "Waveshare SN65HVD230 Can Board" as transceiver. It works well with the ESP32. The correct GPIO ports are defined in the main sketch. For this project, I use the pins GPIO4 for CAN RX and GPIO5 for CAN TX.

The 12 Volt is reduced to 5 Volt with a DC Step-Down_Converter (D24V10F5).

If you want to use an BME280 device, you can have a look to NMEA2000 Workshop examples: https://github.com/AK-Homberger/NMEA2000-Workshop/tree/main/Software

# Remove the 120 ohm resistor from the transceiver
For unknown reasons, many CAN bus transceivers for the ESP32 have a 120 Ohm resistor built into them. The resistor does not belong to the devices at the ends of the stub lines, but to the ends of the backbone cable.

Whether the transceiver contains a 120 ohm resistor can be determined either by looking at the [circuit diagram](https://github.com/AK-Homberger/NMEA2000-Workshop/blob/main/Docs/SN65HVD230%20CAN%20Board_SCH.pdf) or by measuring with the multimeter.

A knife tip is suitable for removing the SMD resistor. Use it to scratch or pry off the resistance. With the transceiver shown here, place the tip of the knife in front of the resistor (between the chip and the resistor) and support the knife against the chip. Then lever the tip against the resistance and use it to scratch / loosen / break the resistance. Whichever happens first.

![Transceiver](https://github.com/AK-Homberger/NMEA2000WifiGateway-with-ESP32/blob/master/CAN-Transceiver.jpg)

It then looks like the picture. Then measure to be on the safe side. Without a 120 ohm resistor, the multimeter shows approx. 75 kOhm.

# Partlist:

- ESP32 [Link](https://www.amazon.de/AZDelivery-NodeMCU-Development-Nachfolgermodell-ESP8266/dp/B071P98VTG/ref=sxts_sxwds-bia-wc-drs3_0?__mk_de_DE=%C3%85M%C3%85%C5%BD%C3%95%C3%91&cv_ct_cx=ESP32&dchild=1&keywords=ESP32) 
- SN65HVD230 [Link](https://www.amazon.de/SN65HVD230-Board-Connecting-Communication-Development/dp/B00KM6XMXO/ref=sxts_sxwds-bia-wc-drs1_0?__mk_de_DE=%C3%85M%C3%85%C5%BD%C3%95%C3%91&cv_ct_cx=SN65HVD230&dchild=1&keywords=SN65HVD230&pd_rd_i=B00KM6XMXO&pd_rd_r=0000ea9b-16c8-4bfc-bb40-b71623633214&pd_rd_w=VecN7&pd_rd_wg=VRb2Q&pf_rd_p=578deb70-f9b7-4aa5-9f96-98765f2717c8&pf_rd_r=H8X4ND0GD8MN6WH9H17A&psc=1&qid=1601309172&s=industrial&sr=1-1-5a42e879-3844-4142-9c14-e77fe027c877)
- D24V10F5 [Link](https://eckstein-shop.de/Pololu-5V-1A-Step-Down-Spannungsregler-D24V10F5)
- BMP280 [Link](https://www.amazon.de/AZDelivery-GY-BMP280-Barometrischer-Sensor-Luftdruckmessung/dp/B07D8TPVVY/ref=pd_sbs_147_2/259-6242313-7239601?_encoding=UTF8&pd_rd_i=B07D8TPVVY&pd_rd_r=861715eb-e73a-4649-8083-0988facd096a&pd_rd_w=yjvNN&pd_rd_wg=uFEZp&pf_rd_p=a03ac387-6e4d-4f6b-96b6-1853da0bb37b&pf_rd_r=844VMA0JWNDXKX5R4Z5A&psc=1&refRID=844VMA0JWNDXKX5R4Z5A)
- PCB universal set [Link](https://www.amazon.de/70Stk-Doppelseitig-Lochrasterplatte-Kit-Lochrasterplatine/dp/B07BDKG68Q/ref=sr_1_6?adgrpid=70589021505&dchild=1&gclid=EAIaIQobChMI07qXtuaN7AIVjentCh3xPg80EAAYASAAEgK_-_D_BwE&hvadid=352809599274&hvdev=c&hvlocphy=9043858&hvnetw=g&hvqmt=e&hvrand=11402952735368332074&hvtargid=kwd-300896600841&hydadcr=26892_1772693&keywords=lochrasterplatine&qid=1601363175&sr=8-6&tag=googhydr08-21)


