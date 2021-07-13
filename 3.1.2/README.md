This repository contains the virtual switch image of Enterprise SONiC Distribution by Broadcom. This image is a virtual image in the QEMU qcow2 format that can be run on any linux host or the standard GNS3 environment( https://www.gns3.com/). The SONiC-VS image is available for users to be familiar with SONiC open-source Network operating system. The users can get acquainted with SONiC command line interfaces, naming convention, system packaging and other capabilities.
SONiC-VS image provides users the ability to verify the control plane functions (for example. BGP, MC-LAG) on a typical data center switch. The data plane functionality (for example ACL, QOS, PBR) is not supported by SONiC-VS as it does not have underlying physical platform.

For SONiC-VS, we recommend using Ubuntu 16.04 server with atleast 16GB of memory & 8 CPUs. This configuration will allow users to run 2+ instances of SONiC-VS to create a typical Data Center Spine-Leaf topology. 

For more information about how to use SONiC-VS please visit : https://www.youtube.com/love2network

For any questions please contact : sonic-info@broadcom.com

# Features Supported with SONiC-VS Image:
- eBGP / iBGP - (underlay and overlay)
- MC-LAG
- OSPF underlay with BGP / EVPN as overlay
- Numbered and un-numbered interfaces
- BGP un-numbered
- Route leaking
- Multi-VRF (Multi-tenants)
- BFD

# Installation steps on a Linux Server

*Note: Ensure the server CPU supports Virtualization technologies
like Intel VT-D/X or AMD-V.  Check BIOS settings and enable if
required.*

## Download files
- Download sonic-vs-3.1.2.img.gz and sonic-vs.xml to a local directory on your server.
- sudo / root privilages are required for installation.


## Install the below packages

sudo apt-get -y install qemu-kvm qemu-utils bridge-utils libvirt-bin

## Create the bridge interface br0 (if it does not exist)
sudo brctl addbr br0

## Unzip the image if its compressed

sudo gunzip sonic-vs-3.1.2.img.gz

sudo cp sonic-vs-3.1.2.img /var/lib/libvirt/images

## Define the VM

sudo virsh define sonic-vs.xml

## Start the VM
sudo  virsh start *vmname*

Note: The <vmname> is as defined in the sonic-vs.xml.
The factory default is specificed as "sonicvs312"

## Connect to the VM
sudo virsh console *vmname*

## Login credentials

Login as admin and use YourPaSsWoRd as the password

## Shutting down the VM

virsh shutdown *vmname*

# Frequently Asked Questions:

Q. Which platforms are supported with Enterprise SONiC by Broadcom?
A. Enterprise SONiC is supported on most commonly available ODM platforms, some example includes Edgecore, Quanta, Dell etc.

Q. How can I get a access to trial image of SONiC on an ODM Platform?
A. Please reach out to "sonic-info@broadcom.com" and provide customer name, customer contact, & intended platform for SONiC.

Q. Can you please share sample SONiC configuration BGP / EVPN?
A. Please check-out the youtube video series : https://www.youtube.com/love2network for sample SONiC configurations.
