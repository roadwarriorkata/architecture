# 1. ADR-0001 RoadWarrior Basic Architecture Pattern
<!-- Architecture Decision Record for relevant/important architecture or design decisions with product, cross product or platforms. The general purpose is to make the problem statement, conflicting requirements and analyzed solutions explicit. Use for important decisions and focus on essential information and diagramming. -->

* Status: accepted <!-- mandatory -->
* Deciders: Jan, Philip, Oliver <!-- mandatory -->
* Date: 09-14-2023 <!-- mandatory -->

## 1.1 Context and Problem Statement

The target is to build an online trip management application to allow travelers to manage their trips and see all of their existing reservations.

![Context View of RoadWarrior](ContextView.png)

User Access to the RoadWarrior will be via Web Browser, iOS or Anroid app.

[Describe the context and problem statement, e.g., in free form using two to three sentences. You may want to articulate the problem in form of a question. Provide background on user journey or challenge that needs to be implemented?]

[Provide relevant diagram for decision, focus on essential information for described problem. examples: Delimit your system, define boundaries and describe external interfaces with context diagram. Provide static decomposition of the product or platform in scope with building block view. Provide runtime view if required with sequence diagram]

## 1.2 Decision Drivers

It needs to be clarified, how the overall architecture pattern looks like. What are the guidelines for composition and communication.

### 1.2.2 Quality Requirements
Quality Requirements: [ISO2510](https://iso25000.com/index.php/en/iso-25000-standards/iso-25010)

For detailled information on relevance for Warrior application please consult: [ProblemDefinition.md](/01%20ProblemDefintion/ProblemDefinition.md)

For the overall architecture pattern decision the following quality requirements are considered most relevant:

| Quality Requirement | Relevance | Description for Road Warrior |
| --- | --- | --- |
| Time Behaviour, Responsiveness | high | response time web: 800ms app: 1400ms|
| Capacity, Scalability | high | 2mio active users per week |
| Elasticity | high | parts of the Arrior application need to adapt to current needs e.g. start of local vacation times, liek christmas or thanks giving. |
| Availability | high | max 5min downtime per month|
| Data Consistency | medium | now extra needs or complex data model |
| Data Currentness | high | during travel the traveler expects absolute consitency of reservation data |
| Recoverability | high | The user needs to be able to revcover his data, if the mobile app crashes or the web browser stops. |
| Testability | high | Testability is critical as the Travel Warrior application needs to be adapted and enhanced easily and frequently. This requires safeguarding with automated testing, hence system design needs to support testablity.|
| Adaptability | high | High requirements to allow for application adaptation according to emerging business needs and changes in market expectations.|


## 1.3 Considered Options and Decision Outcome

[Provide summary of considered options as one liners and provide reasoning for  selected option, based on above Problem Statement, Architecture principles and considered Quality Requirements.]

* Option 1: One Single Page Application with JavaScript (Vue)
* Option 2: Distributed components with individual GUI and data storage

Chosen option: "Option 2 Distirbuted Components", because this architcture style allows to meet different needs regarding elasticity as well as fast development and isolated deployment. It requires highly advanced skill set in development team though.

## 1.4 Pros and Cons of the Options <!-- optional -->

[Highlight business benefits, technical impact and possible new technical debts]

### 1.4.1 [option 1]

[Short description of scetchd solution]

* Good, because [argument a]
* Good, because [argument b]
* Bad, because [argument c]
* … <!-- numbers of pros and cons can vary -->

### 1.4.2 [option 2]

[Short description of scetchd solution]

* Good, because [argument a]
* Good, because [argument b]
* Bad, because [argument c]
* … <!-- numbers of pros and cons can vary -->
