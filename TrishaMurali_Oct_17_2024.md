Name: Trisha Murali <br/>
Date: 10/17/2024

# More STM32 Updates: Stepper Motor 

Video of working stepper: https://drive.google.com/file/d/1gVh-LUYdp4_K_9VkM8eWW64hZQ9rZMUl/view?usp=drive_link

Getting the stepper motor was quite challenging. Debugging this took several hours. I could feel a vibration but the stepper motor would not turn. This was due to the fact that two of the pins needed to be switched from their regular order to function. This was not stated clearly anywhere, so I tried a few other debugging options before this. I thought that the pins in the STM32 weren't sending a high signal, so I turned each one of them on and off to test. It was made clear that all of this worked, so then I assumed that I got the pins wrong on the STM32 or was using them when I shouldn't be. I checked the manual for my dev board and eventually also wired it onto an Arduino for testing and debugging purposes. However, this posed the same issue. I thought that this was an issue with the motor and eventually went to pick up some more from the ECEB. Prior to trying the new motors, however, I looked into the stepper motor documentation more carefully and realized that two of the middle pins had to be swapped in order for the motor to function. 

Below are the clock configurations for the stepper:
![image](https://github.com/user-attachments/assets/2d9b5283-384b-4f6d-b49b-f1f0cc6d49c6)
