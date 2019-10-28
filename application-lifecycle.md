# Software Delivery

## Deployment

Typically, these are 3 separate pipeline to an Application Deployment Lifecycle. 

### Build

The build step is designed to convert code to a bundle:

* How do you build your software? (e.g. Jenkins)
* Do you convert checked in code to a build artifact?
  * If so, what tools do you use to build it?
* Are you implementing CI?

### Release

The release step combines build with config (ready for execution):

* How do you release your software? (e.g. Ansible)
* Do you have a unique id for each release?
* Is the deployment mutated or deployed fresh each time?
* Are you implementing CI?
* How do you manage deployment errors?
* What are the pre/post launch validation plans?

### Run

The Run step launches the application

* After the release step, how is the application started?
  * e.g. Manually, some automated process


## Configuration
* How do you deploy configuration files across environments?
* How do you deploy secret/sensitive files across environments?
* What distinct environments do you have? (e.g. Dev, test, stage, prod)
  * How do you deploy to each of the environments?
* What user does your software run as?
* Do you gracefully drain off traffic when upgrading?

## Timing
* How long does a global rollout take?
* What is your release cycle? (e.g. 1/mo, every merged PR)

## Change Management

* Is there an approval system for change?
* How do you document production changes?

## Resources

* https://12factor.net/