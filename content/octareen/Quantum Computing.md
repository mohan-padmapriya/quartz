# Quantum Computing

-----------------------------
> #Why 
> - [[Limitations of classical computers]] are several, and [[Quantum computers can do everything classical computers can]]. With advancements in [[Quantum Hardware]] and [[Quantum algorithms]], we are ready to exploit the [[Quantum advantage]]. 
---------------------------

- *Indeed, much work on quantum computing is about attempting to develop ways of moving from low levels of abstraction to higher, more conceptual levels.*

## Use cases
- [[PsiQuantum]] is leveraging QC to battle [[climate change]]
	- *The top use cases thus far include batteries with higher density (particularly for transportation and grid storage), perovskites for more efficient solar panels, new solvents for point-source carbon capture and adsorbents for direct-air capture, new zero-carbon cement clinkers, modeling membranes, catalysts and electrical currents in hydrogen production, and (as mentioned earlier) new ways of creating clean ammonia. Real cost reductions drive technology adoption rates, so this should speed up green technology use by five to ten years.*
- 
- [[Drug discovery]]  using QC
- 

From here, you may proceed to 
- [[Quantum information Theory | Quantum Information]]
- [[Quantum Cryptography]]
- [[Quantum Machine Learning]]
- [[Quantum Hardware]]

or, proceed and understand the basics

[[Papers in QC]]


## In a nutshell
With 3 bits, you can encode 0-7, and access each one of those states at a time. Using quantum computing, you can access and manipulate 0-7 in [[superposition]], at once. However, to get the final answer after compuatation, you must perform [[Measurement]] which collapses the superposition to a single state. Then why would this be useful? Because using [[Interference]] effects, we may cancel out the wrong/undesirable answers and make sure when we measure, the desired state is what it collapses to. 


----------------------------------------------------------------

