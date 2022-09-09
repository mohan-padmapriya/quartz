   Using a [[BJT]], we have the common emitter topology
   
   # Properties
  ![](razavi_ce1.png)
  
  # Simplified Diagram
  ![](razavi_ce2.png)
  ![](razavi_ce6.png)
  
  # [[Small Signal Model]]
  **Assumption** - $V_A = \infty$, i.e [[Early Effect]] is negligible, $I_C$ is independent of $V_{CE}$. Therefore, $r_0 = \infty$
  
  ![](razavi_ce3.png)
   
   ## Voltage Gain $A_v$
   It is the $g_m$ multiplied by the *total resistance between $R_c$ and **AC ground** *
   > $$V_{\pi} = V_{in}$$
   > Therefore, $$g_m V_{\pi} = g_mV_{in} $$
   > Applying KCL, we know
   > $$g_m V_{in} + \frac{V_{out}}{R_c} = 0$$
   > $$g_m V_{in} = - \frac{V_{out}}{R_c} $$
   > $$\therefore A_v = \frac{V_{out}}{V_{in}} = -g_m R_c$$

### Limited voltage headroom
$I_C R_C$ limits the gain because its value affects $V_out$ and decides the bias of the BC junction, and therefore controls which region the transistor operates in
   
 ### Inclusion of [[Early Effect]]
 - We know that voltage gain is $g_m$ multiplied by the *total resistance between $R_c$ and **AC ground** *
 - ![](razavi_ec5.png)
 - With [[Early Effect]], we see that $A_v$ is limited further.
<!--ID: 1625799980558-->


#### Intrinsic gain of a transistor
If we didn't have $R_C$, or rather, if $R_C = \infty$, $A_V = -g_m r_0$
- $g_m r_0$ is the intrinsic gain of the amplifier. It is the best the transistor can do.
- Note that $g_m r_0 = \frac{I_C}{V_T} \frac{V_A}{I_C}$
- Therefore, the ratio $\frac{V_A}{V_T}$ is indicative of the intrinsic gain of the transistor.
<!--ID: 1625799980575-->



## Attenuation factor
- We have not considered the internal resistance associated with $V_{in}$ until now.
- Because the mic has some internal resistance $r_m$, the circuit now (ignoring [[Early Effect]]) looks like this -
![](razavi_attn1.png)
![](razavi_attn2.png)
And hence, our gain is now reduced, because the input is attenuated
- $\frac{r_{\pi}}{r_{\pi} r_m}$ is the attenuation factor
<!--ID: 1625799980591-->



# Amplifier Impedance
## Input Impedance
- ***$r_{\pi}$***
- ![](razavi_impe1.png)
<!--ID: 1625799980608-->


### To calculate $R_{in}$
- Set all independent sources to 0
- Apply a small signal voltage source between input terminals and calculate the current supplied by this voltage source 
- $R_{in} = \frac{V_x}{I_x}$
<!--ID: 1625799980624-->


- ![](razavi_impe3.png)
## Output Impedance
- Consider the thevenin's equivalent of the small signal model
- ![](razavi_oimpe1.png)
- $R_C$ determines the voltage that can be got across the load
- Therefore, $R_C$ is known as the output impedance
<!--ID: 1625799980641-->


### To calculate $R_{out}$
- Just like with thevenin's, set all independent sources to 0 to calculate 
- ![](razavi_oimpe1.png)
- If you include [[Early Effect]], $R_{out} = R_C || r_0$
<!--ID: 1625799980657-->


## Summary
![](razavi_oiimpe.png)


# Cascaded stages
If a single stage of a CE amplifier doesn't give you enough gain, use two or more stages in series!
![](razavi_cascade1.png)


# Gain Variation
When $V_A = \infty, A_V = -g_m R_C = \frac{-I_C}{V_T}R_C$
- Due to:
## Temperature
$I_C = I_S e^{\frac{V_{BE}}{V_T}}$
- $I_s, V_T$ are functions of temperature
<!--ID: 1625799980674-->

## Process
- Manufacturing variability in $R_C$
<!--ID: 1625799980690-->

