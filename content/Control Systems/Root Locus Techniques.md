

# Root Locus Techniques

## Root-locus Form
![[Pasted image 20230520215238.png]]
![[Pasted image 20230523132449.png]]
![[Pasted image 20230523132510.png]]

## Angular equality for positive root locus
![[Pasted image 20230523132530.png]]

## Selecting the parameter value from a root locus
![[Pasted image 20230523132544.png]]

## Primary Rules for Plotting Positive Root Locus
- Rule 1 (pole-starting, zero-ending) The n branches of the locus start at the poles of L(s) and m branches end on the zeros of L(s)
- Rule 2 (real axis) The loci on the real axis are to the left of an odd number of poles plus zeros
- Rule 3 (asymptotes) For large s and K, n-m of the loci are asymptotic to lines at angles $\phi_1$ radiating out from the center point s = a 
![[Pasted image 20230523132855.png]]

## (Secondary) Rules for Plotting Positive Root Locus
- Rule 4. (departure/arrival angles)
– the angle(s) of departure of a branch of the locus from a pole of multiplicity q is given by ![[Pasted image 20230523133004.png]]

Rule 5. (stability crossing)
- the locus crosses the jw axis at points where the Routh criterion shows a transition from roots in the left half-plane to roots in the right half-plane

Rule 6. (break-in, breakaway)
-  the locus have multiple roots at points on the locus where the
derivative is zero, or ![[Pasted image 20230523133109.png]]

- the point will be of multiplicity q if it is on the locus and the first q -1 derivatives are zero there. The branches will approach a point of q roots at angles separated by ![[Pasted image 20230523133146.png|100]]

- and will depart at angles with the same separation, forming an
array of 2q rays (q arrivals, q departures) equally spaced.
	• if the point is on the real axis, then the orientation of this array is given by the real axis rule
	• if the point is in the complex plane, then the angle of departure rule must be applied

## General comments on plotting root locus
• All rules are results of complex variables theories
• Nowadays (as oppose to 1940s), CDA (Control Design Automation) tools available to plot RL (by solving roots numerically) very quickly
	RLOCUS in Matlab
• Skills for roughly plotting RL is still quite useful for verifying that the CDA tool use is not GIGO
• The first 3 (primary) rules are simple, the last 3 (secondary) rules are occasionally used

## Feedback Design using Root Locus

## Basic Dynamic Compensation
- Lead compensation
– high-pass filter
– can approximate PD control
– speeds up responses
- Lag compensation
– low-pass filtering
– can approximate PI control
– improves steady-state accuracy
- Lead-lag compensation
– $(lead) \cdot (lag)$ combined, can approximate PID control
- Notch compensation
– band-stop filtering
– improve stability for lightly damped systems

## Lag Compensation
![[Pasted image 20230523133705.png]]
![[Pasted image 20230523133717.png]]

## Notch Compensation

![[Pasted image 20230523133738.png]]
![[Pasted image 20230523133750.png]]
![[Pasted image 20230523133806.png]]

## Extension of Root Locus

## Negative (zero-degree) Root Locus
![[Pasted image 20230523133918.png]]

## Rules for plotting Negative (zero degree) root locus
![[Pasted image 20230523134001.png]]
![[Pasted image 20230523134015.png]]
![[Pasted image 20230523134027.png]]

## Root Locus for Two Parameters
- Standard RL technique can consider only one parameter at a time
- Most control systems have more-than-one parameters to be designed or studied, e.g.:
	– a P-I-D controller has 3 parameters
	– a inner-loop/outer-loop controller structure (successive loop closure controller design flow)
	– both the values of R and L in a RLC circuit have variations
- One remedy is to iteratively plot RL for one parameter at a time, while fixing others
![[Pasted image 20230523134232.png]]

## Effects of time delay
![[Pasted image 20230523134257.png]]

## Pade approximation for time delay
![[Pasted image 20230523134323.png]]
![[Pasted image 20230523134413.png]]

## HW 5 Assignment 
### chap. 5 review questions

1. Give two definitions for the root locus.
a) The root locus is a graphical representation of the possible locations of the closed-loop poles of a system as a parameter (often the gain) is varied.

b) The root locus is a plot showing the paths of the poles of a transfer function in the complex plane as a parameter changes, typically the gain.

2. Define the negative root locus.
The negative root locus refers to the portion of the root locus that lies on the left-hand side of the complex plane (negative real axis).

3. Where are the sections of the (positive) root locus on the real axis?
The sections of the positive root locus on the real axis are located to the left of an odd number of real-axis finite poles and zeros.

