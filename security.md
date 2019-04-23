# Security

This list is intended to list out all of the attack vectors.  Prefix each of these items with "Do you need to consider X?"

## Top Level
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

### Image Security

* [OS + Framework Patching](https://docs.microsoft.com/en-us/azure/container-registry/container-registry-tasks-overview#automate-os-and-framework-patching)
* [Content Trust](https://docs.microsoft.com/en-us/azure/container-registry/container-registry-content-trust) - (e.g. Ensure the integrity of images throughout the lifecycle / images haven't been tampered with)
* Image Scanning - Scan all files in container image for vulnerabilities.  See AquaSec + Twistlock
* Image Pulling - Do you care if images are pubicly available?  
* Permit only approved registries - Open Policy Agent

### Runtime Security

* Enforce least privileges in runtime
  * [AppArmor + seccomp](https://docs.microsoft.com/en-us/azure/aks/operator-best-practices-cluster-security#secure-container-access-to-resources)
  * Avoid running container as Root or with Privileges
* Whitelist files and executables that the container is allowed to access or run

### VM/Agent Security

* Add security patches to Host VM - [AKS + Kured](https://docs.microsoft.com/en-us/azure/aks/operator-best-practices-cluster-security#process-node-updates-and-reboots-using-kured)

### Monitoring

* Log all container administrative user access for auditing
* Monitor container activity and user access
* Monitor container resource activity

### Network Security

* Enforce network segmentation on running containers - Network Policy Enforcement
* Limit outbound traffic from cluster - Azure Firewall

### Administration
* AuthZ + AuthN - [Enable Azure AD for RBAC](https://docs.microsoft.com/en-us/azure/aks/operator-best-practices-cluster-security#secure-access-to-the-api-server-and-cluster-nodes)
* Harden the Dashboard.  (See:  https://redlock.io/blog/cryptojacking-tesla)
* [Staying up-to-date](https://docs.microsoft.com/en-us/azure/aks/operator-best-practices-cluster-security#regularly-update-to-the-latest-version-of-kubernetes)

### Secrets and Configs

* Encryption and Storage of secret data - [Azure Key Vault Plugin for K8S](https://github.com/Azure/kubernetes-kms)
  * Alternative: https://github.com/Azure/kubernetes-keyvault-flexvol

## Credits

Inspired by: 
* [Container Security in MS](https://azure.microsoft.com/mediahandler/files/resourcefiles/container-security-in-microsoft-azure/Open%20Container%20Security%20in%20Microsoft%20Azure.pdf)
* [AKS Container Security](https://info.cloudops.com/azure-kubernetes-services-container-security)
