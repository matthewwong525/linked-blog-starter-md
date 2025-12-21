### LECTURE 1

"Software Engineering" is the fancy way to say how we as programmers approach writing code with standards, structure and technique.
It prioritises efficiency and security in code.

An important topic is #Systems. Systems contain the following elements:
- Central objective (All components work towards an overarching goal)
- Integration (All components complete a system)
- Interaction (System works because of the interworking components)
- Interdependence (Changing one component will affect others)
- Organisation (Hierarchy, components need to be in the right place at the right time)

#Components refer to the following elements of a System:
- Input, processes and output
- Internal and external environment
- System boundary
- Interface
- Feedback and control
#Boundaries are the lines between what is a system and what is its environment, but within a system there are #Interfaces which are the boundaries between a system's components (Which can also be subsystems).

There can also be complex systems that contain #subsystems, arranged in hierarchies and integrated to achieve the overarching goal of the supersystem. Each subsystem has boundaries, interfaces and environments.

#Emergent-Properties are the behaviours that occur when components of a system are properly integrated - they can be functional or non-functional (behaviour of the system in its environment).

What are the necessary details of a #System-Model?
- Components of the system
- Relations between those components
- How the components work together to reach an overarching goal
- How the system interacts with its environment
System models are useful because- they abstract the important practical features, create a concrete display of an idea, help share that idea and allow for early critique.
![[Pasted image 20251012180355.png | 500]]

Software models focus on code organisation, runtime entities/objects and their responsibilities, overall data flow and how those entities message eachother.
UML diagrams are useful for producing models.

#Component-Diagrams help plan out the detailed bits of a system to establish architecture and manage how the components interact.
![[Pasted image 20251012180952.png | 300]] ![[Pasted image 20251012181012.png | 500]]
![[Pasted image 20251012181155.png | 500]]
![[Pasted image 20251012181221.png | 500]]