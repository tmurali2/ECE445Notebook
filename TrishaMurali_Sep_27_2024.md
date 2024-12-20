Name: Trisha Murali <br/>
Date: 09/27/2024

# Updated Block Diagram Paragraphs 
We are writing the design doc and after several reviews of the system block diagram, we have come to a final version. The design doc needs to be updated on the final paragraphs in relation to this: <br/>

![image](https://github.com/user-attachments/assets/53e34620-baf4-4f9a-9613-9f384853f76d)

Note: The block diagram descriptions below are in relation to the picture above. 

The block diagram (Figure 5) details the different subsystems for The Smart Plant Pot. Our hydroponics solution/device can be split into 6 primary subsystems: power, control and UI, water and nutrients, humidity, grow lights, and oxygenation. The power subsystem will work with a 12V wall adapter. To power the parts particular to each subsystem, the appropriate voltage step-down/buck converter will be used, i.e., the 12V to 3.3V or the 12V to 5V. This will be based on each subsystem’s individual supply voltage range and amperage. 

The water and nutrient subsystem has a Total Dissolved Solids (TDS) sensor, providing us with the concentration of dissolved nutrients in the water. As shown in Figure 1, the nutrients will be supplied using a sprayer wand. The analog output from the TDS sensor feeds into the STM32, giving constant feedback on the current amount of dissolved solids in the water. If this number is too low (low amount of nutrients), the necessary 5V will power the sprayer wand to inject more nutrients. Along with the sprayer, there is a main water reservoir temperature sensor and extra water reservoir temperature sensor, and these simply communicate with the STM32 using the Dallas 1-wire protocol. The data from both sensors will be evaluated to ensure that they fall within a temperature range that would not cause damage to the plants. The float switch’s digital output will feed into the microcontroller, ensuring that the water levels are not too low/high. If it is too low/high, the primary hydroponics tank/pot will be refilled/pumped out with the help of the sump pump controlled via digital output from the STM32. These sump pumps along with water level and water temperature sensors will be powered using the 3.3V step-down converter and turned on/off with MOSFET switches. 

The grow lights subsystem has a light sensor (powered by 3.3V) to measure the amount of light received by the plant in a 24 hour period. This data is sent to the STM32 via I2C protocol. If the light received is too little, a signal from the STM32 will feed into the stepper motor driver chip (powered with 5V), which will drive the stepper motor to open the shades (and vice versa if it’s above the range). To prevent damage to the plants, the pre-made grow lights (powered with 5V) will also be turned on or off if the amount of light exposure is considerably out of the range. 

The humidity subsystem uses a humidity sensor (powered with 3.3V) to track the humidity levels within the Smart Pot enclosure. Using I2C communication protocol, the STM32 receives and interprets data from this sensor. This data will be used to actuate the servo motor (powered with 5V) to adjust the vents or the fan to ventilate the enclosure. 
The oxygenation subsystem ensures healthy air circulation for the plant. A 5V-powered air pump is used to power the air stone, which oxygenates and agitates the water in the hydroponics pot setup to prevent bacteria/algae growth. The air pump/stone will be run continuously, while the fan will be controlled using a MOSFET switch (similar to the other subsystems). 

Finally, the Control and UI subsystem has the STM32 microcontroller, which as detailed, is the heart of the Smart Pot. It interprets all sensor data and provides the digital signals to specify actuator control in each subsystem. To increase the ease-of-use of this product, a TFT LCD will be used to show all real time sensor data and maintenance alerts in the case of any necessary manual intervention. Communication between the LCD and STM32 will be done via SPI protocol. A rotary encoder will allow the user to look through a preset list of plants that can be grown in the pot and specify the type to be grown. This will output a digital signal to the microcontroller. 

**Signature: Trisha Murali**
