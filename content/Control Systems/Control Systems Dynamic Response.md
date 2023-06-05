# Control Systems Dynamic Response

# Contents
## • Review of Laplace Transforms
## • System Modeling Diagrams
## • Effects of Poles Locations
## • Time-domain Specs
## • Effects of Zeros and Additional Poles
## • Stability

# Simulating system responses

- Numerical simulation of (usually nonlinear) equations of
    motions
       - based on detailed (first principle) modeling of the underlying physics
       - high accuracy but usually lots of computation work (→slow)
       - e.g.: nonlinear circuit simulation (e.g. SPICE), computational
          electromagnetics, technology CAD
       - best for design verificationbefore controller implementation
- Approximation by linear analysis techniques
    - quickassessment of how the system might be changed to modify the
       response in a desired direction
    - insightinto why the solution has certain features
    - e.g.: small-signal circuit analysis, Fourier analysis of opticsusing
       scalar approximation of EM equations (both uses Laplace/Fourier
       transforms)
    - This lecture introduces and reviews some fundamental math. tools for
       future analysis in the s-plane, frequency response, and state space.

# Signals and Systems

- System: a set of entities, real or abstract, comprising a whole
    where each component interacts with or is related to at least
    one other component and they all serve a common objective.
- Signal: a varying quantity that can carry information
    - e.g., input (u) and output (y) of a system
    - continuous-time (CT) signal: u(t), y(t) are functions of the continuous
       argument t, (tR)
    - discrete-time (DT) signal: u[k], y[k] are functions of the discrete
       argument k (kZ; u[k], y[k], kare discrete sequences)
    - DT can be seen as a special case of CT (details in Digital Control
       Systems)
- e.g. A linear system can be characterized by an special set of
    input and output signals:
       - u(t) = d(t–t) –impulseinput applied at time t
       - y(t) = h(t, t) –output (impulse response) w.r.t to the impulse input
       - details later

## Linear time-invariant (LTI) systems

- A linear system’s input-output response obeys the
    principle of superposition
       - Response to a general signal is a sum of the responses to some
          elementary signals (impulse and exponentialthe most common)
       - Very important for building complex engineering systems!
- The response of a LTI systems can be expressed as the
    convolution of the input with the impulse response of the
    system
       - Thus, it can be shown that the response of a LTI system to an
          exponential input is also exponential
       - The principal reason for the usefulness of Fourier and Laplace
          transforms (both with basis function of the form est) to the study of
          LTI systems.

- Linearity
    - If the system output is y 1 w.r.t. input u 1 ; y 2 w.r.t. u 2 ; and y 3
       w.r.t. u 3 = u 1 + u 2
          →y 3 = y 1 + y 2
    - Called principle of superposition
       - Implication: decomposition of complicated problems to simple ones
- Time-invariance
    - If the system output w.r.t. input u(t) is y(t) → the system
       output w.r.t. input u(t−td) is y(t−td)
          - e.g., impulse responses are the same for an impulse applied at one
             time t 1 and an impulse at the other time t 2

## linear, time-invariant, and LTI?

- Linear
    - Linear but time-variant?
- Time-invariant
    - Time-invariant but nonlinear?
- LTI
    - Neither linear nor time-invariant?
- Draw on the whiteboard
- Best drawing pending...


# Review: Dirac delta function
## • d(t) is a kind of generalized functionor ideal function which
can be used to idealize a physical phenomena
- e.g., impulsechange of momentum =
    If the duration of the force F(t) is very shortat t = a, then
    F(t)→Md(t−a) is called an “impulse force”, where Mis the
    magnitude of the impulse force and d(t−a) is an “unit impulse force”
    at t= a

## • The delta function d(t) has the fundamental property that

