# Precision-Voltage-Monitoring-Switching-ON-Surge-Protection-System
Objective:

The objectives of the project are:
•	Protection against high and low voltages in mains.
•	Protection against Switching-ON surge whenever AC mains restores.


Equipment:

•	Resistors:
1.	R1, R2, R4, R5 = 10k
2.	R3 = 4.7k
3.	R6 = 22k
4.	P1, P2 = 10k potentiometers
•	Capacitors:
1.	C1, C2 = 1000uF/25V
•	Diodes:
1.	D1, D2, D3, D4, D7 = 1N4007
2.	D5, D6, D8, D9, D10 = 1N4148
3.	Zener Diodes Z1, Z2 = 4.7V
•	Transistors:
1. T1, T2 = BC547
•	Op-Amps A1, A2 = Lm324
•	Transformer, TR1 = 12V/1000mA
•	Relay = 12V SPDT

Circuit Diagram

<img width="461" height="323" alt="Circuit Diagram" src="https://github.com/user-attachments/assets/d2b64280-4781-4fca-a97d-edf36ee3a2ed" />


Circuit Operation Process:

Step-Down and Rectification:

1.	The transformer (TR1) steps down the AC mains voltage.
2.	The rectifier (D1–D4) converts AC to DC, and C1 smooths it.


Voltage Sensing Using Window Comparators:

<img width="593" height="365" alt="Comparator working principle" src="https://github.com/user-attachments/assets/36b086c1-390c-4407-ae50-2095bf7b1077" />

1.	A1 and A2 (in LM324) compare the input voltage to preset reference values.
2.	Z1 and Z2 (Zener diodes) provide reference voltages to determine safe operating limits.
 
Undervoltage and Overvoltage Detection:

1.	While the mains AC voltage is within safe limits, the outputs of the op-amp remain at 0V, which keeps the transistor T1 switched OFF. While T1 remains switched OFF, T2 remains switched ON causing the relay also to be in switched ON position. In this position the relay contacts are at the N/O position which allows the Bulb to be switched ON and working.
2.	If voltage is too high, A1's output goes HIGH, turning ON LED1 and turning ON T1 as a result T2 base is grounded by T1, so T2 turns OFF. When T2 switches OFF, it switches OFF the relay as well, causing its contacts to move towards its N/C position.
3.	If voltage is too low, A2’s output goes HIGH, turning ON LED2 and turning ON T1 as a result T2 base is grounded by T1, so T2 turns OFF. When T2 switches OFF, it switches OFF the relay as well, causing its contacts to move towards its N/C position.
4.	With the relay contacts are at N/C position, the voltage supply is cut off for the Bulb, which safeguards it from the abnormal voltage situation.


Relay Operation:

1.	The relay is controlled by T2.
2.	If voltage is abnormal, the relay disconnects appliances.
3.	If voltage is normal, the relay connects appliances.

Switching Surge Protection:

1.	When a power line is opened and closed a sudden rise in voltage occurs, this is known as Switching Surge.

<img width="495" height="313" alt="image" src="https://github.com/user-attachments/assets/d77a702d-ba74-4b9b-80cf-09e78da86793" />

Figure: Initial high magnitude Inrush current when switching on (Switching Surge).


1.	The switch ON voltage surge is handled by the delay ON timer configuration built using D8, C2, R6.
2.	Whenever there is an input AC mains supply failure or interruption, C2 is fully discharged via R6.
3.	Now, when the AC mains voltage returns, T2 and the relay are inhibited from switching ON instantly.
4.	During this period, C2 slowly charges and keeps the base voltage of T2 below 0.6V causing it to be switched OFF, so that the relay and the home appliances also remain switched OFF.
5.	As C2 charges slowly via R5, after some delay the voltage across C2 reaches above 0.6V which is enough to switch ON T2, relay and the appliances very softly.
6.	This slight delayed switch ON after the mains has restored guards the Bulb from a possible hazardous switch ON voltage surge.







