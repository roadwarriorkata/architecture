# Solution Strategy
This Document provides a high level overview of the to be architecture for the Road Warrior application. It is intended to serve as foundation to ensure joint understanding how the defined problem of the traveler domain will translate into a solution, which takes architecture constraints and architecture principles into account.

## Solution Strategy

We are proposing to build the solution with a Service-based architecture with four services. The services follow the user journey analysis described in the [problem definition](/01%20ProblemDefintion/ProblemDefinition.md#user-journeys). We propose to separate these user journeys as they emphasize different architecture characteristics. While a fast response and up-to-date reservation data is particularly important during the travel in case of changing plans or travel schedules, we could lift these requirements a bit during the planning phase of a journey.

We propose to couple the domains loosely by triggering messages between the domains that follow the user journeys. The travel planning domain, for instance, hands over trip and reservation data once a trip starts or gets activated by a user and the _Enjoy your trip!_ domain sends data to the _Time machine_ through the trip archiver service. Using message queues between the domain we can buffer data in case of domain service failure and allow recovery without loosing data.

On the data part we propose to build single data backends per service. If the development team has the skillset to orchestrate services automatically, the _Enjoy your trip!_ domain will benefit from building into a microservice architecture just for that domain as it has the highest requirements in terms of availability and scalability in case of unforeseen traveling events like flight cancellations due to heavy storms. The same holds true for the _Help me!_ domain which requires elasticity in case of larger user request floods due to afore mentioned events.

## Architecture Principles

- Build in the cloud, build cloud native solutions where deployment, monitoring and operations can be automated with APIs.
- Design for simplicity, we strive for simple architectures, which are easier to communicate, build, deploy, operate, and evolve.
- Design for modular landscape, we balance loose coulpling and coherence.
- Design for external integration, we allow to connect to a growing eco system.
- Design for the entire lifecycle, we design for maintainability of technologues, applications and data.
- Design for Security and Compliance, we ensure legal constraints and ensure external regulations by design.

## Informal Overview Diagram

The following diagram provides insights into the overall contexts and respective services and components for the Warrior application. It provides a scetch of the communication and interaction patterns required for cross context communication and external communication with agencies.

![High Level De-Composition](HighLevelComponentView.png)

## Trade Offs 

### Simplicity of approach vs. full elasticity

Considering limited capacity and capability in designing and deploying fully distributed microservice architectures to serve elasticity, it is decided to start with a service based approach, which segregates business domains along expected differences in quality requirements. This allows a fast time to market with the existing group and allows for easy optimization later on the roadmap.

### Short time to market vs. global reach and latency requirements

We assume the market go live is in north america. Here the latency requirements can be met with proposed architecture. Later for internal rollouts to Europe or Asia it is planned to have a content delivery framework integrated as a partner solution to allow full scalling and still provide expected latency requirements even in remote regions.
