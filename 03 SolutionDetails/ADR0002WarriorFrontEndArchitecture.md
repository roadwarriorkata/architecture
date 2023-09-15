# 1. ADR-0002 RoadWarrior FrontEnd Architecture 
<!-- Architecture Decision Record for relevant/important architecture or design decisions with product, cross product or platforms. The general purpose is to make the problem statement, conflicting requirements and analyzed solutions explicit. Use for important decisions and focus on essential information and diagramming. -->

* Status: accepted <!-- mandatory -->
* Deciders: Jan, Philip, Oliver <!-- mandatory -->
* Date: 09-14-2023 <!-- mandatory -->

## 1.1 Context and Problem Statement

The target is to build an online trip management application to allow travelers to manage their trips and see all of their existing reservations.

![Context View of RoadWarrior](/01%20ProblemDefintion/SystemContextView.png)

User Access to the RoadWarrior will be via Web Browser, iOS or Anroid app.
The challenges are driven by a divers user base with little to no training and high expecations on usability. The road warrior application wants to have a very low entry barrier for usage to be outstanding against competitors.

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
| Learnability | high | Travelers will not use this on a daily base, hence the application needs to be very easy to understand |
| Accessability | high | All travlers across the world are targeted with this application, time zones, languages and currencies need to be taken into account. MVP: North America and Europe with English, French, German, Italien, Spanish language. All timezones, Two currencies US dollar and Euro |
| Testability | high | Testability is critical as the Travel Warrior application needs to be adapted and enhanced easily and frequently. This requires safeguarding with automated testing, hence system design needs to support testablity.|
| Adaptability | high | High requirements to allow for application adaptation according to emerging business needs and changes in market expectations.|
| Installability | high | High demands for easy installation to allow all potential travelers in the world to use the Warrios app|

## 1.3 Considered Options and Decision Outcome

[Provide summary of considered options as one liners and provide reasoning for  selected option, based on above Problem Statement, Architecture principles and considered Quality Requirements.]

* Option 1: One Single Page Application with JavaScript (Vue)
* Option 2: Python Flask application

Chosen option: "Option 2 Distirbuted Components", because this architcture style allows to meet different needs regarding elasticity as well as fast development and isolated deployment. It requires highly advanced skill set in development team though.

## 1.4 Pros and Cons of the Options <!-- optional -->

Highlight business benefits, technical impact and possible new technical debts

### 1.4.1 Front End provisioning with Vue based SPA

Front end is provided in a SPA with Vue. Vue will render and update in the Browser and use API calls to the back end only to fetch data updates.

* Good, because a SPA like view allows that all interaction is calculated in the browser with Java Script, hence no call back to the server for new HTML fies is required.
* Bad, because of dependency of the development on Vue competence. Frameworks are not stable over time and require continuous effort for adaption and changes. 
<!-- numbers of pros and cons can vary -->

### 1.4.2 Front End provisioning with Flask

This archtecture would provide web pages with the Flask framework and depending packages to provide rendering and object mapping to DB.

* Good, because it provides a fast way to provide complete web pages.
* Python compentency exists in the company
* Bad, because of dependency of the development on Flask competence. Frameworks are not stable over time and require continuous effort for adaption and changes. 
* Bad, because Flask will have all business logic in one python package with relatively high internal dependency and no options for selective elasticity of different components/packages.

<!-- numbers of pros and cons can vary -->
