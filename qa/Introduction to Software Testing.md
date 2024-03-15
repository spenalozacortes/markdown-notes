# Introduction to Testing

## Verification and Validation

**Verification**
- "Are we building the software **right**?"
- The software should conform to its specification

**Validation**
- "Are we building the **right** product?"
- The software should do what the user really requires

**Techniques for getting software "right"**
- Need to **understand** and **validate** software requirements
- Need to apply multiple V&V techniques throughout the development cycle
	- Inspections
	- Design discussions
	- Static analysis
	- Testing
	- Runtime verification

**Why focus on software testing?**
- The only software defect detection technique that can check the **whole system**
	- Compiler, processor, devices, network, linker, loader, etc.
- Currently, the best way to accurately asses some system behaviors (e.g., performance)
- For contract software, necessary for customer to "accept" the system
- A reasonably good way of documenting expected system behavior
- **But testing is always incomplete**

![[Pasted image 20240312105527.png]]

# Why and How We Test

## Why is software testing challenging?

**The problem with software testing**
... is that it only **samples** a set of possible behaviors.

- Unlike physical systems (where many engineers gained their experience), most software systems are **discontinuous**
- **There is no sound basis for extrapolating from tested to untested cases**
- So we need to consider all possible states of the system
- Even small systems have trillions and trillions of possible states

**What is required to find this bug?**

- Knowledge of where programmer mistakes are likely
	- **Boundary conditions**
	- **Complex boolean expressions**
- Thinking like a "helpful adversary" - how can I break this thing?
- To test well, we must:
	- Examine the requirements (**black box testing**)
	- Examine the code (**white box testing**)
	- 