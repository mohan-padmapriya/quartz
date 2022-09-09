
## Applications
 ## 1. Amplification
 [[Amplifiers]] are used everywhere. 
 The process of amplification can be achieved by using dependent sources. There are 4 types, but we'll use a **voltage controlled current source**.
 Like so: 
 ![](razavi1.png)



How would you implement a *voltage dependent current source*? We can't have an inductor/capacitor/resistor do it. Therefore, we use a transistor. Specifically, a *bipolar junction transistor*

 So essentially, you need a voltage controlled current source to design an amplifying circuit.
 So Shockley and his dudes at Bell Labs come up with the **BJT**.
 - ***The BJT/voltage dependent current source converts voltage to current, and then with the resistor, converts current to voltage again***
 - ![](razavi_vtoitov.png)
 
- BJT is not symmetric, one junction is more heavily doped than the other
![[Pasted image 20210809142251.png]]
### [[Biasing]] - basics
![[Pasted image 20210809142027.png]]
- Unlike two terminal devices, in which one terminal is positive and the other is negative, here, we have several combinations of +/- configurations between terminals. 
- However, not all combinations of voltages around the device is useful
	- EB --> FB
	- CB --> Zero or RB
This is the ***Active forward bias/region***
![](razavi2.png)



> *PNP config*
> ![](razavi_pnp.png)
### Operation
- Primary transportation mechanism inside the device is diffusion.



*In the forward active region -*
The relationship between $I_c$ and $V_{be}$ is exponential. This is what makes it useful for amplification. This is the device's voltage controlled current behaviour.


### Properties
#### Voltage dependence
$$I_C = I_S(e^{\frac{V_{BE}}{V_T}} - 1)$$
We ignore the $1$, because the exponential term is extremely large


![](razavi4.png)
$I_c$ depends on $V_be$
Therefore, ***Voltage dependent*** 						--(1)


#### Current Source
- $I_C$ is independent of $V_CE$ because the electrons that carry collector current are controlled completely by $V_BE$.
- Therefore. $I_C$ vs $V_CE$ graph, when $V_BE$ is constant, is a straight line. Increasing $V_CE$ does nothing.

Because of this constancy, the transistor appears to act as a current source, a device in which current stays constant regardless of the change in $V_ce$.
![](razavi5.png)

Therefore ***Current source*** 							--(2)

From 1 and 2, we've got a ***voltage dependent current source***.

#### I-V Characteristics
![](razavi_iv-bjt.png)
- Each $V_{BE}$ has a corresponding $V_{CE}$, and hence, in a way, a corresponding current source.
- The relationship between $V_{BE}$ and $I_C$ is exponential, and is indicated by the [[Transconductance]]




### Transistor models
*In forward active region -*


#### Model 1 - simplest
![](razavi_bjt1.png)


#todo 
- [ ]  Why not connect the current source between CE, why not between CB?
- [ ]  There is no base to emitter current flowing, which means emitter current is equal to collector current, according to this model. Makes sense, what about the base current?

#### Model 2 - includes *I_B*
![](razavi_bjt2.png)



> - Reverse saturation current of the diode is $\frac{I_S}{\beta}$


# [[Biasing]] techniques
In a complex circuit, it would be quite inconvenient if to bias each BJT, we required a separate battery. Hence, we replace the battery with a more practical circuit, like a resistive divider.
![](razavi_biasing1.png)
## What happens to the input impedance?
- In this new model, what resistances do we have between the input node and AC ground?
	- $R_1, R_2, r_{\pi}$
	- Therefore, $R_{in} = R_1 || R_2 || r_{\pi}$
	- The resistive network has lowered the input impedance of the circuit. *Therefore, we choose $R_1, R_2$ in such a way that its effect is not felt as much.*
	- Therefore we choose $R_1, R_2 >> r_{\pi}$

## What happens to the base current?
![](razavi_biasing2.png)
Note that this equation is not entirely accurate, because for it to be true, we have to assume all the current that flows through $R_1$ flows into $R_2$. But this is not true, this is not a simple voltage divider, because some current flows into the base as well.

- The true equation, owing to the base current is -
- ![](razavi_biasing3.png)

### Analysis to determine $I_B$
Let's find the [[Thevenin]] equivalent of this circuit
- ![](razavi_biasing4.png)
- The equation is non-linear, and so we find $I_B$ by iteration

**However, instead of this approach, we can also approach $I_B$ by considering the $\beta$ of the device**
- We don't want the voltage at the input to be sensitive to the base current. 

*How do we make sure base current is as minimal as possible?*
- By choosing a large enough $\beta$, we pretend that $I_B$ doesn't exist, thereby reducing sensitivity of the voltage to $I_B, \beta$
***- Therefore, we choose $\frac{V_{CC}}{R_1 + R_2} >> I_B$***

## How do we interface this circuit with the preceding stage?
- We have to make sure the output - *collector voltage* of the preceding stage and the input - *input voltage* of the present stage are equal.
- If they are not, they cannot be simply shorted.

