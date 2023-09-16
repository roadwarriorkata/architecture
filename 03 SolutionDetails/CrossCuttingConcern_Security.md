# Cross Cutting Concern Security

This cross cutting concern on security provides market guidelines on how to best tackle common security risks assosiated with the technology stack of the Warrior application.

The document provides a general approach on how to deal with security in the project and provides chapters for the most prominent technologies (Web application, iOS app, Android app and API security)

## General Approach

Security is a complex and very dynamic field, which is of relevance for the successfull Warrior applicaton. In order to adress limited internal capabilities on  this topic, we recomend to have a security specialist onboarded for
- fundational risk analsis and definition of focus areas to best utilize existing know how and optimize learning curve.
- design phase to mitigate risks in design pahse
- Developer coaching to apply best practises and educate team
- Jointly design CICD pipelien to integrate static code analysis
- deployment strategy to understand and apply important cloud native configurations
- and pen testing before go life to validate effectivenss of measures

## Web Based application

Follow guideline from OWASP to minimize attack vectors along vulnerabilities.

[OWASP Web Application security risks](https://owasp.org/www-project-top-ten/)

## iOS App

Follow Apple guidelines for development.

[Apple Developer Security Guideline](https://developer.apple.com/documentation/Security)

## Android App

Follow Android guidelines for development.

[Android developer security guideline](https://developer.android.com/topic/security/best-practices)

## APIs

Follow guidelines from OWASP to minimize attack vectors along known vulnerabilities.

[OWASP Top 10 API security risks](https://owasp.org/API-Security/editions/2023/en/0x11-t10/)
