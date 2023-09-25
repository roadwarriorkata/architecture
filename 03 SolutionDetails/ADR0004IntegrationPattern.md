# 1. ADR-0004 Road Warrior Integration Pattern 
<!-- Architecture Decision Record for relevant/important architecture or design decisions with product, cross product or platforms. The general purpose is to make the problem statement, conflicting requirements and analyzed solutions explicit. Use for important decisions and focus on essential information and diagramming. -->

* Status: accepted <!-- mandatory -->
* Deciders: Jan, Philip, Oliver <!-- mandatory -->
* Date: 09-14-2023 <!-- mandatory -->

## 1.1 Context and Problem Statement

The target is to build an online trip management application to allow travelers to manage their trips and see all of their existing reservations.

![Context View of RoadWarrior](/01%20ProblemDefintion/SystemContextView.png)

The decision which is described in this ADR: **How will communicate the warrior app with external systems and how will communicate the services with each other.** This does not describe the intra-service communication, which will be decided seperatly for the services. But the inter-service communication is desbribed here. 

## 1.2 Decision Drivers

It needs to be clarified, how the overall architecture pattern looks like. What are the guidelines for communication.

### 1.2.1 Architecture principles
From all architecture principles the following ones are most relevent for this decision:
* Design for simplicity, we strive for simple architectures, which are easier to communicate, build, deploy, operate, and evolve.
* Design for modular landscape, we balance loose coulpling and coherence.
* Design for external integration, we allow to connect to a growing ecosystem.


### 1.2.2 Quality Requirements
Quality Requirements: [ISO25010](https://iso25000.com/index.php/en/iso-25000-standards/iso-25010)

For detailled information on relevance for Warrior application please consult: [ProblemDefinition.md](/01%20ProblemDefintion/ProblemDefinition.md)

From the overall architecture pattern decision the following quality requirements are considered most relevant for this ADR, keeping in mind that part of this decision is to manage different quality requirements to the different services:


| Quality Requirement | Relevance | Description for Road Warrior |
| --- | --- | --- |
| Elasticity | high | Parts of the Road Warrior application have to adapt to current needs e.g. start of local vacation times like Christmas or Thanksgiving. Also in case of issues in e.g. air traffic will lead to many more travel updates. |
| Availability | very high | max 5 min downtime per month|
| Data Consistency | medium | no extra needs or complex data model |
| Data Currentness | very high | during travel the traveler expects absolute consistency of reservation data against the source systems. |
| Adaptability | high | High requirements to allow for application adaptation according to emerging business needs and changes in market expectations.|


## 1.3 Considered Options and Decision Outcome

* Option 1: Synchronous API communication
* Option 2: Asynchronous message based communication
* **Option 3: Asynchronous communication for inter-service, but synchronous for external services and the user front end**

**Chosen option: "Asynchronous communication for inter-service, but synchronous for external services and the user front end"**, because this best combines the advantages of both approaches. Services are decoupled via message queues with domain events to avoid blocking and enable independent scaling of (paralell) different services. On the other side use synchronous APIs calls to guarantee instant respsonsivness for the user frontend. The communcation with the external systems are due to simplicity used in the way the external system provide the interfaces, these are currently synchronous APIs.
