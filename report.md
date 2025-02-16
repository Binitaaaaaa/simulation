# A Discrete-Event Simulation Model for Traffic Flow at an Intersection

## Abstract

This project presents a discrete-event simulation of a single intersection controlled by a traffic light. The simulation, implemented in Python using the SimPy library, models vehicle arrivals at random intervals and the operation of a traffic light with fixed green and red durations. Key performance metrics, including vehicle waiting times and queue lengths over time, are captured and visualized using Matplotlib. The study illustrates how simulation can be used to analyze and understand traffic dynamics in a simplified intersection scenario.<br />
## 1. Introduction

Traffic management is a critical area in urban planning and transportation engineering. Simulating traffic flow enables researchers and engineers to evaluate the performance of traffic control strategies before implementation. Discrete-event simulation (DES) is a powerful technique for modeling complex systems where events occur at distinct points in time. This project leverages DES to model a single intersection with a traffic light, focusing on key performance indicators such as waiting times and queue lengths.

The primary objectives of this simulation are:

-   To model vehicle arrivals using an exponential interarrival time distribution.
-   To simulate the operation of a traffic light that alternates between green and red phases.
-   To analyze the impact of traffic light operation on vehicle waiting times and queue lengths.
-   To visualize the simulation results for further insights.

## 2. Methodology

### 2.1 Simulation Approach

The simulation is built using SimPy, a Python library that provides a process-based discrete-event simulation framework. In a DES model, the system is represented as a sequence of events that change the state of the system at specific times. In this project, the events include vehicle arrivals, changes in the traffic light state, and vehicle departures.
### 2.2 Model Components

#### 2.2.1 Traffic Light

The traffic light is modeled as an independent process that cyclically changes its state between green and red. Each state lasts for a fixed duration (10 seconds for both green and red). When the light is green, waiting vehicles are allowed to proceed; when red, vehicles must wait.

#### 2.2.2 Vehicle Generation

Vehicle arrivals are generated based on an exponential distribution, a common assumption in traffic flow theory. The average interarrival time is set to 5 seconds. Each vehicle is represented as a process that:

-   Records its arrival time.
-   Waits until the traffic light is green.
-   Measures its waiting time before passing through the intersection.

#### 2.2.3 Queue Monitoring

A separate process monitors the queue length at the intersection. The queue length is recorded every second, providing a time series that reflects the dynamics of the traffic flow over the simulation period.

### 2.3 Data Collection and Visualization

Two primary metrics are collected:

-   **Car Waiting Times:** The duration each vehicle waits from arrival until the light turns green.
-   **Queue Lengths Over Time:** The number of vehicles waiting at the intersection recorded at regular time intervals.

These metrics are visualized using histograms (for waiting times) and line charts (for queue lengths), providing insights into the performance of the simulated traffic system.

## 3. Implementation

The simulation is implemented in Python with the following key components:

-   **TrafficLight Class:** Defines the traffic light behavior, cycling between green and red.
-   **generate_traffic Function:** Simulates random vehicle arrivals using an exponential distribution.
-   **car Function:** Represents each vehicle's behavior, including waiting for the green light and recording its wait time.
-   **monitor_queue Function:** Periodically records the queue length.
-   **Visualization Functions:** Use Matplotlib to plot the results.
## 4. Results and Discussion

### 4.1 Car Waiting Times

The simulation generates a histogram of vehicle waiting times. The distribution of waiting times offers insight into how the fixed cycle of the traffic light (green for 10 seconds, red for 10 seconds) affects vehicles arriving at different times. For instance, vehicles arriving just after the light turns red may experience longer wait times compared to those arriving during the green phase.

### 4.2 Queue Length Dynamics

A time series plot of the queue length provides a dynamic view of how the queue builds up and dissipates. The results demonstrate peaks in the queue length during the red phases and a rapid decline once the light turns green. This observation is consistent with expectations from traffic flow theory.

### 4.3 Discussion

The simulation successfully illustrates key traffic dynamics at an intersection:

   **Variability in wait times:** Stemming from the random arrival process and fixed traffic light cycle.<br />
  **Queue fluctuations:** Showing accumulation during red phases and dissipation during green phases.<br />

While the model is simplified (e.g., a single lane, fixed signal timing), it serves as a foundational framework. More sophisticated models could incorporate multiple lanes, adaptive signal timing, or interactions with pedestrian flows.

## 5. Conclusion

This project demonstrates the use of discrete-event simulation to model traffic flow at a signalized intersection. Using SimPy, the simulation models vehicle arrivals and traffic light operations, capturing essential performance metrics such as waiting times and queue lengths. The visualizations provide clear insights into the traffic behavior under the assumed conditions.
<br />
Future work could extend this model to more complex traffic scenarios, such as intersections with variable timing, multi-lane roads, and networked intersections, thereby enhancing the model's realism and applicability to urban traffic management.

## 6.References

-   Banks, J., Carson, J. S., Nelson, B. L., & Nicol, D. M. (2010). _Discrete-Event System Simulation_. Pearson.
-   Law, A. M., & Kelton, W. D. (2000). _Simulation Modeling and Analysis_. McGraw-Hill.
-   SimPy Documentation: [https://simpy.readthedocs.io](https://simpy.readthedocs.io)
