# Control Systems - Dynamic Models lecture notes 
## The Need for Mathematical Models in Control
-   The system output y is a function of system input u, i.e., y = G(u); the constraining relation G representing the system dynamic characteristics.
-   The feedback approach corrects the current or next control input based on the current and past measurement of the output.
-   The overall goal of feedback control is for the output of a process to follow a desired reference input, regardless of any external disturbances and any changes of the process dynamics.
-   Model-based controller design (MBCD) takes advantage of the prior knowledge on the system/process to be controlled during the design process.
-   The first step in MBCD is to develop a reasonably accurate mathematical representation (dynamic model, Gm) of the system/process to be controlled; modeling error Δ = Gm − G.

## Typical Usage of Process Models
-   Simulating/predicting the process output y w.r.t. some given process input u before controller design when a model-based control design algorithm is used.
-   Designing a controller when a model-based control design algorithm is used.
-   Simulating/predicting the process output when there is a designed controller attached.

## Two Approaches to Build a Mathematical Model for a System
-   Derivation from physical laws.
    -   E.g., Newton equations, KVL, KCL...
    -   Difficult for complex systems
    -   Parameter values not always (accurately) available
    -   Good for getting insights & determining system orders
-   System identification from observed system response data.
    -   Knowledge of exact system physics not always needed
    -   Can use “black box” input-output model forms, i.e., forms not directly corresponding to the physical structure of the system
    -   Can accurately estimate parameter values from input-output data
-   Bottom line: Use the insight from the first approach to determine a “suitable” model form/structure and system order for the second approach.
-   May need several iterations to obtain an acceptable model.

## A Few Common Physical Systems
-   Mechanical systems
-   Electrical circuits
-   Electromechanical systems
-   Heat and fluid-flow models
-   Complex mechanical systems

## Summary: Developing Equations of Motion (EOM) for Rigid Bodies
1.  Assign variables (e.g., x, θ) both necessary and sufficient to describe an arbitrary position/state of the object.
2.  Draw a free-body diagram of each component. Indicate all forces acting on each (rigid) body and their reference directions. Also indicate the accelerations of the center of mass with respect to an inertial reference for each body.
3.  Apply Newton’s law in translation (SF = ma) and/or rotation (SM = Ia) form(s).
4.  Combine the equations to eliminate internal forces.
5.  The number of independent equations should equal the number of unknowns.
6.  (optional) Linearize the EOMs for linear-system analysis.

## One-Mass Cruise Control Model #example
### Exapmle 2.1
![[Pasted image 20230512145846.png|200]]
Equation of motion: $\Sigma \mathbf{F}=m \mathbf{a}$ 
car position: $x$ 
velocity: $v=\dot{x}$ 
driving force by engine: $u$ 
dynamic friction coefficient $b$ 
linear dynamic friction $b v=b \dot{x}$ (air/body, wheel/road... combined) 

Ignore rotational inertia of the wheel $\rightarrow u-b \dot{x}=m \ddot{x} \leftrightarrow \ddot{x}+\frac{b}{m} \dot{x}=\frac{u}{m} \leftrightarrow \dot{v}+\frac{b}{m} v=\frac{u}{m}$

### Example 2.2
![[Pasted image 20230512150524.png|200]]

Assume a solution in the form $v=V(s) e^{s t}$ 
with an input of the form $u=U(s) e^{s t}$ 
( if $s=\sigma+j \omega \rightarrow U(s) e^{s t}=U(s) e^{(\sigma+j \omega) t}=$ $\left.U(s) e^{\sigma t} e^{j w t}=U(s) e^{\sigma t}(\cos (\omega t)+j \sin (\omega t))\right)$ 
$\dot{v}=s V(s) e^{s t}$
$$
\dot{v}+\frac{b}{m} v=\frac{u}{m} \rightarrow\left(s+\frac{b}{m}\right) V(s) e^{s t}=\frac{u}{m} U(s) e^{s t} \rightarrow \frac{V(S)}{U(S)} = \frac{\frac{1}{m}}{s+\frac{b}{m}}

$$
#### Numerical simulation

![[Pasted image 20230512150805.png]]
![[Pasted image 20230512150826.png]]

## Two-mass vehicle suspension model #example

![[Pasted image 20230512151420.png|400]]