## Signal amplitude
- $g_m$ is not constant with time because when the signal is applied at the input, $I_C$ at the output (sinusoidal) varies. 
- Hence, $g_m$  varies and so does the gain
- The gain at the peak is higher than the gain closer to bias level
- We also observe that the output suffers ***distortion and non-linearity*** (because the positive peak has a different [[Transconductance]] compared to the negative peak of the input signal, and this reflects in the output signal)
- ![](razavi_signalvar.png)
<!--ID: 1625799980706-->


# CE stage with emitter degeneration

^57bd90

![](razavi_ce-degen1.png)
![](razavi_ce-degen2.png)
- If $R_E$ is large enough, it balances out gain variation and ensures the gain is less sensitive to $g_m$

## Properties
1. The gain is less sensitive to temperature and process variations, and to changes in signal amplitude
	- To minimise sensitivity to $I_C$, $R_E >> \frac{V_T}{I_C}$
	- i.e $R_E I_C >> V_T$
	- In summary, if there is a DC drop across $R_E$ which is greater than $V_T$, sensitivity is minimised
	- In which case, $A_V \approx \frac{R_C}{R_E}$
2. Gain is lower with degeneration than without
	- Trade-off 
3. $A_V = \frac{\textrm{Resistance tied between collector and ground}}{1/gm \textrm{ resistance tied between emitter and ground}}$
<!--ID: 1625799980722-->


## Input impedance
- Setting all independent sources to 0, from the small signal model, we see -
- ![](razavi_degen-impe1.png)
- Degeneration increases input impedance
<!--ID: 1625799980738-->


## Output impedance
- Regardless of degeneration, output impedance remains the same
- ![](razavi_degen-impe2.png)
<!--ID: 1625799980755-->


# Self bias CE
![](razavi_selfbias2.png)

   --------------
   #todo 
   - [ ] Why not take output voltage across $R_c$? Is this voltage important anywhere else? What if you took output there, what would happen to the gain?
   - [ ] The voltage gain of the small signal model tells us why our first ever [[Amplifiers]] config with only a mic did not work. Why did it not work?
   - [ ] What is an AC ground?
   - [ ] Because $A_V = -g_m R_c$, to double the gain, can we just double $R_c$?
   > - [ ] $V_{out} = V_1 - R_cI_c$. Changing $R_C$ changes the region in which the transistor operates. So nope, ***voltage headroom is limited***
   - [ ] How about doubling $g_m$?
   > - [ ] $g_m = I_c/V_T$. Therefore, to double $g_m$, we double $I_c$. But doubling $I_C$ changes $V_out$ again
   - [ ] What if you replace $R_c$ with a ideal and constant current source?
   - [ ] How do you know when to include [[Early Effect]] and when not to?
   - [ ] What is the significance of the ratio $\frac{V_A}{V_T}$?
      - [ ] What about taking into account the internal resistance of the mic?
   - [ ] If a mic has a substantial internal resistance, how will you maximise the gain of the amplifier? *What do you do to the input impedance*?
   - [ ] Does [[Early Effect]] change the value of the input impedance? What does $R_{in}$ depend on?
   - [ ] What if you account for the [[Early Effect]] when cascading amps, what happens to the gain formula then?
   - [ ] Variation in signal amplitude causes distortion and variation in the output. How does one overcome this?
   - [ ] How does adding $R_E$ solve the problem?
   - [ ] What is the relationship between $g_m$ and $R_E$? 
   - [ ] Are $R_E$ and $R_{\pi}$ in series? Parallel?
   - [ ] Won't $R_E$ be affected by process variations too?
   - [ ] Why is it called degeneration?
   - [ ] Why does degeneration increase input impedance?
   - [ ] Why do we [[Biasing | bias]] a transistor?
   - [ ] If the base voltage in a CE + degen circuit goes up, what happens to the emitter voltage? What about when w edon't have degen? Why is this important? What happens to the *base emitter* voltage?
   - [ ] What does CE + degen config do for [[BJT#Problem of supply sensitivity]]?
   