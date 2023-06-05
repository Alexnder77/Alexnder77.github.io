# State-Space Methods

A LTI system can be characterized in terms of 
- transfer functions 
- state-space (SS) equations 
	- by simply re-organizing its system differential equations with a set of first-order differential equations 
	
- So far, have introduced RL and FR methods to design feedback compensator D(s) based on transfer functions 
	- essences of classical control
- SS approaches widely used in modern control theory and designs 
	- well suited for analysis with computation-intensive techniques (e.g., numerical linear algebra) 
	- an alternative approach to find D(s)

## Advantages of state-space forms
- Applicable to both linear and nonlinear systems
![[Pasted image 20230523142244.png]]
- Analysis/design techniques readily extended to multiple-input-multiple-output (MIMO) systems 
- Differential equations can be (conceptually) visualized/analyzed by geometries 
	-– e.g., phase plane (position vs. velocity) 
- Describe both external (I/O) and internal states – transfer function only overall I/O behaviors

## Continuous-time LTI state-space description
![[Pasted image 20230523142354.png]]
![[Pasted image 20230523142410.png]]
## Cruise control model
![[Pasted image 20230523142427.png]]
![[Pasted image 20230523142435.png]]

Bridged-tee circuit
![[Pasted image 20230523142612.png]]

Modeling a loudspeaker with circuit
![[Pasted image 20230523142626.png]]

Modeling a DC motor
![[Pasted image 20230523142638.png]]
## Canonical state-space forms
![[Pasted image 20230523142659.png]]
## Obtaining TF from SS
![[Pasted image 20230523142733.png]]

## System poles and zeros directly from SS
![[Pasted image 20230523142756.png]]
## Intro. state-space feedback compensator design
![[Pasted image 20230523142815.png]]

## Full state feedback
![[Pasted image 20230523142906.png]]
![[Pasted image 20230523142917.png]]

## How to select pole locations
• In theory, can use state-feedback to move CL poles to (arbitrarily) desired locations if system controllable 
• However, moving a pole far from its open loop location usually needs a large gain and excessive control effort 
→ move only the undesirable open-loop pole locations 
• Dominant second-order poles 
– design desired dominant poles with standard 2nd -order response 
• easily relating time response spec.’s to CL pole locations 
– move all other poles to be much faster than the dominant poles by state-feedback pole placement 
• Symmetrical root locus (SRL) 
– a simplified results of MIMO (quadratically) optimal control theory in SISO cases 
– can balance (tradeoff) between CL response and control effort required 

## Estimator design
- Full-state feedback requires sensors for all the state variables 
– Extra (sensor) hardware cost can be prohibitive 
– may be impossible/very difficult to measure all states (e.g., in a nuclear power plant)
- Estimation (software) technique needed to reconstruct all state variables with measurements from a few sensors 
- Open-loop estimator (as a plant simulator/predictor) would be susceptible to modeling errors, feedback correction (using sensor measurements) usually needed => closed-loop estimator 
- Estimator feedback gain design equations are analog (called “dual”) to state feedback gain design equations 
	-– (quadratically) optimal (Kalman) estimator from SRL as well

## HW 7 Assignment
### Review questions
The following questions are based on a system in state-variable form with matrices F, G, H, J, input u, output y, and state x. 
1. Why is it convenient to write equations of motion in state-variable form? 
	It is convenient to write equations of motion in state-variable form because it provides a compact and systematic representation of a dynamic system. By representing the system in terms of state variables, we can describe its behavior using a set of first-order differential equations. This allows for easier analysis, modeling, and control design, as it separates the system dynamics from the input and output.

2. Give an expression for the transfer function of this system. 
The transfer function of the system can be expressed as $H(s) = C(sI - A)^{-1}B + D$ where A, B, C, and D are matrices representing the system dynamics and input-output relationships.

3. Give two expressions for the poles of the transfer function of the system. 
	1) The poles of the transfer function correspond to the eigenvalues of matrix A in the state-space representation. 
	2) The poles can also be obtained by finding the roots of the characteristic equation det(sI - A) = 0, where I is the identity matrix.

4. Give an expression for the zeros of the system transfer function. 
The zeros of the system transfer function can be obtained by solving the equation H(s) = 0, where H(s) is the transfer function.

