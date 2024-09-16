Name: Trisha Murali <br/>
Date: 09/04/2024 <br/>
# Final RFA (Meeting 3) 
# Smart Plant Pot

**Team Members**
- Morgan Sukalo (msukalo2)<br/>
- Trisha Murali (tmurali2)<br/>
- Gavin Tian (gtian3)<br/>

# **Problem**

Growing plants in any capacity is a maintenance intensive task and requires a lot of varying inputs and knowledge to accomplish successfully. Automating this process would be a step in automating agriculture in a controlled environment.

# **Solution**

Our solution is to build a hydroponic plant pot that can sustain and grow a plant from sprout or one that has been transplanted while automating all the processes associated with hydroponic plant care. It will have a variety of sensor and actuator based subsystems that perform action items related to hydroponic maintenance. We will then have a central control unit which will interpret all gathered data, and ensure an optimized growth environment. The user will be able monitor the current status of the plant and its environment via the UI subsystem. This system will display sensor data from every other subsystem, report issues requiring more intensive maintenance, and display existing conditions of the plant (example: humidity levels, water temperature, water levels), ultimately making hydroponic agriculture more user-friendly.

# **Solution** Components
*Diagram of System*
https://drive.google.com/file/d/1SQtptcK4uriIv2zN9ECVHA81-U5mPIS0/view

*Humidity Subsystem*
Most house plants need a humidity between 50-60% to protect against transpiration, and tropical plants require a higher humidity than this. The humidity subsystem will maintain a desired humidity level given the type of plant being grown and will consist of a variety of sensors/actuators to do so.

* We will have a humidity sensor (SHT35-DIS-F) which will constantly monitor the humidity within the Smart Pot. For the specified plant, this humidity will have to stay within a certain range, and the sensor will monitor this.
* On top of the clear lid for the pot, there will be an adjustable vent operated by a motor that will remain slightly open at all times to allow for air circulation, but if there is ever conditions that are not ideal to the plant (ex: humidity too high), the opening of the vent will adjust accordingly (ex: open up more to air out the plant if needed).
* All data will be sent to the central control unit. If the humidity is too low, a humidifier will be turned on until a desired humidity level is reached within the Smart Pot enclosure.
* If the humidity is too high, the vent at the top of the Smart Port enclosure will open wide, allowing for some of the gaseous water to escape (lowering humidity).

* SENSOR: humidity sensor for Smart Pot enclosure.
* ACTUATOR: humidifier, servo motor for vent @ top of enclosure
* CONTROL UNIT BEHAVIOR:

If the humidity is too high: open vent via servo motor

If humidity too low: turn on humidifier

*Oxygenation Subsystem*
For hydroponics, water needs to be oxygenated and agitated to facilitate plant growth and impede algae and bacteria.

* An air stone attached to a pump will be placed in the Smart Pot to continuously agitate the water.
* A small fan will be integrated into the side of the Smart Pot lid. This fan will push out the old air from inside of the enclosure.
* An air vent at the top of the Smart Pot enclosure will always be slightly open to allow fresh air into the enclosure. Closing/opening the air vent will be controlled by a servo motor. If the Smart Pot enclosure needs to be aired out, the vents can open wide.
* This system will be connected to the central control unit. The central control unit will allow the air stone to remain on all of the time. The fan will be turned on/off throughout the day as needed.

* SENSOR: n/a
* ACTUATOR: air stone, fan attached to wall of Smart Pot lid, servo motor for vent @ top of enclosure
* CONTROL UNIT BEHAVIOR:

The air stone will always be running.

The fan will only run during set intervals enforced by the control unit.

If airing-out of the Smart Pot is needed, the servo motor attached to the vents will be actuated to maximize Smart Pot air release.



*Grow Lights Subsystem*
As we know, plants require sunlight for growth. During winter, the amount of sunlight and other environmental factors a plant receives may not always be ideal. To offset this and provide for plant growth despite the season, we will be using grow lights.

* As part of this subsystem, we will also have light sensors to keep track of the amount of light the plant receives during a 24hr span. If this value ever becomes too high, the control unit will ensure that the LED growth light is off, and shades to shield the plant from light will be raised. If the control unit detects that the plant did not receive enough light, the LED growth light will be turned on for some amount of time until the light exposure requirement is fulfilled.

