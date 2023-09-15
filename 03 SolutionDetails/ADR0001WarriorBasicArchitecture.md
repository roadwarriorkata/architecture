# 1. ADR-0001 RoadWarrior Basic Architecture Pattern
<!-- Architecture Decision Record for relevant/important architecture or design decisions with product, cross product or platforms. The general purpose is to make the problem statement, conflicting requirements and analyzed solutions explicit. Use for important decisions and focus on essential information and diagramming. -->

* Status: accepted <!-- mandatory -->
* Deciders: Jan, Philip, Oliver <!-- mandatory -->
* Date: 09-14-2023 <!-- mandatory -->

## 1.1 Context and Problem Statement

The target is to build an online trip management application to allow travelers to manage their trips and see all of their existing reservations.

![Context View of RoadWarrior](ContextView.png)

User Access to the Road Warrior will be via Web Browser, iOS or Anroid app.


## 1.2 Decision Drivers

It needs to be clarified, how the overall architecture pattern looks like. What are the guidelines for composition and communication.

### 1.2.1 Architecture Principles

- Build in the cloud, build cloud native solutions where deployment, monitoring and operations can be automated with APIs.
- Design for simplicity, we strive for simple architectures, which are easier to communicate, build, deploy, operate, and evolve.
- Design for modular landscape, we balance loose coulpling and coherence.
- Design for external integration, we allow to connect to a growing eco system.


### 1.2.2 Quality Requirements
Quality Requirements: [ISO2510](https://iso25000.com/index.php/en/iso-25000-standards/iso-25010)

For detailled information on relevance for Warrior application please consult: [ProblemDefinition.md](/01%20ProblemDefintion/ProblemDefinition.md)

For the overall architecture pattern decision the following quality requirements are considered most relevant:

| Quality Requirement | Relevance | Description for Road Warrior |
| --- | --- | --- |
| Time Behaviour, Responsiveness | high | Response time web: 800ms app: 1400ms|
| Capacity, Scalability | high | 2 mio active users per week |
| Elasticity | high | Parts of the Road Warrior application has to adapt to current needs e.g. start of local vacation times like christmas or thanks giving. Also in case of issues in e.g. air traffic will lead to much more travel updates. |
| Availability | high | max 5 min downtime per month|
| Data Currentness | high | during travel the traveler expects absolute consistency of reservation data against the source system. |
| Testability | high | Testability is critical as the Road Warrior application needs to be adapted and enhanced easily and frequently. This requires safeguarding with automated testing, hence system design needs to support testablity.|
| Adaptability | high | High requirements to allow for application adaptation according to emerging business needs and changes in market expectations.|



## 1.3 Considered Options and Decision Outcome

![architecture_styles](architecture_styles.png)

* Option 1: Modular Monolith
* Option 2: Microservices
* **Option 3: Service-Based**

Of course we have to balance the different decision drivers but in the end we decided for option 3 with the opportunity to further split some services in direction of microservices if it is required after the MVP.

**Chosen option: "Option 3: Service-Based"**, because this architcture style is coarse-grained and based on this is more simple and less costs,  but allows to be flexible to further split the services. Especially for elasticity reasons it could make sense to get to a more fine grained service split. In general it allows fast development and isolated deployment. It requires highly advanced skill set in development team though.

## 1.4 Pros and Cons of the Options <!-- optional -->


### 1.4.1 Modular Monolith

Not distributed, single deployment but possibilities to cluster domains. One data store behind and one unser front end on top.
* Good, because very simple architecure and can be learned very easy
* Good, because of less costs
* Bad, because of bad elasticty and scalability
* Bad, because of big deployments and all the disadvantages as e.g. high time-to-market 


### 1.4.2 Microservices

Highly distributed independent single purpose services with own data (store).

* Good, because very focused small deloyments lead to less dependencies and less impact of changes. This results in fast releases and very low time-to-market.
* Good, because independent deployments in cloud infrastructures.
* Bad, because duplication of data as each service own its data
* Bad, because hard to split all domains in a single purpose independent parts.
* Bad, because very cost intensiv.
* Bad, because of high number of services not simple to understand and organize.

### 1.4.3 Service-Based

Few distributed independent domain deloyments. Not as fine grained as microservices but much smaller deployments as in the monolithic area. There is the possibility to have domain based data store. This approach can be seen as a trade-off between the simpicity of monolithic and the flexibility of microservices. It is open to be enhabced that some of the serrvices can be further spillted to microservices.

* Good, because agility and time-to-market of seperate smaller deployments
* Good, because more simple and less costs than microservices
* Good, because (if domains right sized) possibility to bundle communication to other domains.
* Bad, because no fine grained control about scaleability and elasticity

