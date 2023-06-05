# Dynamic Response

## Simulating system responses
Numerical simulation of (usually nonlinear) equations of  
motions  
– based on detailed (first principle) modeling of the underlying physics  
– high accuracy but usually lots of computation work (→slow)  
– e.g.: nonlinear circuit simulation (e.g. SPICE), computational  
electromagnetics, technology CAD  
– best for design verification before controller implementation  
• Approximation by linear analysis techniques  
– quick assessment of how the system might be changed to modify the  
response in a desired direction  
– insight into why the solution has certain features  
– e.g.: small-signal circuit analysis, Fourier analysis of optics using  
scalar approximation of EM equations (both uses Laplace/Fourier  
transforms)  
– This lecture introduces and reviews some fundamental math. tools for  
future analysis in the s-plane, frequency response, and state space.

## Content
- Review of Laplace Transforms  
- System Modeling Diagrams  
- Effects of Poles Locations  
- Time-domain Specs  
- Effects of Zeros and Additional Poles  
- Stability

## Signals and Systems
System: a set of entities, real or abstract, comprising a whole where each component interacts with or is related to at least one other component and they all serve a common objective.
Signal: a varying quantity that can carry information
- e.g., input $(u)$ and output $(y)$ of a system
- continuous-time (CT) signa: $u(t), y(t)$ are functions of the continuous argument $t,(t \in \mathbf{R})$ $t=K \cdot T_s$
- discrete-time (DT) signal: $u[k], y[k]$ are functions of the discrete argument $k(k \in \mathbf{Z} ; u[k], y[k], k$ are discrete sequences)
- DT can be seen as a special case of CT (details in Digital Control Systems)
e.g. A linear system can be characterized by an special set of input and output signals:
- $u(t)=\delta(t-\tau)-$ impulse input applied at time $\tau$
- $y(t)=h(t, \tau)$ - output (impulse response) w.r.t to the impulse input


## Linear time-invariant (LTI) systems 
- A linear system’s input-output response obeys the principle of superposition 
	- Response to a general signal is a sum of the responses to some elementary signals (impulse and exponential the most common)
	- Very important for building complex engineering systems! 
- The response of a LTI systems can be expressed as the convolution of the input with the impulse response of the system 
	- Thus, it can be shown that the response of a LTI system to an exponential input is also exponential 
	- The principal reason for the usefulness of Fourier and Laplace transforms (both with basis function of the form e st) to the study of LTI systems.

Linearity 
- If the system output is $y_1$ w.r.t. input $u_1 ; y_2$ w.r.t. $u_2$ ; and $y_3$ w.r.t. $u_3 = u_1 + u_2$ → $y_3 = y_1 + y_2$ 
- Called principle of superposition 
	 Implication: decomposition of complicated problems to simple ones
	 
Time-invarience
- If the system output w.r.t. input $u(t)$ is $y(t) \rightarrow$ the system output w.r.t. input $u\left(t-t_d\right)$ is $y\left(t-t_d\right)$
	 e.g., impulse responses are the same for an impulse applied at one time $t_1$ and an impulse at the other time $t_2$


### Can you draw signals to explain linear, time-invariant, and LTI
Linear – Linear but time-variant?  
Time-invariant – Time-invariant but nonlinear?  
LTI – Neither linear nor time-invariant?

## Review: Dirac delta function
- $\delta(t)$ is a kind of generalized function or ideal function which can be used to idealize a physical phenomena
	- e.g., impulse $\equiv$ change of momentum $=\int_{-\infty}^t F(t) d t$ If the duration of the force $F(t)$ is very short at $t=a$, then $F(t) \rightarrow M \cdot \delta(t-a)$ is called an "impulse force", where $M$ is the magnitude of the impulse force and $\delta(t-a)$ is an "unit impulse force" at $t=a$
- The delta function $\delta(t)$ has the fundamental property that $\int_{-\infty}^\tau \delta(t) d t=1(\tau)$ and $\int_{-\infty}^{+\infty} g(t) \delta(t-a) d t=g(a)$
$1^{\text {st }}$ eqn: $\delta(t)$ has an unit area
$2^{\text {nd }}$ eqn: $\delta(t)$ is very short

