# Z-Pro application

An Hybrid Application with VM.

- MCM 2.0
- Hybrid Application.
- VM


## Installation

#### Placement rule

Change the PlacementRule cluster the text "name: mcm-managed-cp4a-cluster" appropriately in the yaml file.

#### VM

The pre-requisite to deploy vm in Infrastructure Management(IM) is to have a service in IM which provisions a virtual machine in any environment like AWS, Azure or VMware which is managed in IM.
The `spec.options` values of the `VirtualMachine` resource need to be filled in using the output of Infrastructure Management API - which retrieves the details of service template used to provision the vm.  

Ex: In IM, if the service template ID of service used to provision VM in AWS account is 1, then 
GET `https://<IM_URL>/api/service_templates/1`

#### Deploy
Run the below command to deploy the app.

```
oc apply -f zpro.yaml
```

## Topology

<img src="images/topology.png">
