# Containers

## Orchestration

* Do you plan to use a managed service?  (e.g. AKS, EKS)
  * Kubernetes?
* Do you plan to use the Docker/Moby runtime?  (e.g. No, need to use CoreOS)

## Security

Inspired by: [Container Security in MS](https://azure.microsoft.com/mediahandler/files/resourcefiles/container-security-in-microsoft-azure/Open%20Container%20Security%20in%20Microsoft%20Azure.pdf)
* Security considerations
  * Kernel exploits
  * Denial-of-service attackds
  * Container breakouts
  * Poisoned Images
  * Compromising secrets

* Security approaches
  * Use vulnerability mgmt as part of development lifecycle
  * Scan vulnerabilities before pushing images to the registry
  * Continue scanning in the registry
  * Map image vulnerabilities to running containers
  * Ensure only approved images are used in your envs
  * Permit only approved registries
  * Ensure the integrity of images throughout the lifecycle
  * Enforce least privileges in runtime
  * Reduce the container attack surface by removing unneeded privileges
  * Whitelist files and executables that the container is allowed to access or run
  * Enforce network segmentation on running containers 
  * Monitor container activity and user access
  * Monitor container resource activity
  * Log all container administrative user access for auditing
  
