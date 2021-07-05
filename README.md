
# SimpleElectronicLoad 

#### Table of Contents 
[General Description](#general-description)
[Schematic](#schematic)  
[Function Principle](#function-principle)  
[Modifications](#modifications)  
[Usage](#usage)  
[BOM](#bom)  
[Calibration](#calibration)  
[Limitations](#limitations)  
[Author] (#author)
[License](#license)  

## General Description

The goal of this project is to design a simple but robust dummy load/electronic load using the fewer components 
possible but providing with a product that can do its job reasonably well and cheap.

Also a greath customization of the circuit was archieved, both in the components and in 
the maximun ratings (current, voltage, power...)
## Schematic 

![circuit schematic](/schematic/schematic.png "Circuit schematic")

## Function Principle

The main part of the circuit is the U1A OpAmp (LM358). In this configuration it operates like a error amplifier. 
The voltage feedback from the shunt resistor (R11) gets compared with voltage setted by the user using RV2 and, 
by OpAmp effect the output changes until both voltages are the same.    

The equation for the current is: 

![current equation](/img/current_equation.png "Current Equation")    

The current set circuitry functions as follow: The TL431 sets arround 2.5v of bias voltage to RV2. This pot is the
one that the user manipulates in order to modify the current. The voltage swing of this pot is 0v - 2.5v.
RV3 takes as input the voltage from RV2 and outputs a calibrated voltage more suitable for the shunt's output 
i.e the voltage swing of this pot is 0v -  I * R(shunt) and thus obtaining the most effective voltage swing almost
independendent of the shunt resistor value.

The fan driver functions as follows: R2, R3 & R4 set the hysteresis  in this case is 1v i.e if the upper limit 
is lets say 9v, the fan only turns on when the voltage reaches that value, and it only turns off when it reaches 
9 - 1 = 8v. RV1 sets the upper and lower bounds of the hysteresis (separated by 1v as disscused). If you want to 
modify the values I recomend this site: https://www.daycounter.com/Calculators/Comparator-Hysteresis-Calculator.phtml

## Modifications

There are some things that can be modified in the circuit. As you can see in the schematic the current set 
circuitry can be changed to acomodate other types of voltage references (either by the use of a zener diode,
voltage divider, LM317...). RV3 can be as well substituted by a voltage divider, but is not encouraged.  
The thermistor and resistor can be modified as well.
In the fan driver circuit, if you already know the RV1 voltage you need, you can substitute RV1 with a voltage 
divider. Feel free to use any mosfet/bjt that you have in hand and can withstand the fan currents.  

Following the nature of the project, depending on the maximun specifications you are willing to impose in the 
circuit, the MOSFETS (model and number), voltmeter, amperemeter, input diodes, shunt resistor and heatsink can 
be adjusted to your need.  

That is, for example if you only need a 1A, 15V dummy load you should be good with only one MOSFET a 15V voltmeter
, 1A amperemeter, a simpler input diode, maybe a higher shunt and a smaller heatsink. But if in the other hand 
you want a 200W dummy load you will need to beef up the components.

## Usage 

The usage is very simple in nature. The user only needs to insert leads in the input conectors, switch on the 
input switch (SW1) and adjust RV2 to the desired current (that the user can read in the included amperemeter)


## BOM

You can see the BOM [here](schematic/bom.txt)

## Calibration

### Current calibration
For current calibration you will need a power supply capable of providing the max current you want the dummy load
to sink, a multimeter capable of reading that current and probably a screw driver to adjust RV3. Disconecting the 
system amperemeter is encouraged.  
    
1. First connect the power supply to the multimeter and the dummy load. Please make sure the system amperemeter
is indeed disconected.
2. Turn all the way up RV2, the current shoud rise.
3. Then adjust RV3 until the read in the multimeter matches with the maximun rating of your dummy load.
4. Dont forget to reconect the amperemeter.

### Temperature limiting

This type of circuit is sadly a guessing game. According to the maths, roughly 
8.0v in RV1 gives a ~90ºC upper threshold. But this voltage will vary a lot depending on your NTC value and 
temperature curve. Adjust as necessary.

## Limitations

The most obvious limitations are the voltmeter & amperemeter absolute maximun ratings. But keep in mind that in 
reality the most important part of this project is the heatsink and not providing the MOSFETS with enough
cooling will cause they destructions

## Author 
Raul Estevez Gomez. Contact email: estevezgomezraul@gmail.com  
Please feel free to contact me if you have any type of suggestion or question. If you build this please send me a 
photo i will feel very motivated!

## License
You can read the license [here](LICENSE)
