# What ATI is trying to do



















## To learn
2.2.2. Motion planning
Motion planning is an essential part of the vision-based guid-
ance systems and manipulation of equipment. Using the input
of the environmental representation, the motion planner can
calculate the robot’s size and dynamics and a feasible, collision-
free path from the initial point to the final position (Karaman &
Frazzoli, 2011). Further, the motion planning algorithms provide
speed and turning commands to the vehicle actuators such as
wheels or manipulator to reach the set of guidance points along
the path. Sensors and the SLAM technology allow the AMR tra-
jectory to be tracked and provide feedback to correct its position.
In dynamic environments, the motion planner allows the AMR
to adapt to traffic or congestion by reducing speed, or even by
stopping the vehicle. If planned paths are no longer feasible due to
an emerging obstacle, a new collision-free path will be generated.
Decisions that must be made about the guide path, routing, and
obstacle avoidance are all taken by the AMR itself. Several open
source platforms provide codes for the control of AMRs (and other
robots). Examples include Robotics and Autonomous Systems by
Intel (https://01.org/robotics-autonomous-systems), the Robot Op-
erating System (https://www.ros.org/), Yet Another Robot Platform
(https://www.yarp.it/) and the Mobile Robot Programming Toolkit
(https://www.mrpt.org/).

2.2.3. Artificial intelligence
Facilitated by hardware developments, AI techniques can be ap-
plied to support AMRs in both navigation and providing services.
Compared to AGVs, for which most situations and tasks are pre-
dictable and therefore solvable by predefined decision rules, AMRs
navigate autonomously in a dynamic and unpredictable environ-
ment. AI techniques such as vision systems and machine learn-
ing (ML) enable the identification and classification of obstacles.
Fuzzy logic, neural networks and neuro-fuzzy and genetic algo-
rithms are examples of well-known fusion techniques that help
move the robot from the starting point to the target, while avoid-
ing collisions with any obstacles along its path (Almasri et al.,
2016; Dias et al., 2018). These techniques are inspired by the ability
of the human brain to perform complex tasks by reasoning about,
and adapting and responding to changes in the environment. Such
behavior-based learning methods can be used to solve complex
control problems that autonomous robots encounter in an unfa-
miliar, real-world environment. Without these techniques, AMRs
would react to all obstacles in the same way. The introduction of
AI affects all decision areas by opening new approaches to making
decisions. The AI branches of vision, ML and planning, have been
found to be very promising. As AI continues to advance, the ability
to interact and collaborate with AMRs will increase. For example,
in warehouses in which a human in the picking role and an AMR
in the fetching role collaborate in order picking (Fig. 3 (i)), the hu-
man picker can use speech or gesture instead of tactile communi-
cation to confirm that picking tasks have been completed or to ask
for help in finding items.

3. Planning and control framework for AMRs
The new developments and possibilities of AMRs, compared to
AGV systems, require a new decision-making framework for plan-
ning and control.
409



![[Pasted image 20220808124256.png]]

The largest Amazon warehouses control thousands of mo-
bile robots. Such systems are often divided into modules that con-
sist of pods positioned in a grid structure, picking and replenish-
ment stations, and vehicles (Lamballais et al., 2020). The system
can easily be scaled up by adding vehicles or modules. In such in-
tralogistics environments, decentralized control of navigation and
task allocation can help to handle the high number and density of
vehicles by reducing elevated levels of traffic and congestion. The
degree of decentralization of operations and the responsibility of
the AMRs must be decided at the strategic level.


The
speedy establishment and easy change of zones enables opera-
tional flexibility that keeps AMR responsiveness high. Within these
zones, service positions for tasks such as picking items or collabo-
rating with humans can simply be added, assigned, or configured
on a short-term basis. The zones can provide travel directions, traf-
fic levels and other relevant information to reduce congestion and
the risk of accidents. Both the service zone and service point lo-
cations have a strong impact on travel times and lead times. The
increased flexibility requires new principles for scheduling and dis-
patching and how to allocate idle AMRs for maximum responsive-
ness




#### Control decentralisation level
The level of control decentralization is a fundamental strategic
decision. Determining which parts of a system should be controlled
in a centralized or decentralized manner plays a crucial role in
defining the interfaces between AMRs and their operating environ-
ment



#### Number and type of sherpas
Combining the analysis of both the distances in the fixed guide
path and the number of trips with AGV characteristics tradition-
ally supported decisions on fleet size. However, due to the nav-
igational flexibility of AMRs, travel distances and times between
service points are highly variable or even uncertain. While AGV
routing only has a limited number of possibilities to connect two
points within the guide path, the autonomous path finding mecha-
nism that AMRs use means the possibilities are effectively endless.
AMRs currently operate in application areas in which humans, such
as hospital visitors, may be unfamiliar with AMR tasks. Congestion
and high traffic are unavoidable, which will hinder AMR perfor-
mance and increase travel time. Thus, new methods are needed to
calculate the right number of vehicles. The flexible platform also
enables different types of AMRs that vary by equipment, size, or
function within a single fleet. The number of vehicles and the type
of equipment must also be determined at the tactical level.


#### 3. Zoning and servicing points
Problem
The transition from providing services along fixed guide paths
to flexible areas requires decisions to be made regarding the
design of zones and service points. In some AMR application
areas, the number and location of service points can be decided
dynamically. Examples include guidance assistance in hospitals
or shopping malls and RMF systems or collaborating fetchers in
warehouses. Dividing the service areas into several zones with
single or multiple vehicles can improve cost and productivity per-
formance. Limiting the operating area for each vehicle improves
the overall responsiveness of the system, since only short trips are
performed, and vehicles are available more quickly. Therefore, zon-
ing comprises the activities and decisions involving (I) analyzing
the area in which the service must be provided, (II) determin-
ing fixed and/or dynamic service points, (III) configuring zones
(adding, removing, dividing or overlaying zones, and defining flow
direction) and (IV) determining the number of vehicles in each
zone. The sequence of these steps can vary

#### 4. Charging station positioning
Current AGVs can only provide few handling activities (e.g. lift-
ing and moving), since they are equipped with only a single han-
dling unit (e.g. lifting unit). However, in robotics and flexible man-
ufacturing, it is common to exchange equipment. AMRs can load,
use, unload, exchange equipment, and charge or exchange batter-
ies. The AMR’s platform allows a wide range of resources to be
used and shared. The decision-making processes of location plan-
ning, scheduling, and dispatching these resources are essential to
their optimal utilization and thus to high AMR productivity perfor-
mance.


#### 5. Scheduling - esp decentralised scheduling
Problem
A substantial body of literature has been developed to sup-
port the decision-making process in scheduling material handling
systems simultaneously with machines, humans, equipment, parts,
and containers. In manufacturing, most studies consider a low
number (fewer than 50) of vehicles under centralized, hierarchical
control applying mixed integer programming models with heuristic
algorithms. Mathematical modeling and optimization approaches
have been widely developed to solve scheduling problems, mostly
in manufacturing since the number and type of tasks are typically
higher than in a warehouse. Some of the papers have also inte-
grated simulation models to validate and generalize their results.
A new stream of research uses AI techniques, such as evolutionary
algorithms, which is now possible due to the advances in computa-
tional power. However, decentralized scheduling methods in which
AMRs negotiate or bid for tasks are still scarce



##### AI based algs -
AI-based methods for multi-objectives or constraint problems
Due to advances in computational power and the applica-
tion of AI techniques, the use of multi-objective or constraint
scheduling models has become more feasible, in particular in com-
plex environments, such as manufacturing with multiple jobs and
machine centers. Some authors have developed genetic and ant
colony optimization algorithms (Udhayakumar & Kumanan, 2010;
Saidi-Mehrabad et al., 2015), or a sheep flock heredity algorithm
(Anandaraman et al., 2012), hybrid evolutionary or genetic algo-
rithms, particle swarm optimization (Gen et al., 2017; Mousavi
et al., 2017; Rahman et al., 2020), and a whale optimization algo-
rithm (Petrovi  ́c et al., 2019). The whale optimization algorithm is
inspired by humpback whale hunting. It first explores the ‘ocean’
looking for ‘prey’ (exploration phase). This corresponds to agents
searching the state space by changing their locations while at-
tempting to find global optima. When a location near a global op-
timum is found, they stop. After the first phase, the whales start
diving in a spiral shape in order to trap the prey. This is called ex-
ploitation phase. In the algorithm, the agents follow a ‘leader’ and
change their locations according to a shrinking encircling mecha-
nism, while updating their location data, until the final location.
These methods perform well for solving multi-objective problems,
combining e.g. minimization of makespan, travel time, and tardi-
ness, with maximization of battery charging efficiency and vehicle
utilization.
Methods for decentralized scheduling and task allocation
Current information sharing and computing technologies pro-
vide a new information processing method for online machine and
vehicle scheduling, enabling new dimensions of agility and flexi-
bility. High levels of connectivity and communication are needed
when decentralizing task allocation. Zeng et al. (2018) propose a
collaborative and distributed scheduling approach for decentral-
izing task allocation, based on dynamic communication between
vehicles and machines, using a hormone-regulation mechanism. A
new promising approach in decentralized scheduling is offered by
auction-based methods where an announcer (machine) and bidder
(AMR) cooperate to achieve high performance in task allocation.
De Ryck et al. (2020a) classify different auction-based methods for
task allocation in single, bundled, and combined items offered and
bid on these in sequential or parallel auctions. The bid calculation
is a crucial element since it reflects the cost for the AMR to per-
form the specific task, and therefore for scheduling and task allo-
cation. Even while executing a given task, AMRs can bid on new
tasks and thus locally optimize the task list and use this informa-
tion to calculate the next bid. Bids can be calculated based on the
cost to perform the tasks by the AMRs, or on the marginal cost
considering also the other tasks in the list. Each type of calcula-
tion has its most suitable bidding algorithm. For the first type of
cost CNET, OCA-Alloc, CBAA and CBBA are used, while marginal
cost is used in Prim Allocation, SIT- and SET-MASR algorithms (see
De Ryck et al. 2020a for an overview). These action-based methods
overcome the limitations of previous OR approaches, and extend
to large vehicle fleets, while introducing flexibility and scalability.
The computation is distributed, so it can be applied to very com-
plex problems with many constraints. The collateral effect is the
increase in demand for computational power for each single AMR,
with negative impact on battery consumption. Further opportuni-
ties for improving these methods will be in the integration of this
decision area with resource management and dispatching.



#### 6. Dispatching
Problem
Smart dispatching methods, that allow AMRs to be close to
the point of demand before an actual need is announced, can in-
crease performance. The increased flexibility of accessing a wide
area and of free positioning due to autonomous navigation, enable
new opportunities for positioning and for cruising while an AMR is
idle. Centralizing the decision-making processes of distributing and
dispatching AMRs requires a system that analyzes the AMR posi-
tions and the demand data. ML and big data analysis of demand
can support the optimization of vehicle distribution over the sys-
tem. However, large-scale AMR systems need high computational
power to analyze and communicate in real time. Decentralizing
this process will decrease the need for high-power cloud comput-
ing. Each AMR will optimize its available time based on historical
data and on data shared with neighboring AMRs. Continuous com-
munication and negotiations will optimize the AMR’s ability to re-
act quickly to demand.





#### 7. Path planning
4.7. Path planning
Problem
Path planning is the task of finding a continuous, deadlock-free
path, with little congestion delay for the AMR from the start to
the goal position so that it can navigate autonomously between lo-
cations, potentially within a large swarm. Compared to AGV rout-
ing, which uses a guide path as input, path finding for AMRs
uses a representation of the environment to mathematically find
the shortest and conflict-free path. An AMR always creates a new,
unique path when moving from one point to another. Constraints
of static and dynamic obstacles, feasible curvature, robot size, lane
dimensions, and speed may be included to find the optimal path
with single or combined objectives. In static environments, the
path planning is often performed only once, but dynamic environ-
ments can require repeating the process of finding a collision-free
path multiple times, for multiple vehicles to bypass or to remove
the obstacles.







## Look at 
- robotic mobile fulfilment RMF systems
- Control decentralisation level



## Interesting papers
file:///home/padmapriya/Desktop/energies-15-01769-v2.pdf



## Proposals
### One

Consider a shopfloor operating using a bunch of autonomous vehicles. Seasonal disruptions from the norm, i.e during covid when the demand for oxygen cylinders goes up, cause a change in demand and therefore the routine functioning of the shopfloor. Certain routes may get busier, and other abnormal occurences like blocking off of a path might occur due to material being placed there temporarily. These things have to be learnt by the sherpa and new routes might have to be found and normalised. 


## Two

Data collection and analysis. And then machine learning for rerouting.


## Resources:
- Coursera course