- 1 steqn: d(t) has an unit area
- 2 nd eqn: d(t) is very short
[http://mathworld.wolfram.com/DeltaFunction.html](http://mathworld.wolfram.com/DeltaFunction.html)
- DT delta function:
- Delta functions are key to appreciate LTI systems.



# Output of a linear system

## • The delta function d(t) has the fundamental property that Can be viewed as representing u(t) as a sum of impulses## of intensity u(t) at different values of t

→From superposition, for general linear systems:



# Output of a linear system (cont.)

## • For general linear systems:

- For linear time-invariant systems:

#### Understanding superposition and convolution integrals

#### in the discrete-time domain

- DT-LTI input-output:


## Transfer functions

- From convolution integral, the response of a

#### LTI system to an exponential input is also


## Frequency response

- From convolution integral, the response of a

#### LTI system to an sinusoidal input is also

#### sinusoidal



# Frequency response (cont.)

## • Bode plot:

## – Gain plot: M() vs. , in log-log scale

## – Phase plot: () vs. , in linear-log scale

## Frequency response

#### (cont.)

- Response to a sinusoidal input
    starting from t = 0
       - Transient resp. + “steady-state”
          sinusoidal resp.

## Laplace transform and Fourier transform

- Fourier transform is a special case of two-sided

#### Laplace transform

- In many applications, conv. with one-sided L-T
- Inverse L-T


## Transform techniques for linear

## time-invariant (LTI) systems

- Many powerful math. techniques available for analyzingand
    synthesizingLTI systems by taking transforms, e.g., Fourier series
    (F.S.), Fourier Transform (FT), Laplace Transform (LT), z-transforms
    (ZT), ...
- Many LTI-related transforms are special cases of (two-sided) Laplace
    Transform (TS-LT)
       - e.g.,


### Laplace transform table

### and properties

## Applications of L-T to CT-LTI systems

- Constant-coefficient linear ordinary differential equations:
    usually derived from physic laws
- Laplace Transforms to convert differential equations to
    algebraic equations
       - s-domain/s-plane techniques to analyze and synthesize
          filters/controllers (details later)
- e.g.,

## Poles and zeros

- A rational transfer function can be factored as:
- Zeros: correspond to signal transmission-blocking

properties of the system

- Usually called transmission zeros
- In time domain, a non-zero input u(t) = u 0 exp(z 0 t) → y(t) = 0
- Poles: determines system stability properties
- Usually called system modes
- |H(pi)|= 
- Locations of poles and zeros on the s-plane lie at the

heart of feedback control design (e.g., root locus later)

- 

# Basic block diagram properties

## • For feedback connection:

## – Rule of thumb: feedforward gain/( 1 − loop gain)


# Block diagram reduction

# Block diagram reduction (cont.)

# First-order response


## Response vs. zero locations (real roots)

## Response of 2nd-order systems

- standard 2nd-order under-damped (<1) CT system

1: over-damped (2 ) 4 0 ( ) has two real poles;
1: under-damped (2 ) 4 0 ( ) has two complex pole :

= and (1 )
: damping ration; : natural frequency ; (undamped) atural frequency
sin or =sin , both indication of how far the 2 -order system is
from an

(undamped) simple harmonic oscillator

#### Impulse response of a standard 2nd-order systems

- standard 2nd-order under-damped (<1) CT system

: damping ration; :damped natural frequency ; undamped natural fr

### Step response of a standard 2nd-order systems


Impulse response:


## Time-domain spec. definitions

- rise timetr: the time needed for the system to reach the
    vicinity of its new set point (usually 0.1 −0.9)
- setting timets: the time needed form the system transients
    to decay
- peak timetp: the time needed for the system to reach the
    max. overshoot point
- overshootMp(%): maximum system overshoots its final
    value divided by the final value


```
Control Sys. Spr '23
Prof. Kuen-Yu Tsai/NTUEE 38
```
## Rise time

- rise time tr: the time needed for the system to reach the
    vicinity of its new set point
- for under-damped 2nd-order systems, rise time roughly
    the same

## Settling Time

- settling time ts: the time needed form
    the system transients to decay
- for under-damped 2nd-order systems,
    setting time roughly the same

## Overshoot and peak time

## Review: CT design specifications

- standard 2nd-order under-damped (<1) CT

#### system – step response

- n  1.8 / tr( = 0.5)
- d=  / tp
-  = n = 4.6 / ts (1%)
- peak overshoot ([FPW] Fig. 2.7, eqn 7.3)


```
Control Sys. Spr '23
Prof. Kuen-Yu Tsai/NTUEE 43
```
## Review: CT Design Specifications (cont.)

- standard 2nd-order under-damped (<1) CT

#### system – impulse response



Control Sys. Spr '23
Prof. Kuen-Yu Tsai/NTUEE 45

# Effects of additional zeros

- Poles determine the shape of the exponential response
    terms.
- Zeros modifies the coefficients of the exponential response
    terms.
- The coefficients can be computed by PFE:
    - If F(s) has a zero near the pole at s= p 1 , the value of F(s) will be
       small because the value of sis near the zero, thus C 1 will be small.


### Effect of proximity of a real zero to a real pole

### location on the transient response (ex. 3.26)

- additional overshoot for
    z = 1, 2, 3 (zeros close
    to origin)
- pole canceled for z = 4,
    6, no overshoot
- z=5 no overshoot either
    Control Sys. Spr '23
       Prof. Kuen-Yu Tsai/NTUEE 46


Figure 3.30 Effect of zero on transient response

#### Adding one zero to a standard 2nd-order system

- effects of one additional real zero
    large if < 3, small if > 3


#### Adding one RHP zero to a standard 2nd order system

- If < 0, the zero is the on the right-half-plane. The derivative term is
    subtractedrather than added. The response initially goes in the opposite
    direction vs. steady state.
- called a RHP zero or a nonminimum-phase (NMP) zero



### Proximity of complex zeros to light damped

### poles (Ex. 3.27)

- Oscillations caused by the lightly

```
damped poles reduced when
approached by the zeros
```
- exact pole-zero cancellation

```
problematic in practice since
exact pole locations often
unknown (a topic for robust
control)


#### Adding one LHP pole to a standard 2nd-order system

- An additional LHP pole significantly
    increases the rise time if < 3



## Bounded-input–bounded-output stability

- A system is said to have BIBO stability if every bounded

input results in a bounded output regardless of what goes on
inside the system.

## Stability of LTI systems

- A LTI sys. is internally stable iff all its poles are in LHP
    - unstable if there is any pole on RHP
    - any pole on the j axis:
       - Neutrally stable if no RHP poles, the poles on the jaxis are not repeated
       - Unstable if any of the poles on the jaxis are repeated

## Routh’s stability criterion

- Several methods available to obtain the root

```
locations of a polynomial without actually solving
for the roots
```
- Routhtable, root-locus, ...
- useful for analysis or design of FB control systems
- a sufficient condition for LTI stability:
    - if a LTI sys. stable ai> 0 (converse not always true!!)
    - i.e. if any ai< 0 the LTI sys. not stable
- a necessary and sufficient condition for LTI stability:
    - a LTI sys. stable all elements in the first column of the
       Routharraypositive (Routh1874; Hurwitz 1895)
    - number of unstable (RHP) poles = number of sign changes in
       the first column


## Routh stability test (cont.)

- A necessary and sufficient condition for LTI stability:
    - a LTI sys. stable all elements in the first column of the Routharray
       positive(Routh1874; Hurwitz 1895)
    - number of unstable (RHP) poles = number of sign changes in the first
       column


## Routh stability test (example)



#### Routh test example − stability vs. controller parameter

(this also demonstrates the power/effectiveness of model based control design
vs. trial-and-error parameter tuning)
```

#### Routh’s Test − stability vs. controller parameter

(proportional-integral (PI) control)

stabilizing controller
parameter values

(this also demonstrates the power/effectiveness of model based control design
vs. trial-and-error parameter tuning)
```
## Routh stability test − Special Case I

- when only the first element in one of the rows is zero:
    - replacethe zero with a small positive constant > 0 and proceed as before
    - apply the stability criterion by taking the limit →0 from both sides

## Routh stability test − Special Case II

- when an entire row of the Routharray is zero:
    - indicates there are complex conjugate pair of roots on the imaginary axis
    - if the ith row is zero, form a auxiliary polynomial from the previous nonzero
       row: a 1 (s)= 1 si+1+  2 si-^1 +  3 si-^1 + ..., {i}: coeff. of the (i+1)throw
    - replace the ithrow by the coeff. of the derivative of the aux. polynomial
    - roots of the aux. polynomial are also roots of the characteristic equation
       5 4 3 2



### Obtaining models from experimental data

### (system identification)

- In practice, theoretical model built from EOMs only an

approximation of reality

- can be quite accurate for rigid spacecraft (rigid body)
- very approximate for chemical processes
- important and prudent to verify the theoretical model with reality
    (experiment data) before controller design/implementation
- when process physics too complicated or poorly understood,

experimental data the more reliable information

- System dynamics can change over time/environment
    - e.g., aircraft dynamics at diff. altitude or speed; circuit eqns. at
       diff. operating points (temperature/process “corners”), need to
       retune controller w.r.t. a new model with new experimental data
Control Sys. Spr '23
Prof. Kuen-Yu Tsai/NTUEE 61


### Types of experimental data

- transient response
    - impulse or step input → impulse or step responses
    - representative of the input signal of many control systems
    - for control design, usually further data processing needed (e.g.,
       fitting to a transfer function)
    - often difficult to collect high S/N signals (esp. when closer to ‘0’
       steady states); increasing input mag. easily leads to saturation
- frequency-response data / Bode plot
    - obtained directly freq. by freq. (swept sine); freq. resp. design
       method (ch.6) can be proceed immediately
    - poles/zeros can be estimated by fitting to transfer functions or
       straight-line asymptotes (lect. 6)
    - can be quite time consuming, esp. for large-time-constant/long
       oscillation period systems (e.g., chemical/thermal processes)
Control Sys. Spr '23
Prof. Kuen-Yu Tsai/NTUEE 62


### Types of experimental data (cont.)

- stochastic steady-state information
    - during sys. operation, e.g., an airplane flying through turbulence
    - inconsistent data quality, tending to be worst when control/sys.
       output the best (small fluctuation); some or even most of the
       modes hardly excited
    - during fitting, need to separate contributions of disturbance and
       control input to the sys. output, difficult for closed-loop operation
- pseudorandom-noise data
    - pseudorandom signals usually generated by digital computers
    - pseudorandom binary signal (PRBS) alternates between +Aand −A
       randomly with a selected level A, a broadband (white signal) quite
       suitable for identification
- details covered in [FPW] and System Identification course,

```
basic tools including least-squares and cross-correlation
Control Sys. Spr '23
Prof. Kuen-Yu Tsai/NTUEE 63
```

### Amplitude/time scaling for numerical accuracy

- magnitude of variables in a problem can be very different,

causing numerical difficulties

- a serious problem when using analog computers, scaling a
    routine
- floating-point numbers in digital computers increase the scale,
    but do not entirely eliminate the problems (e.g., poles with
    natural freqs. of very different orders; roots sensitivity to coeffs.)
- amplitude scaling
- pick appropriate units!!
- normalized w.r.t the largest expected value(s), such that
the new variable(s) vary between  1
- e.g., x=Sxx, , substitute into the DEs
Control Sys. Spr '23
Prof. Kuen-Yu Tsai/NTUEE 64

x' ==S x xxx, ' S x


### Amplitude/time scaling for numerical accuracy

- time scaling
    - pick an appropriate unit!! (e.g., sec. vs. s)
    - normalized, substitute into the DEs
    -
### Mason’s rule and signal-flow graph ([FPW] W3)

- A general way to simplify complex block diagrams
- redraw standard block diagrams to signal-flow

#### graphs, then apply Masons’s rule:

```
### Mason’s rule and signal-flow graph (App. W3)

```
Figure W.1: Block diagrams and corresponding
signal flow graphs
```

## Historical perspective

- P.-S. Laplace (1749-1827)
    - study origin and dynamical stability of the solar system
    - concept of potential as in gravitational or electrical field, Laplace’s equation
       (a 2nd-order PDE, EM, fluid dynamics, astronomy...)
    - Laplace transform techniques reformulate PDEs and ODEs to algebraic eqns.
       which are much easier to manipulate in engineering applications
- J. B. J. Fourier (1768-1830)
    - Fourier seriesfor solving heat conduction eqn. –periodic signals
    - Fourier transform: a special case of LT (Laplace was one of Fourier’s
       teachers), non-periodic signals
    - greenhouse effect
- O. Heaviside (1850-1925)
    - Heaviside step function
    - electrical engineer (start as a telegraphy operator), mathematician, physicist
    - reformulated Maxwell’s eqns. to the present form
    - foundations of telecommunication, existence of ionosphere
       Control Sys. Spr '23
          Prof. Kuen-Yu Tsai/NTUEE 68

# HW 3 Assignment

## 1. [FPE] chap. 3 review questions

1. What is the definition of "transfer function"?
2. What are the properties of systems whose response can be described by transfer
functions?
3. What is the Laplace transform of f(t -) 1(t -) if the transform of f(t) is F(s)?
4. State the Final Value Theorem.
5. What is the most common use of the Final Value Theorem in control?
6. Given a second-order transfer function with damping ratio ; and natural frequency
    n, what is the estimate of the step response rise time? What is the estimate of the
percent overshoot in the step response? What is the estimate of the settling time?
7. What is the most noticeable effect of a zero in the RHP on the step response of the
second-order system?
8. What is the major effect of a zero in the LHP on the second-order step response?
9. What is the main effect of an extra real pole on the second-order step response?
10. Why is stability an important consideration in control system design?
11. What is the main use of Routh'scriterion?
12. Under what conditions might it be important to know how to estimate a transfer
function
from experimental data?


# HW 3 Assignment (cont.)

## 2. [FPE] Prob. 3.23
For the electric circuit shown in Fig. 3.56. find the following:
(a) The time-domain equation relating i(t) and v 1 (t);
(b) The time-domain equation relating i(t) and v2(t);
(c) Assuming all initial conditions are zero, the transfer function V 2 (s)/V 1 (s) and the damping
ratio and undampednatural frequency nof the system;
(d) The values of Rthat will result in v 2 (t) having an overshoot of no more than 25%, assuming v 1 (t)
is a unit step, L= 10 mH, and C= 4 F.

## 3. [FPE] Prob. 3.25


For the unity feedback system shown in Fig. 3.58, specify the gain and pole location
of the compensator so that the overall closed-loop response to a unit-step input has an
overshoot of no more than 25%, and a 1% settling time of no more than 0.1 sec. Verify
your design using MATLAB.

## 4. [FPE] Prob. 3.32
## 5. [FPE] Prob. 3.47


Consider the system shown in Fig. 3.68.
(a) Compute the closed-loop characteristic equation.
(b) For what values of (T, A) is the system stable? Hint: An approximate answer may be
found using 𝑒−𝑇𝑠≅ 1 −𝑇𝑠or 𝑒−𝑇𝑠≅^1 −

𝑇𝑠 2
1 +𝑇𝑠 2 for the pure delay. As an alternative, you
could use the computer MATLAB (SIMULINK®) to simulate the system or to find the
roots of the system's characteristic equation for various values of Tand A.

### Chapter 2 Mathematical Models of Systems
- Introduction
- Differential Equations of Physical Systems
- Linear Approximations of Physical Systems
- The Laplace Transform
- The Transfer Function of Linear Systems
- Block Diagram Models
- Signal-flow Graph Models
- Design Examples


