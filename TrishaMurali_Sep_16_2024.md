Name: Trisha Murali <br/> 
Date: 09/16/2024 <br/> 

# Rough Draft 2 of Project Proposal (Meeting 6)
Note: Project Proposal is almost done. Just waiting on TA Feedback and Machine Shop Feedback <br/>
<br/>







<p align="center">
ECE 445 Smart Pot Plant Proposal <br/>
Team 3 <br/>
Morgan Sukalo, Gavin Tian, Trisha Murali <br/>
TA: Surya Vasanth <br/>



## Introduction<br/>
Growing indoor plants can help with the environment as well as provide a method to growing food quickly and sustainably. However, without the proper knowledge base and constant attention, plants can quickly die or become a chore to take care of. Switching to a hydroponics approach can fix some of these problems, primarily the ambiguity of soil nutrients. However, there are new challenges posed such as water reservoir temperature, proper root aeration, and automatic top off and purging. These issues require constant manual labor maintenance. Automating these based on different stimuli can be a proof of concept for scaling this for general purpose agriculture.

## Solution <br/>
We want to create, what we are calling, The Smart Plant Pot. Our solution is based on the technique of hydroponics. We will be eliminating the meticulous caretaking that growing plants normally necessitates, that is, our solution will require little to no human intervention. Our solution will monitor the temperature, humidity, light, and water levels concerning the plant and ensure that it is within the necessary range for a particular plant type. We will have a TFT LCD and an easy-to-use rotary encoder displaying hydroponic plant options that the user can easily peruse and pick from. 

We will have a humidity control system with adjustable vents, a fan for careful air circulation to maintain the humidity levels necessary for the plant. Our device will automatically calibrate the settings based on the plant type and the humidity sensor that will be monitoring real-time data. We will also have a temperature system closely monitoring the temperature of the water along with a water-level sensor to track our Smart Plant Pot’s water reservoirs, which will be filled/drained depending on when it is due for either. For the lights, we will be using grow lights, considering our solution focuses on houseplants. These grow lights and our device’s adjustable shades will be tuned according to the data from the light sensor in concert with how much light a plant needs. All of the plant stats will be recorded and displayed on the TFT LCD for the user. We will also have a maintenance alert system in the case that manual intervention becomes necessary, but our sensors and our in-built automatic systems will be used to surveil the plants/plant-growth at all times. 

