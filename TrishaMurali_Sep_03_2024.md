Name: Trisha Murali <br/>
Date: 09/03/2024 <br/> 
# RFA Planning (Meeting 2)<br/> 

The Smart Pot is a hydroponic based solution to our problem. It will consist of a rectangular pot and a clear lid (not a flat lid, but one with height). It will have many subsystems, most of which will be sensor/actuator based. We will then have a central control unit which will interpret all gathered data, and ensure an optimized growth environment. A user interface will be included with the Smart Pot, where the user can specify the type of plant being grown within the Smart Pot.<br/> 

### Humidifier/Dehumidifier Subsystem: <br/> 
- Option 1: https://sensirion.com/products/catalog/SHT35-DIS-F<br/> 


- Option 2: https://www.digikey.com/en/products/detail/sensirion-ag/SHT35-DIS-B10KS/14322753?<br/> utm_adgroup=&utm_source=google&utm_medium=cpc&utm_campaign=PMax%20Shopping_Product_High%20ROAS%20Categories&utm_term=&utm_content=&utm_id=go_cmp-20222717502_adg-_ad-__dev-c_ext-_prd-14322753_sig-CjwKCAjw59q2BhBOEiwAKc0ijba1TcZARP6X747d08II0WZLXDlN10U_gFPdBFIxPsX4AbG4DndK3xoCXKQQAvD_BwE&gad_source=1&gclid=CjwKCAjw59q2BhBOEiwAKc0ijba1TcZARP6X747d08II0WZLXDlN10U_gFPdBFIxPsX4AbG4DndK3xoCXKQQAvD_BwE

- Why: Most house plants need a humidity between 50-60%, and tropical plants need a value higher than this to protect against transpiration.<br/> 
- On top of the clear lid for the pot, there will be an adjustable vent operated by a motor that will remain slightly open at all times to allow for air circulation, but if there’s ever conditions that are not ideal to the plant, the opening of the vent will adjust accordingly (ex: open up more to air out the plant if needed). This vent will be a part of the humidity control system.<br/>  
- We will have a humidity sensor which will constantly monitor the humidity within the Smart Pot. For the specified plant this humidity will have to stay within a certain range, and the sensor will monitor this.<br/>  
- All data will be sent to the central control unit. If the humidity is too low, a humidifier will be turned on until a desired humidity level is reached within the Smart Pot enclosure. <br/> 
If the humidity is too high, the vent at the top of the Smart Port enclosure will open wide, allowing for some of the gaseous water to escape (lowering humidity). <br/> 

### Oxygenation Subsystem: <br/> 
- Why: For hydroponics water needs to be oxygenated such that the plants can use this for healthy growth. Oxygen helps plants absorb water and nutrients. <br/> 
- An air stone will be placed in the Smart Pot to continuously oxygenate the water. An air pump will need to be connected to the air stone. <br/> 
- The air vent at the top of the Smart Pot enclosure will always be slightly open to allow fresh air into the enclosure. If the Smart Pot enclosure needs to be aired out (for whatever reason), the vents can open wider.<br/>
- A small fan (possibly a computer fan) will be incorporated into the side of the Smart Pot lid. This fan will push out the old air inside of the enclosure.<br/>
- This system will be connected to the central control unit. The central control unit will allow the air stone to remain on all of the time. The fan will be turned on/off throughout the day as needed.<br/>

### Grow lights: 
- Why: Plants need light to photosynthesize, but too much light or too little light can kill the plant. 
For the lights, we can either buy pre-made lights that are cheaper or SMT horticulture LEDs that can be placed on a PCB (more expensive). We need to decide which route to go with. The LEDs give us more flexibility, however there is less possibility of error with using the pre-made lights.<br/>
- Shading: Along with a timer controlled grow light, we also want to prevent the plant from receiving any extra light 
Light sensor will need to be used to detect the amount of sunlight the plant is getting every day. This data will be sent to the main control unit. If the plant did not receive enough light during the day, turn on the LEDs for some amount of time. If the plants are receiving too much light, ensure that the LEDs are off and engage plants shades. <br/>
  
Note: Option 1, 2, 3 - Low wattage (may not be enough according to hydroponics system on amazon b/c they have one that’s 24W) so check out Option 4 for similar grow lights 

