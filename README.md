# Robot-s-Eyes-Circuit_Astable-Multivibrator_Multisim
The purpose of this project is first to design a circuit that builds the eyes of the robot such that it goes off for some time without being detected by humans’ eyes in order to decrease power consumption. And then to design a circuit that power the robot’s eyes circuit that was designed using voltage regulator. 
# Robot's Eys Circuit Design using Multisim 
I choose to design the robot’s eyes circuit with the astable multivibrator due to its ability of making LEDs blinking and control that blinking rate (a blink/s) in order to make the LEDs turning ON and OFF, or simply “oscillating”. The question is, what frequency range of the electromagnetic spectrum cannot be detected by humans’ eyes? The answer is, humans’ eyes can see waves that ranges from 4.3x10^14 – 7.5x10^14 HZ which known as visible light waves. Which means any other waves with frequencies beyond this range cannot be seen by humans’ eyes. This phenomena assist in designing the circuit such that it oscillates with a frequency beyond the visible light frequency range but with considering other factors such as LEDs specifications and standard values of resistors and capacitors. 
The frequency can be calculated using the following formula:
f=1/(ln⁡(2)×2×R×C)
Where R=RB1=RB2 and C=C1=C2. There are some rules to choose the values of R and C. Firstly, all values should be identical in order to have an identical operation that is RB1=RB2, RL1=RL2 and C1=C2, Secondly, RL1 and RL2 must be less than RB1 and RB2. Finally, the lower the values of the timing elements C1, C2, RB1 and RB2, the higher the frequency and vice versa. 

The figure below illustrates the circuit that build the robot’s eyes with a 721.35 blink/s. (Multisim file of the circuit is uploaded)
The components of the circuit are:
RL1 & RL2: Resistors for LEDs protection.
RB1 & C2, RB2 & C1: RC circuits for timing the circuit by controlling the base voltages of the two transistors. 
Q1 & Q2: Two BC547 transistors used as switches for turning the LEDs ON and OFF.
LED1 & LED2: Two loads that represents the eyes of the robot.
VCC: A 5V voltage source to power the circuit (will be replaced by the other circuit to be designed).

![image](https://user-images.githubusercontent.com/85955049/123556607-c7136200-d794-11eb-9f03-868a99188433.png)

Note: RB1 and RB2 may be replaced by a variable resistor to vary the resistance until we get the desired output.

The simple operation of the circuit can be explained with two states, State 1 and State 2. 
State 1: Assume Q1 is ON (short-circuit) that is the base receives about 0.7 V while Q2 is OFF (open-circuit) with base voltage less than 0.7 V. Capacitor C2 is initially “charging” which means the charges are moving from the positive terminal of the capacitor to the negative. Then by adding the voltage drop across resistor RL2 with the voltage of the capacitor C2, a voltage that is approximately 0.7V results at the base of Q1 which cause it to turn ON (in the saturation region). At the same time, capacitor C1 is “discharging” which means the charges are moving from the negative of C1 to the positive, which result in a negative voltage drop at the base of Q2. See the figure below.
Note: The values of RB2, RB1, C1 and C2 were changed to visualize the switching states between the transistors.

![image](https://user-images.githubusercontent.com/85955049/123556690-502a9900-d795-11eb-9b19-0c20ef749a1e.png)

State 2: Now Q2 is ON and Q1 is OFF which means the opposite of state 1 will be repeated. Alternatively, C2 is discharging which cause a negative voltage drop at the base of Q1 while C1 is charging which cause a voltage drop at the base of Q2 of about 0.7V. See the figure below.

![image](https://user-images.githubusercontent.com/85955049/123556851-42c1de80-d796-11eb-8d4e-39952870bb2b.png)

# Pwoer Circuit (Adjustable Output Voltage Regulator) using Multisim

The this section the 5V battery of the circuit shown in figure above will be replaced by a power circuit. One method to construct a power circuit is to use a voltage regulator circuit. The concept of a voltage regulator, as its name implies, is to “regulate” or simply, “convert” the input voltage to a different voltage value (the desired output).  the figure below shows an adjustable output voltage regulator circuit that regulates a 9V input to a 5V output.  In order to have a different output voltage the voltage regulator block can be replaced by another value such as LM7808 to have an 8V output. (Multisim file of the circuit is uploaded)

![voltage regulator](https://user-images.githubusercontent.com/85955049/123557214-4e160980-d798-11eb-827c-d48227598913.png)

A 0-200 ohm variable resistor R2 is used to set the required output of the circuit. For instance, if the resistance is 200 ohm, the output voltage is approximately 7.5V. Similarly, if the variable resistor is 0 ohm, then the output is 5V. The following equation is used to calculate the output:
Vo=Vx+(Vx/R1 +Io)R2,   

Where,
Vx: The desired output.
Io: The output current.

The figure below illustrates how the voltage regulator circuit is connected to the robot’s eyes circuit.

![image](https://user-images.githubusercontent.com/85955049/123557258-93d2d200-d798-11eb-94e1-5f19dfed5e86.png)

