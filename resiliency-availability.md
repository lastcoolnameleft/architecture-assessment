# Resiliency and High Availability

* What is your service's SLA?  (e.g. QPS, Latency, Availability)
  * How do you know if they've been met?
* What is your service's Recovery Point Objective (RPO)?
* What is your service's Recovery Time Objective (RTO)?

## BC/DR

See: https://azure.microsoft.com/en-us/features/resiliency/ 

* Do you need Availability Zones?
  * How many?
* Do you need multiple regions?
  * Which regions?
  * Hot/Cold?  Hot/Warm?  Hot/Hot?

## Failures

* Are there any SPOF (Single Points of Failure)?
* How/What do you detect when a disk is full?
