# Solution Strategy
This Document provides a high level overview of the to be architecture for the Road Warrior application. It is intended to serve as foundation to ensure joint understanding how the defined problem of the traveler domain will translate into a solution, which takes architecture constraints and architecture principles into account.

## Solution Strategy

(containing architecture goals and their supportive architecture approaches)
- leading ideas/concepts
  - service architecture
  - decoupeling via message - address architecture characteristics per service
  - one databayse per service

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

### simplicity of approach vs. full elasticity

Considering limited capacity and capability in designing and deploying fully distributed microservice architectures to serve elasticity, it is decided to start with a service based approach, which segregates business domains along expected differences in quality requirements. This allows a fast time to market with the existing group and allows for easy optimization later on the roadmap.

### short time to market vs. global reach and latency requirements

We assume the market go live is in north america. Here the latency requirements can be met with proposed architecture. Later for internal rollouts to Europe or Asia it is planned to have a content delivery framework integrated as a partner solution to allow full scalling and still provide expected latency requirements even in remote regions.
