# Multivariable Optimal Control

## Contents
- Review: Pole Placement Control Design for MIMO Systems
	– Limitations
- Infinite number of possible solutions for state feedback gain K
- Difficult to modify control effort like R.L. (k $\leftrightarrow$ u)
- Introduction to MIMO Linear Quadratic (LQ) Optimal Control
	– Quadratic cost functions
	– Solution of optimal u for Finite-horizon cost
	– infinite-horizon case
- Special LQ: Symmetric Root Locus for SISO systems
	– LQ cost for SISO systems
	– Design tradeoff between control effort and state convergence
	– Determine SLR from closed-loop characteristic equations

## Review: Pole placement Regulator design (CT, SISO)
![[Pasted image 20230604213523.png]]
![[Pasted image 20230604213541.png]]

### Limitations 1 
![[Pasted image 20230604213617.png]]

### Introduce Optimal Control to pick one K
- A strategy for determining the feedback gains:
	– Choose the “best” (optimal) K to optimize some closedloop performance, e.g.,:
	- the control effort (maximum force; energy spent)
	- the transient and/or steady-state errors
	- the dollar cost of an operation
	- …
	– Specify a cost function (performance index) in a optimization problem from which K can be solved by using mathematical optimization

### Pole-placement for MIMO systems－Limitations 2
![[Pasted image 20230604213819.png]]

## Introduction to MIMO Linear Quadratic (LQ) Optimal Control
![[Pasted image 20230604213854.png]]
![[Pasted image 20230604213906.png]]
![[Pasted image 20230604213919.png]]
![[Pasted image 20230604213937.png]]
![[Pasted image 20230604214001.png]]

### Special LQ: Symmetric Root Locus for SISO systems
![[Pasted image 20230604214025.png]]
![[Pasted image 20230604214035.png]]

### Symmetric Root Locus SISO examples
![[Pasted image 20230604214105.png]]
![[Pasted image 20230604214118.png]]

### Design tradeoff between control effort and state convergence through p
![[Pasted image 20230604214150.png]]

### Easy way to plot SRL in Matlab
![[Pasted image 20230604214209.png]]
![[Pasted image 20230604214218.png]]
### SRL for DT systems
![[Pasted image 20230604214322.png]]
![[Pasted image 20230604214331.png]]

### SRL for CT＆ DT
![[Pasted image 20230604214409.png]]
![[Pasted image 20230604214418.png]]

### Q, R selection rule of thumbs
![[Pasted image 20230604214444.png]]

### Discrete Cost Equivalence
![[Pasted image 20230604214507.png]]

### Settling time constraint
![[Pasted image 20230604214520.png]]

### Modifying state feedback controllers (e.g. LQG): From regulator to tracking control
![[Pasted image 20230604214548.png]]
![[Pasted image 20230604214626.png]]





