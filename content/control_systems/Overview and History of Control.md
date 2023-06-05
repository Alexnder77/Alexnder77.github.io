# Overview and History of Control

## Overview
- This is a mathematics-intensive engineering course.  Self preview/review very important.  
- Main focus is classical (frequency-domain) control  theory which for decades is the foundation of rigorous control engineering education in universities worldwide.

## Course description
• Control is the action of causing a system variable to approach some desired value.  
• Control is a fundamental and universal problem-solving approach in not only traditional but also interdisciplinary fields.  
• A control system, in a very general sense, is a system with an (reference) input that can be applied per the desired value and an output from which how well the system variable matches to the desired value (e.g., errors) can be determined

## Course goals
Basic:  
– Awareness of the strength and the importance of control systems, especially the effectiveness of feedback  
– Ability of deriving dynamic models and simulating dynamic responses  
– Ability of analyzing and designing feedback controllers for linear SISO systems in the frequency domain using root locus and frequency response techniques

Bonus:  
– Awareness of some advanced control topics (e.g., state-space methods, digital control, and nonlinear systems)  
– Development of technical writing skills in English

## What is Control Engineering?  
• “Control is the process of causing a system variable to conform to some desired value, called a reference value .”
• “A control system is a system in which a desired effect (or objective) is achieved by operating on the various manipulable inputs to the plant until the output, which is a measure of the desired effect, falls within an acceptable range of values.”

A methodology to maintain system functioning and enhance system performance  
• Any engineering/math. problem associated with constraining or minimizing the difference (error) between desired output (yd) and actual system output (y) w.r.t. some decision (control/input) variable(s) (r or u)  
– involved with mathematical optimization  
• e.g. Least-square problems: $min_U ||Y_d−Y||^2$, 
where Y=AU: a vector of system output; 
U: a vector of decision (input) variables; 
A: a known system model matrix.  
– can represent a rocket propulsion problem, or DVD read-head positioning prob., an estimation prob. for wireless communication, or wafer alignment prob., etc.  
• With this general sense, amazingly, quite many system engineering problems fall within the scope of control engineering!!  
– e.g. signal processing, communication, circuit/photomask design...  
– There are always problems/jobs for control engineers to solve/do!!  
– Very powerful generalization once comprehended

Two major approaches in control  
• Feedforward (FF) / open-loop  
– UFF is not a direct function of system output (y)  
• Feedback (FB) / closed-loop  
– UFB is a function of system output (y)  
• Almost all control textbooks talk only about FB and the associated stability properties. However, both FF and FB should be considered in a complete controller design.  
– FF is effective if the disturbance can be predicted or measured.  
• not effective if there is un-measurable disturbances or if the (open-loop  
unstable) system needs stabilization  
• can be more effective in performance enhancement (vs. FB closed-loop  
stability usually a concern/tradeoff)  
• usually readily solved by mathematical optimization  
– FB is effective if the disturbance is unpredictable or un-measurable,  
and for stabilizing (open-loop unstable) systems  
• FB only: errors have to happen before being corrected!  
• e.g., driving a car in a very thick fog, or by just looking at the rear mirrors  
– Try to study/consider both FF and FB in practice!!  

FF/FB  
• The feedback method corrects the current or next control input based on the current and past measurement of the output.  
• The feedforward method does not use the output measurement directly. Instead, it predicts the best control input based on some assumptions, e.g. the prior knowledge  
of reference input and deterministic disturbances.  

![[Pasted image 20230516155256.png]]
## Elementary Feedback Control Block Diagram
![[Pasted image 20230516155330.png]]

## Open-loop vs. closed-loop Control
In open-loop control, the output of the system is not used to adjust the input. In closed-loop control, the output of the system is used to adjust the input in order to keep the system's output at a desired value.

Open-loop control is simpler to design and implement than closed-loop control. However, open-loop control is not as accurate as closed-loop control. This is because the output of the system can vary from the desired value due to disturbances.

Closed-loop control is more accurate than open-loop control because the output of the system is constantly being adjusted to keep it at the desired value. However, closed-loop control is more complex to design and implement than open-loop control.