$$
\Sigma \mathbf{F}=m \mathbf{a}
$$
For mass 1 (1 wheel):
$$
b(\dot{y}-\dot{x})+k_s(y-x)-k_w(x-r)=m_1 \ddot{x}
$$
For mass 2 ( $1 / 4$ body):
$$
-k_s(y-x)-b(\dot{y}-\dot{x})=m_2 \ddot{y}
$$
Rearrange:
$$
\begin{aligned}
& \ddot{x}+\frac{b}{m_1}(\dot{x}-\dot{y})+\frac{k_s}{m_1}(x-y)+\frac{k_w}{m_1} x=\frac{k_w}{m_1} r \\
& \ddot{y}+\frac{b}{m_2}(\dot{y}-\dot{x})+\frac{k_s}{m_2}(y-x)=0
\end{aligned}
$$
subsitute $d / d t$ with $s$ :
$$
\begin{aligned}
& s^2 X(s)+\frac{b}{m_1}(X(s)-Y(s))+\frac{k_s}{m_1}(X(s)-Y(s))+\frac{k_w}{m_1} X(s)=\frac{k_w}{m_1} R(s) \\
& s^2 Y(s)+\frac{b}{m_2}(Y(s)-X(s))+\frac{k_s}{m_2}(Y(s)-X(s))=0
\end{aligned}
$$
Rearrange:
$$
\frac{Y(s)}{R(s)}=\frac{\frac{k_j b}{m_1 m_2}\left(s+\frac{k_s}{b}\right)}{\left.s^4+\left(\frac{b}{m_1}+\frac{b}{m_2}\right) s^3+\left(\frac{k_s}{m_1}+\frac{k_s}{m_2}+\frac{k_w}{m_1}\right) s^2+\left(\frac{k_k b}{m_1 m_2}\right) s+\frac{k_w k_s}{m_1 m_2}\right)^{-}}
$$

### Satellite attitude control model
![[Pasted image 20230512151743.png]]






## Historical perspective on physics modeling

1687 (Newton, “Philosophiae Naturalis Principia Mathematica”) –laws of motions and gravitation
- combination of calculus developed by him, and work/observation by earlier scientists (N. Copernicus, G. Galilei (strongly suggested F=ma), J. Kepler, etc.)
- actually done 20 years earlier before publishing
- basis for almost all dynamics analysis

Faraday – EM lines of force, induction (Faraday’s Law)

Maxwell – integrate observations by Faraday, Coulomb, and Ampere to Maxwell’s Equations
- concepts of field and waves for EM; light as EM waves, primary colors, constant speed of light
- also stability of Saturn’s rings and FB control systems

1900s (Einstein) – special theory of relativity/addition of relativistic effects to Newton’s laws, partly motivated by that Maxwell’s constant light speed difficult to reconcile with Newton’s laws

![[Pasted image 20230512152534.png]]

Modern physics (after ~1890)
– Theory of relativity 
– Quantum mechanics
- Schrödinger equation
    - Time-dependent Schrödinger equation
    - Time-independent Schrödinger equation
– Quantum field theory
- a theoretical framework for constructing quantum mechanical models of systems classically parametrized (represented) by an infinite number of dynamical degrees of freedom, that is, fields and (in a condensed matter context) many-body systems.
- Quantum electrodynamics: QM generalization of classical electrodynamics including Maxwell’s Equations
– String theory
- attempts to reconcile quantum mechanics and general relativity

## Linearization of Nonlinear Systems
-   Nonlinear systems are often encountered in practice.
-   Linearization is a technique to approximate the behavior of a nonlinear system around an operating point.
-   It involves finding a linear model that closely approximates the nonlinear system in the vicinity of the operating point.
-   Linear models are easier to analyze and design controllers for.
-   Linearization is typically done using Taylor series expansion or small-signal analysis.

## Notes
-   Mathematical models play a crucial role in control systems engineering.
-   They provide a mathematical description of the system behavior and enable analysis and design of control systems.
-   Models can be derived from physical laws or identified from experimental data.
-   State-space representation and transfer function representation are widely used to describe dynamic systems.
-   Linearization is a useful technique for approximating the behavior of nonlinear systems.
-   Overall, control systems and dynamic models provide a foundation for understanding and improving the performance of various engineering systems.

