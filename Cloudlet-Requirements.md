# Cloudlet Resource and Configuration Requirements

## Compute and Storage

| Resource | Mandatory Minimum | Recommended | Notes                                                                                                           |
| -------- | ----------------- | ----------- | --------------------------------------------------------------------------------------------------------------- |
| vCPU     | 32                | 200         |                                                                                                                 |
| RAM      | 128 GB            | 500         |                                                                                                                 |
| Disk     | 500 GB            | 2000 GB     | Local or shared storage.                                                                                        |
| GPU      | 0                 | ?           | PCI PassThrough GPU (eg: NVIDA T4) or vGPU enabled with corresponding flavors and licenses available to use it. |


## Networking

| Network           | Required  | Minimum        | Recommended | Notes                                                                           |
| ----------------- | --------- | -------------- | ----------- | ------------------------------------------------------------------------------- |
| Internet external | Mandatory | /28 with 8 IPs | /24         | External network with internet access to MobiledgeX public endpoints.           |
| Wireless external | Optional  | /28 with 8 IPs | /24         | Operator has the option to have a separate external network for edge workloads. |


## Flavors / Instance Types

## Images

MobiledgeX requires Images/Templates to be installed on the IaaS stack for provisioning the CRM and the edge workload VM's.

