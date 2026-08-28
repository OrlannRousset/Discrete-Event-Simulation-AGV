Discrete-Event Simulation of an AGV Logistics System

Overview

Group project completed as part of the SY15 course at the University of Technology of Troyes (UTT).

The objective of the project was to model and simulate the operation of an industrial logistics system composed of two autonomous guided vehicles (AGVs), one loading area and several unloading areas.

Based on observations of the real system, the work consisted in identifying flows, events and characteristic times, then developing a discrete-event simulator in C to analyze system performance and study the impact of operating changes.

Studied system

The simulated system includes:

2 AGVs transporting batches

1 loading area

4 unloading areas

a queue for batches waiting to be handled

travel, loading and unloading times represented using probability distributions

Simulation principle

The program is based on a discrete-event simulation approach.

The main modeled events are:

arrival of a new batch

end of batch loading

arrival of an AGV at an unloading area

end of unloading

AGV return

An event schedule stores the next events to be processed. The simulation moves directly from one event to the next until the defined simulation horizon is reached.

Probabilistic modeling

Several probability distributions are used to represent the stochastic behavior of the system:

exponential distribution for interarrival times between batches

discrete distribution for assigning batches to the different unloading areas

normal distribution for some loading, travel and unloading times

Normally distributed values are generated using the Box-Muller method from pseudo-random uniform values.

Performance indicators

The simulator measures several indicators to analyze system behavior:

number of processed batches

number of waiting situations caused by the loading area being unavailable

number of waiting situations when an AGV reaches an occupied unloading area

maximum queue length

These indicators can be used to compare different system configurations or operating rules.