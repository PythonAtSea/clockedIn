# ClockedIn

## 6/15/25, 1 hour

### General idea

Essentially a nixie tube clock with GPS syncronization. I also want to give it a case out of laser cut aluminum and *maybe* some laser cut wood, I need to do some more research. 

### Powahhhhhhh

Nixie tubes operate at 170v, I'm planning to use [this](https://omnixie.com/products/nch8200hv-nixie-hv-power-module?variant=36238768242855) and have a bunch of shift registers to actually drive them.

## 6/16/25, X hours

### Shift registers

I'm using the [TPIC6B595N](https://www.digikey.com/en/products/detail/texas-instruments/TPIC6B595N/277601) shift registers. They each have 8 bits, and I have 10 digits + a decimal place for each so I have 11 * 6 = 66 total pins to drive, so I need 9 shift registers (yay).

![image](https://github.com/user-attachments/assets/033dcdc0-d627-43d1-bd5c-12e6d1fe89ee)
i love not being able to read any of the text when i can see all of them

## 6/17/25, 2 hours

### MCU
I'm planning on using the RP pico w, so I can have it host a webpage or something to control the clock. Still want the time to be set using GPS tho. 

![image](https://github.com/user-attachments/assets/b6a79d47-9cf3-411d-b6b4-bb30019cf0c6)

### Other stuff

I've begun to figure out which components I'm gonna use, most of which I'm ordering from [DigiKey](https://www.digikey.com/en/mylists/list/VY0OA4IGPM), mainly cuz shipping is fast and cheap, even if the component prices aren't the greatest. I'm planning on powering it using a ~~12v~~5v (i realised that the 170v boost convertor I'm using takes in 5v, not 12v 🤦) barrel jack, and I'm gonna use TPIC6B595N shift registers.