## Visual Aid: <br/>
![GetFileAttachment](https://github.com/user-attachments/assets/9b8e8fb2-58e2-4414-9406-ff00ec192a37)

## High-level requirements list
1. The system should be able to measure data from all of the sensors at any time, and keep track of the amount of time since a device was last actuated. UI needs to reflect data tracked within the last minute.
2. The Smart Pot actuators should respond to sensor stimuli within <1 minute. Stimuli linked to actuation will be specified in subsystem requirements.
3. The Smart Pot should have the ability to change actuation configuration from the user interface either via preset configurations based on the plant or manual adjustment.

## Design Block Diagram <br/> 
![Screenshot 2024-09-16 191806](https://github.com/user-attachments/assets/1cbd470b-f053-4756-890d-2377c033851f)






# Subsystem Overview:
## Power:
The power subsystem ensures that every other subsystem receives a uniform supply voltage. Due to the fact that the Smart Pot is stationary with a goal of needing minimal user assistance, a constant power supply is needed. As such, wall power will be utilized. A power adapter will convert the 120V from the outlet to 12V that the water/nutrient subsystem solenoid valves and grow lights subsystem stepper motor may use. This 12V will also be an input to two step-down voltage regulator ICs; one of which performs a 12V to 3.3V conversion, while the other is 12V to 5V. The 5V will power the servo motors within the oxygenation/humidity subsystems as well as the air pump within the oxygenation subsystem. The 3.3V will power the rest of the devices in the Smart Pot (STM32, LCD, temperature sensors, etc.). RC circuits will be employed to filter out power supply noise for the 12V, 5V and 3.3V sources, and fuses will be used to protect the rest of the system from surge currents. The STM32 will also monitor its power supply and can send warnings to the user interface subsystem if the voltage were to ever dip too low. 


## Control/UI: 
The Control and UI subsystem houses the microcontroller(STM32), TFT LCD, and rotary encoder. The STM32 will be supervising all of the different subsystems by taking in the sensor readings and sending out digital GPIO to control the actuators in each subsystem. In this subsystem alone, the STM32 will communicate with a TFT LCD to display a user interface allowing the user to both view the sensor readings and make changes to actuation thresholds. A rotary encoder will be used to control the user interface. Rotation will manipulate selection and the inbuilt button switch will select the currently selected item. This system will have an enclosure holding the 3 components and allow for IO wires to go to each of the systems. A PCB will need to be made with the STM32 chip to facilitate power flow to the sensors as well as make the headers of the STM32 GPIO available for use with ports.


## Humidity:
The humidity subsystem tracks the humidity levels of the plant’s environment/enclosure, thereby controlling the associated device settings to allow for better air circulation to either increase or decrease the humidity. Different plant types at different stages of their growth require certain levels of humidity. For instance, if the chosen hydroponic plant type was Spinach, it would require 40%-70%. Maintaining the numbers between this range is important for the healthy growth of Spinach. This will be attained by recording real-time data of the humidity levels with a humidity and temperature sensor (SHT35-DIS-F). If the levels are too high, our device will adjust the vents. This will be tuned using a servo motor (SER0011). Once the ideal humidity level is reached, the vents will maintain this level by closing in. The fan from the oxygenation system will also assist in maintaining these levels. It will circulate the air out of the enclosure, getting rid of some of the moist air. Once a measurement within the range necessary for the specific hydroponic plant type is achieved, the fan will be turned off and the vents will be closed. In terms of its behavior and interaction with other subsystems, the humidity sensor will communicate with the STM32 by sending and receiving relevant humidity. This will be done using I2C. If a value within the ideal range is detected, everything will remain as is. If this is not the case and the value is higher than the given range, the servo for the enclosure vent will be powered and the STM32 will send a signal to open the vents and fan out the air. If the value is lower than the range, it will close up any open vents and turn the fans off. 

## Nutrient/Water:
The water and nutrient subsystem allows for water monitoring and maintenance to be automated. The first part is the topping off and water change system. A reserve reservoir will be kept alongside with the main reservoir that the plant sits atop of. We will use room temperature water to initially fill the main reservoir and apply nutrient solution according to what's specified on the bottle. A TDS reading will be taken and saved. From then on the system will take in a temperature reading of both reservoirs and determine if there is a significant temperature difference. If the temperatures are largely equal, the main reservoir will be topped off as the nutrient water is consumed. A timer for 3 weeks will be set and once the timer expires, a valve inside the main reservoir drains into a drainage basin for disposal. The reserve reservoir drains its water and fills the main reservoir with fresh water and a motor driven spray bottle head sprays nutrients in the system.  Along with this automatic nutrient system, the TDS sensor(SEN0244) will be used to monitor the Total Dissolved Solids in the water. If the TDS drops by a significant amount the motorized spray bottle will spray to drive the TDS to a nominal value. 


## Oxygen:
The oxygenation subsystem oxygenates and agitates the hydroponic water to facilitate plant growth and impede algae and bacteria. It also ensures constant air flow within the Smart Pot enclosure, protecting the plant from rot and mold. To perform these operations, an air stone attached to an air pump will be inserted into the Smart Pot water. A fan will be incorporated into the side of the Smart Pot enclosure, and air vents controlled via a motor will be located at the top (of the enclosure). The air stone will continuously run, while the fan and air vent will be turned on/opened on a timed basis. The control unit (STM32) will send a signal to the fan and air vent motor when the air in the enclosure should be refreshed. This will turn the fan on and open the enclosure vents for some time, followed by then shutting off/closing again. Note that the fan and air vent are also considered a part of the humidity subsystem, and aid in lowering enclosure humidity if it ever is too high. Also, aside from being connected to the power subsystem and control subsystem, the oxygenation subsystem is standalone. 

## Lights:
The grow lights subsystem plays multiple roles in plant care. Not only do grow lights help expose the plant to the required light but they also produce heat. This subsystem is straightforward in that our device will use pre-made grow lights. The type of plant will determine how much light is necessary along with how much light the plant has already received, which will be data gathered by the light sensor (LTR-329). For instance, Spinach requires 12 hours of light per day along with a temperature of 60-70 degrees Fahrenheit. This subsystem will ensure that this happens. Balancing a cooler temperature while shining grow lights that produce heat can be a difficult optimum to reach. This is where the shade comes into the picture. Based on the data, the STM32 will provide a signal to the stepper motor (1528-1367-ND) for the shades to provide coverage for the plants. While the device will have an actuator turning the lights off after 12 hours, will also be providing for a shade to be able to attain a balance of receiving the necessary amount of light while also maintaining temperatures and keeping the enclosed environment cool. Essentially at some points, just because the temperature is too high, the device will not turn the lights off. We have fans for air circulation and a shade to help maintain a cool environment as well. The shade is a component exclusive to the grow lights subsystem, but since all of these environment factors go hand-in-hand, the other subsystems will work together to attain the necessary balance. 


# Subsystem Requirements: 
## Power:
- The power subsystem must convert wall power to 12V+/-0.1V, approx 3A as calculated from current draw for all system devices. 
- The 12V to 3.3V step down voltage regulator IC needs to supply 3.3V+/-0.1V with a max of 1.2A. This value was calculated from the maximum current drawings of all devices powered by the 3.3V rail. 
- The 12V to 5V step down voltage regulator IC needs to supply 5V+/-0.1V with a max of 0.53A. This value was calculated from the maximum/necessary current drawings for the motors, fan and air pump attached to it. 
- Fuses with max current ratings of 1.2A and 0.53A will be placed in series with the 3.3V and 5V power supplies respectively. 
## Control/UI:
- The rotary encoder will control a user interface and a user interface will be displayed onto the TFT LCD.
- The STM32 will take in sensor readings and time as well to produce outputs for the actuators
- Data from the sensors will be able to be displayed on the TFT LCD
- A enclosure will be made to house the encoder, LCD, and STM32
## Humidity:
- The SHT35-DIF-F sensor constantly provides data on humidity levels
- The STM32 being able to interpret this information and communicate with the servo motors and actuator for the fan appropriately to dissipate humidity
- Desired humidity level is maintained with the subsystem actuators

## Nutrient/Water:
- Water will drain every 3 weeks and be replenished, alarm or notification will be sent if water isn't fully replenished. Drainage and replenishment cycle will occur if both reservoirs have similar temps. Nutrients will spray during this replenishment period
- Water temperature for both reservoirs, TDS, and pH will be recorded and trigger alarms
- When the float switch is cut and both reservoirs have similar temps, meaning that the water level drops below normal, the system will be able to top off the main reservoir with the reserve reservoir.
- When the TDS of the main reservoir is significantly decreased, the system should auto replenish nutrients with a sprayer.
## Oxygen:
- Air pump should continuously run while the system is powered on.
- The fan should be actuated when the STM32 directs it to do so.
- The motor to control the vent position should be able to both open and close the vent. 
## Lights:
- 1528-1367-ND light sensor and MCU will be able to adjust actuation thresholds based on preconfigured settings or manual configuration
- STM32 is able to utilize timer and light sensor data in order to actuate the grow light on and off
- Servo Motor shade is able to shade the plant to prevent excessive sunlight by using an light sensor array





## Risk Analysis: 
The most difficult portion of the project is the nutrient and water subsystem. This is because the system contains the most variables to control for as well as being the basis for plant growth and the project itself. The nutrient sprayer will be something difficult to mechanically design as it is based on an off-the-shelf sprayer head. In addition, dialing in nutrients is difficult as there is a risk of rendering the water toxic. An acceptable tolerance for the temperature between reservoir water and main reservoir temperature should be between 65-77 degrees. Since this will be an indoor system, the water temperature would not be a big issue unless the reservoir water came out of a tap. In that case the water will sit until it reaches that temperature threshold.  
## Tolerance Analysis: 
The power subsystem poses the greatest risk to the successful completion of this project. Supplying too little or too much power can damage the system, so calculations must be done to ensure that this does not happen. 
To start, the voltages needed to supply the system are 12V, 5V and 3.3V. The necessary currents drawn from these voltages are calculated based on the devices that need to be powered by these rails. These devices are listed below, as well as their current ratings. 


![Screenshot 2024-09-16 192143](https://github.com/user-attachments/assets/fdc30671-1409-4200-96c1-51f679de74dd)



Some of the devices (such as the motors and temperature sensors) do not give current ratings (or power ratings) on their data sheets - only voltage ratings. This being said, research was conducted to estimate the current rating for these devices. Either devices with similar specifications or other projects involving these products online were referenced. <br/>
I<sub>max for 3.3V</sub>=250A +1500A+120mA+29mA+1A+2(40mA) = 1.23A<br/>
I<sub>max for 5V</sub>=0.2A+3(40mA)+0.25A = 0.57A<br/>
I<sub>max for 12V</sub>=[1.23A]+[0.57A]+2(320mA)+0.7A = 3.14A<br/>
The 12V to 3.3V voltage step down component needs to produce around 1.23A of current, while the 12V to 5V regulator will need to produce around 0.57A of current in order to power all of the devices connected to them. These are relatively large current values, so using a divider or voltage regulator will need to be decided based on which of these can handle the currents. This enforces the need for a 12V, 3A power adapter to attach to the wall power supply. <br/>
After defining the specifications needed for each component in the power subsystem, it is important to think about tolerances when it comes to connecting each subsystem to power. This pertains to trace diameters and n-channel MOSFETs (which are used to turn on/off motors and open/close the valves. 
The diameter of a trace depends on the current passing through it. The IPC standard for trace width and current for only a 10*C temperature rise is 50mils for 3A, 30 mils for 2A and 10mils for 1A. These IPC recommendations should be followed when mapping the power subsystem. <br/>

## Ethics and Safety
Assess the ethical and safety issues relevant to your project. Consider both issues arising during the development of your project and those which could arise from the accidental or intentional misuse of your project. Specific ethical issues should be discussed in the context of the IEEE and/or ACM Code of Ethics. Cite, but do not copy the Codes. Explain how you will avoid ethical breaches. Cite and discuss relevant safety and regulatory standards as they apply to your project. Review state and federal regulations, industry standards, and campus policy. Identify potential safety concerns in your project. Overall, discuss safety concerns (electrical, mechanical, lab).
## Safety: 
Safety for this project mainly revolves around the usage of high voltage AC power sources. For the Smart Pot, the power subsystem will be directly connected to an outlet. This being said, it is imperative that proper precautions are taken when interacting with this source. According to UIUC Electrical Safety policy, it is important to disconnect any power sources before providing maintenance to a system. In the case of the Smart Pot, this means unplugging the power subsystem from the wall every time PCB manipulation is required. Doing so eliminates the possibility of a person coming in direct contact with the outlet power supply. This recommendation is also repeated by OSHA, while adding that properly insulated tools should also be used when working with these sources. <br/>

Working with high voltage power sources poses an increased risk when doing so around water, which is the case for the Smart Pot. This being said, it is important to ensure that all water canisters/containers are properly maintained and sealed such that the possibility of leaks is minimized. This is an industry standard, as seen through most laboratories being a “No Food, Not Drinks Allowed” space (emphasis on the “No Drinks”). This is especially echoed here at UIUC, especially in the ECE 385, ECE 391 and ECE 486 laboratories. Note that in these labs, water bottles (which are sometimes permitted) are required to have a sealed top to protect any power sources from coming in contact with their contents. As one can see, water and power do not (and should not) mix, which means precautions will have to be taken when working on the Smart Pot system. Systemwide leakage surveys should be conducted prior to powering on the Smart Pot to eliminate the risk of water damage and electric shock. If water leakage is spotted, the Smart Pot should immediately be disconnected from power, and the area thoroughly cleaned. <br/>

The last area of concern revolves around the mishandling of liquid nutrients. Though they are used by millions of people every day, it is important to remember that they are chemicals and should be handled with care. Most liquid plant fertilizers contain nitrogen; this is great for facilitating plant growth, however when exposed to in large amounts, it can cause skin redness, irritation, or lack of oxygen to parts of the body. This being said, following Federal chemical handling guidelines would be a great way to keep anyone who needs to handle liquid nutrients safe. According to OSHA, proper PPE must be worn when working with chemicals. This includes gloves, safety goggles, etc. This rule is seconded by UIUC, where the use of fume hoods are also recommended. With this being said, our group will need to hold each other accountable for ensuring proper PPE use when handling liquid nutrients. <br/>

## Ethics: 
This project sets the stage for automated farming in the future, and with it brings ethical dilemmas. First and foremost, there is the concern that the Smart Pot can be used to grow plants to create illicit substances. Plants such as cannabis, coca and opium poppy can be used to create drugs like cocaine and morphine (which are often abused). With the current design of the Smart Pot, there is no way to inhibit a user from growing these plants with one of our devices. By making plants easier to grow, the Smart Pot could possibly increase drug production and support a criminal trade. The IEEE Code of Ethics states that the safety, health and welfare of the public is paramount and that unlawful conduct should be avoided. This however begs the question: how can we protect against the misuse of the Smart Pot? Well, if the Smart Pot were to ever become commercial, background checks could be conducted on consumers interested in purchasing it. Not only this, but in future versions computer vision can be implemented to recognise the type of plant being grown in the Smart Pot, and if this plant falls under a restricted category, the Smart Pot will cease growing the plant. Protecting the consumer is of the utmost importance, and ensuring that this technology is not used for wrong is imperative. <br/>

The last ethical issue of the Smart Pot is the impact it could have on working class families. To elaborate further, if all farming becomes autonomous in the future, then many individuals who work on farms as laborers could possibly lose their jobs. The IEEE Code of Ethics emphasizes avoiding conflicts of interests when it comes to new technologies, and this situation is clearly a conflict of interest with respect to this demographic of workers. If the Smart Pot were to ever make it to market and be largely commercialized, free classes could be offered to teach these laborers a new skill set - maintaining this new technology. While farming technology evolves, the jobs associated with it will evolve too. <br/>


## Citations and References 
Sources for safety/ethics: <br/>
https://www.osha.gov/laws-regs/regulations/standardnumber/1910/1910.132#:~:text=Protective%20equipment%2C%20including%20personal%20protective,of%20hazards%20of%20processes%20or<br/>
https://www.healthline.com/health/fertilizers-and-household-plant-foods#causes<br/>
https://drs.illinois.edu/Page/SafetyLibrary/ElectricalSafetyInTheResearchLaboratory<br/>
https://www.osha.gov/laws-regs/regulations/standardnumber/1910/1910.269_2#:~:text=The%20employer%20shall%20ensure%20either,item%20or%20apparatus%20under%20test.
https://www.autodesk.com/products/fusion-360/blog/trace-width/<br/>


Lights section: <br/> https://www.gardeningknowhow.com/edible/vegetables/spinach/growing-spinach-using-hydroponics.htm<br/>

Humidity section: <br/> https://greg.app/spinach-humidity/#:~:text=Dialing%20in%20the%20Perfect%20Humidity%20for%20Spinach&text=Aim%20for%20a%20relative%20humidity,fungal%20diseases%20to%20a%20feas<br/>

**Signature: Trisha Murali**








