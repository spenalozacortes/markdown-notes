# Foundations

## Voltage, current, and resistance

### Voltage and current

There are two quantities that we like to keep track of in electronic circuits: voltage and current. These are usually changing with time; otherwise nothing interesting is happening.

**Voltage** (symbol V or sometimes E). Officially, the voltage between two points is the cost in energy (work done) required to move a unit of positive charge from the more negative point (lower potential) to the more positive point (higher potential). Equivalently, it is the energy released when a unit charge moves “downhill” from the higher potential to the lower. Voltage is also called *potential difference* or *electromotive force* (EMF). The unit of measure is the *volt*. A joule (J) of work is done in moving a coulomb (C) of charge through a potential difference of 1 V.

**Current** (symbol I). Current is the rate of flow of electric charge past a point. The unit of measure is the ampere, or amp. A current of 1 amp equals a flow of 1 coulomb of charge per second. By convention, current in a circuit is considered to flow from a more positive point to a more negative point, even though the actual electron flow is in the opposite direction.

Important: from these definitions you can see that currents flow *through* things, and voltages are applied (or appear) *across* things. So you’ve got to say it right: always refer to the voltage between two points or across two points in a circuit. Always refer to current through a device or connection in a circuit. However, we do frequently speak of the voltage *at a point* in a circuit. This is always understood to mean the voltage between that point and “ground,” a common point in the circuit.

We *generate* voltages by doing work on charges in devices such as batteries (conversion of electrochemical energy), generators (conversion of mechanical energy by magnetic forces), solar cells (photovoltaic conversion of the energy of photons), etc. We *get* currents by placing voltages across things.

In real circuits we connect things together with wires (metallic conductors), each of which has the same voltage on it everywhere (with respect to ground, say).

1. The sum of the currents into a point in a circuit equals the sum of the currents out (conservation of charge). This is sometimes called Kirchhoff’s current law (KCL). Engineers like to refer to such a point as a *node*. It follows that, for a series circuit (a bunch of two-terminal things all connected end-to-end), the current is the same everywhere.
2. Things hooked in parallel have the same voltage across them. Restated, the sum of the “voltage drops” from A to B via one path through a circuit equals the sum by any other route, and is simply the voltage between A and B. Another way to say it is that the sum of the voltage drops around any closed circuit is zero. This is Kirchhoff’s voltage law (KVL).
3. The power (energy per unit time) consumed by a circuit device is
$$P = VI$$
For V in volts and I in amps, P comes out in watts. A watt is a joule per second (1W = 1 J/s).

Power goes into heat (usually), or sometimes mechanical work (motors), radiated energy (lamps, transmitters), or stored energy (batteries, capacitors, inductors).

### Relationship between voltage and current: resistors

Crudely speaking, the name of the game is to make and use gadgets that have interesting and useful I-versus-V characteristics. Resistors (I simply proportional to V ),
capacitors (I proportional to rate of change of V ), diodes (I flows in only one direction), thermistors (temperature-dependent resistor), photoresistors (light-dependent resistor), strain gauges (strain-dependent resistor), etc., are examples. Perhaps more interesting still are three-terminal devices, such as transistors, in which the current that can flow between a pair of terminals is controlled by the voltage applied to a third terminal.

#### A. Resistance and resistors

It is an interesting fact that the current through a metallic conductor (or other partially conducting material) is proportional to the voltage across it. This is by no means a universal law for all objects.

A resistor is made out of some conducting stuff (carbon, or a thin metal or carbon film, or wire of poor conductivity), with a wire or contacts at each end. It is characterized by
its resistance:
$$R = V/I$$
