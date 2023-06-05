
# Frequency response method

probably the most widely used and the most effective for designing control systems  
– provide good designs with plant model uncertainty  
• one of the main reasons to use feedback  
• motivated robust control theories  
– ease of integration with experimental information (freq. resp. measurement)  
• determining/fitting plant poles and zeros (as in root locus) not necessarily needed

## Contents  
• Frequency Response Fundamentals  
• Bode Plot Sketching Technique  
• Nyquist Stability Criterion  
• Stability Margins  
• Lead/Lag Compensator Design Techniques

## Frequency Response Fundamentals  
### Frequency response for LTI systems

Frequency response is the system steady-state (t →$\infty$) response to a sinusoidal signal
– Note: if u = 0 for t < 0 and $u = sin(\omega t)$, then there will be a transient response
	• the transient may not settle due to system stability (more later)
– a common myth is that frequency response does not exist for unstable systems.

• For LTI systems, frequency response is also a sinusoid of the same frequency, with gain/phase of $H(j\omega)$ (for continuous-time sys.) or $H(e^{j\omega})$ (for discrete-time sys.)
	– freq. resp. measurement plot: plotting the measured/estimated gain |H| and phase $\angle H$ vs. freq. $\omega$
	– Bode plot: plotting the gain vs. freq. in log-log, and the phase vs. freq. in linear-log scales
	
![[Pasted image 20230604193516.png]]

### Initial response to a sinusoid input
![[Pasted image 20230604193549.png]]
![[Pasted image 20230604193603.png]]
![[Pasted image 20230604193628.png]]

### Bode plot/freq. resp. of a lead compensator
![[Pasted image 20230604193717.png]]

### Frequency response specifications
![[Pasted image 20230604193733.png]]
![[Pasted image 20230604193817.png]]

### Advantages of Bode plots
- Can design dynamic compensators entirely based on Bode plots
- Can be measured experimentally (freq. meas. by sweepsine techniques)
- Taking log for mag. simplifies multiplication to add for systems in series connection (better human perception for synthesis)
- Taking log for freq. permits a much wider range to be displayed
- Bode plots can be quickly sketched by hands (as root locus plots) for intuitive analysis and compensator designs

## Bode Plot Sketching 
### Bode plots - decomposition
![[Pasted image 20230604194922.png]]
![[Pasted image 20230604194932.png]]
![[Pasted image 20230604194943.png]]
![[Pasted image 20230604194955.png]]
![[Pasted image 20230604195008.png]]
![[Pasted image 20230604195020.png]]
![[Pasted image 20230604195037.png]]
### Nonminimum-phase systems
![[Pasted image 20230604195102.png]]
### Steady state errors 
![[Pasted image 20230604195124.png]]

## Nyquist Stability Criterion
### Neutral stability
![[Pasted image 20230604195203.png]]

- In many cases, increasing feedback gain decreases stability
	– but sometimes the reverse is true
	– root locus can be used for analysis but requires open-loop pole and zero locations (parametric transfer function)

