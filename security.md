# Security

Prefix each of these items with "Do you need to consider X?"

## Build Security
* Scan vulnerabilities before pushing images to the registry
* Use vulnerability mgmt as part of development lifecycle
* Continue scanning in the registry

## Runtime Security
* Ensure the integrity of images throughout the lifecycle
* Enforce least privileges in runtime
* Reduce the container attack surface by removing unneeded privileges
* Whitelist files and executables that the container is allowed to access or run
* Map image vulnerabilities to running containers
* Ensure only approved images are used in your envs
* Permit only approved registries
* Container breakouts
* Kernel exploits
* Denial-of-service attacks
* Compromising secrets

## Monitoring
* Log all container administrative user access for auditing
* Monitor container activity and user access
* Monitor container resource activity

## Network Security
* Enforce network segmentation on running containers

Inspired by: [Container Security in MS](https://azure.microsoft.com/mediahandler/files/resourcefiles/container-security-in-microsoft-azure/Open%20Container%20Security%20in%20Microsoft%20Azure.pdf)
