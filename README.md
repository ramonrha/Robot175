# RobotDSP
Embeded DSP software

The DSP that will be used in this project is from the family C2000 Microcontrollers TMS32028377s LaunchPad Development kit from Texas Instruments. 

--------------------------
Big picture of the project
--------------------------
The project consist on a 2 degree of freedom robot control, with the aim of identify the friction in the robot by performing several experiments to determina the static and dynamic friction of the robot links. For this purpose it is required to colect al information regarding to the motors atached to each link such as the Current, the position, the speed and the voltage applied to the motors. The information collected by the DSP will be sended to a computer to process it after.

With that information stored, it will be possible to identify not only the model of the motors but also the model of the friction in the robot. The friction values that will be determined are: Static friction, Coulomb friction and Viscous friction. Finaly dynamic friction models will be developed such as the Dhal model, Lu-Gre model, Stribek, etc.

The second and last task the DSP will perform is to control the robot by using the different estimated models. Therefore, the control loop will be embeded in the DSP no matters it nature. 

-------------------------------------
Additional hardware used in the robot
-------------------------------------
The robot has one rotary encoder for each motor (2), one Current sensor Allegro to measure the Current all time in each motor, one mosfet driver from Texas Instruments with the part number:DRV8704EVM CB, which has 8 mosfter to controll two motors by using a H bridge for each one, the robot has two DC brushed motors of 12 V each of almost 40 watts and each motor uses a transmision to increas the Torque by reducing the speed of the chaft with a relation 1/18 and 1/19.7 for the small motor and the big motor respectively.

--------------------------------------------------
How the information will be sended to the computer
--------------------------------------------------
The information will be sended to the computer through through RS232 every 5 ms with the next information:
1. position of motor1
2. position of motor2
3. current of motor1
4. current of motor2
All the information of above will be sended through a stream of 13 bytes, using the fist byte as the beggining of the stream with a flag 0XAF. In case this flag is not detected by the computer, the information will be discarted by the computer and a new one