- Nyquist plot relates open-loop frequency response to the number of closed-loop poles in the RHP
	– plot real and imag. parts of G(s), count number of encirclements
	– (usually) no need to know open-loop poles and zeros (cf. Routh table)
	– based on [[Frequency response method#Argument principle|Argument principle]]
### Nyquist plot for a 2nd-order system
![[Pasted image 20230604195437.png]]
### Argument principle
![[Pasted image 20230604195455.png]]
![[Pasted image 20230604195644.png]]

### CT Nyquist stability criterion
![[Pasted image 20230604195714.png]]
![[Pasted image 20230604195727.png]]
![[Pasted image 20230604195740.png]]
![[Pasted image 20230604195755.png]]
![[Pasted image 20230604195808.png]]
![[Pasted image 20230604195824.png]]

## Stability Margins
For many “common/simple” systems (e.g., no open-loop unstable poles, increasing gain reduces stability)
- Gain margin (GM): The factor by which the gain can be raised before instability
- Phase margin (PM): The amount by which the phase of G(j$\omega$) exceeds -180$^{\circ}$  when | KG(j$\omega$)| =1
- widely used, but can have ambiguities, USE WITH CAUTION!

Vector gain margin (VGM)
- the shortest distance from the Nyquist plot to the -1 point
- leads to robust stabilization conditions in robust control

### Neutral stability in terms of GM and PM
![[Pasted image 20230604200240.png]]
![[Pasted image 20230604200256.png]]
![[Pasted image 20230604200307.png]]
![[Pasted image 20230604200337.png]]

## Lead/Lag Compensator Design Techniques
![[Pasted image 20230604200404.png]]
![[Pasted image 20230604200419.png]]
![[Pasted image 20230604200432.png]]
![[Pasted image 20230604200447.png]]
![[Pasted image 20230604200500.png]]
![[Pasted image 20230604200513.png]]
![[Pasted image 20230604200536.png]]
![[Pasted image 20230604200549.png]]
![[Pasted image 20230604200606.png]]
![[Pasted image 20230604200617.png]]
![[Pasted image 20230604200630.png]]
![[Pasted image 20230604200639.png]]

### PID/Lead-Lag Compensation
![[Pasted image 20230604200653.png]]

### Findings from lead and lag designs
- Both can be used to meet LF and PM specs.
	– lead usually leads to higher bandwidth
	– in practical systems, saturation and sensor noise may prevent using lead to raise BW much higher than a system’s natural frequency. Lag preferred!

- Can be combined into a lead-lag compensator, e.g.
	– use lag for LF specs only
	– use lead for HF specs only
	– may reduce the (ambiguous) design iteration required

- Both are iterative procedures, rely on accumulated design experiences
	– Concept of Control Design Automation (CDA) is critical to facilitate practical control applications

	- set. the specifications
	- CDA quickly gives controller parameters to meet (most) specs
	- verification before implementation (by simulation)
	- verification after implementation (with test data)
	- similar with EDA flow. CDA can be a part of system level design

## HW 6 Assignment
### chap. 6 review questions

1. Why did Bode suggest plotting the magnitude of a frequency response on log-log coordinates?
Because it simplifies the representation of the frequency response of the systems. (On a log-log plot, multiplicative factors become additive, and exponentials become linear)

2. Define a decibel.
A decibel (dB) is a logarithmic unit used to express the ratio of two values of a physical quantity, often power or intensity.

In terms of power the dB scale can be defined as: $dB = 10 log_{10}(P1/P2)$

3. What is the transfer function magnitude if the gain is listed as 14 db?

To convert from dB to magnitude, we use the following formula:$$\text{Magnitude} = 10^{\frac{\text{dB}}{20}}$$Plugging in the given gain of 14 dB, we get:$$\text{Magnitude} = 10^{\frac{14}{20}} \approx 3.98$$
4. Define gain crossover.
Gain crossover is a point in a Bode plot where the magnitude plot crosses 0 dB.

5. Define phase crossover.
Phase crossover is the frequency at which the phase shift is 180 degrees in a Bode plot. It's a critical frequency as it is a precursor to potential instability (as the system will start to feedback positively at this point).

6. Define gain margin, GM.
Gain margin (GM) is a measure of how much change in system gain can be tolerated before the system becomes unstable. It is measured in dB and is calculated at the phase crossover frequency (where phase is 180 degrees).

7. Define phase margin, PM.
Phase margin (PM) is a measure of how much additional phase lag at the gain crossover frequency can be added to the system before it becomes unstable. It's an important measure of the relative stability of a control system.

8. What Bode plot characteristic is the best indicator of the closed-loop step response overshoot?
1The best indicator of the closed-loop step response overshoot on a Bode plot is the phase margin. A smaller phase margin typically results in more overshoot.

9. What Bode plot characteristic is the best indicator of the closed-loop step response rise time?
The best indicator of the closed-loop step response rise time on a Bode plot is the gain crossover frequency. Higher gain crossover frequency corresponds to lower rise time.

10. What is the principal effect of a lag compensation on Bode plot performance measures?
Lag compensation generally increases the phase margin which improves the stability of a system. However, it reduces the bandwidth of the system which can make the system slower.

11. What is the principal effect of a lead compensation on Bode plot performance measures?
generally increases both phase and gain margins, which improves the stability of the system. It can also increase the bandwidth, which can make the system respond quicker.

12. How do you find the $K_v$ of a Type l system from its Bode plot?
The velocity error constant $K_v$ of a Type 1 system from its Bode plot is calculated as the inverse of the magnitude of the system's frequency response as the frequency approaches 0.

13. Why do we need to know beforehand the number of open-loop unstable poles in order to tell stability from the Nyquist plot?

The number of open-loop unstable poles is needed to tell stability from the Nyquist plot because it is used in the Nyquist Stability Criterion. According to the criterion, if the number of counterclockwise encirclements of the point -1 in the Nyquist plot equals the number of open-loop unstable poles, then the system is stable.


14. What is the main advantage in control design of counting the encirclements of $-1/K$ of $D(j\omega)G(j\omega)$  rather than of $KD(j\omega)G(j\omega)$ rather
because the former is the actual location of the critical point in the Nyquist plot for a closed-loop system with unity feedback. So it directly gives us the information about stability of the closed-loop system.

15. Define a conditionally stable feedback system. How can you identify one on a Bode plot?
A conditionally stable feedback system is a system that is stable for a certain range of gain values but becomes unstable if the gain exceeds this range. On a Bode plot, this system can be identified by noting the gain margin. If the gain margin is small, or the gain plot intersects the 0 dB line at a frequency where the phase is already -180 degrees or less, then the system is conditionally stable.

16. A certain control system is required to follow sinusoids, which may be any frequency in the range $0 \leq w_l \leq$ 450 rad/sec and have amplitudes up to 5 units, with (sinusoidal) steady-state error to be never more than 0.01. Sketch (or describe) the corresponding performance function $W_1(\omega)$.
For a control system required to follow sinusoids in the range $0 \leq w_l \leq$ 450 rad/sec with amplitudes up to 5 units, and the steady-state error to be never more than 0.01, the performance function $W_1(\omega)$ should specify that for frequencies up to 450 rad/sec, the magnitude response of the system should be at least 500 (since 5/0.01 = 500) to ensure that the steady-state error remains below the specified limit. Thus, $W_1(\omega)$ would be a constant line at 54 dB (since 20log10(500) = 54) for frequencies from 0 to 450 rad/sec on a Bode plot.

### 6.2
![[Pasted image 20230604194648.png]]

### 6.8
![[Pasted image 20230604194726.png]]

### 6.18
![[Pasted image 20230604194807.png]]

### 6.58
![[Pasted image 20230604194833.png]]

### 6.52
![[Pasted image 20230604194856.png]]

