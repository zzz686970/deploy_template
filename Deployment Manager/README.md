Enable Google Cloud Deployment Manager V2 API. first!

- autonetwork-template.jinja


- customnetwork-template.jinja


- subnetwork-template.jinja


- firewall-template.jinja

ipCidrRange: IP address range of the subnet
network: Name of the subnet's network
region: Region that the subnet is created in

- instance-template.jinja

machineType: Machine type and zone
zone: Instance zone
networkInterfaces: Network and subnetwork that VM is attached to
accessConfigs: Required to give the instance a public IP address (required in this lab). To create instances with only an internal IP address, remove the accessConfigs section.
disks: The boot disk and its name and image

- config.yaml


```
gcloud deployment-manager types list | grep network
gcloud deplogcloud deployment-manager types list | grep firewall
gcloud deployment-manager types list | grep firewall
gcloud deployment-manager types list | grep instance

```
