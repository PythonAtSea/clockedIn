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

## 6/19/25, 4 hours

### Schematic "done"
The schematic is kinda done, I'm planning on connecting the shift registers based on what makes sense geographically. I'm also still thinking about having colons be lit up, but I might just have them as part of the case.

![image](https://github.com/user-attachments/assets/5fe4cd15-cf9e-4ee2-a8f1-a39183c45a95)
![image](https://github.com/user-attachments/assets/d67abc03-793b-4bd6-b49b-0047ff64fbd7)
![image](https://github.com/user-attachments/assets/11861b00-b1fd-4327-82b5-03dd8c1a08a0)

### Handmade IN-12A/B footprint

There doesn't seem to be a footprint for the IN-12 nixie tubes that isn't goofed in at least one way, being it lopsided or the holeds just not being in the right place 😭. I spent a absurd amount of time trying to find a good footprint but to no avail. I did, howver find a [translated version of the origional russian datasheet!](https://drive.google.com/file/d/1VCBgA3ZlsqFrKxp0Fkk9OuxMdr5gytET/view) I used a drawing in it to recreated the footprint in KiCad, which _should_ work. 

![image](https://github.com/user-attachments/assets/2a3587e9-a686-442f-9aa5-3747e7689276)
![image](https://github.com/user-attachments/assets/eee8e0d0-dc4a-4e6b-ab86-d7fe3986a4a7)

## 6/20/25

## Clearances
I spent like at least 45 minutes figuring out how kicad netclasses work :sob:

### idk what to call this
Because the shift registers have 8 pins and the tubes have 11 cathodes, there isn't a quick and easy way to connect them in the schematic. Additionally, half the pins on the shift register are on one side and the other half are on the other side. So I can't really connect them in the schematic before I know how the PCB is gonna look. So, I position the shift registers next to the nixie tubes and figure out what connections I should make and go back to the schematic and make them! It takes a very long amount of time. ahhhh

![image](https://github.com/user-attachments/assets/9bc53001-0be1-4e97-98ce-b2a65380e6cb)

## 6/21/25, 1 hour

### More routing
I routed the first 2 nixie tubes completely, it takes a bit ahhhhhhh. i feel like i should have more to say for a hours work but i don't really

![image](https://github.com/user-attachments/assets/c04a1ba2-a7ff-46a1-bbae-15644bc25b1c)