Light sensor:<br/>
- https://www.digikey.com/en/products/detail/adafruit-industries-llc/5591/16733167?utm_adgroup=&utm_source=google&utm_medium=cpc&utm_campaign=PMax%20Shopping_Product_Low%20ROAS%20Categories&utm_term=&utm_content=&utm_id=go_cmp-20243063506_adg-_ad-__dev-c_ext-_prd-16733167_sig-CjwKCAjwufq2BhAmEiwAnZqw8vTTt7t84qwqNDhhxrVi0rFfNOZoV20z_cYxc7-sf1siu5umzqQI_BoClHMQAvD_BwE&gad_source=1&gclid=CjwKCAjwufq2BhAmEiwAnZqw8vTTt7t84qwqNDhhxrVi0rFfNOZoV20z_cYxc7-sf1siu5umzqQI_BoClHMQAvD_BwE<br/>


- Option 1: https://www.amazon.com/Ceiling-yadoker-Spectrum-Voltage-Dimmable/dp/B0CY1SKS24/ref=asc_df_B0CY1SKS24/?tag=hyprod-20&linkCode=df0&hvadid=692875362841&hvpos=&hvnetw=g&hvrand=4229644456219518566&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9022185&hvtargid=pla-2281435178538&mcid=7a6129a644fc36b98f2a5437690b6f4a&hvocijid=4229644456219518566-B0CY1SKS24-&hvexpln=73&th=1<br/>

- Option 2: 
https://www.amazon.com/Lights-Spectrum-Indoor-5-Level-Dimmable/dp/B085CDPSMR/ref=asc_df_B085CDPSMR/?tag=hyprod-20&linkCode=df0&hvadid=693712983265&hvpos=&hvnetw=g&hvrand=17834180270296090192&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9022185&hvtargid=pla-899642583595&mcid=c81603ebf2ea3857a28f4355223a1f88&th=1<br/>

- Option 3: https://www.amazon.com/Indoor-Bamboo-Garden-Adjustable-Automatic/dp/B0CRTNWQHP/ref=asc_df_B0CRTNWQHP/?tag=hyprod-20&linkCode=df0&hvadid=692875362841&hvpos=&hvnetw=g&hvrand=18325231426038929058&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9022185&hvtargid=pla-2281435179498&mcid=9cc187df22e0356f8cb050aac2075658&hvocijid=18325231426038929058-B0CRTNWQHP-&hvexpln=73&th=1<br/>

- Individual LEDs(Midpower blue):
https://www.digikey.com/en/product-highlight/w/wurth-electronics/led-it-grow<br/>

- Option 4: 
https://www.amazon.com/Equivalent-Bright-Spectrum-Sunlight-Greenhouse/dp/B099PN1ZY8/ref=asc_df_B099PN1ZY8/?tag=hyprod-20&linkCode=df0&hvadid=693713553286&hvpos=&hvnetw=g&hvrand=15512015799893323515&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9022185&hvtargid=pla-1414219273815&mcid=0895e6d9468f3f658dda28dfa0a2bc1d&th=1<br/>

- Hydroponics system: 
https://www.amazon.com/Hydroponics-Growing-System-Indoor-Garden/dp/B0C4LK65S6/ref=asc_df_B0C4LK65S6/?tag=hyprod-20&linkCode=df0&hvadid=693713553088&hvpos=&hvnetw=g&hvrand=18325231426038929058&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9022185&hvtargid=pla-2205435688784&mcid=a98e194baed53a5eaa50b0fe6e444889&th=1<br/>

### Water Subsystem: <br/>
- Float switch (41 mm, which is approx. 1.6 inch): we like this. <br/>
https://www.digikey.com/en/products/detail/pic-gmbh/PLS-041A-3PAI/9687300?utm_adgroup=&utm_source=google&utm_medium=cpc&utm_campaign=PMax%20Shopping_Product_High%20ROAS%20Categories&utm_term=&utm_content=&utm_id=go_cmp-20222717502_adg-_ad-__dev-m_ext-_prd-9687300_sig-EAIaIQobChMI44rE_PKoiAMVPjYIBR2TFStgEAQYAiABEgKrf_D_BwE&gad_source=1&gbraid=0AAAAADrbLlh2kuFc46Z_rzUv8gqhFD1WQ<br/>

