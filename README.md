# Solar Smartphone Charger

This is the the project, assigned by [Dr. Rob Frohne](https://github.com/frohro), that [Joshua Mularczyk](https://github.com/JoshuaMularczyk) and I designed for our Power Electronics class. This project used our knowledge of power efficiency and stepping down voltage along with our knowledge of KiCAD and LTSpice to create our own portable solar phone charges. 

## Design Objectives:
- Output 5V from a higher input voltage
- Draw 1A at the output
- Inexpensive ($20-$30 Budget)
- AS efficient as possible

## Overview

<img width="803" alt="Capture" src="https://user-images.githubusercontent.com/103919092/172073393-7d0b4d4d-99ac-4203-9fa4-bd4a26a79dc6.PNG">

Josh and I wanted to design a solar phone charger because we thought of the potential use of people who spend a lot of time outside. We also knew that Apple products need certain specifications to charge as oppose to Andriod products so we set out to figure out how to make our charger work for both.

The first simulation/schematic of our project allowed us to get the desired outputs, but we found that it was not very efficient, so we decided to redesign our board and end up with a new string of designs

The heart of our circuit is the [LM3478](https://www.ti.com/lit/ds/symlink/lm3478.pdf?HQS=dis-dk-null-digikeymode-dsf-pf-null-wwe&ts=1654180125781&ref_url=https%253A%252F%252Fwww.ti.com%252Fgeneral%252Fdocs%252Fsuppproductinfo.tsp%253FdistId%253D10%2526gotoUrl%253Dhttps%253A%252F%252Fwww.ti.com%252Flit%252Fgpn%252Flm3478) which is a high-efficiency low-side n-channel controller. This allows us to regulate any voltage between 2.39 and 40V that could come from our 10W solar panels

## Rev 7 Design

<img width="814" alt="schematic2" src="https://user-images.githubusercontent.com/103919092/171946765-55e72f38-f459-4aac-95c0-715ab55abb05.PNG">

This is the most recent KiCad schematic for our circuit design. Josh used the Texas Instrument [Webench Power Designer](https://www.ti.com/design-resources/design-tools-simulation/webench-power-designer.html) to generate this step-down circuit. The design specified a 5V to 12V input voltage based on the likely solar panel outputs. We also specified the a maximum of 1A should be be able to be drawn from our circuit.

## Rev 7 Simulation
<img width="937" alt="sim" src="https://user-images.githubusercontent.com/103919092/171796889-ca19fa5c-3ef4-4bb1-9945-8d61918285da.PNG">
This is the complete simulation of our circuit. We can see here that at around 7ms, the output voltage of circuit is 5V

### Voltage Outputs (5V 2.7V 2V)
<img width="960" alt="ThreeOutputVoltages" src="https://user-images.githubusercontent.com/103919092/171797195-8e6268f1-bec3-4a75-8258-a8a130c296d0.PNG">

This is the simulation of the voltage dividers that shows the voltage going to our USB pins. V+, D+, and D-. This will be talked about more in the testing section.

### Input and Output Current
<img width="958" alt="currentsim" src="https://user-images.githubusercontent.com/103919092/171947246-d86cb5ba-57f3-49fe-8221-589e6aca34f5.PNG">

This simulations shows us that we achieved the low input voltage that we need. The 5 Ohm resistor allowed us to simulate the current our phone would draw from the circuit. The output current of 1A will allow us to power our phone with 5W.

## Rev 7 PCB Design
<img width="730" alt="pcb2" src="https://user-images.githubusercontent.com/103919092/171952596-56a447e4-df71-455a-acbc-5d2364d089b8.PNG">

This is the PCB design of the board we sourced from [JLCPCB](https://jlcpcb.com/VGS?utm_source=gg_vgs&utm_medium=cpc&gclid=Cj0KCQjwqPGUBhDwARIsANNwjV4Y9aU908uwwHsgXCAJ3L9PZ44l-hPgCvsU4kgto-ll1H0iRJroh1UaAsKwEALw_wcB),

## Rev 6 Testing
<img width="500" alt="IMG-2079" src="https://user-images.githubusercontent.com/103919092/172071789-ddb3b23f-fdcf-4cd2-8f8e-7058f5be7122.png"><img width="500" alt="IMG-2080" src="https://user-images.githubusercontent.com/103919092/172071805-037e6bf5-900f-40e0-b412-12e99efecea5.png">

Josh and I each constructed a our own boards and tested them. When testing the boards with a 0-18V 1A power supply, we found that the boards could charge Ti-84 calculators and Andriod phones, but not an iPhone. To see if we couldn't draw enough current from the power supply, we connected our board to 24V 3A power supply and saw the same results. After we performed some research, Josh found that we needed voltage across the D+ and D- pins, 2.7 and 2V respectivly. To achieve this, we created a votalde dividers using through-hole resistors and soldered them to the back of the boards. We then tested the boards and found that we were able to succesfully charge our iPhones.

![image](https://user-images.githubusercontent.com/103695977/172703383-8192ec97-55e3-4943-acb7-ccd2cf2812ec.png)
![image](https://user-images.githubusercontent.com/103695977/172703418-6e0d1762-f83f-49cc-a7bb-411f2b994870.png)

After we tested the boards in the lab, we connected our boards to our solar panels and tested them outside. We found that we were getting around 4.8V and .96A at the output which gave us 4.61W at the output. 

## Rev 6 Results
The image on the left shows the voltage being supplied to the iPhone through the 24V 4A power suplies. The image on the right shows the current being drawn by the iPhone.

<img width="400" alt="IMG-1079" src="https://user-images.githubusercontent.com/103919092/172072088-5cb21dbd-36de-4d5a-aee9-864d0d37841f.jpg"><img width="400" alt="IMG-1081" src="https://user-images.githubusercontent.com/103919092/172072099-f12144a6-9be4-4a8b-8c2a-dc5363fb0343.jpg">

More images are avaialble in the [pictures](https://github.com/cwill713/Solar-Panel-Phone-Charger/tree/main/Pictures) folder. The video of testing made by Josh is availabel [here](https://youtu.be/SS7m2UqrDPg).
