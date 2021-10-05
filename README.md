# crm-docs

Revisions to the CRM plugin docs to ensure they are complete and consistent across all stacks.

Source is https://operators.mobiledgex.com/product-overview/cloudlet-onboarding/

* CRM Plugin needs to move from "Product Overview" to a specific "CRM Deployment" section that provides the requirements details for each IaaS and the instructions for creating cloudlets.
* Overview pages serve no purpose and should be removed
* Page structure for each IaaS
  * Architecture and Options (Diagram(s) plus description of each deployment option)
  * Network and Resource Requirements and Recommendations
    * Clear tabular info for each item describing. What the item is and why it's needed. Minimum settings, Recommended settings etc
  * Seecurity and Firewall Requirements
    * List of Generic FW rules required
    * Details of IaaS permissions required by Tenant/ Service Account used by CRM
  * Flavor / Instance Type requirements
    * Ram, CPU, Disk, (GPU)
