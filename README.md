# Traffic Flow Modeling Using Markov Jump Process

### Authors
- **Soumodeep Hoodaty**
- **Akshita Kumar**

### Project Overview
This project applies the **Markov Jump Process** to model traffic flow across road sections. Vehicles are represented as particles, and road sections are modeled as discrete sites, with the aim to simulate traffic dynamics, incorporating vehicle density and flow rate across different sections. The model builds on a **totally asymmetric misanthrope Markov jump process** and utilizes principles from mesoscopic approaches to capture a balance between individual vehicle behaviors and overall traffic flow.

### Key Components

#### 1. Jump Process Fundamentals
The project begins by introducing **jump processes** as stochastic processes representing random changes in state, defined formally through probability and algebraic functions. In particular, a **Markov Jump Process** is used, characterized by the memoryless property where future states depend only on the present state, not past states.

#### 2. Traffic Flow Model Description
The model uses road sections as discrete sites, with vehicles moving between sections based on defined jump rates, which depend on vehicle density. The **maximum number of vehicles per section** is capped to account for road capacity, and traffic flow between sections is defined by mesoscopic characteristics, reflecting a mix of microscopic and macroscopic modeling.

#### 3. Assumptions
1. **Section Capacity**: Each road section can accommodate a maximum number of vehicles, denoted by $N$, and the length of each vehicle is assumed to be 1 unit.
2. **Sequential Movement**: Vehicles can only move to the adjacent section, with one vehicle moving at a time.
3. **Jump Timing**: Jump times between sections follow an exponential distribution, influenced by the number of vehicles in both the departure and destination sections.
4. **Capacity Handling**: If a section reaches its maximum capacity, vehicles must wait until there is space available.

### Parameters
1. **Jump Rate Function** $(b_{x})$: Determines the likelihood of a vehicle moving from one section to the next.
2. **Section Size** $(D_{x})$: The physical size or capacity of each section.
3. **Maximum Vehicles** $(N_{x})$: Maximum vehicle count per section, with the assumption that $(D_{x} = N_{x})$.

The **jump rate function** is computed based on **demand** (from the current section) and **supply** (from the adjacent section) as follows:

$$b_{x}(\eta(x), \eta(x+1)) = \min\{\Delta_{x}(\eta(x)/D_{x}), \Sigma_{x+1}(\eta(x+1)/D_{x+1})\}$$

### Model Equations
The model defines flow volumes $(Q_{x}(\rho))$ based on the **macroscopic Edie-Underwood model**, where:
$$Q_{x}(\rho) = V \rho e^{-\lambda \rho}$$
with **critical density** $(rho^{cr)}$ set by $lambda$, which represents sensitivity or relaxation time. The jump rate calculation balances demand and supply based on vehicle density in each section.

### Novel Contributions
This project introduces a **novel theoretical proof** that shows that in the special case of a single section with open boundaries, the markov process is irreducible since for all states x and y, 
$\mathbb{P}(\eta_{t}=y|\eta_{0}=x) = P_{t}(x,y) > 0$ for some $t>0$.

### References
- **Edie, L. C.** - *Traffic Flow Theories* – Provides foundational concepts in traffic flow that support the jump rate function used in this model.
- **Underwood, R. T.** - *Speed, Volume, and Density Relationships* – Used for the macroscopic modeling approach that informs flow volume calculations.
- **Grimmett, G. R. and Stirzaker, D. R.** - *Probability and Random Processes* – References for theoretical grounding in stochastic processes and Markov properties used in this project.
- **Ethier, S. N., and Kurtz, T. G.** - *Markov Processes: Characterization and Convergence* – Further reading on Markov jump processes and their application in modeling random systems.
