Name: Trisha Murali <br/>
Date: 11/05/2024

# Soldering 
Once the TFT LCD and LTR-329 came in, I realized that they did not come in with wires, so I had to order: BOJOUL for 20 Sets JST SH 1.0mm 4 Pin Male Connector and 28AWG Female Connector Plug with Wire Cable 20cm Used in PCB Toys Household Appliances etc, Brand: BOJOUL. This was the same issue that Morgan ran into as she was working on the humidity and temperature sensor at the same time. While waiting, however, I soldered the header pins in case they took a while to arrive. As for the LCD, we wanted to avoid using the SPI cable since we thought that simplified the process and wanted to do more on our own. After soldering the pins and now having received the LCD and light sensor in person. I looked into how this could be integrated with the rest of the project. 

The plan at this point: 

As mentioned in the Design Document, the type of plant being grown will determine how much light is necessary. The light sensor (LTR-329) will be used to track the amount of light the plant has received in a 24-hour period, and this will be stored in the STM32’s flash memory. The sensor data will be communicated using I2C protocol. The appropriate connection labels can be seen in Figure 13 and Figure 18. The SCL pin is an I2C serial clock input and the SDA is an I2C serial data input/output pin. According to the datasheet, there’s a read bit that has to be set in order to access the data. Once the data has been read, the status bit is set to 0 to prevent a repeated read of the same data [7].

The connectors for the sensor was not provided as part of the order (JST SH 4-pin to Premium Male Headers), so I placed these later and I am currently waiting on it, but I have written out the logic and defined the exposure threshold values (ex: actuation upon < 12 hours of light) complying with what was mentioned previously, adhering to the I2C communication. 

The TFT LCD, as part of the breakout board, comes with the ability to use SPI cables. Prior to soldering the header pins, I used this to display options/text onto the LCD. This LCD was smaller than I expected it to be, so the number of pages the user would click through has increased. Ideally, a rotary encoder would be used to scroll through (turn) and select (click/press down). Since this is being tested by another group member, an alternative solution using buttons (up and down and “select”) was used. Here, the up and down buttons are to flip between the pages (go forward/backward). This is set up with 5 manual plant types – Spinach, Kale, Celery, Chives, and Oregano. All of these fall within the PPM range described above. If selected, the plant statistics from the LTR-329 are set to display for the associated plant type. Finally, any maintenance alerts, also based on the float switch, are displayed. 

![image](https://github.com/user-attachments/assets/cc18155c-c32b-4183-a746-29cea32d1e31)

References: 

[7] “Optical Sensor Product Data Sheet LTR-329ALS-01,” LITEON Optoelectronics, Mar. 2020. Available: https://cdn-shop.adafruit.com/product-files/5591/LTR-329ALS-01-Lite-On-datasheet-140998467.pdf

**Signature: Trisha Murali**