- Detects water: 
https://www.adafruit.com/product/4965?gad_source=1&gbraid=0AAAAADx9JvT_pg5vyvs--PZdGtEXAr2W5<br/>

- Ultrasonic not made for water environments – there’s waterproof ones JSN-SR04T<br/>

- Why: water may evaporate and the plants need to consume water for growth. In addition, certain nutrients may be preferred and stripped out of the water leading to imbalances. Therefore a system is required to monitor water level, pH, temperature
This system will have 2 water reservoir canisters, one waste canister, and one nutrient canister. <br/>
- This is a gravity-based system. So, when the valve is opened between the nutrient canister and the Smart Pot, gravity will allow the nutrients to flow into the Smart Pot. <br/>
- The two water reservoir canisters will be connected to the Smart Pot via a valve, the nutrient canister will be connected to the Smart Pot via a valve, and the Smart Pot will be connected to the waste canister via a valve. Opening these valves will allow for the contents of one container to flow into the other. <br/>
- Before allowing any new water to enter the Smart Pot, the temperature of the reservoir water will need to be compared to the temperature of the Smart Pot water. If they are similar, the reservoir water can go into the Smart Pot (we are trying to eliminate temperature shock). <br/>
- This design eliminates the need for pumps and having to run long tubes throughout the house, however the water canisters will need to be manually refilled, and the waste canister manually disposed of. <br/>
- Temp sens for water:  
https://www.digikey.com.br/en/products/detail/dfrobot/DFR0198/7597054<br/>

### User Interface: <br/>
https://www.adafruit.com/product/772<br/>

https://www.amazon.com/HiLetgo-Expansion-Backlight-4-5-5-5V-Duemilanove/dp/B00OGYXN8C/ref=asc_df_B00OGYXN8C/?tag=hyprod-20&linkCode=df0&hvadid=692875362841&hvpos=&hvnetw=g&hvrand=12867897236003667265&hvpone=&hvptwo=&hvqmt=&hvdev=m&hvdvcmdl=&hvlocint=&hvlocphy=9022196&hvtargid=pla-2281435177858&psc=1&mcid=74df76aae28838a4a9b7db507fea1c89&hvocijid=12867897236003667265-B00OGYXN8C-&hvexpln=73<br/>

LCD TFT: We like this. https://www.digikey.com/en/products/detail/dfrobot/DFR0664/13166503?utm_adgroup=&utm_source=google&utm_medium=cpc&utm_campaign=PMax%20Shopping_Product_Medium%20ROAS%20Categories&utm_term=&utm_content=&utm_id=go_cmp-20223376311_adg-_ad-__dev-m_ext-_prd-13166503_sig-EAIaIQobChMIoJOJms-piAMV5kb_AR3LQRdaEAQYASABEgJOIPD_BwE&gad_source=1&gbraid=0AAAAADrbLlgDNBnFqpR3K3M6KIgTCADSO<br/>

- LCD display with buttons on the pot or the encapsulating setup<br/>
- Approximately, 5V supply <br/>
- Better option in terms of compatibility might be the LCD TFT (bit more on the expensive side) and wire a rotary encoder
- Scrolling the encoder left/right: used to select which type of hydroponics plant (herbs, spinach, other small leafy greens)<br/>
- we can also display other stats such as water level, oxygenation, humidity and notification status (alerts) <br/>
- Software depending on microcontroller: ESP32 or STM32 (prefer STM32): STM32CubeIDE — GPIO peripheral <br/>
- Some resources: https://medium.com/vicara-hardware-university/stm32-guide-gpio-and-buttons-8303e6c8cb44<br/>

