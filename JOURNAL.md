---
title: "ClockedIn"
author: "pythonatsea"
description: "GPS synced nixie tube clock"
created_at: "2025-06-15"
---

# ClockedIn

## 6/15/25, 1 hour

### General idea

Essentially a nixie tube clock with GPS syncronization. I also want to give it a case out of laser cut aluminum and *maybe* some laser cut wood, I need to do some more research. 

### Powahhhhhhh

Nixie tubes operate at 170v, I'm planning to use [this](https://omnixie.com/products/nch8200hv-nixie-hv-power-module?variant=36238768242855) and have a bunch of shift registers to actually drive them.

## 6/16/25, 2 hours

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

## 6/21/25, 3 hours

### More routing
I routed the first 2 nixie tubes completely, it takes a bit ahhhhhhh. i feel like i should have more to say for a hours work but i don't really

![image](https://github.com/user-attachments/assets/c04a1ba2-a7ff-46a1-bbae-15644bc25b1c)

### Routing "done"

I've finished the first draft at routing for the nixie tubes, YAY!!!!

![image](https://github.com/user-attachments/assets/71a51415-b572-45ed-a456-1bad6144b5e1)

## 6/23/25, 4 hours

### GPS Module

I've decided to use this [adafruit GPS module](https://www.adafruit.com/product/746), mainly cuz it's easy to wire and has support for an external antenna, which I'll need since I'm planning on have a aluminum case (mainly cuz I have a weird desire for it to have some heft, y'know). I'm using [this antenna](https://www.adafruit.com/product/1858), as well as a [adapter](https://www.adafruit.com/product/851). The GPS module also has  RTC, which means I don't need a seperate module! The GPS modue connects with a simple 9pin 0.1" pitch header.

![image](https://github.com/user-attachments/assets/89e400af-e558-48fa-9bed-80355d6b384a)


### MCU

I'm planning on using the [Waveshare RP2040-Tiny](https://www.waveshare.com/wiki/RP2040-Tiny) as the MCU, mainly cuz it's tiny. I did have to make a custom footprint for it, because the only one I could find was goofed. 

![image](https://github.com/user-attachments/assets/8adc78be-5276-4445-9dff-d2bd14d31102)

### Routing

I did a bunch of routing with the shift registers and their data, latch, and clock lines.

## 6/24/25, 4 hours

### Buttons

I want a way to interect with the clock to disable all lighting for the night when I go to sleep (i'm very sensitive to light and noise when i'm sleeping), among other things. I'm planning to use 4 of these [stainless steel buttons](https://www.aliexpress.us/item/3256805624137497.html), mainly cuz they look _awesome!_

### PCB Done!(ish)

The pcb is "done", although I'm probably gonna realize a couple dozen mistakes I need to fix soon. It's quite large, but I can't find a better way to lay things out that would reduce the size in a meaningful way. I've put 4 M4 mounting holes in the corners, which I'm planning to connect to the case with standoffs.

![image](https://github.com/user-attachments/assets/da6568bf-657f-4b80-8baa-0ae4950db564)

### Case

I'm planning to make the case out of a bunch of laser cut aluminum plates stacked and bolted together, mainly becuase I want it to have some weight.

## 7/2/2025, 5 hours

### Case sillyness

So it seems that a aluminum case is gonna be way, way too expensive! So first I tried just having a bent sheet metal stand, but I couldn't get fabworks to quote it, even though I spent like a long time on it ahhh. So I eventually settled on having a SLS 3d printed case from JLCPCB, which should have a nice finish and look better than a standard FDM print. 

### Actual case work

I'm gonna have the case made out of two parts, the main part and the front plate. The buttons will be mounted to the front plate, and the GPS antenna + the barrel jack will be mounted on the back. also i realize why cadding takes for my robotics team takes so long, you spend a _lot_ of time just staring at the screen thinking about what to do.

![Part Studio 1](https://github.com/user-attachments/assets/8993a312-bb09-4dd8-a645-a2a5a7288714)