* SENSOR: light sensor for plant
* ACTUATOR: LED grow light (pre-made), shades with stepper motor
* CONTROL UNIT BEHAVIOR:

If the value tracked by light sensors become too high, grow light is turned off and shades move to cover the plant

If plant did not receive enough light, the LED grow light will be turned on and the shades will be moved out



*Water and Nutrient Subsystem*
Automated hydroponics requires a water and nutrient module to ensure water stability and sufficient nutrient levels. To deter algae and bacteria growth, water changes will need to be made every two weeks to ensure an optimized growth environment. This subsystem will monitor water level and water temperature.

* This is a gravity-based system and will include a water reservoir canister, a waste canister, and one nutrient canister.
* The water reservoir canister, nutrient canister and waste canister will be connected to the Smart Pot via 12V solenoid valves. Opening these valves will allow for the contents of one container to flow into the other.
* The water level of the Smart Pot will be monitored via a float switch (PLS-041A-3PAI), and a temperature sensor (DFR0198) will be used to observe the temperatures of the Smart Pot water and the water reservoir canister.
* If the water level falls below a specified threshold, the water reservoir temperature will be compared to the Smart Pot water temperature. If so, the valve connecting the water reservoir canister to the Smart Pot will be opened, and the Smart Pot will be filled to the desired level.
* Every two weeks, the water in the Smart Pot will be drained. Prior to draining, the temperature of the Smart Pot water and the water reservoir will be compared. If these values are similar, draining will commence.
* While the valve between the water reservoir and the Smart Pot remains closed, the valve between the Smart Pot and the waste canister will open when draining begins. All water from the Smart Pot will flow into the waste canister. This valve will then close, and the Smart Pot is refilled with freshwater from the water reservoir. Nutrients are then injected into the Smart Pot.

* SENSOR: temperature sensors, water level sensor (float sensor)
* ACTUATOR: Valves that are between all canisters and the Smart Pot
* CONTROL UNIT BEHAVIOR: will keep track of time passes since last water change, monitor water temperatures and water level. Will control when valves open/close.


*User Interface Subsystem*
The User Interface is a helpful feature for the users to track the environment of the plant.

* The user interface will allow the user to specify what plant type the user is currently trying to grow in the Smart Pot. These plant types will be displayed on a TFT LCD (DFR0664) and can be selected using a rotary encoder (PEC11R-4115F-S0018). Once selected, this information goes to the control unit, and all desired humidity levels, pH levels, light levels, etc. are set. The user interface will also display real time data coming from all of the sensors listed above. This gives the user information on the current status of their plant’s environment in the Smart Pot. In addition to this, any maintenance alerts will be displayed. This is where any alerts concerning manual overrides or human intervention will show. The overall idea here is that the rotary encoder will be used to browse through these different selections and the push button feature will be used to select an option.

* SENSOR: rotary encoder with push button feature
* ACTUATOR: TFT LCD screen to display real time temperature, humidity, etc. specs of Smart Pot
* CONTROL UNIT BEHAVIOR: display hydroponic plant types, plant status/stats, warning and alerts for the user



*Power Subsystem:*
The power subsystem aims to take wall power and convert it to voltages that are safe and usable for all sensors/actuators/devices that are needed to keep the Smart Pot up and running.

* The power system comprises a custom PCB with a step down IC, 12V DC wall adapter.
* The wall adapter is currently under contention as the amperage needs of the project need to be determined to pick the correct product.
* The PCB will route 12V and limit to the solenoids that control water flow as those require the highest voltage. It will also step down 12V to 3.3V DC for the microcontroller and sensors.

* SENSOR: n/a
* ACTUATOR: 12V, 3.3V, GND power rails
* CONTROL UNIT BEHAVIOR:

Step down voltages and supply power to all the subsystems

# **Criterion** For Success
The Smart Pot subsystems prove individual functionality as well as collaborative functionality. Ultimately, the Smart Pot will be able to sustain all subsystems and care for the plant for 4 weeks without human intervention.

To test, we want to check that all systems respond accurately and appropriately to their related sensor stimuli. The sensor readings themselves should match real life conditions in a reasonable manner and will be displayed on a UI for easy monitoring.
