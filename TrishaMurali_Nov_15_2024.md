Name: Trisha Murali <br/>
Date: 11/15/2024 

# LCD Updates: 
I got the LCD to show different pages and live expressions. I also created the rotary encoder to be able to move around and select different options. In order to do this, we use the live expressions tab on the STM32 and printed our real-time data/values. This was then printed onto the screen using the WriteString function. Something to note here is that in order to show real-time data changing, the numbers/values from the reading prior to this one had to be cleared since the pixels would stay on the screen otherwise and the values would not read accurately. I had to overwrite the max number of pixels/fill the screen to the background color on each write in order to cover that up and show the fresh, new values. Here is a picture of what it finally looked like: 

![image](https://github.com/user-attachments/assets/bafdbfac-b5b2-458e-b5e5-57f2dcaecfa1)

In addition to this, I had to use the rotary encoder to read in user input and make it appear as though the user would be able to go through the options. Since the rotray encoder was incremented each time and there was no modulus logic, this is something I had to implement. This, however, made it difficult still and there were a lot of little quirks since if I went to one particular page and pressed the button it would react differently than if I accidentally moved the rotary encoder to be a larger number and then pressed the button. This was because the modulus logic I applied had to account for the fact that there were only 4 options on the first page versus only a back option on the statistics page, and 6 different options along with a back option on the plant types page. This had to be accounted for in the code and taking care of each case was a trial and error process.

![image](https://github.com/user-attachments/assets/4e95d727-9eac-496b-8a9a-03477fe57c58)
![image](https://github.com/user-attachments/assets/9b794e14-40c2-4555-bd89-10c183cedc0c)
![image](https://github.com/user-attachments/assets/c86f1bf0-9e15-452d-93e9-1e369868b5e7)

Rotary Encoder Logic: <br/> 
![image](https://github.com/user-attachments/assets/50e0cd67-c7ae-44a1-b404-19578a54d1f8)

**Signature: Trisha Murali**
