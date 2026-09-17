# Designing layout 
- Sun Aug 29th
- 1.5 hr

I spent time planning out what type of keyboard I want, features to implement, and the layout of the keys. 
I've decided I wanted features of a split-wired keyboard, row staggering, Alice curved, extra keys for shortcuts, gasket mount with 3 layers, mousebites on PCB, and a foldable keyboard stand.
I'm thinking of implementing LEDS, Hot-swaps, a keyboard strap, PETG instead of PLA, and some other aesthetics.
Some things I want to change and work on from my previous keyboard design are: Use less PCB space, use less space for the keyboard on unnecessary things, and don't add extra colours / designs on the top / bottom case. These reasons are because of mainly cost, aesthetics and looks, and just in general how useless to is to have a bigger keyboard.

<img width="512" height="698" alt="image" src="https://github.com/user-attachments/assets/0d780c20-dd6a-4727-859e-88c82f279638" />

In this photo, I sketched out what the layout of my keys should be like. I also included a rotary encoder in the top left for probably brightness or volume. Afterwards, I wanted to switch to a curved Alice keyboard instead of a original Alice.

<img width="1116" height="810" alt="image" src="https://github.com/user-attachments/assets/13bde227-23d3-4969-af57-c7d156a3b503" />
These are the two types side by side. 

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# Designing Schematics
- Tue Sep 1 
- 3 hr

When making schematics I had to download marbastlib and panelization.pretty for 3d models and footprints. These libraries were used for switches, stabilizers, rotary encoder switch, and mousebites. Afterwards, I started to work on symbols and traces. Overall, designing schematics was not difficult, but just time-consuming because of designing the matrix for the switches and then fixing bugs in the Electric Rules Checker in Inspect tab. 

Working on the TRRS Jack (an audio port) as my interconnect cable, it was overall easy to add into as there only 4 points: Tip, Ring, Ring, Sleeve. Or known as Ground, VCC (5V or 3.3V), SERIAL as a Net Label, then Ground. Here's a picture of the microcontroller and TRRS Jack.
<img width="2186" height="588" alt="image" src="https://github.com/user-attachments/assets/2ff9238b-88b3-4b01-8dd8-0a1bc8a6037e" />

Here's a picture of the left side of the keyboard
<img width="1456" height="1378" alt="image" src="https://github.com/user-attachments/assets/f5d72aac-f432-4d68-a3ab-c4d4442c795c" />

Right side
<img width="1436" height="1228" alt="image" src="https://github.com/user-attachments/assets/3244c5a7-e0fc-426d-ad6f-3fdad745d330" />

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# Fixing Schematics + Assigning Footprints
 - Fri Sep 4
 - 1.5 hr

 I spent time after the last post to assigning footprints to the symbols and fixing schematic bugs. In the matrix, I fixed one switch by pushing it up a row because in the layout it was supposed to be one of the arrow keys, instead it was on an empty space.
<img width="1468" height="956" alt="image" src="https://github.com/user-attachments/assets/476fe8a8-3962-4b69-949d-fc339e91710d" />

Afterwards, I edited the TRRS Jack symbol pins from S, R1, R2, T, to 4, 3, 2, 1. The reason I did this was because when assigning footprints and updating PCB from Schematics, it gave me a huge amount of errors + warnings about the pins from the footprints and schematics being different. All I did was go into symbol editor for both TRRS Jacks and switched the pins. 
<img width="1966" height="1050" alt="image" src="https://github.com/user-attachments/assets/324e8708-a670-47fa-b63a-e68404390e9a" />

The footprint in PCB:

<img width="504" height="1020" alt="image" src="https://github.com/user-attachments/assets/aef91f99-198d-492a-914c-507e479bcf41" />

When finished, I just assigned all the footprints to the symbols. 

RaspberryPi_Pico - Module:RaspberryPi_Pico_Common_THT, 

Mousebite - Panelization.pretty-master:mouse-bite-5mm-slot, 

1N4148 - Diode_THT:D_DO-35_SOD27_P7.62mm_Horizontal, 

AudioJack4 - Keebio-Parts.pretty-master:TRRS-PJ-320A,

MX_stab - PCM_marbastlib-mx:STAB_MX_2u, 

RotaryEncoder_Switch - Rotary_Encoder:RotaryEncoder_Alps_EC11E-Switch_Vertical_H20mm, 

SW_Push - Button_Switch_Keyoard:SW_Cherry_MX_1.00u_PCB

This is a picture of updating the PCB from schematics:
<img width="1692" height="1302" alt="image" src="https://github.com/user-attachments/assets/fb6297fa-2937-434e-aaaf-1ca130201e0d" />

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# Redesigning keyboard schematics + footprints + layout
 - Sat Sep 12
 - 2.5 hrs

The last few days I was busy with other work and school, where I don't think I don't have enough time to finish some portion of the keyboard. The switches on either side was incredibly hard to set up in PCB because when using coordinates and tilted switches, the x + y are different from 19.05 and I had no solution for setting up the ai03 plate generator. That's why this keyboard won't be a split alice keyboard. I'm gonna use a 60% gasket mount keyboard that is row staggered and is hot-swappable. This keyboard should be easy for me to complete by the end of this event. I also don't have any photos of me attempting to create the alice keyboard. When reediting the schematics & footprints, it wasn't hard because all I did was combine the two switch matrix's, remove TRRS Jack, and use only one raspberry Pi Pico for the entire keyboard. I then edited footprints by using marbastlib's hotswap footprints. 

<img width="894" height="385" alt="image" src="https://github.com/user-attachments/assets/6ea5877a-42d6-4fb0-b064-af7ee377e5dd" />
This photo is a reference to what keyboard I'm trying to recreate. 

