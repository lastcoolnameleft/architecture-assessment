# Microservice/Container Maturity Questionaire

## Background

Utilizing "The Cloud" or "Containers" provides numerous benefits for both application developers and operators.  However, this journey requires careful planning and preparation.

## Purpose

Because each application is a special snowflake, this document is designed to provide a starting point to reveal any challenges or "red flags" you might encounter before running in a containerized environment.

These are designed to ask probing questions to determine the application's maturity in migrating to containers, but could also be applied to any Cloud Native solution.

_NOTE: Many of these questions are inspired by: "12 Factor apps"._

## Benefit

* What is your main benefit you plan to utilize with containers?

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
  * Database (e.g. SQL Server, MySQL, Postgres, Oracle)
  * Message/Queue system (e.g. Service Bus, Kafka)
  * SMTP
  * Cache (e.g. Redis)
  * Other API
* Can replace any instance above without a code change?

## Build/Release/Run

Ideally, these are 3 separate pipelines to an Application Deployment Lifecycle.  This section is designed to discover how they are implemented.

### Build

The build step is designed to convert code to a bundle:

* Do you convert checked in code to a build artifact?
  * If so, what tools do you use to build it?
  * Where is that artifact stored?

### Release

The release step combines build with config (ready for execution)

* Do you have a unique id for each release?
* Is the deployment mutated or deployed fresh each time?

### Run

The Run step launches the application

* After the release step, how is the application started?
  * e.g. Manually, some automated process

## Application Process

* Does the processes store any state?
* Does the application need to support "sticky sessions"?

## Service Exposure

* What ports are used?
* What ports are exposed externally?
  * Are these exposed to the public internet?
* How are ports declared?
* What security needs to be in place for these services (e.g. SSL, WAF, etc.)

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
* What distinct environments do you have? (e.g. Dev, test, stage, prod)
  * How is the application moved from dev->test->stg->prod?

## Monitoring

* How do you know if the system goes down?
* How do you determine which component of the system needs investigation?
* How do you debug the system?

## Logging

* How are logs collected and aggregated?
* Where are logs stored locally?

## Culture

* Who is driving this initiative? (e.g. top-down (CTO), bottom-up (devs/ops), or both)
  * For maximum effectiveness a company wide, not project specific approach, is recommended
  * However, it's recommended to start with a single project to develop confidence + competence
* How would you rate yourself from an automation perspective?

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