### Power System: <br/>
- Need to calculate amperage estimation for each component<br/>
- Since most valves run on 12v, a 12v wall power adapter is needed, the distribution board will need to contain a 5v step down circuit for the micro electronics.<br/>
- LM2575/76 plus some misc components<br/>
- https://www.digikey.com/en/products/base-product/texas-instruments/296/LM2575/2289(12v-5v)<br/>
- https://www.digikey.com/en/products/detail/texas-instruments/LP2980IM5-3.3%2FNOPB/364529?utm_adgroup=&utm_source=google&utm_medium=cpc&utm_campaign=PMax%20Shopping_Product_Medium%20ROAS%20Categories&utm_term=&utm_content=&utm_id=go_cmp-20223376311_adg-_ad-__dev-c_ext-_prd-364529_sig-Cj0KCQjwiuC2BhDSARIsALOVfBK7aI9NKCPqD04jhD7kXE3Q_YH4gSgpmfC1PKa7r5_96yRTe63_508aAn6DEALw_wcB&gad_source=1&gclid=Cj0KCQjwiuC2BhDSARIsALOVfBK7aI9NKCPqD04jhD7kXE3Q_YH4gSgpmfC1PKa7r5_96yRTe63_508aAn6DEALw_wcB(12v-3.3v)<br/>
- Will used supplied ground from the 12v wall power adapter.<br/>

### Main Control System: <br/> 
- Will be a PCB that is connected to various sensors/actuators. This PCB will have a microcontroller on it, and this is where the main control system will reside. <br/>
- Data from all sensors will need to be interpreted and signals will need to be sent to actuators. The main control system will handle all of this. <br/>
- Humidity Subsystem: 1i2o<br/>
  - SENSOR: humidity sensor for Smart Pot enclosure<br/>
  - ACTUATOR: humidifier, motor for vent @ top of enclosure<br/>
  - CONTROL UNIT BEHAVIOR: <br/>
      If the humidity is too high: open vent via motor<br/>
      If humidity too low: turn on humidifier<br/>
- Oxygenation Subsystem: 2o(?)
  - SENSOR: n/a
  - ACTUATOR: air stone, fan attached to wall of Smart Pot lid, motor for vent @ top of enclosure
  - CONTROL UNIT BEHAVIOR:<br/>
    Air stone will oxygenate the water for good plant growth. Fan will pull fresh air into the enclosure, while the vent @ the top of the enclosure will remain slightly open to allow for old enclosure air to escape. The air stone will always be running, while the fan will only run during set intervals enforced by the control unit. <br/>
- Growth Lights Subsystem: 1i 2o<br/>
  - SENSOR: light sensor for plant<br/>
  - ACTUATOR: LED growth light (pre-made), shades<br/>
  - CONTROL UNIT BEHAVIOR: <br/>
    The light sensor will keep track of the amount of light the plant receives during a 24hr span. If this value ever becomes too high, the control unit will ensure that the LED growth light is off, and shades to shield the plant from light will be raised. If the control unit detects that the plant did not receive enough light, the LED growth light will be turned on for some amount of time until the light exposure requirement is fulfilled.<br/> 
- Water Subsystem (based on Morgan’s new idea): 3i2o
  - SENSOR: temperature sensors, water level sensor (float sensor), pH sensor<br/>
  - ACTUATOR: Valves that are between all canisters and the Smart Pot<br/>
  - https://www.adafruit.com/product/997?gad_source=1&gclid=Cj0KCQjwiuC2BhDSARIsALOVfBIGDuxtINjDYnOlPYoaa3q-eV651qHiS4VmW1M9uu9M1Xm4lfb8UTgaAu4lEALw_wcB<br/>
  - CONTROL UNIT BEHAVIOR: <br/>
    The control unit will constantly monitor the water level of the Smart Pot and the temperatures of the extra water reservoirs. <br/>
    If the water level falls below a specified threshold, the control unit will check to see if the water reservoir temperature is similar to the Smart Pot water temperature. If so, the valve connecting the water reservoir canister to the Smart Pot will be opened, and the Smart Pot will be filled to the desired level. <br/>
    The pH of the Smart Pot will be constantly monitored by the control unit, and if this value falls within an unsatisfactory range, the control unit will send a warning to the user interface. This warning will advise the user to manually clean out the Smart Pot, because high and low pH can be indicative of bacteria. Also, low pH can mean that the water has too many nutrients+bacteria. <br/>
    Every two weeks, the water in the Smart Pot will be drained. The control unit will keep track of this time, and will initiate the draining process. <br/>
   When two weeks have passed since the last draining, the temperature of the Smart Pot water and the water reservoir will be compared. If these values are similar, draining will commence. <br/>
   While the valve between the water reservoir and the Smart Pot remains closed, the valve between the Smart Pot and the Waste canister will open when draining begins. All water from the Smart Pot will flow into the Waste canister. Then, this valve is closed, and the Smart Pot is refilled with freshwater from the water reservoir. <br/>
