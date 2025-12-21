#SDLC or Software Development Lifecycle is a layout for the different phases of development when producing software. SDLC is what moves we need to make to develop software and also an approach to how we do this in a workflow.
![[Pasted image 20251012193055.png | 500]]

Lifecycle phases:
Domain analysis (Study what we already have) ->
Specification/Requirements Engineering (User requirement analysis, system analysis etc) ->
Design (Software prototypes, interfaces and component models etc) ->
Implementation (Source code, databases etc) ->
Validation (Component testing, integration testing etc) ->
Deployment (Release, documentation and manuals etc)

We have two types of lifecycles:

#Waterfall is a now extinct approach to development, going from A to B.
![[Pasted image 20251012193508.png | 400]]
![[Pasted image 20251012193558.png | 400]]
#Unified is iterative. We go from inception -> elaboration -> construction -> transition (deployment).
#Agile is another approach to software development.
![[Pasted image 20251012193809.png | 300]] ![[Pasted image 20251012193821.png | 300]]
#Scrum is all about transparency, inspection and adaptation.
#Scrum involves a product owner, a development team and the scrum master. These involved parties come together to "sprint" produce a complete product.

## #Activity_Diagrams

Activity diagrams show high-level actions (actions described abstractly) in a visual workflow to show how a transaction will occur in the system.
![[{B9F31411-71E5-41B7-943D-BD866FBD976C}.png | 500]]
Actions start when they receive "control tokens" which are initiators. Diamond symbols are used to depict decision and merging pathway nodes.
![[{B78AF705-34B8-4736-9904-2F43EC9164E3}.png | 500]]
Parallel activities are depicted with forks (the big line) and joins (the next big line). The actions within the forks and joins must take place for the rest of the activity diagram to proceed.
![[{D7541728-CF12-46A6-A535-D016D4332A8A}.png | 500]]
Hourglass symbols are used to depict ETA events.
![[{24E5A2F8-39CF-4040-86AE-C80C4CEDB9C0}.png | 500]]
If an external factor like a process is involved, a "signal" is used to represent it.
![[{A92656EA-2CAD-427A-A7C4-C0FACF58C222}.png | 500]]
Also, activity diagrams will often use a dotted box and a bolted arrow to indicate that a receive signal can disrupt a process.
![[{0AF10C78-C72C-470A-98C9-2DD0C7721A9E}.png | 500]]
For example here, if an order is cancelled it breaks the original process of shipping the order and cancels the order entirely.

Objects involved with a process are represented by either nodes or "pins" in an activity diagram (little squares latched onto actions).
![[{4EF02E3F-B05C-4954-A03A-7980C7C54568}.png | 500]]
Output pins are for showing what object is pushed by an action, and input pins show that an action requires an object to proceed.

"Swimlanes" or partitions are lines that cut through the whole diagram to depict which components do what. These swimlines allow an activity diagram to go against a linear workflow as not all actions are 1-2-3.
![[{1DDD2C7C-5E7F-4182-A866-D5ED747600D2}.png | 500]]
