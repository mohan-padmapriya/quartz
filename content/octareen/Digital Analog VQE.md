Different from just [[Variational Quantum Eigensolver]].
*--> we propose to merge digital single-qubit operations with analog multi-qubit entangling blocks in an approach we call digital-analog quantum computing (DAQC).*

What is analog quantum computing then?
*The complexity of classical simulations of many-body quantum systems typically grows exponentially with the dimension of the system. This was first recognized by Richard Feynman in a seminal paper from 1982 [3], in which he proposed as an efficient solution the simulation of these problems employing another fully-controllable quantum system with a similar encoded dynamics [7]. This was the origin of what is now called analog quantum computing (AQC)*
**Analog Quantum simulators**
The simplest approach to perform quantum simulations is the use of a controllable quantum system whose effective dynamics is similar to the one of the desired model. Such singlepurpose devices are called analog quantum simulators (AQS).

Analog simulators are limited by the hamiltonians they can simulate


And what is digital quantum computing?
*. The discovery of universal sets of quantum gates and quantum error correction [8–10] provided a clear roadmap towards a scalable QC mimicking the history ∗ mikel.sanz@ehu.es of classical computers. This approach is called digital quantum computation (DQC) [11, 12], based on an algorithmic sequence of one-qubit and two-qubit gates [6*
**Digital quantum simulators**

that digital quantum simulators (DQS), whose evolutions are decomposed in a universal set of quantum gates acting on a register of qubits, can simulate efficiently any quantum system. 

Digital simulators are not limited by their hamiltonians, and can simulate any hamiltonian. 

***This approach allows for universal simulation of quantum dynamics while replacing two qubit gates for an analog Hamiltonian and has been argued to be more resilient against certain types of noise than digital quantum computing.***


*Likewise, continuous algorithms such as the quantum adiabatic algorithm [16, 17] and quantum random walk algorithms [18, 19] make use of a predefined analog Hamiltonian with generally limited programmability to solve computational problems. Discrete algorithms, on the other hand, are defined in terms of sequences of digital unitary gates. A gate-based quantum computer can perform any discrete, gate-based algorithm, including Trotterized versions of continuous algorithms [20]. Whereas, a device designed for continuous quantum algorithms, though may be theoretically universal, will generally only be able to run the restricted set of time evolutions for which they are built—it is in theory possible to express any discrete time quantum algorithm (e.g. Shor’s) as a continuous time quantum algorithm, but generally not practical [*

![[Pasted image 20220830004303.png]]

*Digital quantum simulations* decompose the dynamics of a quantum system to be simulated into a circuit of discrete gate operations that are implemented on a quantum processor. 

> *Second quantization?*


This is useful to simulate a wide range of quantum problems. 

Problem?
Current quantum processors have only a limited coherence time and lack the capability to correct errors that come up during computation. The gates introduce a bunch of noise, so we want to get rid of them.
So how does analog solve this?

Analog quantum simulations map the problem [[Hamiltonian]] to be simulated to the hamiltonian of the quantum simulator. The results are mapped back to the problem. 

$$\hat H_{sys} = \hat H_{sim}$$


This prevents *crosstalk*. Nay, it leverages crosstalk. 
Analog allows the system to interact naturally and leverages that. 

![[Pasted image 20220815193412.png]]

This limits the range of problems, because only some problems can be efficiently mapped. 

> *How is this mapping done? Also for LiH, what is the system?*


Therefore, this is similar to looking for problem inspired ansatz
[[Problem Inspired Ansatz]]

But, analog simulators are limited to hamitonians they can simulate only. Therefore, we use the digital-analog approach. The underlying processor's hamiltonian is used here. 


# The problem
**Output:** A new VQE ansatz
> *so we need to find the hamiltonian of the processor we are using?*



How?
Switch the multi-qubit gates in the ansatz to analog multiqubit blocks. 


Where to start:
1. Use Ising hamiltonian as your analog hamiltonian and implement. Compare this to digital. 
2. Modify the ising hamiltonian and try. 


## Metrics
1. Working implementation for DAQC VQE 
	1. H2 usecase
	2. One more use-case
2. Analysis
	1. Use different hamiltonians
		1. How to do this?







## Call
- How to decide on an ansatz
	- Look at problem inspired ansatz in papers and draw solutions from there
		- digital single qubits, then analog, then single qubit gates again - 
		- More blocks, better it should get, because more parameters and mor etypes of enganglements and more hilbert space is accessible
		- But, more blocks means more noise - NISQ be like that

*Almost any two-body hamiltonian is universal*
any unitary can be arbitrarily close simulated employing these resources.