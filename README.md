# Architecture Assessments

This repo is designed to be a checklist of questions when migrating a system to a [Cloud Native](https://www.cncf.io/) Architecture.

## Intent

As a Cloud Solution Architect for Microsoft, I need to be able to quickly vet and understand a wide range of solutions before starting the discussion of architecture or implementation.  These pages are designed to help cover all bases during the investigation stage of a project.

## How to use

Start with the [Intial Assessment](initial-assessment.md) and then dig deeper into the following topics as needed:

* [Application Lifecycle](application-lifecycle.md) - CI/CD, DevOps
* [Capacity](capacity.md) - Scaling, RPS, etc.
* [Containers](containers.md) - Docker, K8S, etc.
* [Microservices](microservices.md) - Distributed Application Design
* [Multi-Tenancy](multi-tenancy.md) - Isolating multiple apps or multiple types of apps in the same cluster
* [Networking](networking.md) - Connectivity requirements (e.g. Ingress and Egress traffic)
* [Security](security.md) - Day 0 exploits, DDoS, etc.
* [Observability](observability.md) - Monitoring, Alerting, etc.
* [Other](other.md) - Data retention, HIPPA, SOX
* [Resiliency/Availability/Business Continuity/Disaster Recovery](resiliency-availability.md) - RTO, RPO, SLA
* [External Services](external-services.md) - Databases, Cache, etc.
