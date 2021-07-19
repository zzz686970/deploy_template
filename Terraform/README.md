- Create a configuration for a custom-mode network
- Create a configuration for a firewall rule
- Create a module for VM instances
- Create a configuration for an auto-mode network
- Create and deploy a configuration
- Verify the deployment of a configuration

```
## check terraform
terraform --version


```
## provider.tf
Terraform uses a plugin-based architecture to support the numerous infrastructure and service providers available. Each "provider" is its own encapsulated binary distributed separately from Terraform itself. Initialize Terraform by setting Google as the provider.

## managementnet.tf
The name field allows you to name the resource, and the type field allows you to specify the Google Cloud resource that you want to create

a custom mode network does not automatically create a subnetwork in each region. Therefore, you are setting auto_create_subnetworks to false.

The google_compute_subnetwork resource is a subnet. You are specifying the name, region, VPC network and IP CIDR range for managementsubnet-us .

The google_compute_firewall resource is a firewall rule. 

Because this firewall rule depends on its network, you are using the google_compute_network.managementnet.self_link reference to instruct Terraform to resolve these resources in a dependent order. In this case, the network is created before the firewall rule.

The list of allow rules specify which protocols and ports are permitted.

This resource is leveraging the module in the instance folder and provides the name, zone, and network as inputs. Because this instance depends on a VPC network, you are using the google_compute_network.managementsubnet-us.self_link reference to instruct Terraform to resolve these resources in a dependent order. In this case, the subnet is created before the instance.


## instance/main.tf
The google_compute_instance resource is a Compute Engine instance. 
Because you will be using this module for all VM instances, you are defining the instance name as an input variable. This allows you to control the name of the variable from managementnet.tf

define the zone and machine type of the instance as input variables.
defines the boot disk to use the Debian 9 OS image. Because all four VM instances will use the same image, you can hard-code this property in the module.
defines the network interface by providing the subnetwork name as an input variable and the access configuration. Leaving the access configuration empty results in an ephemeral external IP address (To create instances with only an internal IP address, remove the access_config section.)

By giving instance_type a default value, the variable is optional. The instance_name, instance_zone, and instance_subnetwork are required, and you will define them in managementnet.tf.

## privatenet.tf
- Add the VPC network 
- Add the privatesubnet-us subnet
- Add the privatesubnet-eu subnet resource
- Add the firewall resource
- Add the VM instance resource

## mynetwork.tf
- VPC networks
- subnetworks
- firewall rules
- vm instances
- internal ip




