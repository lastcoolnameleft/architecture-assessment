# Security

This document is designed to list potential attack vectors and solutions to them.

## Container Threat Vectors

* Kernel exploits
* Denial-of-service attacks
* Container Breakouts
* Poisoned Images
* Compromising Secrets

## Principles to follow

* Minimize the attack surface
* Apply the principle of least privilege
* Segregation
* Don’t forget security in DevOps
* Always trust your sources

## Practices

### Cluster Security

* [Kube-Bench](https://github.com/aquasecurity/kube-bench) - Uses [CIS Benchmark](https://www.cisecurity.org/) to evaluate your cluster
* [Stay up-to-date](https://docs.microsoft.com/en-us/azure/aks/operator-best-practices-cluster-security#regularly-update-to-the-latest-version-of-kubernetes)
* [OS + Framework Patching](https://docs.microsoft.com/en-us/azure/container-registry/container-registry-tasks-overview#automate-os-and-framework-patching)

### Software Supply Chain

* [Content Trust](https://docs.microsoft.com/en-us/azure/container-registry/container-registry-content-trust) : Ensure the integrity of images throughout the life cycle / images haven't been tampered with
* [Container Image Scanning](https://docs.docker.com/ee/dtr/user/manage-images/scan-images-for-vulnerabilities/) : Scan all files in container image for vulnerabilities
  * [AquaSec](https://www.aquasec.com/)
  * [Twistlock](https://www.twistlock.com/)
* Image Availability : Do you care if images are publicly available?
* [Open Policy Agent](https://www.openpolicyagent.org/) : Only allow pulling from specific container registries

### Runtime Security

* Enforce least privileges in runtime
  * [AppArmor + seccomp](https://docs.microsoft.com/en-us/azure/aks/operator-best-practices-cluster-security#secure-container-access-to-resources)
  * Avoid running container as Root or with Privileges
* Whitelist files and executables allowed to access or run

### VM/Agent Security

* [AKS + Kured](https://docs.microsoft.com/en-us/azure/aks/operator-best-practices-cluster-security#process-node-updates-and-reboots-using-kured): Add security patches to Host VM

### Monitoring

* Log all container administrative user access for auditing
* Monitor container activity and user access
* Monitor container resource activity

### Network Security

* [Network Policy Enforcement](https://docs.microsoft.com/en-us/azure/aks/use-network-policies): Enforce network segmentation on running containers
* [Azure Firewall](https://azure.microsoft.com/en-us/services/azure-firewall/): Limit egress traffic from cluster

### AuthN and AuthZ

* Manage access to the cluster
  * [Kubernernetes RBAC](https://kubernetes.io/docs/reference/access-authn-authz/rbac/)
* Manage access within the cluster
  * [Enable Azure AD for RBAC](https://docs.microsoft.com/en-us/azure/aks/operator-best-practices-cluster-security#secure-access-to-the-api-server-and-cluster-nodes)
  * [Harden the Dashboard](https://redlock.io/blog/cryptojacking-tesla)

### Secrets and Configs

* [Azure KeyVault for Secret Management](https://github.com/Azure/kubernetes-keyvault-flexvol)
  * BETA: [Azure KeyVault Plugin for K8S](https://github.com/Azure/kubernetes-kms)

### Application

* [Web Application Firewall](https://azure.github.io/application-gateway-kubernetes-ingress/) : L7 Protection from cross-site scripting (XSS) attacks, SQL injection attacks, session hijacking and buffer overflows

## References and Credits

* [Securing Kubernetes](https://info.aquasec.com/securing_kubernetes)
* [Container Security in MS](https://azure.microsoft.com/mediahandler/files/resourcefiles/container-security-in-microsoft-azure/Open%20Container%20Security%20in%20Microsoft%20Azure.pdf)
* [AKS Container Security](https://info.cloudops.com/azure-kubernetes-services-container-security)
