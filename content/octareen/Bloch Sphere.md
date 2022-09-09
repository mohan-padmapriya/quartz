-----------------
> #Why
> *The Bloch sphere is a intuitive, minimalist, visual representation of the state of a qubit. All normalised, pure states can be illustrated on the surface of the Bloch Sphere.



[[The Bloch Sphere is an accurate visualisation tool]]

![[Attachments/Bloch Sphere_2021-10-06 11.15.26.excalidraw.md]]



A [[Qubit]] state $\ket \psi$ can be parametrised in terms of two angles $\theta \in [0, \pi], \phi \in [0, 2\pi]$


For $$\ket \psi = \alpha \ket 0 + \beta \ket 1$$
$$\alpha = cos(\theta/2)e^{i\phi_\alpha}, \beta = sin(\theta/2)e^{i\phi_\beta}$$
$$\therefore \ket \psi = cos(\theta/2)e^{i\phi_\alpha} \ket 0 + sin(\theta/2)e^{i\phi_\beta} \ket 1$$
$$= e^{i\phi_\alpha}[cos(\theta/2)\ket 0 + sin(\theta/2)e^{i\phi}\ket 1$$
- $\phi = \phi_\beta - \phi_\alpha$

- $\psi$ describes the relative phase
- $\theta$ describes the probability to measure $\ket 0, \ket 1$
	- $\therefore P(0) = cos^2\frac{\theta}{2}, P(1) = sin^2\frac{\theta}{2}$
		- And, $P(0) + P(1) = 1$

- Pure states are represented on the surface of the sphere.
- Mixed states can be illustrated inside the sphere.

[[classical bit]]

> *Bloch vector* - 
$$
\begin{pmatrix}
sin\theta cos\theta \\
sin \theta sin\phi \\
cos\theta
\end{pmatrix}
$$


- *This parametrisation can be represented as a Bloch Sphere*

# Derivation

From 4 parameters, now we end up with 3 parameters! $r_0, r_1$ and $\varphi := \varphi_1 - \varphi_0$. It turns out we can do more: remember that $|c_0|^2 + |c_1|^2 = 1$. After easy algebraic manipulations, this translates into: $r_0^2 + r_1^2 = 1$, reducing the number of unknowns to 2! Using the angle representation of the above equality and setting $r_0 = \cos \theta ~\text{and}~ r_1 = \sin \theta$, we obtain the equivalent repsentation of $|\mathbf{\psi} \rangle$:

However, in the case of quantum bits, we know that a quantum state does not change if we multiply it with any number of unit norm; i.e., $| \mathbf{\psi} \rangle = e^{j \xi}| \mathbf{\psi} \rangle$ Let’s set $\xi = -\varphi_0$. Then, our (equivalent) state is:

To answer your question about what $\theta$ represents, taking a look at the Bloch sphere might help. 
As for where $\theta$ comes from, and to elaborate on the parameter representation, here's how you could derive it -

Any state of a qubit  can be represented by $$\ket{\psi} =  \alpha .\ket{0} + \beta .\ket{1} ~\text{where}~ \alpha, \beta \in \mathbb{C}$$
If you consider $\alpha = r_0e^{i\phi_0}$ and $\beta = r_1e^{i\phi_1}$, where $r_i$ represent the amplitudes, $\phi_i$ the phases, and $r_i, \phi_i \in \mathbb{R}$, our representation becomes $$\ket{\psi} = r_0e^{i\phi_0} .\ket{0} + r_1e^{i\phi_1} .\ket{1}$$
Notice how we've gone from 2 complex parameters to 4 real parameters.

However, global phase is irrelevant to us; we use $\phi := \phi_1 -\phi_0$ to indicate relative phase, reducing the number of parameters from 4 to 3.
We now have
$$\ket{\psi} = r_0 .\ket{0} +e^{i\phi} r_1 .\ket{1}$$
Additionally, since the qubit state must be normalised,
($|\alpha|^2 + |\beta|^2 = 1$ and therefore $r_0^2 + r_1^2 = 1$), 
we can further reduce the number of parameters to 2 -
$$\ket{\psi} = \cos\theta .\ket{0} +e^{i\phi} \sin \theta .\ket{1}$$ ,
where $\theta, \phi \in \mathbb{R}$
($\sin^2\theta + \cos^2\theta = 1$ and $r_0 = \cos \theta; r_1 = \sin \theta$) 

The Bloch Sphere allows us to represent these parameters geometrically. $\theta, \phi$  in sperical co-ordinates, are the co-latitude and the longitude with the $z$-axis and the $x$-axis respectively.


------------
[[Measurement]]
- The Z measurement corresponds to a projection onto the z axis of the bloch sphere
- Similarly for x and y measurements too


--------------------------
#todo 
- [ ] Bloch sphere uses the [[Spherical Co-ordinate System]]. What advantages does this system offer compared to the rectangular or cylindrical coordinate systems? 
- [x] How accurate is the bloch sphere as a visualisation tool?
	- [[The Bloch Sphere is an accurate visualisation tool]]