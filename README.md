
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
[License](#license)  

## General Description

The goal of this project is to design a simple but robust dummy load/electronic load using the fewer components 
possible but providing with a product that can do its job reasonably well and cheap.

The nature of the project is also providing a gread costumization of the cuircuit, either the components or the 
maximun ratings (current, voltage, power...)
## Schematic 

![circuit schematic](/schematic/schematic.png "Circuit schematic")

## Function Principle

The main part of the circuit is the U1A OpAmp. In this configuration it operates like a error amplifier. 
The voltage feedback from the shunt resistor (R11) gets compared with votlage setted by the user using RV2 and, 
by OpAmp effect the output changes until both voltages are the same (in theory).    

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
voltge divider, LM317...). RV3 can be as well substituted by a voltage divider, but is not encouraged.  
In the fan driver circuit, if you already know the RV1 voltage you need, you can substitute RV1 with a voltage 
divider. Feel free to use any mosfet/bjt that you have in hand and can withstand the fan currents.  

Following the nature of the project, depending on the maximun specifications you are willing to impose in the 
circuit, the MOSFETS (model and number), voltmeter, amperemeter, input diodes, shunt resistor and heathsink can 
be adjusted to your need.  

That is, for example if you only need a 1A, 15V dummy load you should be good with only one MOSFET a 15V voltmeter
, 1A amperemeter, a simpler input diode, maybe a higher shunt and a smaller heathsink. But if in the other hand 
you want a 200W dummy load you will need to beed up the components.


## Usage 

The usage is very simple in nature. The user only needs to insert leads in the input conectors, switch on the 
input swith (SW1) and adjust RV2 to the desired current (that the user can read in the included amperemeter)


## BOM

## Calibration

## Limitations

## License
