
## LTspice BJT Current Mirror Simulation
This repository contains the schematic and simulation files for a basic BJT (Bipolar Junction Transistor) Current Mirror designed in [LTspice](https://www.analog.com/en/resources/design-tools-and-calculators/ltspice-simulator.html). The circuit uses two matched 2N2222 NPN transistors to copy (mirror) a reference current from one branch into a load branch.
------------------------------
## 🛠️ Circuit Components & Parameters

* Voltage Source ($V_1$): Supplies a 12V DC rail voltage to drive the circuit.
* Reference Transistor ($Q_2$): Connected in a diode-configured setup (collector shorted to the base). This forces the transistor to operate in the active region and establishes the base-emitter voltage ($V_{BE}$).
* Mirror Transistor ($Q_1$): Shares the exact same base-emitter voltage ($V_{BE}$) as $Q_2$. Because the transistors are identical models, it mirrors the current flowing through $Q_2$.
* Resistors ($R_1, R_2$): Both are set to $10\text{k}\Omega$.
* $R_2$ sets the reference input current ($I_{ref}$).
   * $R_1$ acts as the load resistor for the output current ($I_{out}$).

------------------------------
## 📊 Mathematical Analysis & Expected Values## 1. Reference Current ($I_{ref}$)
The current passing through the reference branch ($Q_2$) is determined by Ohm's Law across $R_2$:
$$I_{ref} = \frac{V_1 - V_{BE}}{R_2}$$ 
Assuming a standard silicon BJT base-emitter drop of $V_{BE} \approx 0.7\text{V}$:
$$I_{ref} = \frac{12\text{V} - 0.7\text{V}}{10\text{k}\Omega} = \frac{11.3\text{V}}{10\text{k}\Omega} = \mathbf{1.13\text{ mA}}$$ 
## 2. Output Current ($I_{out}$)
Because $R_1 = 10\text{k}\Omega$ matches $R_2$, and both transistors share the same $V_{BE}$, the output current through $Q_1$ will mirror the reference current closely:
$$I_{out} \approx I_{ref} \approx \mathbf{1.13\text{ mA}}$$ 
(Note: There will be a minute discrepancy due to the transistor base currents ($I_B$) and the Early Effect, which can be observed during simulation.)
------------------------------
## 🚀 How to Run the Simulation

   1. Download and install LTspice.
   2. Open the .asc schematic file.
   3. The simulation is pre-configured with a transient analysis command: .tran 10 (runs for 10 seconds).
   4. Click the Run icon (running man) on the top toolbar.
   5. Use the current probe (hover over the components until a clamp icon appears) to click on:
   * The collector of $Q_2$ to view the Reference Current.
      * The collector of $Q_1$ to view the Mirrored Output Current.