- User Interface Subsystem: 4o(SPI), 3i<br/>
  - SENSOR: rotary encoder W/ BUTTON  to select plant type and other settings <br/>
  - ACTUATOR: TFT LCD screen to display real time temperature, humidity, etc. specs of Smart Pot<br/>
  - https://www.amazon.com/GeeekPi-Interface-Adapter-Backlight-Raspberry/dp/B086VVT4NH?source=ps-sl-shoppingads-lpcontext&ref_=fplfs&psc=1&smid=AOP0CH6UTUPHT<br/>
- CONTROL UNIT BEHAVIOR: <br/>
  The user interface will allow the user to specify what plant type the user is currently trying to grow in the Smart Pot. This plant type can be selected by using buttons. Once selected, this information goes to the control unit, and all desired humidity levels, pH levels, light levels, etc. are set. <br/>
  The user interface will also display real time data coming from all of the sensors listed above. This gives the user information on the current status of their plant’s environment in the Smart Pot. <br/>
- Power Subsystem: <br/>
  - SENSOR: Have the microcontroller monitor its own PWR supply. <br/>
  - ACTUATOR: n/a<br/>
  - CONTROL UNIT BEHAVIOR: <br/>
   The control unit will monitor its own power supply (power supply to the microcontroller). This can be done with either enabling internal supervision within the MCU itself, or using a supervisor IC. <br/>
- Microcontroller Research: <br/>
  - Youtube video which talked about all the major MCUs out there: https://www.youtube.com/watch?app=desktop&v=wXtIVnwHUmE&t=1231<br/>
  - There are many different types of microcontrollers out there, and each of them are good for certain things. For example, the ESP32 is good for projects that will utilize bluetooth or WIFI. <br/>
  - PIC by Microchip: <br/>
     - One of the first good ones that came out, and has been improved upon since.<br/>
     - It is limited, memory is limited, CPU is limited. <br/>
     - Are extremely cheap<br/>
     - Easy to use and program<br/>
     - Have their own IDE that is dedicated to their products (Microchip). <br/>
     - Have direct access to all registers, and the datasheets are extremely helpful. <br/>
     - Really good for working with peripherals <br/>
     - Limited instruction set<br/>
  - AVR<br/>
    - Free software <br/>
    - Supports arduino IDE <br/>
    - Access to object oriented programming<br/>
    - This is good for anything that uses string based communication<br/>
    - C, C++, assembly language<br/>
  - STM32 (WHAT I WANT TO USE) <br/>
    - Has its own IDE that you can download <br/>
    - You can also use the arduino IDE to code the STM32<br/>
    - Documentation on how to use the STM32 IDE is terrible though. <br/>
    - Used in any project that needs a beefy computer, has peripherals, and needs the arduino library. <br/>
    - Good for working with many peripherals<br/>
    - Is used a lot in industry<br/>
    - C, C++, Micropython, Rust<br/>
- MCU Likes<br/>
  - STM32 based<br/>
  - Large amount of IO<br/>
  - Supports I2C<br/>
  - Brown out protection<br/>
  - Cortex M0(cost effective, low power consumption)<br/>
  - Dev Board or Standalone Chip? - I think we have to use standalone chip cause we need to make a PCB. <br/>
- Dev boards(picking NUCLEO branded boards mainly)<br/>
  - F302R8(owned)<br/>
- Chips for building a board<br/>
   - STM32L071CBT6TR: https://www.digikey.com/en/products/detail/stmicroelectronics/STM32L071CBT6TR/6621798<br/>
   - STM32L010C6T6: https://www.digikey.com/en/products/detail/stmicroelectronics/STM32L010C6T6/9770445<br/>
- The option of ESP32 Wi-Fi enabling STRETCH GOAL<br/>

Signature: Trisha Murali 