4. What are the angles of departure from two coincident poles at s = -a on the real axis? There are no poles or zeros to the right of -a.
The angles of departure from two coincident poles at s = -a on the real axis are 180 degrees or π radians.

5. What are the angles of departure from three coincident poles at s = -a on the real axis? There are no poles or zeros to the right of s = -a.
The angles of departure from three coincident poles at s = -a on the real axis are 120 degrees or 2π/3 radians, 240 degrees or 4π/3 radians, and 360 degrees or 2π radians.

6. What is the principal effect of a lead compensation on a root locus?
to shift the root locus towards the left-hand side of the complex plane, thus improving the stability of the system. Lead compensation can help to increase the phase margin and reduce the settling time.

7. What is the principal effect of a lag compensation on the steady-state error to a polynomial reference input?
The principal effect of a lag compensation on the steady-state error to a polynomial reference input is to decrease the steady-state error. Lag compensation increases the low-frequency gain of the system, improving the tracking of the reference input signal.

8. What is the principal effect of a lag compensation on a root locus in the vicinity of the dominant closed-loop roots?
The principal effect of a lag compensation on a root locus in the vicinity of the dominant closed-loop roots is to pull the root locus closer to the original dominant poles. This effect increases the damping and stability of the system.

9. Why is the angle of departure from a pole near the imaginary axis especially important?
The angle of departure from a pole near the imaginary axis is particularly important because it determines the direction in which the root locus branches towards the complex plane. It influences the stability and dynamic response of the system. A small change in the angle of departure can lead to significant changes in the closed-loop behavior.

10. Define a conditionally stable system.
A conditionally stable system is a system that can be stable or unstable depending on certain conditions. It means that the system may exhibit stable behavior within a specific range of parameters, but outside that range, it becomes unstable.

11. Show, with a root-locus argument, that a system having three poles at the origin MUST be conditionally stable
A system having three poles at the origin (s = 0) must be conditionally stable. To show this using a root-locus argument, we consider a system with three poles at the origin. Since the poles are at the origin, the system is open-loop unstable. As we increase the gain, the root locus will move away from the poles at the origin, but it will always approach the poles at the origin. Therefore, the system cannot become stable regardless of the gain value, indicating that it is conditionally stable.

### 5.14 
![[Pasted image 20230523200137.png]]

The characteristic equation: 
$$L(s) = \frac{10s}{s^2 + s+ 10}$$
```
num = [10 0];
den = [1 1 10];
L = tf(num, den);

desired_damping_ratio = 0.6;

% Calculate the poles and zeros of the transfer function
[num_roots, den_roots] = tfdata(L, 'v');
poles = roots(den_roots);

% Calculate the desired pole location based on the damping ratio

desired_pole = -desired_damping_ratio * real(poles(1));

% Calculate the gain for the desired pole location

desired_gain = abs(polyval(num_roots, desired_pole) / polyval(den_roots, desired_pole));

disp(['The desired root locus point with 0.6 damping: ', num2str(desired_pole)]);

disp(['The corresponding gain (k): ', num2str(desired_gain)]);
```

this returned: 
k: 0.28874

![[Pasted image 20230523203432.png|200]]

### 5.20
![[Pasted image 20230523200340.png]]

plots:  (a and b are reversed)
![[Pasted image 20230523203936.png]]

### 5.27 #TODO
![[Pasted image 20230523200406.png]]

### 5.33
![[Pasted image 20230523200450.png]]
(a) The locus in this case is the imaginary axis and cannot meet the specs for any K
(b) The specs require that $\zeta>0.6, \omega_n>18$. 
start with  $z=15$  - > The locus will be a circle with radius 15

Because of the zero, the overshoot will be increased and plot indicates that we'd better make the damping greater than 0.7. 
we can lower the overshoot by setting the zero at a low value and putting the poles on the real axis. The plot shows the result if $D=25(s+4)$.

(c) In this case, we take $D(s)=20 \frac{s+4}{0.01 s+1}$

(d) With the resonance present, the only chance we have is to introduce a notch as well as a lead. The compensation resulting in the plots shown is $D(s)=11 \frac{s+4}{(0.01 s+1)} \frac{s^2 / 9.25+s / 9.25+1}{s^2 / 3600+s / 30+1}$

![[Pasted image 20230604203458.png]]
![[Pasted image 20230604203515.png]]
![[Pasted image 20230604203536.png]]

### 5.42
![[Pasted image 20230523200612.png]]
$L(s)=\frac{s+1}{s^2+s+1}$. the system is stable for all $a>-1$. The complete locus is a circle of radius 1 centered on $s=-1$.