http://mathworld.wolfram.com/DeltaFunction.html
- DT delta function:
$$
\delta[k]=\left\{\begin{array}{cc}
1 & k=0 \\
0 & \text { else }
\end{array} \text { and } \sum_{l=-\infty}^{\infty} g[l] \delta[l-k]=g[k]\right.
$$
- Delta functions are key to appreciate LTI systems.

## Output of a linear system
the delta function $\delta(t)$ has the fundamental property that $$u(t)=\int_{-\infty}^{+\infty} \delta(\tau-t) u(\tau) d \tau=\int_{-\infty}^{+\infty} \delta(t-\tau) u(\tau) d \tau$$$\text { since } \delta(\tau-t)=\delta(t-\tau)$

- Can be viewed as representing u(t) as a sum of impulses of intensity $u(\tau)$ at different values of $\tau$

→ From superposition, for general linear systems:

$$y(t)=\int_{-\infty}^{+\infty} h(t, \tau) u(\tau) d \tau$$
where $h( t,\tau)$ is the impulse response at to an impulse applied at $\tau$

For linear time-invariant systems:
$$
h(t, \tau)=h(t-\tau)
$$
since the response at $t$ to an input at $\tau$ depends on the (fixed) time difference $t-\tau$
$$
\begin{aligned}
y(t) & =\int_{-\infty}^{+\infty} h(t-\tau) u(\tau) d \tau \text { (superposition integral) } \\
& =\int_{-\infty}^{+\infty} u(t-\tau) h(\tau) d \tau \text { (convolution intergral) }\left(\mathrm{pf} \text {. define } \tau^{\prime}=t-\tau\right)
\end{aligned}
$$

## Transfer functions 
From convolution integral, the response of a LTI system to an exponential input is also exponential
($s =\sigma+j \omega$)
$$
\begin{aligned}
& \text { let } u(t)=A e^{s t} 
 \rightarrow y(t)=\int_{-\infty}^{+\infty} u(t-\tau) h(\tau) d \tau=\int_{-\infty}^{+\infty} A e^{s(t-\tau)} h(\tau) d \tau \\
& =\int_{-\infty}^{+\infty} e^{-s \tau} h(\tau) d \tau \cdot A e^{s t}=H(s) \cdot A e^{s t}
\end{aligned}
$$
$Y(s) / U(s) \triangleq H(s)=\int_{-\infty}^{+\infty} e^{-s s} h(\tau) d \tau$ (transfer function is the L-T of the impulse resp.)

E.g. Solve
$$
y(t)+k y(t)=u(t)=A e^{s t}
$$
Assume $y(t)=H(s) \cdot A e^{s t} \rightarrow j(t)=H(s) \cdot A s e^{s t}+k H(s) \cdot A e^{s t}=A e^{s t}$
$$
\rightarrow H(s)=\frac{1}{s+k} \rightarrow y(t)=\frac{1}{s+k} \cdot A e^{s t}
$$


## Frequency response 
From convolution integral, the response of a LTI system to an sinusoidal input is also sinusoidal

Let $u(t)=A e^{s t} \rightarrow y(t)=H(s) \cdot A e^{s t}$
For $u(t)=A \cos (\omega t)=\frac{A}{2}\left(e^{j \omega t}+e^{-j \omega t}\right) \rightarrow y(t)=\frac{A}{2}\left[H(j \omega) e^{j \omega t}+H(-j \omega) A e^{-j \omega t}\right]$$\rightarrow y(t)=\frac{A}{2}\left[M(\omega) e^{j(\omega t+\phi)}+M(-j \omega) e^{-j(\omega t+\phi)}\right]=A \cdot M(\omega) \cos (\omega t+\phi)$
(amplitude gain $M(\omega)=|H(j \omega)|$, phase shift $\phi=\angle H(j \omega)$ )
E.g.
$$
H(s)=\frac{1}{s+k} \rightarrow H(j \omega)=\frac{1}{j \omega+k} \rightarrow M(\omega)=\frac{1}{\sqrt{\omega^2+k^2}}, \phi(\omega)=-\tan ^{-1}\left(\frac{\omega}{k}\right)
$$

**Bode plot:** 
– Gain plot: $M(\omega)$ vs. $\omega$, in log-log scale 
– Phase plot: $\phi(\omega)$ vs. $\omega$, in linear-log scale


![[Pasted image 20230516172331.png]]

Response to a sinusoidal input starting from t = 0 
– Transient resp. + “steady-state” sinusoidal resp.
$$\begin{align*}
& \begin{aligned}
\text{let } H(s) &= \frac{1}{s+a}, \\
u(t) &= \left\{\begin{array}{cc}
0 & t \leq 0 \\
\sin (\omega t) & t>0
\end{array}\right.
\end{aligned} \\
& \begin{aligned}
\rightarrow U(s) &= L\{u(t)\} = \frac{\omega}{s^2+\omega^2}(\mathrm{~L}-\mathrm{T} \text{ table) }, \\
Y(s) &= H(s) U(s) = \frac{1}{s+a} \frac{\omega}{s^2+\omega^2} \\
&= \frac{\alpha_1}{s+a}+\frac{\alpha_0}{s+j \omega}+\frac{\alpha_0^{+}}{s-j \omega} \\
& \text{(partial-fraction expansion)}
\end{aligned} \\
& \begin{aligned}
\rightarrow \ldots \rightarrow y(t) &= \underbrace{\alpha_1 e^{-a t}}_{\text{transient}}
 + \underbrace{|H(j \omega)| \sin (\omega+\angle H(j \omega))}_{\text{steady-state}}
\end{aligned}
\end{align*}$$

(Inverse L-T)
## Laplace transform and Fourier transform 
• Fourier transform is a special case of two-sided Laplace transform
$$
\begin{aligned}
& L\{g(t)\}=G(s)=\int_{-\infty}^{+\infty} e^{-s \tau} g(\tau) d \tau \\
& F\{g(t)\}=G(j \omega)=\int_{-\infty}^{+\infty} e^{-j \omega \tau} g(\tau) d \tau=\left.L\{g(t)\}\right|_{s=j \omega}
\end{aligned}
$$
In many applications, conv. with one-sided $L-T$
$$
\begin{aligned}
& L_{-}\{g(t)\}=G(s)=\int_{0^{-}}^{+\infty} e^{-s \tau} g(\tau) d \tau \\
& L_{+}\{g(t)\}=G(s)=\int_{0^{+}}^{+\infty} e^{-s \tau} g(\tau) d \tau
\end{aligned}
$$
Inverse L-T
$$
L^{-1}\{G(s)\}=g(t)=\frac{1}{2 \pi j} \int_{\sigma_{\varepsilon}-j \infty}^{\sigma_c+j \infty} G(s) e^{s t} d s
$$
## Transform techniques for linear time-invariant (LTI) systems 
• Many powerful math. techniques available for analyzing and synthesizing LTI systems by taking transforms, e.g., Fourier series (F.S.), Fourier Transform (FT), Laplace Transform (LT), z-transforms (ZT), ... 
• Many LTI-related transforms are special cases of (two-sided) Laplace Transform (TS-LT)

![[Pasted image 20230516173616.png|300]]

## Applications of L-T to CT-LTI systems

Constant-coefficient linear ordinary differential equations: usually derived from physic laws 
• Laplace Transforms to convert differential equations to algebraic equations 
	 s-domain/s-plane techniques to analyze and synthesize filters/controllers (details later)
e.g.
$$
\begin{aligned}
& d_0 y+d_1 \dot{y}+d_2 \ddot{y}=n_0 u+n_1 \dot{u} \\
& d_0 Y(s)+d_1 s Y(s)+d_2 s^2 Y(s)=n_0 U(s)+n_1 s U(s) \\
& G(s) \equiv \frac{Y(s)}{U(s)}=\frac{n_0+n_1 s}{d_0+d_1 s+d_2 s^2} \equiv \frac{N(s)}{D(s)}
\end{aligned}
$$
$|G(s)|, \angle G(s) \rightarrow$ Bode plots/frequency response
$N(s)=0, D(s)=0 \rightarrow$ zeros, poles, stability, root locus

## Poles and zeros
- A rational transfer function can be factored as:
![[Pasted image 20230516173857.png]]
- Zeros: correspond to signal transmission-blocking properties of the system – Usually called transmission zeros – In time domain, a non-zero input $u(t) = u_0 exp(z_0 t) → y(t) = 0$
- Poles: determines system stability properties
	 – Usually called system modes
	 ![[Pasted image 20230516174038.png|100]]
- Locations of poles and zeros on the s-plane lie at the heart of feedback control design (e.g., root locus later) 
- $n \geq m$ for physical (causal) systems

## Basic block diagram properties
![[Pasted image 20230520131342.png|200]]
$\frac{Y_2(s)}{U_1(s)} = G_2G_1$
![[Pasted image 20230520131338.png]]
$\frac{Y(s)}{U(s)} = G_1 + G_2$

![[Pasted image 20230520131601.png]]
$\frac{Y(s)}{R(s)} =\frac{G_1}{1+ G_1G_2}$

For feedback connection: 
![[Pasted image 20230520132831.png]]
*Rule of thumb: feedforward gain/(1-loop gain)*


## Block diagram manipulation
![[Pasted image 20230520133132.png]]
## Block diagram reduction
![[Pasted image 20230520133153.png]]
![[Pasted image 20230520133215.png]]

## Resp. vs. pole locations (real & complex)

![[Pasted image 20230520133320.png]]

## First-order response
![[Pasted image 20230520133404.png]]

## Response vs zero locations (real roots)

![[Pasted image 20230520133446.png]]

## Response of 2nd-order systems
![[Pasted image 20230520133517.png]]

## Impulse response of a standard 2nd-order systems

![[Pasted image 20230520133608.png]]

## Step response of a standard 2nd-order systems
![[Pasted image 20230520133644.png]]

## Time-domain spec. definitions
![[Pasted image 20230520133746.png]]

- rise time $t_r$: the time needed for the system to reach the vicinity of its new set point (usually 0.1 - 0.9)
- setting time $t_s$: the time needed form the system transients to decay 
- peak time $t_p$: the time needed for the system to reach the max. overshoot point 
- overshoot $M_p$ (%): maximum system overshoots its final value divided by the final value

## Rise time
- rise time $t_r$: the time needed for the system to reach the vicinity of its new set point 
- for under-damped 2nd-order systems, rise time roughly the same

![[Pasted image 20230520134026.png]]

## Settling Time
![[Pasted image 20230520134110.png]]

## Overshoot and peak time

![[Pasted image 20230520134135.png]]

## Time domain specifications for 2nd-order systems - Summary
![[Pasted image 20230520134238.png]]

## Review: CT design specifications
![[Pasted image 20230520134302.png]]
![[Pasted image 20230520134318.png]]

## Effects of additional zeros

- Poles determine the shape of the exponential response terms.
- Zeros modifies the coefficients of the exponential response terms.
![[Pasted image 20230520134443.png]]
• The coefficients can be computed by PFE:
![[Pasted image 20230520134521.png]]

	If F(s) has a zero near the pole at s = p1, the value of F(s) will be small because the value of s is near the zero, thus C1 will be small

![[Pasted image 20230520140609.png]]
![[Pasted image 20230520140629.png]]![[Pasted image 20230520140638.png]]![[Pasted image 20230520140651.png]]![[Pasted image 20230520140704.png]]

## Stability 
![[Pasted image 20230520140739.png]]
## Stability of LTI systems
![[Pasted image 20230520140751.png]]

## Routh's stability criterion
![[Pasted image 20230520140829.png]]
![[Pasted image 20230520140901.png]]
![[Pasted image 20230520140913.png]]
## Routh test example - stability vs. controller parameter
![[Pasted image 20230520140941.png]]
![[Pasted image 20230520141010.png]]
## Routh stability test - Special Case I
![[Pasted image 20230520141034.png]]
![[Pasted image 20230520141055.png]]

## Obtaining models from experimental data
In practice, theoretical model built from EOMs only an approximation of reality
– can be quite accurate for rigid spacecraft (rigid body)
– very approximate for chemical processes
– important and prudent to verify the theoretical model with reality (experiment data) before controller design/implementation

When process physics too complicated or poorly understood, experimental data the more reliable information

System dynamics can change over time/environment
– e.g., aircraft dynamics at diff. altitude or speed; circuit eqns. at diff. operating points (temperature/process “corners”), need to retune controller w.r.t. a new model with new experimental data

## Types of experimental data
**transient response**
– impulse or step input → impulse or step responses
– representative of the input signal of many control systems
– for control design, usually further data processing needed (e.g., fitting to a transfer function)
– often difficult to collect high S/N signals (esp. when closer to ‘0’ steady states); increasing input mag. easily leads to saturation
**frequency-response data / Bode plot**
– obtained directly freq. by freq. (swept sine); freq. resp. design method (ch. 6) can be proceed immediately
– poles/zeros can be estimated by fitting to transfer functions or straight-line asymptotes (lect. 6)
– can be quite time consuming, esp. for large-time-constant/long oscillation period systems (e.g., chemical/thermal processes)

**stochastic steady-state information**
– during sys. operation, e.g., an airplane flying through turbulence
– inconsistent data quality, tending to be worst when control/sys. output the best (small fluctuation); some or even most of the modes hardly excited
– during fitting, need to separate contributions of disturbance and control input to the sys. output, difficult for closed-loop operation

**pseudorandom-noise data**
– pseudorandom signals usually generated by digital computers
– pseudorandom binary signal (PRBS) alternates between +A and -A randomly with a selected level A, a broadband (white signal) quite suitable for identification


## Amplitude/time scaling for numerical accuracy
• magnitude of variables in a problem can be very different, causing numerical difficulties
– a serious problem when using analog computers, scaling a routine
– floating-point numbers in digital computers increase the scale, but do not entirely eliminate the problems (e.g., poles with natural freqs. of very different orders; roots sensitivity to coeffs.)

• amplitude scaling
– pick appropriate units!!
– normalized w.r.t the largest expected value(s), such thatthe new variable(s) vary between -1 and 1

• time scaling 
– pick an appropriate unit!! (e.g., s vs. $\mu s$) 
– normalized, substitute into the DEs

## Mason's rule and signal flow graph 
![[Pasted image 20230520141744.png]]
![[Pasted image 20230520141758.png]]

## HW 3 
review questions 
1. What is the definition of "transfer function"? 
The transfer function of a system is a mathematical representation, in the frequency domain, that relates the output of a system to its input. 

2. What are the properties of systems whose response can be described by transfer functions? 
 and . 

Linearity - Linear systems obey the principles of superposition and homogeneity. 

Time-invariance - implies that the behavior and characteristics of the system do not change over time.

3. What is the Laplace transform of $f(t - \lambda )$ if the transform of f(t) is F(s)? 

(where λ is a positive constant) is e<sup>-sλ</sup>F(s), according to the time-shift property of the Laplace transform.

4. State the Final Value Theorem. 

if we have a system with Laplace transform F(s), the final value f(∞) in the time domain is given by $f(∞) = lim[s→0] sF(s)$

5. What is the most common use of the Final Value Theorem in control? 
to predict the steady-state value (the value as time goes to infinity) of a system's response to a step input. This allows engineers to estimate how the system will behave in the long run without having to solve the complete differential equation.

6. Given a second-order transfer function with damping ratio $\zeta$; and natural frequency $\omega_n$ , what is the estimate of the step response rise time? What is the estimate of the percent overshoot in the step response? What is the estimate of the settling time? 

-   The rise time, $T_r$, approximates how long it takes the system's step response to rise from 10% to 90% of the final value. For an underdamped system (0 < ζ < 1), the rise time $T_r$ is typically approximated as $T_r ≈ 1.8/(ω_n√(1-ζ^2))$.
-   The percent overshoot, expressed as a percentage, describes how much the peak response exceeds the final steady-state value. For an underdamped system (0 < ζ < 1), the percent overshoot, $M_p$, is typically approximated as $M_p$ ≈ 100 * e^(-πζ/√(1-ζ^2)).
-   The settling time, Ts, estimates how long it takes the system's step response to stay within a certain error band (usually 2% or 5%) of the final value. For an underdamped system (0 < ζ < 1), the settling time Ts is typically approximated as $T_s ≈ 4.6/(ζω_n)$.
 
7. What is the most noticeable effect of a zero in the RHP on the step response of the second-order system? 

A zero in the right half-plane (RHP) of the complex plane for a second-order system can cause a non-minimum phase behavior, which means it will introduce an initial response in the opposite direction of the final steady-state value. This can lead to an initial "kick" in the response.

8. What is the major effect of a zero in the LHP on the second-order step response? 
A zero in the left half-plane (LHP) in a second-order system tends to speed up the system response. It makes the transient response faster, allowing the system to reach its steady-state faster, and reducing the overshoot.

9. What is the main effect of an extra real pole on the second-order step response? 
The introduction of an extra real pole to a second-order system typically leads to a slower system response. The system becomes a third-order system, and it typically has a slower rise time, increased settling time, and decreased overshoot, compared to the original second-order system.

10. Why is stability an important consideration in control system design? 
Stability is a crucial consideration in control system design because it ensures that the system will not respond to inputs or disturbances with unbounded outputs. An unstable system could potentially result in catastrophic failure.

11. What is the main use of Routh's criterion? 
Routh's criterion is a mathematical algorithm that can be used to determine the stability of a linear time-invariant system. It involves constructing the Routh array from the coefficients of the characteristic polynomial of the system and checking the number of sign changes in the first column. If there are no sign changes, the system is stable.

12. Under what conditions might it be important to know how to estimate a transfer function from experimental data?
It's important to know how to estimate a transfer function from experimental data when the system's mathematical model is either not available or too complex. These situations might include system identification tasks, where the dynamics of a system are unknown and need to be determined from measured data, or in cases of complex systems where a simple approximation of the dynamics is sufficient

### 3.23
![[Pasted image 20230604211413.png]]

(a)
$$
v_1(t)=L \frac{d i}{d t}+R i+\frac{1}{C} \int i(t) d t
$$
(b)
$$
v_2(t)=\frac{1}{C} \int i(t) d t
$$
(c)
$$
\frac{v_2(s)}{v_1(s)}=\frac{\frac{1}{s C}}{s L+R+\frac{1}{s C}}=\frac{1}{s^2 L C+s R C+1}
$$
(d) For $25 \%$ overshoot $\xi \approx 0.4$,
$$
\begin{aligned}
0.4 & \approx \zeta=\frac{R}{2 \sqrt{\frac{L}{C}}} \\
R & =2 \zeta \sqrt{\frac{L}{C}}=2 \times 0.4 \sqrt{\frac{10 \times 10^{-3}}{4 \times 10^{-6}}}=40 \Omega .
\end{aligned}
$$

### 3.25
![[Pasted image 20230604211439.png]]
![[Pasted image 20230604212106.png]]

$$
\frac{Y(s)}{R(s)}=\frac{100 K}{s^2+(25+a) s+25 a+100 K}=\frac{100 K}{s^2+2 \zeta \omega_n s+\omega_n^2}
$$
given information:
$$
\begin{aligned}
R(s) & =\frac{1}{s} \quad \text { unit step. } \\
M_p & \leq 25 \%, \\
t_s & \leq 0.1 \mathrm{aec} .
\end{aligned}
$$
Solve for $\zeta$ :
$$
\begin{aligned}
M_p & =e^{-\pi \zeta / \sqrt{1-\zeta^2}}, \\
\zeta & =\sqrt{\frac{\left(\ln M_p\right)^2}{\pi^2+\left(\ln M_p\right)^2}} \geq 0.4037 .
\end{aligned}
$$
Solve for $\omega_n$ :
$$
\begin{aligned}
& e^{-\zeta \omega_n t_z}=0.01 \quad \text { For a } 1 \% \text { aettling time. } \\
&t_s \leq \frac{4.606}{\zeta \omega_n}=0.1, \\
&\Longrightarrow \omega_n \approx 114.07 .
\end{aligned}
$$
Now find $a$ and $K$ :
$$
\begin{gathered}
2 \zeta \omega_n=(25+a), \\
a=2 \varsigma \omega_n-25=92.10-25=67.10, \\
\omega_n^2=(25 a+100 K), \\
K=\frac{\omega_n^2-25 a}{100} \approx 113.34 .
\end{gathered}
$$

in matlab: 
Step-response
![[Pasted image 20230604212609.png]]

### 3.32
![[Pasted image 20230604211550.png]]

### 3.47
![[Pasted image 20230604211648.png]]