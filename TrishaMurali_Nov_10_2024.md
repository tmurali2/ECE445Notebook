Name: Trisha Murali <br/> 
Date: 11/10/2024 

# LCD and Light Sensor

I got the light sensor working and the TFT LCD. For the LCD, in order to get it working on the STM32, I had to make use of the ST7735 libraries provided by adafruit. This provided some functions such as Fill_Rectangle, ST7735_FillScreen, WriteString. These were some of the functions that I used the most. There were other functions provided such as DrawImage, InvertColors, SetGamma, ST7735_DrawPixel, but these weren't of relevance to us. 

For the WriteString, which was used to create the options. This function took in x, y, char*, font, color, bgcolor. The x and y is used to specify where you want the text to be displayed. The char* is where you pass the string you want to print, in this case, the options on the front/start screen. The font is how big you want the text displayed. In this case, there were the fonts file which provided 3 different fonts (Font_7x10, Font_11x18, Font_16x26). There were also provided colors, which was sufficient for our project purposes (examples: ST7735_GREEN, ST7735_BLACK). The background color was essentially the background on which you wanted to write the text. There is also an initialization function to make use of while using it. This was very difficult to integrate with our particular dev board since there was a lot to be modified even though it was provided by adafruit. This is because this module/library was provided for an Arduino. 

To create the illusion of different pages and/or to display data that was constantly changing, either that part of the screen or the entire screen needed to be cleared, which I just did by filling the screen to white since that was our default background color. 

This is an example of a function that was provided by the library. A lot of it was strategic placement in order to get the screen to look the way I wanted it to:
![image](https://github.com/user-attachments/assets/722d5a6b-172a-4580-a4f8-3d48dcff6eb4)

As for the light sensor, a lot of debugging took place. This took several hours. The I2C communication wasn't as easy as I thought it would be and I could not use online libraries as much and had to write/re-write/modify this entirely from scratch. There also weren't as many resources present for the LTR-329 with the STM32. This is an example of one of the functions I had to modify. 

![image](https://github.com/user-attachments/assets/aa9d3fe1-9f5f-4ad4-a496-15b9ed9024b6)

The main big difference is that I originally used Master_Transmit/Master_Receive for communcation, but I was only reading errors. I was not capturing light data. Instead, I used the HAL_I2C_Mem_Read/HAL_I2C_Mem_Write as shown below as well. 

![image](https://github.com/user-attachments/assets/03ae642b-b077-4326-82a7-e6aa9e3a31c3)

**Signature: Trisha Murali**
