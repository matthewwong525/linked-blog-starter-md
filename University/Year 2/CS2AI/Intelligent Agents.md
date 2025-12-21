An intelligent agent is a reactive component of AI, it perceives and reacts to its environment.
An agent is anything that can perceive or ==sense== its environment and act upon the environment or ==actuate==.
==Percept== = agent's perceptual input at a given time.
==Percept== sequence" history of everything the agent has perceived.
An agent's ==action== at any time depends on the percept sequence observed.
==Agent program== run in cycles of :
- Perceive
- Think
- Act rationally
Agents often ==assume== - they perceive their own actions but not the effects.
![[{70B7DBCD-83B5-4E46-A66D-A3B98D4DA36C}.png]]
==Sensor== is a device that detects change in an environment and directs the information to other components/devices.
==Actuator== is a component that converts energy into motion, such as an electric motor or a gear.

"Human agent"
- eyes, ears and other organs for sensors
- hands, legs, mouth etc for actuators
"Robotic agent"
- cameras and infrared range finders for sensors;
- various motors for actuators
"Software agent"
- Keystrokes, file contents, received network packages as sensors
- Screen display, files and sent network packets as actuators

Think of a roomba for an example of an agent!!
![[{1B2A12F8-A787-40AD-AA52-4F4E6DAC6A89}.png]]

## Agent Functions and programs
Agent behaviour is described by the agent function, which maps percept histories to actions,
- f:P* -> A
We need to implement a rational agent function concisely AKA design an agent program.
==Agent = Agent program + Architecture==
"Architecture" is a computing device that provides the sensors and actuators.
"Agent program" takes the percept as input from the sensors and returns an action to the actuators.
Agent programs take current percept as input whereas agent function takes the whole percept history.
Agents need to remember the entire percept sequence.

***Agent Program is like the brain. Agent function is the person***
![[{DDD39890-3EC1-4A7B-8E6E-DCF198740B93}.png]]
"Rational Agent" chooses actions that maximise performance given the current percept sequence.
==Agent percepts -> Action Sequences -> Environmental changes==
- If the sequence of states that change the environment are desirable, then the agent performed successfully.
This can be measured using a performance measure, an objective criterion for its success.
E.g., we can measure a roomba's success with how much dirt it cleaned, how clean the environment is and how much dirt was cleaned per unit of electricity used.
==Performance measures should be based on what is desired in the environment and how the agent should act.==

## PEAS Analysis
- ==Performance measure== is the unit to define the success of an agent.
- ==Environment== is the surrounding of the agent at any time, it can change if the agent is in motion.
- ==Actuator== is the component of the agent that delivers the output of the action.
- ==Sensor== are the receptive parts of the agent which take input.

Examples - Internet shopping agent:
- Performance measure = price, quality, appropriateness, efficiency
- Environment = current and future WWW sites, vendors, shippers
- Actuators = display to user, follow URL, fill-in form
- Sensors = HTML pages
Examples - Automated taxi shopping agent:
- Performance measure = safety, destination, profits, legality, comfort
- Environment = streets/freeways, traffic pedestrians, weater
- Actuators = steering, accelerator, brake, horn, speaker/display
- Sensors = video, accelerometers, gauges, engine sensors, keyboard, gps

## Environment types
An environment is what surrounds the agent, but it can have various attributes:
 - Fully observable = agent has access to all relevant information about the environment to make any decisions.
 - Partially observable = agent must make informed guesses based on what information it does have.
![[{B4D0027D-3478-4431-ADB6-30F0F7AE41EE}.png]]
- Deterministic = the next state of the environment is determined by the previous or current state alongside the agent's action, e.g., a Rubix's cube.
- Stochastic = the outcome of an action is uncertain and based on probability.
![[{EF9D87A0-CD1D-4F0D-82E6-E15B9BDEDBD7}.png]]
- Episodic = agent's actions are independent episodes, and each action is not dependent on the previous.
- Sequential = Actions are dependent on previous or current actions.
![[{0D1131DA-2B74-417E-83DE-6BEE3C922035}.png]]
- Static = environment that doesn't change while the agent is deciding what action to take.
- Dynamic = environment that changes, so the agent has to consult the environment while choosing actions and anticipate incoming changes.
- Semidynamic = environment does not change but the agent's performance does.
![[{1E6CCD09-D2F5-4DF7-A540-9026E780B18D}.png]]
- Discrete = environment has a finite number of distinct states, actions and percepts, like a turn-based board game.
- Continuous = actions performed can't be numbered as the environment keeps changing.
![[{00425073-65F4-43E9-A6AE-504D0D2F96B1}.png]]
- Single agent = agent operating solo in an environment, like a maze-solving robot working on a puzzle alone.
- Multiagent = multiple agents working together.
![[{B2782398-A440-4034-BCB3-89B03D09F6B3}.png]]

Agent Types:
- Reflex: agent whose action depends only on the current precept.
  Holds no memory, functions on a set of rules AKA reflexes.
  -Limited intelligence, too big to generate and store, not adaptive.
- Model-based: agent whose action depends on its internal model of the current world state that is updated over time.
  Uses both memory and perception to maintain an internal world model. Model is updated as it receives new information. Partial observability.
  -Needs to store information on how the world evolves independently from the agent, and how the agent's actions affect the world.
- Goal-based: agent that selects actions that it believes will achieve explicitly represented goals.
  Holds an internal model + goal/s. This agent searches for action sequences that reach the goal and plans before acting on them. Behaviour can be easily changed.
- Utility-based: agent that selects actions that it believes will maximize the expected utility of the outcome state. The agent aims for the best way to reach the goal. Agent "happiness" must be considered, AKA utility.
- Learning: agent whose behaviour improves over time based on its experience.
- Autonomous/Agent AI: agent that integrates learning, memory, reasoning, tool use and operates with significant independence and persistence over long-term tasks.
![[{66978480-2C20-43E5-8F0D-BFE05CA2A069}.png]]

![[{1997B78B-9A60-492A-8295-795A1C08260C}.png]]
