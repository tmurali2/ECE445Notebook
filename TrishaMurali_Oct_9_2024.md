Name: Trisha Murali <br/>
Date: 10/09/2024

# Placed order and split workload 
We had the PCB review with the TA, which went pretty well and I placed parts order. Since we haven't received any parts, we split up work. I was assinged to firmware and Gavin and Morgan were assigned to hardware/CAD design. My next goals right now are to the get the stepper motor and servo motor working on the STM32 dev board while also experimenting with libraries and the STM32 IDE. At the next meeting, we hope to discuss all our findings related to the project and how we can collaborate and further assign tasks. 

The servo motor that I was working with was the HS-311. This motor is supposed to be used for the shades. Here, the PWM (Pulse Width Modulation) signals and figuring out the clock settings was quite difficult. In terms of the STM32 environment -- setup was a bit challenging at first, but once the CubeIDE was all setup it was pretty smooth sailing from there: 

0.5 ms PWM is associated with 0 degrees, 1.5 ms PWM is associated with 90 degrees, 2.5 ms PWM is associated with 180 degrees. 

![image](https://github.com/user-attachments/assets/cf93667d-a0b5-42a2-b8f9-d692bd5354b1)

References: https://controllerstech.com/servo-motor-with-stm32/

**Signature: Trisha Murali**
