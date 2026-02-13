# Metadata file structure

## Alignment between metadata file and disk file

The name of the disk file will be based on the name of the metadata file itself. Example: 
Given "vltestt001.at.inside.json" as metdadata file the expected disk file needs to be named "vlttestt001.at.inside.qcow2" and be readable within the same source as the metadata file.

## Description and examples

### org_id
The Exoscale organization this VM should be imported to.

The org_id is unique and mandatory.
Type: UUID

### name
The name of the VM. This name is used to display the VM, if cloud-init is configured this hostname will be set on start up.

The name is unique and mandatory
Type: string

### zone
The name of the zone the VM should be imported to.

The zone is unique and mandatory.
Type: string

### deploy_target
The UUID of the environment the VM should be provisioned in. Blank is not allowed as we need to provision on the specialized hypervisor farm.

The deploy_target is unique and mandatory.
Type: UUID

### service_offering
The UUID of the service offering (t-shirt) for the VM.


The service_offering is unique and mandatory.
Type: UUID

### disk_size
Disk size in GiB to be used for the VM. Provided as number without 

The disk_size is unique and mandatory.
Type: int

### template_id
UUID of the template to use as basis for the VM. Can be a standard Exoscale template or a custom template used as placeholder.

The template_id is unique and mandatory.
Type: UUID

### ip_assignment
ipv4: First NIC will be attached to Exoscale network infrastructure and will receive a public IPv4 IP out of Exoscales pool via DHCP  
ipv6: First NIC will be attached to Exoscale network infrastructure and will receive a public IPv4 and IPv6 IP out of Exoscales pool via DHCP  
private: All NICs will be attached to Exoscale private networks configured. If no private networks configured VM will be deployed without NIC  

The ip_assignment is unique and mandatory.
Type: string

### vtpm
Set to true if vTPM should be attached to the VM. Set to false if vTPM is not required.

The vtpm is unique and mandatory.
Type: boolean

### secureboot
Set to true if secureboot should be attached to the VM. Set to false if secureboot is not required.

The secureboot is unique and mandatory.
Type: boolean

### uefi
Set to true if system is UEFI, set to false if system is BIOS/Legacy

The uefi is unique and mandatory.
Type: boolean

### vss
Set to true if system should use VSS as snapshot technology, set to false if VSS technology should not be used.

The vss is unique and mandatory.
Type: boolean

### labels
Enter one or multiple key-values as labels

The labels are not mandatory and not unique.
Type: key-value

### private_networks
Enter none or multiple UUIDs of private networks the VM should be attached to.

The private_networks are not mandatory and not unique
Type: UUID

### security_groups
Enter one or multiple UUIDs of security groups the VM should be attached to. Only necceary if "ip_assignment" is no private.

The security_groups are mandatory and not unique.
Type: UUID
