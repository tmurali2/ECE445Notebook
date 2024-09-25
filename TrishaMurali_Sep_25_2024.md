Name: Trisha Murali <br/>
Date: 09/25/2024

# Circuit Diagram Prep 

## Specifics of Parts (Humidity + Lights) 
### Stepper Motor: Adafruit: 918, Digikey: 1528-1367-ND <br/>
- 5V-12V DC suggested operation
- Connect red to ground, orange and pink to one motor port (say M1) and blue and yellow to the other motor port (say M2). In this case, the motor ports can be connected to the microcontroller.
- Orange and pink (power)
- PA0/PA1 on microcontroller?

### Light Sensor: Adafruit LTR-329 Light Sensor - STEMMA QT / Qwiic
- Power -> Active -> Check status (reg 0x8C) [keep checking status if no new data) -> read data -> MCU actions
- 0x8C: status register (data valid bits B7, B2 bit depending on old data/new data) -> read data (high or low)