Tuning Process for Window Comparator:

1.	Take a variable DC power supply.
2.	Disconnect the transformer stage from the circuit.
3.	Connect variable power supply to the op amp circuit.
4.	Keep R5 end disconnected from the positive supply.
5.	P1 is used for upper voltage limit point, and the P2 lower voltage limit point.
6.	Make P1 to minimum and P2 to maximum..
7.	Adjust the power supply to around 14V and switch it ON, in this situation the LED1, LED2, LED3 will remain OFF.
8.	Then P1 potentiometer is carefully adjusted until the LED2 just illuminates. By doing this, the higher limit point is tuned.
9.	Then P2 potentiometer is carefully adjusted until the LED2 just illuminates. By doing this, the lower limit point is tuned.
10.	Now restore the connections of the transformer and R5.
11.	Now the circuit is ready for operation.

Practical Circuit:

<img width="976" height="510" alt="image" src="https://github.com/user-attachments/assets/65a676b7-a5dd-4bea-975b-1a8208be4fff" />
<img width="974" height="615" alt="image" src="https://github.com/user-attachments/assets/758c56a5-d4c3-4c00-acf2-5e3d0ef89536" />

Application:
1.	Home Appliance Protection : Protects household devices such as televisions, refrigerators,fans, and air conditioners from overvoltage and undervoltage conditions.
2.	Industrial Equipment Safety : Ensures the safety of sensitive industrial machines, including motors and control systems, by preventing voltage-related damage.
3.	Lighting Protection System : Safeguards lighting devices (bulbs/LEDs) from sudden voltage fluctuations.
4.	Automatic Voltage Cut-off System : Automatically disconnects the power supply when the voltage exceeds or drops below safe limits.
5.	Switching Surge Protection : Provides protection against high inrush voltage when the power supply is restored.
6.	Voltage Monitoring System : Continuously monitors the voltage level and detects abnormal conditions in real time.



Limitation:

1.	Manual Tuning Required : The upper and lower voltage limits must be adjusted manually using potentiometers.
2.	Limited Precision : The system does not provide highly accurate measurements compared to advanced industrial-grade systems.
3.	Voltage-Only Protection : The circuit monitors only voltage; it does not consider current, power factor, or frequency.
4.	Limited Load Handling Capacity : The load capacity depends on the relay rating; higher loads require additional components such as contactors.
5.	Sensitivity to Noise and Temperature : Being an analog circuit, its performance may be affected by electrical noise and temperature variations.
Discussion:
In this project, we tried to improve the surge protector circuit of experiment 6 of our EEE4154 lab manual. In the lab manual, a NE555 timer was used to protect the load from high and low voltage. Here, we used a Window Comparator configuration for high and low voltage protection. Some fundamental advantages of using window comparator instead of NE555 timer are:
1.	Precise Voltage Control: The op-amps act as highly accurate voltage comparators, ensuring a quick and precise response to voltage variations.
2.	Fast Response Time: A NE555 timer, which relies on capacitor charge/discharge cycles, op-amps provide instantaneous output changes when the voltage crosses set thresholds.
3.	Lower Power Consumption: The NE555 timer requires a constant power supply for its internal oscillations, whereas op-amps only consume power when switching states.
4.	Better Stability & Noise Resistance: Op-amps offer better stability in voltage sensing circuits, whereas the NE555 can be affected by power supply fluctuations and noise.
5.	Independent Upper & Lower Voltage Limits: A window comparator with two op-amps allows independent control over upper and lower voltage thresholds. With an NE555, additional circuits (e.g., a Schmitt trigger) would be needed to achieve similar control.

<img width="564" height="272" alt="Table" src="https://github.com/user-attachments/assets/2833bf22-30ba-4af8-ae46-d4ae7e54db46" />

This project that we built can be used with any home appliances for protection purposes. Future improvements may include more compact, user-friendly system, power waste reduction etc.

