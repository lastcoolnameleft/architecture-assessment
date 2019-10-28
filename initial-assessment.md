# Initial Cloud Native Application Assessment

## Background

Utilizing the cloud or containers provides numerous benefits for both application developers and operators.  However, this journey requires careful planning and preparation.

## Purpose

Because each application is a special snowflake, this document is designed to provide a starting point to reveal any challenges or "red flags" you might encounter before running in a containerized environment.

These are designed to ask probing questions to determine the application's maturity in migrating to containers, but could also be applied to any Cloud Native solution.

## Benefit

* What is your main benefit you plan to utilize with going Cloud Native?

## Application Codebase

* What OS does the service run on?
* How do user's interact with the application?  (e.g. Browser, RDC, Run on Desktop, etc.)
* How are you storing your code? (e.g. Github, VSTS, TFS, GitLab, etc.)
* Do you have one repository per code base?
* How do you deploy your services?
  * Do you deploy your UI separately from your API?
  * What are your deployment artifacts? (e.g. Java WAR, .EXE, Container)
* What programming languages are used?

## Dependencies

* How do you declare your build dependencies? (e.g. Maven, config files)
* How do you include your dependencies in your application? (e.g. Built into application artifact, deployed in separate build process)

## Config

* How/where do you store your application config?
* How/where do you store your infrastructure config?
* How do you update config?
* Could you Open Source your application without exposing credentials?
  * Not interested if you plan to, but is just a litmus test

## Backing Services

* Do you use: (and if so, which one and what version)
  * Database (e.g. SQL Server, MySQL, PostgreSQL, Oracle)
  * Message/Queue system (e.g. Service Bus, Kafka)
  * SMTP
  * Cache (e.g. Redis)
  * Other API
* Can replace any instance above without a code change?

## Build/Release/Run

* How do you build your application? (e.g. Jenkins, custom scripts)
  * Where are the artifacts stored? (e.g. Artifactory?  Azure Container Registry)
* How do you release your application? (e.g. Screwdriver, etc.)
  * Do you have a unique id for each release?
  * Is the deployment mutated or deployed fresh each time?
* How do you start your application?  (e.g. Manually; some automated process)

## Application Process

* How do the processes manage and store state?
* Does the application need to support "sticky sessions"?

## Service Exposure

* What ports are exposed internally?
* What ports are exposed externally?  
* How are these ports exposed?
* What security needs to be in place for these services? (e.g. SSL, WAF, etc.)

## Concurrency

* Are there different process types?
  * e.g. Admin process, client, server, db migration, one-time scripts
  * How are they run?
* How do you scale processes?
  * Follow-up:  Can you scale processes independently?

## Disposability

* Can the processes be start/stopped on a moment's notice?
* What is the process start time?
* Can you run SIGTERM on them?
* Are there background jobs?
  * Are the jobs re-enterant? (can be interrupted during exe and restarted safely)
  * Are the jobs idempotent?

## DevOps

* How often do you release?
* Are you implementing CI/CD?
* What distinct environments do you have? (e.g. Dev, test, stage, prod)
* How is the application moved from the environments listed above?

## Observability

* How do you detect an outage?
* How do you pinpoint the source of the outage?
* How are logs accessed?

## Culture

* Who is driving this initiative? (e.g. top-down (CTO), bottom-up (devs/ops), or both)
  * For maximum effectiveness a company wide, not project specific approach, is recommended
  * However, it's recommended to start with a single project to develop confidence + competence
* How would you rate yourself from an automation perspective?

## Networking

* Any IPv4/IPv6 requirements?
* What is the expected traffic volume/pattern? (e.g. 1000 rps from 5-9, 50 rps otherwise; bursty during European daylight)
* Will the application be exposed to the public internet?
* Is a Network or Web Application Firewall required?

## Policies

* What are your network policy requirements?
* What are your pod security policy requirements?
* What are your access control policy requirements?
* What are the compliance/governance requirements? (e.g. HIPPA, HITRUST, Gov Cloud, etc.)

## Other

* What are the High Availability/Business Continuity/Disaster Recovery requirements?

## Resources

* https://12factor.net/