# Microservice/Container Maturity Questionaire

## Background

Migrating an application to "The Cloud" or "Containers" provides numerous benefits for both application developers and operators.  However, this journey requires careful planning and preparation.

## Purpose

Because each application is a special snowflake, this document is designed to provide a starting point to reveal any challenges or "red flags" you might encounter before running in a containerized environment.

These are designed to ask probing questions to determine the application's maturity in migrating to containers, but could also be applied to any Cloud Native solution.

_NOTE: Many of these questions are inspired by: "12 Factor apps"._

## Benefit

* What benefit are you most interested in gaining from Microservices?  (e.g. 
## Application Codebase

* What OS does the service run on?
* How do user's interact with the application?  (e.g. Browser, RDC, Run on Desktop, etc.)
* How are you storing your code?
  * e.g. VSTS, TFS, GitLab, etc.
  * This question is designed to underand how developers interact with their source code.  It can also be a leading indicator to their maturity model.  i.e. CVS is a red flag
* Do you have one repository per code base?
  * This question is to understand if the are able to build/deploiy their services separately.
* How do you deploy your services?
  * Follow up questions:
    * Do you deploy your UI separately from your API?
    * What are your deployment artifacts?
      * e.g. Java WAR, .EXE, Container
* What languages are used?

## Dependencies

* How do you declare your build dependencies?
  * e.g. Maven, config files
* How do you include your dependencies in your application?
  * e.g. Built into application artifact, deployed in separate build process

## Config

* How/where do you store your config?
* How do you generate your config?
* How do you update config on your application?
* Could you Open Source your application without exposing credentials?
  * Not asking if you plan to, but is just a litmus test

## Backing Services

* Do you use: (and if so, which one and what version)
  * Database (e.g. SQL Server, MySQL, Postgres, Oracle)
  * Message/Queue system (e.g. Service Bus, Kafka)
  * SMTP
  * Cache (e.g. Redis)
  * Other API
* Can replace any instance above without a code change?
* Do you expect the DBA to keep the same role after the transition?

## Build/Release/Run

Ideally, these are 3 separate pipeline to an Application Deployment Lifecycle.  This section is designed to discover how they implement them.

### Build

The build step is designed to convert code to a bundle:

* Do you convert checked in code to a build artifact?
  * If so, what tools do you use to build it?

### Release

The release step combines build with config (ready for execution)

* Do you have a unique id for each release?
* Is the deployment mutated or deployed fresh each time?

### Run

The Run step launches the application

* After the release step, how is the application started?
  * e.g. Manually, some automated process

### Follow-up

Is it clear that the 3 processes are separated and able to be run independently?

## Application Process

* Do the processes store any state?
* Do they need to support "sticky sessions"?
* Do they share anything with other processes?

## Service Exposure

* What ports are used?
* What ports are exposed externally?
  * Are these exposed to the public internet?
* How are ports declared?

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

* What is your release cycle?
* Are you implementing CI/CD?
  * If your CI/CD build servers were destroyed, how easily could you re-create it?
* Does the Development Team contribute to Operations procedures?
* Does the Operations Team contribute to Development application?
* What distinct environments do you have?
  * e.g. Dev, test, stage, prod
    * How close does the development environment resemble test?
    * How close does the test environment resemble stage?
    * How close does the stage environment resemble production?

## Monitoring

* How are you currently monitoring the application?
* How do you know if it goes down?
* What alerts do you currently receive?

## Logging

* How are logs collected?
* How are logs aggregated?
* Where are logs stored locally?
* Are all logs send to standard out?

## Culture

* Who is driving the initiative?
  * e.g. top-down (CTO), bottom-up (devs/ops), or both
  * For maximum effectiveness a company wide, not project specific approach, is recommended
  * However, it's recommended to start with a single project to develop confidence + competence
* How would you rate yourself from an automation perspective?
  * NOTE: If you rely on humans, you won't be able to scale.

## Networking

* Any IPv4/IPv6 requirements?
* What is the expected traffic volume? traffic pattern?
* What are the DR/HA requirements?

## References

* Building Microservices by Sam Newman
  * http://shop.oreilly.com/product/0636920033158.do
* Production Ready Microservices by Susan Fowler
  * http://shop.oreilly.com/product/0636920053675.do
* Designing Distributed Systems
  * http://shop.oreilly.com/product/0636920072768.do
* GitOps
  * https://www.weave.works/blog/gitops-operations-by-pull-request

## Conclusion

The keen observer will note that none of the questions above mentioned containers, but instead explored the process and standards which make for great containerized apps.
