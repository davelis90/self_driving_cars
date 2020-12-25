# Lesson 1: Safety Assurance for Self-Driving Vehicles

## Recent accidents
- hard to predict all actions that can happen on the road
- overreaction to small collision, controller couldn't handle it
- knocked over a motorcyclist instead of crashing into 2 vehicles (what is the right action?)
- no real time checks on safety drivers/ attentiveness, he was watching his phone
- woman walking with bicycle > classified as vehicle and then bicycle. Detections were ignored because the classification changed too much

## Safety concepts
- Harm
- Risk = Probabability + Severity
- Safety = absence of Hazard
- Hazard


## Hazard sources
- mechanical
- electrical
- hardware
- software (bugs)
- sensors
- behavioral (Planning/decision making) e.g. behaviour for a scenario was not designed correctly
- fallback to driver
- cyber e.g. hacks

## Safety requirements/ Safety assessment framework (NHTSA)
- released in 2017
- 12 areas of safety

- systems design approach to safety
- left 11 areas to 2 categories: autonomy design and testing and crash mitigation
- autonomy design: well-defined ODD (Operational Design Domain-scenarios), OEDR (object and event detection and response system), Fallback mechanism, traffic laws follow, cybersecurity, HMI
- testing and crash mitigation: extensive testing (simulation, closed track testing, public road driving), crashworthiness (mitigate injury during crashes), post crash behaviour,
data recording, consumer Education (for the fallback/consumer driver)


# Lesson 2: Industry Methods for Safety Assurance and Testing

## Industry perspectives
- Waymo report
- GM report
- Waymo safety level: behavioral level (traffic rules, wide range of scenarios in ODD), functional safety (redundancies), crash safety (ensure min damage), operational safety (intuitive interfaces)
non collision safety (danger with interacting with the car)
- Waymo safety processes: how to reach a safe state through different scenarios
- preliminary analysis
- fault tree
- design failure modes & effect analyses
- extensive testing to ensure safety 
- continuous simulation (10k miles per day)
- testing with real-life data and data fuzzing (changing positions/speed)
- closed-course testing
- real world driving

- GM follows all 12 elements of NHTSA
- FMEA
- HAZOP
- Fail safes/ backups
- SOTIF (evaluation for unpredictable scenarios)
- Fault injection testing


## Approaches to demonstrate safety

- Analytical: works in theory and meets requirements
- Data-driven: validation through experience (on road scenarios and larges number of kms) - comparison with human driving
- are autonomous cars safer?
- Disengagement rates: how often must the fallback driver intervene (either requested by the vehicle itself or decided by the driver)
- 400 years needed with a fleet of 100 vehicles travelling all time (8 billion miles) to assess if the autonomous cars are safer than human driving

## Waymo report
- Waymo cars use pre-built maps with real-time sensor data
- see VRUs, obstructions, road work, traffic lights
- can see up to 300 m away
- prediction of movement based on speed and trajectory
- 360 degrees vision
- Appendix A. Basic Behavioral Competency Testing
- Appendix B. Avoidance or Mitigation of Common Crash Scenarios
- Glossary (terms explanation)


# Lesson 3: Safety Frameworks for Self-Driving

## Generic Safety frameworks: Fault trees (FTA), FMEA, HAZOP
- Fault tree analysis: preliminary analysis, top down analysis, boolean logic
-  assign probabilities to fault "leaves"
- OR (P(A) + P(B)), AND (P(A)*P(B))

-FMEA: bottom up process, can be combined with FTAs
- Failure Mode
- Effect analysis
- how serious? 
- how frequently?
- how easily detected?
- score 1 to 10
- RPN: risk priority number 

- HAZOP: hazard and operability study
- qualitative brainstorming

## Autonomous Safety frameworks: Functional Safety, Safety of Intended Functionality

- Functional Safety (FuSa)
- ISO 26262
- HARA (hazard and risk assessment)
- worst case requirements & implement software/hardware with minimal risk
- V-shaped process

-Safety of Intended Functionality (SOTIF)
- - ISO/PAR 21448.1
- performance limitations of sensors, actuators and algorithms
- misuse by user (overload, confusion)
- designed for level 0-2 autonomy
- extension of FuSa
- V process
- HARA
