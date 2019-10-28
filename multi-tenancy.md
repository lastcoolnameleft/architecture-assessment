# Multi-Tenancy

If your system is designed to support multiple tenants, the approaches to solve this problem are usually:

* Application based - All requests from a tenant use a single infrastructure and application deployment
* Infrastructure based - Each tenant gets their own "stamp" of the application and requests.  Likely Network isolated.
* Hybrid - This is a combo where part of your system is App based and others are Infra based.

## Concerns of Multi-tenancy

Boils down to different types and levels of isolation.  

* Noisy Neighbor (CPU boundary)
* DoS each other (Network)
* Intercept traffic (Network)
* Privilege escalation (Kernel/Process)
* Secrets (User/Pass, Certificates)

## Models of Multi-tenancy

* Hard multi-tenancy - 0 Trust between tenants
* Soft multi-tenancy - Some trust. (Maybe different teams within same company)
* Somewhere on the spectrum between the two

## Design Considerations

When possible, use logical isolation for your cluster (e.g. namespaces) instead of physical isolation (e.g. separate clusters)

* Authentication and authorization
  * Internal to Cluster - e.g. [Kubernetes RBAC Role/ClusterRole](https://kubernetes.io/docs/reference/access-authn-authz/rbac/)
  * External to Cluster - e.g. [Azure Active Directory](https://docs.microsoft.com/en-us/azure/aks/azure-ad-integration)
* Isolation
  * [Pod Security Policy](https://kubernetes.io/docs/concepts/policy/pod-security-policy/)
  * [Network Policy](https://kubernetes.io/docs/concepts/services-networking/network-policies/)
  * [Namespaces](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/)
* Fair Sharing
  * [Resource Quota](https://kubernetes.io/docs/concepts/policy/resource-quotas/)
  * [Resource Limit](https://kubernetes.io/docs/concepts/policy/limit-range/)
  * [Limit Ranges](https://kubernetes.io/docs/concepts/policy/limit-range/)
  * [Quality of Service](https://kubernetes.io/docs/tasks/configure-pod-container/quality-service-pod/)
  * [Affinity/Anti-Affinity](https://kubernetes.io/docs/concepts/configuration/assign-pod-node/#affinity-and-anti-affinity)

## Questions

* How do you onboard a new tenant?
* How does your application determine the tenant?  (e.g. Host/Path/URL based routing)

## Kubernetes

* Does Namespace isolation meet your needs?
  * Can you use Namespace as a virtual cluster?
  * Is it ok if pods from the different namespaces are on the node?
* Is Control Plane multi-tenancy ok?
* Is Ingress multi-tenancy ok?
* Any Ingress/Egress considerations?

## References

* <https://docs.microsoft.com/en-us/azure/aks/operator-best-practices-cluster-isolation>
* <https://www.infoq.com/presentations/multi-tenancy-kubernetes/>