Examples of open-loop control systems:
-   A thermostat that turns on a heater when the temperature in a room falls below a certain level and turns off the heater when the temperature rises above that level.
-   A cruise control system that maintains a car's speed at a set level.
-   A sprinkler system that turns on when the ground moisture level falls below a certain level.

Examples of closed-loop control systems:
-   A system that controls the speed of a motor by adjusting the amount of current that is flowing through the motor.
-   A system that controls the position of a robot arm by adjusting the angles of the joints in the arm.
-   A system that controls the temperature of a chemical reaction by adjusting the amount of heat that is being added to the reaction.

In general, closed-loop control is preferred over open-loop control because it is more accurate. However, open-loop control may be sufficient in some cases where accuracy is not critical.

## History
**Classical Control (1940s)**
-   Started with feedback amplifier design
-   Used vacuum tubes, operational amplifiers, and high open-loop gains
-   Based on Laplace transforms in the s-domain
-   Model uncertainty captured in Bode/frequency response plots (e.g., gain/phase margins)
-   Can be extended to the z-domain
-   Uses root locus, lead-lag compensation, Nyquist plot, and Nichols chart

**Modern Control (1960s)**
-   Used for spacecraft control (rigid body) and MIMO systems
-   Works well when model uncertainty is negligible
-   Uses state-space, pole placement, and linear-quadratic optimal control

**Post-Modern or Contemporary Control (1980s-Present)**
-   Used for flexible structures (e.g., hard/optical disk drives, piezo-actuators)
-   Extends state-space approach to handle model uncertainties
-   Utilizes advanced optimization techniques to directly solve controller parameters
-   Uses robust control (H∞, L1, μ-synthesis/DKIT), multi-objective synthesis (mixed H2/H∞, DQIT), and other methods

## HW 1 
### Review questions
**1. What are the main components of a feedback control system?**
-   **Sensor:** The sensor measures the process variable and sends the signal to the controller.
-   **Controller:** The controller compares the measured value to the setpoint and generates an output signal to the actuator.
-   **Actuator:** The actuator takes the output signal from the controller and applies it to the process to change the process variable.
-   **Process:** The process is the physical system that is being controlled.
-   **Setpoint:** The setpoint is the desired value of the process variable.

**2. What is the purpose of the sensor?**

To measure the process variable and send the signal to the controller. 

**3. Give three important properties of a good sensor.**

-   **Accuracy:** The sensor should be able to measure the process variable accurately.
-   **Sensitivity:** The sensor should be able to detect small changes in the process variable.
-   **Response time:** The sensor should be able to respond to changes in the process variable quickly.

**4. What is the purpose of the actuator?**

To take the output signal from the controller and apply it to the process to change the process variable. 

**5. Give three important properties of a good actuator.**
-   **Power:** The actuator should be able to apply enough force or torque to the process to change the process variable.
-   **Reliability:** The actuator should be able to operate for a long time without breaking down.
-   **Control range:** The actuator should be able to move the process variable over a wide range of values.

**6. What is the purpose of the controller?**

To compare the measured value to the setpoint and generate an output signal to the actuator. 

**7. What are the input(s) and output(s) of the controller?**

The input(s) of the controller are the measured value and the setpoint. The output(s) of the controller are the signal to the actuator.

**8. What physical variable(s) of a process can be directly measured by a Hall effect sensor?**

A Hall effect sensor can be used to measure the position, speed, or direction of a magnetic field.

**9. What physical variable is measured by a tachometer?**

The speed of a rotating shaft.

**10. Describe three different techniques for measuring temperature.**

1.  **Resistance temperature detector (RTD):** An RTD is a resistor that changes its resistance with temperature.
2.  **Thermocouple:** A thermocouple is a device that generates an electric current when two different metals are connected and there is a temperature difference between them.
3.  **Pyrometer:** A pyrometer is a device that measures the infrared radiation emitted by an object to determine its temperature.

