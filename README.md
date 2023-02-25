# Engine-and-Fuel-Saving-System

PROBLEM:- I am working in a workshop of fleet size of 310 CNG buses and we faced a big issue of engine failure from very long.

A - The major cause of Engine failure are:-
            
1.OVERHEATING - 
If any vehicle is running with overheating issue and driver not observe that engine is started to getting overheated and won't stop vehicle even after crossing safe working temperature zone then, due to overheating issue engine can get seized or say failed. This type of engine failure may range from minor repairs to even complete engine failure in worst cases. Our cost of replacement of this type of failure is ranging from 50 Thousand INR upto 2 Lakh INR.

2.LUBE LEAKAGE -
If due to leakages or due to may be some under chassis accident, engine oil starts to leaking and driver not observe that on time then, complete engine will be get seized or say failed. This type of failure requires complete engine replacement as majority of parts are badly hampered and are out of repairing. Our complete engine replacement costs us around 2 Lakhs INR.
             
B - Another issue is with is due very big fleet size, keep the checking for any vehicle is standing in workshop or in parking area in engine start condition is tough and not consistent and also requires too much of dedicated manpower. Also there are times when, driver not turned off engine when not in use. These both issues wasted a lot of fuel which can be saved easily using right technology.
           
C. - Another is related with overcharging of alternator and if not stopped on time can cause premature battery failures, electronic components failure and in worse case may catch fire due to wiring system is not able to withstand this excessive voltage load.
           
D - Another is related with self starter, when due to some reason, could be clutch life is over and clutch is failed when vehicle is in use. Driver many times take that vehicle back to workshop by starting the vehicle when its in gear(Beacuse due to clutch failure, gears won't engage after engine is started). This will puts massive amount of pressure to all electrical components of self starter and even on battery as well and thus they failed early on.
           
SOLUTION:-

As most of failure are due to negligence and can be controlled easily. We designed a system to stop these failures. There are some sensors which are already fitted with standard engine assembly and are used to control emission and all this sensor data can be accessed using CAN PROTOCOL. We need following data from ECU to make system work and fool proof as well:-
1-ENGINE OIL TEMPERATURE
2-ENGINE OIL PRESSURE
3-COOLANT TEMPERATURE
4-ENIGNE RPM
5-ACCELERATOR POSITION
6-BATTERY VOLTAGE
7-NEUTRAL SENSOR
           
We need to fit an extra neutral sensor as exisiting sensor is of mechanical type and its life is very limited too and we are using a CONTACTLESS TYPE NEUTRAL SENSOR for this project.
Another is ENGINE OIL TEMPERATURE SENSOR because data of this sensor is not available with CAN PROTOCOL and ENGINE OIL PRESSURE SENSOR as this sensor is not attached with ECU and only provides reading to INSTRUMENT CLUSTER ONLY.
           
Intially we decoded CAN PROTOCOL first and calibirated its data accordingly, next start to read data from ENIGINE OIL PRESSURE SENSOR AND ENGINE OIL TEMPERATURE SENSOR using a 12 bit Analog to Digital Convertor and made calibiration accordingly. NEUTRAL SENSOR is connected via a mosfet circuit to provide feedback to microcontroller Now a PCB is designed using MCP2515 CAN IC, MCP3204 12 bit ADC, AN RTC CLOCK IC and a ATMEGA328P microcontroller, also other supported components are added to system like voltage regulators, capacitors, resistances,inductors, mosfets(To control self, ignition and isolator relays), diodes, tvs diodes, etc. A display is also used to display all information to driver. And system is designed such a way that if ground or power supply both are not present in system, system will not turned on or patially turned on and starts to malfuncting or components may fail.

After PCB is assembled, we use data from CAN and ADC to monitor all sensor and NEUTRAL SENSOR feedback from mosfet circuit. If any sensor is disconnected from system, system will stop engine and won't allows engine to start unless that disconnected sensor is connected to system again. If any reading coming from sensor is going out of its safe working limits, system will start to give warning on display screen and also produce sound via buzzer attached with system and if driver won't stop vehicle and continue to driver, system will interven in and stop the vehicle automatically and won't allows to start engine again unless all sensors reading came back to its safe working zone limits. RTC, ENGINE RPM SENSOR, NEUTRAL SENSOR AND ACCELERATOR POSITION SENSOR is utilize to monitor engine ideal condition and stops engine after 5 minutes of ideal usage automatically and whole system will go to sleep after 15 minutes if left unattended by turning off isolator(Also known as remote battery cut-off switch) relay. To start the system again user need to toggle NEUTRAL SENSOR BY SHITING GEAR BACK AND FORTH or by turn ignition, self or isolator switches on or off.