## HW 2 
### review questions 

1. What is a "free-body diagram"? 
A free-body diagram is a visual representation that shows all the forces acting on a single object

2.  What are the two forms of Newton's law? 
	1) Object's motion remains unchanged unless acted upon by a force. 
	2) F=ma

3. For a structural process to be controlled, such as a robot arm, what is the meaning of "collocated control"? "Noncollocated control"? 
Collocated control: Sensors and actuators at the same position. Noncollocated control: Sensors and actuators at different positions.

4. State Kirchhoff's current law.
Total current into a junction equals total current out.

5. State Kirchhoff's voltage Jaw.
Total voltage around a loop is zero.

6. When, why, and by whom was the device named an "operational amplifier"?

7. What is the major benefit of having zero input current to an operational amplifier?
Zero input current allows for ideal voltage amplification.

(Zero input current means that the input impedance of the operational amplifier is infinitely high, which minimizes the loading effect on the input signal source and ensures accurate signal amplification.)

8. Why is it important to have a small value for the armature resistance Ra of an electric motor?

to minimize power losses and maximize efficiency

9. What are the definition and units of the electric constant of a motor?

10. What are the definition and units of the torque constant of an electric motor?
The conversion factor between the motor's torque (in Newton meters) and the current applied to the motor. 

The units are Newton meters per ampere (Nm/A).

11. Why do we approximate a physical model of the plant (which is always nonlinear) with a linear model?
simplification, easier to analyze

12. Give the relationships for (a) heat flow across a substance, and (b) heat storage in a substance.
a) Fourier's law of heat conduction. It states that the rate of heat flow (Q) through a material is directly proportional to the temperature gradient (∆T) across the material and the cross-sectional area (A)

Mathematically:
Q = -k * A * (∆T/∆x)

b) Heat storage in a material is described by the equation 
Q = mc∆T,  
Q - the heat energy transferred, 
m - mass 
c - heat capacity,
∆T  - the change in temperature.

13. Name and give the equations for the three relationships governing fluid flow.

### Prob. 2.5
For the car suspension discussed in Example 2.2, plot the position of the car and the wheel after the car hits a “unit bump” (i.e., r is a unit step) using MATLAB. Assume that m1 = 10 kg, m2 = 350 kg, Kw = 500000 N/m, Ks = 10000 N/m. Find the value of b that you would prefer if you were a passenger in the car


The transfer function was given in the example in Eq. (2.12) in the course book:
![[Pasted image 20230523154007.png]]

using that and the values above we can generate some plots for different values of b using the following code:
```
m1 = 10;
m2 = 350;
kw = 500000;
ks = 10000;
B = [ 1000 2000 3000 4000 ];
t = 0:0.01:2;

for i = 1:4
	b = B(i);
	num = kw*b/(m1*m2)*[1 ks/b];
	den = [1 (b/m1+b/m2) (ks/m1+ks/m2+kw/m1) (kw*b/(m1*m2)) (kw*ks/(m1*m2))];
	sys = tf(num,den);
	y = step(sys, t);
	subplot(2,2,i);
	plot(t, y, ':');
	legend('Wheel');
	ttl = sprintf('Response with b = %4.1f ',b);
	title(ttl);
end
```

![[Pasted image 20230523153636.png]]

From the figures, b = 3000 would be acceptable. There is a lot of overshoot for lower values, and the system gets fast (and harsh) for larger values.

### Prob. 2.9
In many mechanical positioning systems there is flexibility between one part of the system and another. An example is shown in Figure 2.6 where there is flexibility of the solar panels. Figure 2.42 depicts such a situation, where a force u is applied to the mass M and another mass m is connected to it. The coupling between the objects is often modeled by a spring constant k with a damping coefficient b, although the actual situation is usually much more complicated than this.
(a) Write the equations of motion governing this system.
(b) Find the transfer function between the control input, u; and the output, y
![[Pasted image 20230523154253.png]]