**11. Why do most sensors have an electrical output, regardless of the physical nature of the variable being measured?**

Most sensors have an electrical output because it is easy to transmit electrical signals over long distances and to process them electronically.

[FPE] Prob. 1.1 (a)(d) 
Draw a component block diagram for each of the following feedback control systems.  
(a) The manual steering system of an automobile  

![[The manual steering system of an automobile.excalidraw]]

(d) Watt's steam engine with fly-ball governor
![[Watt's steam engine.excalidraw]]
3. [FPE] Prob. 1.8
Feedback control requires being able to sense the variable being controlled. Because  
electrical signals can be transmitted. amplified, and processed easily, often we want to have a sensor whose output is a voltage or current proportional to the variable being measured. Describe a sensor that would give an electrical output proportional to:  
**(a) pressure**  
Piezoelectric Pressure Sensor, it consists of a piezoelectric material that generates an electrical charge when pressure is applied. The generated electrical charge or voltage is proportional to the pressure being applied.

**(b) temperature**  
Resistance Temperature Detector - An RTD uses a temperature-sensitive resistor, usually made of platinum, nickel, or copper, whose resistance changes with temperature. The change in resistance is proportional to the change in temperature. By passing a constant current through the resistor and measuring the voltage drop across it, an electrical output proportional to temperature can be obtained.

**(f) linear position**  
Linear Potentiometer: A linear potentiometer is a variable resistor with a sliding contact that moves along a resistive track. The position of the contact determines the resistance, and an electrical output proportional to position can be obtained by measuring the voltage across the potentiometer when a constant current is applied.

**(g) linear velocity**  
Optical Encoder: An optical encoder uses a light source, a photodetector, and a slotted or patterned disk to measure linear velocity. As the disk moves, it interrupts the light beam, causing the photodetector to generate an electrical signal proportional to the velocity of the disk.

**(i) translational acceleration**
Capacitive accelerometer, consists of a fixed plate and a movable plate with a mass attached. As the sensor experiences acceleration, the mass moves, causing a change in capacitance between the plates. This change can be measured as a voltage or current, providing an electrical output proportional to the acceleration.

4. [FPE] Prob. 1.9
Each of the variables listed in prob. 1.8 can be brought under feedback control.  
Describe an actuator that could accept an electrical input and be used to control the  
variables listed. Give the unites of the actuator output signal

a) Proportional solenoid valve, an actuator that can regulate fluid pressure by adjusting the valve's opening in response to an electrical input signal. The electrical input controls the solenoid's magnetic field strength, which in turn controls the valve position. The actuator output signal is fluid pressure, usually measured in units such as Pascals (Pa) or pounds per square inch (psi).

b) An electric heater with proportional control can accept an electrical input signal to regulate the amount of heat generated. The electrical input controls the power supplied to the heating element, allowing precise temperature control. The actuator output signal is temperature, measured in units such as Celsius (°C)

f) Linear Electric Motor: A linear electric motor is an actuator that converts electrical energy into linear motion. It consists of a stator with coils and a moving part (slider or plunger). The electrical input signal controls the current in the coils, generating a magnetic field that drives the moving part. The actuator output signal is linear displacement, measured in units like millimeters (mm) or inches.

g) A DC motor with a gearbox and a linear drive (such as a lead screw or a belt drive) can be used to control linear velocity. The electrical input signal controls the motor's speed, which is then translated into linear motion through the gearbox and linear drive. The actuator output signal is linear velocity, measured in units like millimeters per second (mm/s) or inches per second (in/s).

i) A voice coil actuator, an actuator that consists of a coil of wire and a magnetic field source, similar to the setup in a loudspeaker. The coil is attached to a mass or movable part, and the electrical input signal controls the current in the coil. This generates a magnetic field that interacts with the field source, producing a force that accelerates the mass. The actuator output signal is translational acceleration, measured in units such as meters per second squared (m/s²) or g (9.81 m/s²).

5. Read the pdfs
[[Future Directions in Control in an Information-Rich World]]
[[The Impact of Control Technology (IoCT) summary]]