5. Under what conditions will the system be observable from the output y? 
The system will be observable from the output y if and only if the observability matrix $[C, CA, CA^2, ..., CA^{(n-1)}]$ has full rank, where n is the dimension of the state vector x.

6. Under what condition will the state of the system be controllable? 
The state of the system will be controllable if and only if the controllability matrix [B, AB, A^2B, ..., A^(n-1)B] has full rank.

7. Give an expression for the closed-loop poles if state feedback of the form u = −Kx is used. 
If state feedback of the form u = -Kx is used, the closed-loop poles can be obtained by evaluating the eigenvalues of the matrix A - BK, where K is the feedback matrix.

8. Under what conditions can the feedback matrix K be selected so that the roots of $a_c (s) = 0$ are arbitrary? 
The feedback matrix K can be selected so that the roots of ac(s) = 0 are arbitrary if and only if the pair (A, B) is controllable.

9. What is the advantage of using the LQR or SRL in designing the feedback matrix K? 
The advantage of using the Linear Quadratic Regulator (LQR) or Systematic Robust Control (SRL) in designing the feedback matrix K is that they provide systematic methods for optimizing the control performance. These techniques consider the system dynamics, cost criteria, and possible uncertainties to determine the optimal feedback gains, resulting in improved control performance, stability, and robustness.

10. What is the main reason for using an estimator in feedback control?
The main reason for using an estimator (such as a state observer or Kalman filter) in feedback control is to estimate the system's unmeasured states. In many practical scenarios, not all states of the system are directly measurable. By using an estimator, we can obtain an estimate of the unmeasured states based on the available measurements. This estimated state information can then be used for feedback control, enabling the control system to operate based on a more complete understanding of the system's dynamics.

### 7.3
![[Pasted image 20230523162549.png]]
all of them can be calculated with matlab using the tf2ss comand

a) F = -0.1000; G = 1; H = 0.1000; J = 0
b) F = 10; G = 1; H = 200; J = 25:

c)
![[Pasted image 20230523162943.png]]![[Pasted image 20230523162832.png|150]]

d) ![[Pasted image 20230523163057.png|150]]
e) ![[Pasted image 20230523163241.png]]

### 7.15
![[Pasted image 20230523163314.png]]

We are given $\dot{x} = Fx + Gu$. Steady-state means that $\dot{x} = 0$ and a step input (or unit step) means u = 1(t). 

we can calculate x by:
$$
0=\mathbf{F x}_{z z}+\mathbf{G} \Longrightarrow \mathrm{x}_{z z}=-\mathbf{F}^{-1} \mathrm{G}=\left[\begin{array}{cc}
-4 & 1 \\
-6 & -1
\end{array}\right]^{-1}\left[\begin{array}{l}
0 \\
1
\end{array}\right]= 

\frac{1}{(-4 \cdot -1) - (1 \cdot -6)} \left[\begin{array}{cc}
-1 & -1 \\
6 & -4
\end{array}\right]\left[\begin{array}{l}
0 \\
1
\end{array}\right]


= \left[\begin{array}{l}
-1/10 \\
-2/5
\end{array}\right]
$$

### 7.24

![[Pasted image 20230523165016.png]]
a) the system in control canonical form:
$$
\begin{aligned}
{\left[\begin{array}{l}
\dot{x}_1 \\
\dot{x}_2
\end{array}\right] } & =\left[\begin{array}{cc}
0 & -4 \\
1 & 0
\end{array}\right]\left[\begin{array}{l}
x_1 \\
x_2
\end{array}\right]+\left[\begin{array}{l}
1 \\
0
\end{array}\right] u, \\
y & =\left[\begin{array}{ll}
1 & 0
\end{array}\right] \mathbf{x} .
\end{aligned}
$$
b) If $u=-\left[K_1 K_2\right] \mathbf{x}$, the poles of the closed-loop system satisfy $\operatorname{det}(s \mathbf{I}-\mathbf{F}+\mathbf{G K})=0$. Thus,
$$
\operatorname{det}\left[\begin{array}{cc}
s+K_1 & -1+K_2 \\
4 & s
\end{array}\right]=0 \Longrightarrow s^2+K_1 s+4+K_2=0 .
$$
The closed-loop characteristic equation is,
$$
(s-6-6 j)(s-6+6 j)=s^2-12 s+72=0 
$$
Comparing coefficients, we have $K_1=12$ and $K_2=72$. 