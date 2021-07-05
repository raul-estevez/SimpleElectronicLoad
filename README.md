
# SimpleElectronicLoad 

#### Table of Contents 
[Schematic](#schematic)  
[Function Principle](#function-principle)  
[Customitations](#customitations)  
[Usage](#usage)  
[BOM](#bom)  
[Calibration](#calibration)  
[Limitations](#limitations)  
[License](#license)  

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
## Customitations

## Usage 

## BOM

## Calibration

## Limitations

## License
