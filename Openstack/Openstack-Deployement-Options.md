# Overview

For an OpenStack Cloudlet deployment, MobiledgeX is given credentials for an OpenStack tenant account to enable the cloudlet to be deployed and for it to manage VM's and networks. 

* The Operator manages the underlying OpenStack IaaS system, flavors and external networking.
* MobiledgeX maintains the cloudlet and supports the deployment of edge workloads

Any OpenStack implementation that utilizes the supported versions and the standard OpenStack API's is supported, such as VMware VIO, Redhat RHOSP and Cisco VIM.

Typically the tenant account has access to UE Wireless and External Internet Provider networks.

Once the tenant account has been created with the required permissions and the external networks have been set up, the cloudlet can be deployed either by MobiledgeX (Direct mode), or by the Operator (Restricted mode). 

# Cloudlet Resource and Configuration Requirements

## OpenStack Requirements

| Requirement                   | Details                                                                                                                                             |
| ----------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| **OpenStack Version**         | Queens or Higher                                                                                                                                    |
| **Tenant Service/API Access** | Heat, Glance, Ceilometer, Neutron, Nova                                                                                                             |
| **Tenant Permissions**        | CRUD for VM instance, flavor, stack and network level operations                                                                                    |
| **Other Settings**            | - No CPU and RAM overcommit ratio set on compute nodes  <br>- Neutron ML2 port security enabled <br>- VM instance console access (VNC, SPICE, etc.) |

## Compute and Storage

| Resource | Mandatory Minimum | Recommended     | Notes                                                                                                           |
| -------- | ----------------- | --------------- | --------------------------------------------------------------------------------------------------------------- |
| vCPU     | 32                | 200             |                                                                                                                 |
| RAM      | 128 GB            | 500             |                                                                                                                 |
| Disk     | 500 GB            | 2000 GB         | Local or shared storage.                                                                                        |
| GPU      | 0                 | Operator choice | PCI PassThrough GPU (eg: NVIDA T4) or vGPU enabled with corresponding flavors and licenses available to use it. |

## Networking

| Network           | Required  | Minimum        | Recommended | Notes                                                                           |
| ----------------- | --------- | -------------- | ----------- | ------------------------------------------------------------------------------- |
| Internet external | Mandatory | /28 with 8 IPs | /24         | External network with internet access to MobiledgeX public endpoints.           |
| Wireless external | Optional  | /28 with 8 IPs | /24         | Operator has the option to have a separate external network for edge workloads. |


## Flavors

### PlatformVM

The flavor required for the PlatformVM must have the following configuration.

| Resource       | Value |
| -------------- | ----- |
| vCPU:          | 2     |
| RAM Size (MB): | 4096  |
| DISK (GB):     | 40    |

### Edge application workload

The following minimum set of flavors must be provided for edge applications.

| Flavor     | vCPU | RAM   | DISK | GPU          |
| ---------- | ---- | ----- | ---- | ------------ |
| m4.small   | 2    | 2048  | 20   | 1 - Optional |
| m4.medium  | 2    | 4096  | 40   | 1 - Optional |
| m4.large   | 4    | 8192  | 80   | 1 - Optional |
| m4.xlarge  | 8    | 16384 | 160  | 1 - Optional |
| m4.xxlarge | 16   | 32768 | 160  | 1 - Optional |


## Images

MobiledgeX requires Images/Templates to be installed on the IaaS stack for provisioning the CRM and the edge workload VM's. The base image required for the PlatformVM must be uploaded to Glance, by the Operator, prior to cloudlet deployment.

MobiledgeX will provide details of the current image version prior to deployment.