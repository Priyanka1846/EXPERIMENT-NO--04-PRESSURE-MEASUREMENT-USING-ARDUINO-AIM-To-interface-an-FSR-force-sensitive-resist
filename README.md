# EXPERIMENT-NO--04-PRESSURE-MEASUREMENT-USING-ARDUINO-AIM-TO-INTERFACE-AN-FSR-FORCE-SENSITIVE-RESISTOR
## DATE : 29-02-2024
## NAME : PRIYANKA K																			             
## ROLLNUMBER : 212223230162
## DEPARTMENT : ARTIFICIAL INTELLIGENCE AND DATA SCIENCE


## AIM: 
To interface an FSR(force sensitive resistor) and scale the output voltage obtained to pressure applied 
 
### COMPONENTS REQUIRED:
1.	FSR  (force sensitive resistor)
2.	1 KΩ resistor 
3.	Arduino Uno 
4.	USB Interfacing cable 
5.	Connecting wires 


### THEORY: 
FSRs are basically a resistor that changes its resistive value (in ohms Ω) depending on how much it is pressed. These sensors are fairly low cost, and easy to use. They also vary some from sensor to sensor perhaps 10%. FSR's resistance changes as more pressure is applied. When there is no pressure, the sensor looks like an infinite resistor (open circuit), as the pressure increases, the resistance goes down. This graph indicates approximately the resistance of the sensor at different force measurements.
 
### FIGURE 01 GRAPH OF FORCE vs RESISTANCE **
![image](https://user-images.githubusercontent.com/36288975/163532939-d6888ae1-4068-4d83-86a7-fc4c32d5179e.png)


### FIGURE 02 FORCE SENSITIVE RESITOR FOIL DISC TYPE  
![image](https://user-images.githubusercontent.com/36288975/163532957-82d57567-a1c3-48c5-8a87-7ea66d6fca49.png)


FSRs are often a polymer with conductive material silk-screened on. That means they're plastic and the connection tab is crimped on somewhat delicate material. The best way to connect to these is to simply plug them into a breadboard.

The easiest way to measure a resistive sensor is to connect one end to power and the other to a pull-down resistor to ground. Then the point between the fixed pull down resistor and the variable FSR resistor is connected to the analog input of a microcontroller such as an Arduino The way this works is that as the resistance of the FSR decreases, the total resistance of the FSR and the pull down resistor decreases from about 100Kohm to 10Kohm. That means that the current flowing through both resistors increases which in turn causes the voltage across the fixed 10K resistor to increase.

### TABLE -01 FORCE AND OUTPUT VOLTAGES**
 ![image](https://user-images.githubusercontent.com/36288975/163532972-2b909551-12c9-485d-adb1-d1e988d557bd.png)
	
  Table -01 indicates the approximate analog voltage based on the sensor force/resistance w/a 5V supply and 10K pull down resistor.

### Vo = Vcc ( R / (R + FSR) )								Eq-01

Where R= 1KΩ in this experiment 
That is, the voltage is proportional to the inverse of the FSR resistance.

### FIGURE-03 CIRCUIT DIAGRAM
![image](https://user-images.githubusercontent.com/36288975/163532979-a2a5cb5c-f495-442c-843e-bebb82737a35.png)

### PROCEDURE:
1.	Connect the circuit as per the circuit diagram 
2.	Connect the board to your computer via the USB cable.
3.	If needed, install the drivers.
4.	Launch the Arduino IDE.
5.	Select the board (If you the board is arduino uno, select accordingly).
6.	Select your serial port, accordingly ( E.g. COM5 )
7.	Open the file of the program  and verify the error , clear if any errors that are existing 
8.	Upload the program and check for the physical working. 
9.	Ensure safety before powering up the device 
10.	Plot the graph for the output voltage vs the resistance 


### PROGRAM 
```
DEVELOPED BY: PRIYANKA K
REGISTER NUMBER: 212223230162

int fsr;
int LED = 7;
void setup()
{
  pinMode(LED , OUTPUT);
  Serial.begin(9600);
}

void loop()
{
  fsr = analogRead(A0);
  Serial.print("raw value");
  Serial.println(fsr);
  delay(1000);
  float m;
  m = map(fsr,0,159,0,10);
  Serial.print("mapped value");
  Serial.println(m);
  delay(1000);
  
 if (m>5);
  {
    digitalWrite(LED,HIGH);
    delay(500);
    digitalWrite(LED,LOW);
    delay(500);
  }
}
```
### TABLE -02 
### Standard deviation table:
![image](https://github.com/Priyanka1846/EXPERIMENT-NO--04-PRESSURE-MEASUREMENT-USING-ARDUINO-AIM-To-interface-an-FSR-force-sensitive-resist/assets/139425809/3b562c8e-cf0c-4871-a50c-a2fc1149d410)
### Graph:
![image](https://github.com/Priyanka1846/EXPERIMENT-NO--04-PRESSURE-MEASUREMENT-USING-ARDUINO-AIM-To-interface-an-FSR-force-sensitive-resist/assets/139425809/192a00fa-a7f9-4f2c-91d9-820fc7cb2764)
### Circuit Diagram:
![image](https://github.com/Priyanka1846/EXPERIMENT-NO--04-PRESSURE-MEASUREMENT-USING-ARDUINO-AIM-To-interface-an-FSR-force-sensitive-resist/assets/139425809/4810f583-2ef7-4829-917a-d7587360c810)
### Schematic Diagram:
![image](https://github.com/Priyanka1846/EXPERIMENT-NO--04-PRESSURE-MEASUREMENT-USING-ARDUINO-AIM-To-interface-an-FSR-force-sensitive-resist/assets/139425809/86b19648-5ba8-4dfe-87d8-98fa40f61770)


### POPULATION STANDARD DEVIATION:
The population standard deviation, the standard definition of σ, is used when an entire population can be measured, and is the square root of the variance of a given data set. In cases where every member of a population can be sampled, the following equation can be used to find the standard deviation of the entire population:

Where
xi is an individual value
μ is the mean/expected value
N is the total number of values

For those unfamiliar with summation notation, the equation above may seem daunting, but when addressed through its individual components, this summation is not particularly complicated. The i=1 in the summation indicates the starting index, i.e. for the data set 1, 3, 4, 7, 8, i=1 would be 1, i=2 would be 3, and so on. Hence the summation notation simply means to perform the operation of (xi - μ)2 on each value through N, which in this case is 5 since there are 5 values in this data set.

### CALCULATION: 
μ = (2+3+4+5+6+7+8+8+9+10) / 10 = 6.2      
σ = √[(2 - 6.2)2 + (3 - 6.2)2 + (4 - 6.2)2 + (5 - 6.2)2 + (6 - 6.2)2 + (7 - 6.2)2 + (8 - 6.2)2 + (8 - 6.2)2 +(9 - 6.2)2 + (10 - 6.2)2 ]/10
σ = √(17.64 + 10.24 + 4.84 + 1.44 + 0.04 + 0.64 + 3.24 + 3.24 + 7.84 + 14.44)/10 = √(6.336)
σ≈2.52

### RESULTS : 
Arduino uno is interfaced with FSR and output values are indicated on a graph.