#todo 
- [x] Why use vectors to represent quantum states? What does this have to do with superposition and the ability to exist in any and all states when not being measured?
- [ ] Relationship between collapsing of wave, [[superposition]], [[dot product]], [[Projections]], etc etc? 
- [ ] *There are an infinite number of states between 0 and 1*. Justify. Are all states *allowed*?
- [ ] [Why do we need classical parts in a quantum circuit?](https://qiskit.org/textbook/ch-algorithms/defining-quantum-circuits.html#why-classical) ^88bb7b
- [ ] Why did #AlbertEinstein object to [[Quantum Entanglement]] so strongly? What is [[Spooky action at a distance]]?
- [ ] [[Quantum Information is analog AND digital]]
- [x] What is the language of computers? - [[Computer-speak]]
- [x] The state of a qubit is 2D vector only? Can we have higher dimensional state spaces?
- [ ] Is the [[Dirac notation]] superior to normal vector notation? Why?
- [x] Can we discriminate only orthogonal states
- [ ] State with too much entropy vs state with too much noise --> what is the difference?
- [ ] [[Will aliens have computers?]]
- [ ] [[It is impossible to tell for sure what the measurement of a qubit will give us - PARTIALLY TRUE]]
- [ ] [[Any measurement on a qubit changes it - PARTIALLY TRUE]]

-----------------

- [[Measurement]]

- Will aliens have computers?
- [[Hilbert 1928]]
- What is an [[Algorithm]]?
- [[Turing Machine]]
- [[Quantum Dots]]

## [[Qubit]]
## [[Quantum gates]]
## [[quantum wire]] and [[Quantum circuits]]




#GargiDasgupta
#MSSanthanam
#LVenkataSubramaniam
#VRamakrishna 

- [[Limitations of classical computers]]
- [[Quantum advantage]]
- [[IBM]]'s [[Quantum Roadmap]]
- [[Quantum volume]]


### Q mission in India
- [[General purpose Quantum Computer?]]
- [[Quantum algorithms]] and their speed ups

- Brief introduction to Applications of Quantum
- [Watch this!](https://www.youtube.com/watch?v=voSRtTKiTQo)

### Postulates of [[Quantum Mechanics]] 
> - *What is the underlying physical description of a qubit?*
> - *How do we represent physical properties of such quantum systems?*
> - *How do such quantum systems evolve with time? How do we **transform* * such quantum systems?*

- [[Qubit]]
- [[Two level quantum systems]]
- [[Postulates of QM in QC]]
- [[Bra-ket]]
- [[Normalisation]]
- [[Bloch Sphere]]
- [[Hadamard gate]]
- [[Quantum Entanglement]]


# [[Quantum algorithms]]
# [[Quantum Error Correction]]

#DavidDeutsch 's [[Desiderata for a Universal Quantum Computer]]
[[Variational Quantum Algorithms]]
- [[VQE]]
- [[No-cloning theorem]]

--------------------------------
Quantum Computing uses [[Quantum Mechanics]] as a basis to compute - specifically the quantum mehanical phenomenon of [[Interference]], [[superposition]], and [[Quantum Entanglement | entanglement]]. 
There are several [[Limitations of classical computers]] that the [[Quantum advantage]] can overcome. 

## QM behind the QC
> -   _What is the underlying physical description of a qubit?_
> -   _How do we represent physical properties of such quantum systems?_
> -   _How do such quantum systems evolve with time? How do we **transform_ _such quantum systems?_

[[Postulates of QM in QC]] have the answers to these fundamental questions. 

The physical model for quantum [[Measurement]] is the [[Stern-Gerlach experiment]] from 1922. 

## Basic differences between classical and quantum systems

| Classical Systems                                          | Quantum Systems                                                                 |
|:---------------------------------------------------------- | ------------------------------------------------------------------------------- |
| [[classical mechanics]]                                    | [[Quantum Mechanics]]                                                           |
| [[classical bit]]                                          | [[Qubit]]                                                                       |
| Classical bits take on Deterministic states                | [[qubits]] take on [[Probability \| Probabilistic states]]                      |
| Operate on [[Boolean Algebra]]                             | Operates using [[Linear Algebra]]                                               |
| Manipulated using *Logic gates*                            | Manipulated using [[Quantum gates]]                                             |
| [[Logic gates]] are logical operations that are reversible | [[Quantum gates]] are [[Matrix Multiplication]]s that are irreversible          |
| State space = *N*, where *N* is the number of inputs       | State space = $2^N$, where *N* is the number of inputs                          |
| [[Linear]] in the size of inputs                           | [[Exponential]] in the size of inputs                                           |
| States exists exclusively in either 0 or 1                 | States exists in a [[superposition]] of 0 and 1                                 |
| Operations are irreversible                                | Operations are reversible                                                       |
| Copying an arbitrary bit is a basic operation              | Arbitrary qubits cannot be copied, as established by the [[No-cloning theorem]] |                                                           |                                                                                 |


-----------------------------------

## The notation
Quantum computing uses [[Dirac notation]]. 
Quantum systems are defined over the [[Hilbert Space]]

----------------------------

## The qubit
The ***[[Qubit]]*** is the fundamental unit of information in a [[Quantum Mechanics | Quantum mechanical system]]. It is an example of [[Two level quantum systems]]. There are several ways in which [[Physical realisation of a qubit | qubits are implemented physically]]

***A qubit probabilistically collapses to either one of the basis states*** upon [[Measurement]]. The probability of a qubit collapsing to a particular state is given by [[Born's Rule]]. The [[Normalisation]] constraint applies on the probabilities. 

The [[Bloch Sphere]] is a handy tool to visualise a single qubit system. It uses the [[Spherical Co-ordinate System]]

--------------------------------

Qubits do not exist in isolation, therefore, we study [[multipartite quantum states]]. Multipartite states that are [[Quantum Entanglement | entangled]]; they cannot be represented as a [[Tensor product]] of two qubit states. 

[[Bell States]] are *maximally entangled*.
[[Bell States|EPR pair]]s are particularly useful in the process of [[Quantum teleportation]].

We use different [[Quantum gates]] to construct [[Quantum circuits]] that implement [[Quantum algorithms]].
In [[Quantum circuits]], we apply suitable [[Global and relative phase | phase]] changes to [[superposition]] states to amplify desired states and diminish other states.


--------------------------------

## Beyond the basic
- [[Quantum Machine Learning]]
- [[Quantum information Theory]]
- [[Quantum Cryptography]]



#AndyMatuschak
#MichaelNeilsen