### DC Coupling
- Direct shorting
- $V_{CE} of Q_0 = V_{in} of Q_1$
- - ![](razavi_biasing6.png)

### AC Coupling
- Using a capacitor
- - $V_{CE} of Q_0 \neq V_{in} of Q_1$
- When we're doing analysis with purely DC quantities, the capacitor in the middle acts as a short circuit and the stages can be analysed and designed independent of each other.
- When the signal comes in, the capacitor conducts. 


#### Choosing the capacitor
- $C_1$ should be a reasonable short circuit at the lowest signal frequency.
- We require the impedance of the capacitance to be much lesser than the input impedance of the last stage, so that it provides low attenuation 
- - ![](razavi_biasing7.png)

## Design procedure for simple [[biasing]]
Summary -
To determine $R_1, R_2$ -
- - ![](razavi_biasing8.png)

## Problem of supply sensitivity
= We have taken care of the sensitivity to $\beta. I_B$
- What about sensitivity to $V_{CC}$?
- ![](razavi_supplysen.png)


**Turns out, [[Common Emitter#CE stage with emitter degeneration]] helps here too. **
How?

![](razavi_supplysen1.png)
The condition $R_EI_C >> V_T$ is what matters

## What about $R_C$?
An upper bound for $R_C$ is given by -
$$V_C = V_{CC} - R_CI_C \geq V_X$$
Where $V_X$ is the voltage at the input

## Increasing gain without changing bias components
$$A_V = \frac{-R_C}{1\g_m +R_E}$$
- If you decrease $R_E$, you could increase gain.
- But this would change the DC config too. You need something that works only when the signal comes in.
- A component *whose impedance reduces as the frequency increases* --> A capacitor!
- So simply put a capacitor in parallel with $R_E$
- $\frac{1}{C_E \omega}$ must be small, so $C_E$ must be reasonably big, if possible
-------------------------

#todo 

- [ ]  Forget diode related things for [[amplifiers]]. How else would you build one?
- [ ]  What about taking into account the internal resistance of the mic?
- [ ]  Is the amplifier we've build above a satisfactory [[amplifier]]? Are we satisfying the condition of BC junction reverse or zero biased? What to add to make sure of this?
> - [ ]  *Check [[Common Emitter]] topology*
- [ ]  Why do you have the resistor in the above amplifier circuit?
- [ ]  Forget dependent source related design. How else would you design one?
- [ ]  Why is silicon so popular when you've got germanium?
- [ ]  Why can't you just stick two diodes back to back to get a BJT? Why would that not work?
- [ ]  Why is the base region super thin?
- [ ]  Why connect a battery between emitter and collector rather than a battery between collector and base? Why choose $V_{CE}$ instead of $V_{CB}$?
	- [ ]   Why not the first config, why the second config?
	> ![](razavi3.png)
- [ ]  So the electrons from the emitter can go either to the base or to the collector. Why does Ic depend on Ib then? Doesn't it depend on Vbe and Vce instead?
- [ ]  **By what mechanism do electrons flow through the base? [[Diffusion]] or [[drift]]?**
- [ ]  What happens if Vbe increases? Ic increases. But why?
- [ ]  Is BJT a current controlled device? Or is it a voltage controlled device? Which model for which context?
- [ ]  Why does the area of the emitter matter so much?
- [ ]  Increasing $V_CE$ does nothing. Why, justify.
- [ ]  Holes that base supplies to the emitter is the base current. But why does collector *depend* on this?
- [ ]  At the base emitter junction - some holes recombine, some holes cross to the emitter. More the holes, more the recombination, therefore less collector current? Why is this not the case? Also why are the electrons from the emitter going to the collector at all?
- [ ]  What is $I_S$?
- [ ]  How does temperature change change terminal currents in a BJT?
- [ ]  Why is this a useless amplification circuit, how will you modify it to make it better? 
	- [ ]  ![](razavi6.png)
	- [ ]  Explain with respect to [[transconductance]]
- [ ]  Which operating point is better and why? What metric hints at which one is better?
	>  ![](razavi7.png)
- [ ]  If the microphone signal of an amplifier is a sinusoid, is the Ic obtained also necessarily a sinusoid?
- [ ]  Why do we need small and large signal models for BJTs but not resistors?
- [ ]  What happens to batteries/constant voltage sources in small signal analysis?
	> *Small signal models only represent perturbations. Therefore, they are replaced by 0/short circuits*
- [ ]  True or false - *Large signal models are for DC and small signal models are for AC*
- [ ]  In a complex circuit, is each stage biased with a separate battery? How do we bias a stage without connecting a battery explicitly?
	- [ ]  Resistive divider
	- [ ]  What else could you use in place of a battery to bias circuits, like a resistive divider? Where else would you need to replace batteries like this?
- [ ]  WHy should the capacitor in AC coupling have low frequency?
> How does having a low impedance capacitor minimise attenuation, behave as a short circuit?
- [ ]  How do you change thegain without changing bias components?