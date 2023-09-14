# Problem Defintion

## Mission Statement

The target is to build an online trip management application to allow travelers to manage their trips and see all of their existing reservations.

## User Journeys

The main interaction of the traveler (user) for the MVP is scetched with the following user journey: 

### Planning Journey

The target of the planning journey is to plan an prepare an upcomming trip (travel)

![Panning Journey](PlanningJourney.png)

### Travel Journey

The traget of the travel journey is to support the traveler while on the journey and provide himn with always up to date information on his upcomming reservations. He also should be able to trigger or digest changes in schedule, accomodaton or connection details.

The user wants to share his travel with freinds and family via social media.

![Travel Journey](TravelJourney.png)

### Help Journey

In case the traveler runs into conflicting information or problems when traveling, each of the agencies provide contact details, which are provided to him for easy access and fast issue resolution.

![Help Journey](HelpJourney.png)

## System Context

The traveler interacts with the Travel Warrior application (either via smart phone or web browser). The rich interface provides access to all relevant agencies for car, hotel oder flight reservations. 
Also the traveler can access reservation details from platforms like Sabre or Apollo.
The Warrior application provides interfaces to social media channels like Instagram, Whatsapp and Facebook.
For convenience reasons the traveler can allow the Warrior application to scan his mail folder (IMAP) in order to filter for travle relevant information and provide an additional input channel for travle updates as some agencies prefer this channel.

![System Context View](/03%20SolutionDetails/ContextView.png)

The Warrior application is split into user interface components, business logic and persistency components along travel related contexts. For details please see [SolutionStartegy.md](/02%20SolutionStrategy/SolutionStrategy.md).

## Architecture Goals

Quality Requirements: [ISO2510](https://iso25000.com/index.php/en/iso-25000-standards/iso-25010)


| Quality Requirement | Relevance | Description for Road Warrior |
| --- | --- | --- |
| Time Behaviour, Responsiveness | high | response time web: 800ms app: 1400ms|
| Capacity, Scalability | high | 2mio active users per week |
| Elasticity | high | parts of the Arrior application need to adapt to current needs e.g. start of local vacation times, liek christmas or thanks giving. |
| Learnability | high | Travelers will not use this on a daily base, hence the application needs to be very easy to understand |
| Accessability | high | All travlers across the world are targeted with this application, time zones, languages and currencies need to be taken into account. MVP: North America and Europe with English, French, German, Italien, Spanish language. All timezones, Two currencies US dollar and Euro |
| Availability | high | max 5min downtime per month|
| Data Consistency | medium | now extra needs or complex data model |
| Data Currentness | high | during travel the traveler expects absolute consitency of reservation data |
| Recoverability | high | The user needs to be able to revcover his data, if the mobile app crashes or the web browser stops. |
| Confidentiality | medium | Data rivacy requirements need to be taken into account, namely GDPR in Europe. API calls need to be secured accordingly.|
| Integrity | low | There is no reservation data generated in Road Warrior. All data is comming from agencies or travel platforms as system of record. Hence no critical integrity requirements need to be considered with Road Warrior.|
| Non-Repudiation | low | Data is only read from agency APIs, no write back. No special requirements for non repudiation.|
| Testability | high | Testability is critical as the Travel Warrior application needs to be adapted and enhanced easily and frequently. This requires safeguarding with automated testing, hence system design needs to support testablity.|
| Adaptability | high | High requirements to allow for application adaptation according to emerging business needs and changes in market expectations.|
| Installability | high | High demands for easy installation to allow all potential travelers in the world to use the Warrios app|


## Essential Constraints

The company is a start up with limited experience and capacity in developing and deploying modern architecture. 

## Greatest Risks