(a) The equations of motion for the given system are:
$$
\begin{aligned}
& m \ddot{x}_1=-k\left(x-y\right)-b\left(\dot{x}-\dot{y}\right) \\
& M \ddot{y}=u + k\left(x-y\right)+b\left(\dot{x}-\dot{y}\right)
\end{aligned}
$$
<=>
$$
\begin{gathered}
\vec{x}+\frac{k}{m} z+\frac{b}{m} \dot{z}-\frac{k}{m} y-\frac{b}{m} \dot{y}=0 \\
-\frac{k}{M} z-\frac{b}{M} \dot{z}+\bar{y}+\frac{k}{M} y+\frac{b}{M} \dot{y}=\frac{1}{M} u
\end{gathered}
$$
(b) If we take the Laplace transform of the equations we get:
$$
\begin{gathered}
s^2 X+\frac{k}{m} X+\frac{b}{m} z X-\frac{k}{m} \Psi^{-}-\frac{b}{m} \Sigma^{-}=0 \\
-\frac{k}{M} X-\frac{b}{M} s X+v^2 Y^{-}+\frac{k}{M} I^{-}+\frac{b}{M} \Delta \Sigma^{-} \frac{1}{M} U
\end{gathered}
$$
In matrix form,
$$
\left[\begin{array}{cc}
m s^2+b s+k & -(b s+k) \\
-(b s+k) & M s^2+b s+k
\end{array}\right]\left[\begin{array}{l}
\mathrm{X} \\
Y
\end{array}\right]-\left[\begin{array}{l}
0 \\
U
\end{array}\right]
$$
From Cramer'a Rule.
$$
\begin{aligned}
Y  & =\frac{\operatorname{det}\left[\begin{array}{cc}
m z^2+b s+k & 0 \\
-(b z+k) & U
\end{array}\right]}{\operatorname{det}\left[\begin{array}{cc}
m s^2+b s+k & -(b s+k) \\
-(b s+k) & M s^2+b s+k
\end{array}\right]} \\
& =\frac{m s^2+b s+k}{\left(m s^2+b s+k\right)\left(M s^2+b o+k\right)-(b s+k)^2} U
\end{aligned}

$$
$\Leftrightarrow  \frac{Y}{U} = \frac{m s^2+b s+k}{\left(m s^2+b s+k\right)\left(M s^2+b o+k\right)-(b s+k)^2}$

### 2.10 and 2.12
![[Pasted image 20230523160544.png]]

Calculate the transfer function:

$$
\begin{aligned}
& \frac{V_{i n}-V_{-}}{R_{i n}}=\frac{V_{-}-V_{\text {out }}}{R_f} \\
& V_{-}=\frac{R_f}{R_{i n}+R_f} V_{i n}+\frac{R_{\text {in }}}{R_{i n}+R_f} V_{\text {out }} \\
\end{aligned}
$$
$$\begin{aligned}
& V_{\text {out }}=\frac{10^7}{s+1}\left[V_{+}-V_{-}\right] \\
& =\frac{10^7}{s+1}\left(V_{+}-\frac{R_f}{R_{i n}+R_f} V_{i n}-\frac{R_{\text {in }}}{R_{i n}+R_f} V_{\text {out }}\right) \\
& =-\frac{10^7}{s+1}\left(\frac{R_f}{R_{i n}+R_f} V_{i n}+\frac{R_{\text {in }}}{R_{i n}+R_f} V_{\text {out }}\right) \\
&
\end{aligned}$$
$$
\frac{V_{\text {out }}}{V_{i n}}=\frac{-10^7 \frac{R_f}{R_{i n}+R_f}}{s+1+10^7 \frac{R_{i n}}{R_{i n}+R_f}}
$$
Show that, with the non-ideal transfer function of Problem 2.10, the op amp connection shown in Fig. 2.45 is unstable.
![[Pasted image 20230523161237.png]]
$$
\begin{aligned}
& V_{\text {in }}=V_{-}, V_{+}=V_{\text {out }} \\
& V_{\text {out }}=\frac{10^7}{s+1}\left[V_{+}-V_{-}\right] \\
& =\frac{10^7}{s+1}\left[V_{\text {out }}-V_{\text {in }}\right] \\
& \frac{V_{\text {out }}}{V_{\text {in }}}=\frac{\frac{10^7}{s+1}}{\frac{10^7}{s+1}-1}=\frac{10^7}{-s-1+10^7} \cong \frac{-10^7}{s-10^7} \\
&
\end{aligned}
$$
The transfer function has a denominator with s 107; and the minus sign means the exponential time function is increasing, which means that it has an unstable root.