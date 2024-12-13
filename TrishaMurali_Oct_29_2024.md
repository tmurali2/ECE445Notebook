Name: Trisha Murali <br/> 
Date: 10/29/2024 

Similarly, the stepper motor also follows similar steps. The stepper motor (290-028) needs a driver to go along with it (ULN2003) for appropriate functioning. This is a 5-wired, 5V, unipolar stepper. This is just plugged into the driver and wired into 4 pins on the STM32, let’s say A1-A4 and 2 other pins for ground and power (same as the STM32 NUCLEO board). The pinouts and clock settings for this follow the same pattern as for the servo motor, but as for the specific settings [6], the HSI is selected for the PLL Source Mux, with an 8 x 9 = 72 MHz for the SYSCLK and the HCLK eventually getting this value over to the APB2 Timer clocks. This is of concern as a result of using TIM1 for the timers. 

Here, the code is dependent on setting specific angles and values to rotate to. In the case of the project, it is used to rotate in the shades to ensure that the light exposure does not exceed those required for the plant. 

![image](https://github.com/user-attachments/assets/8a9dc809-66f3-45a4-bd02-8d3c3cd5eae1)

References: <br/>
[6] “How to Interface Stepper motor with STM32”, Controller’s Tech, https://controllerstech.com/interface-stepper-motor-with-stm32/