<img width="2176" height="698" alt="image" src="https://github.com/user-attachments/assets/ca203166-761c-4867-b7ac-c103c1246ff3" />
Here is the new switch matrix, where there is no F row, no arrow keys, and renamed net labels. 

<img width="694" height="954" alt="image" src="https://github.com/user-attachments/assets/371eaca6-772c-4b7e-a306-04e7a37e65fb" />
One Raspberry Pi_Pico for 14 columns and 5 rows. removed GND and VCC. 

<img width="984" height="676" alt="image" src="https://github.com/user-attachments/assets/983e4b2e-e4d8-4f94-8dec-13413dae9b78" />
<img width="998" height="594" alt="image" src="https://github.com/user-attachments/assets/d011ce5d-6f07-44d4-8ac7-c9e2e0807b28" />
The footprint for Hot Swap switches

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# Redesigning PCB, finalizing PCB, Adding 3d models, and exporting
 - Sat Sep 13
 - 3 hrs

 I spent the day basically just working on changing the PCB by updating the PCB from schematic changes, then reworked on organizing the switches. Afterwards, I placed diodes and traced everything together. I tried to compact the microcontroller as close to the switch matrix because I didn't want a large PCB, making it more difficult for the cost and size of the case I'm designing. It would also be aesthetically uncomfortable for a huge amount of space on the top. After adding the edge.cuts, I added some silkscreen pictures and drew filled zones for the PCB. I had to add in the 3d models for the switches because for some reason the footprint only came with the hotswaps. I also had to do the same process with the stabilizers. When finished with the PCB, I exported my gbr files and added in the KiCad files in the repository.

 Process of making the layout
<img width="1446" height="988" alt="image" src="https://github.com/user-attachments/assets/9bc45c45-48e4-48d8-85d5-7fba20558804" />
<img width="1674" height="612" alt="image" src="https://github.com/user-attachments/assets/33dac834-afa5-4eeb-a697-1ad1a75d5a2c" />
<img width="1708" height="850" alt="image" src="https://github.com/user-attachments/assets/1db5a2e3-c332-410e-b723-7f399570e535" />
<img width="1710" height="964" alt="image" src="https://github.com/user-attachments/assets/e50b6c9e-1ccc-47f7-8790-32a26119331a" />

3D model
Front
<img width="1864" height="888" alt="image" src="https://github.com/user-attachments/assets/436b1ad9-34df-4536-acdc-f3612cdd4748" />
<img width="1848" height="868" alt="image" src="https://github.com/user-attachments/assets/7894290e-ca86-4e90-a28f-5c962c416375" />

Back
<img width="1988" height="900" alt="image" src="https://github.com/user-attachments/assets/e7914559-d557-4a2d-adbe-7adc2dce7f1e" />
<img width="2044" height="926" alt="image" src="https://github.com/user-attachments/assets/4af08d2a-bc6b-4505-919a-a0096ad5e272" />

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 # Making gasket mount + Case, exporting into github 
 - Tue Sep 15
 - 4 hrs

 I have worked on the case and designing the gasket mount so the porons would fit properly with the plate. The first thing I did was export KiCad's 3d viewer model into a .stl file so I can use it for modelling my case. Afterwards, I went into ai03's plate generator and asked an ai for the format in 60% keyboards. I downloaded the DFX and uploaded to Fusion360's uploads for the plate. After exporting both the model and plate, I started working on the case. I made the thickness of the plate 1.5mm and descaled every side of the switches by -0.2mm because there may be issues for fitting because of 3d printing. I then worked on the gasket mount with first making the porons and then building off it. I got information of dimensions of the porons just asking ai and giving it the source to what i'm deciding to buy from. A problem I had was because the top part of my PCB was empty, I was worried about sagging when making the keyboard. I just ignored this as I would just use more porons or damping foam to hold the keyboard from sagging. the top and bottom case took me a while just because I had to constantly check if the porons if between the case and plate + PCB. I also added the USBC hole for the bottom case + 6 holes through top and bottom case for screwing in with heat-set inserts. After finalizing the entire case, I added fillets and made the colour beige (just so it's easy to differentiate from the other components. I then exported the cad files into Github for 3d printing and proof of work. Here's some photos:

Process of making the gasket mount case + the porons + PCB + plate
<img width="2048" height="1292" alt="image" src="https://github.com/user-attachments/assets/4aeabeef-a81c-4339-be0d-669e88527944" />
<img width="2086" height="1064" alt="image" src="https://github.com/user-attachments/assets/ad2a8759-dbe9-4713-a925-c0794651c43b" />
<img width="1966" height="754" alt="image" src="https://github.com/user-attachments/assets/b2a02b8b-c62b-4b68-886c-f044af85872c" />
<img width="2232" height="1090" alt="image" src="https://github.com/user-attachments/assets/63778e73-ca8b-4887-b9e0-3073cd80b252" />

FINAL model showcase
<img width="1578" height="1398" alt="image" src="https://github.com/user-attachments/assets/56e68a33-a7a2-4f6b-9836-6d05cee63606" />
<img width="1976" height="766" alt="image" src="https://github.com/user-attachments/assets/6851f988-db7c-41d7-b2be-ba503f2cb1da" />
<img width="1758" height="520" alt="image" src="https://github.com/user-attachments/assets/23f95dba-b6e6-417e-b874-19260a6d46f2" />

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 # Finishing, writing README.md, writing BOM.csm, and writing submission form for grant
 - Wed Sep 16
 - 1.5 hrs
it's finally finished










 


 

