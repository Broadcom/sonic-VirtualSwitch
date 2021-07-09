This repository contains the virtual switch image of Enterprise SONiC Distribution by Broadcom. This image is a virtual image in the QEMU qcow2 format that can be run on any linux host or the standard GNS3 environment( https://www.gns3.com/). The SONiC-VS image is available for users to be familiar with SONiC open-source Network operating system. The users can get acquainted with SONiC command line interfaces, naming convention, system packaging and other capabilities.
SONiC-VS image provides users the ability to verify the control plane functions (for example. BGP, MC-LAG) on a typical data center switch. The data plane functionality (for example ACL, QOS, PBR) is not supported by SONiC-VS as it does not have underlying physical platform.

For SONiC-VS, we recommend using Ubuntu 16.04 server with atleast 16GB of memory & 8 CPUs. This configuration will allow users to run 2+ instances of SONiC-VS to create a typical Data Center Spine-Leaf topology. 

For more information about how to use SONiC-VS please visit : https://www.youtube.com/love2network

For any questions please contact : sonic-info@broadcom.com

Features Supported with SONiC-VS Image:
- eBGP / iBGP - (underlay and overlay)
- MC-LAG
- OSPF underlay with BGP / EVPN as overlay
- Numbered and un-numbered interfaces
- BGP un-numbered
- Route leaking
- Multi-VRF (Multi-tenants)
- BFD

Installation steps on a Linux Server

Note: Ensure the server CPU supports Virtualization technologies
like Intel VT-D/X or AMD-V.  Check BIOS settings and enable if
required.

# Install the below packages

sudo apt-get -y install qemu-kvm
sudo apt-get -y install qemu-utils
sudo apt-get -y install bridge-utils
sudo apt-get -y install libvirt-bin


# Unzip the image if its compressed
gunzip sonic-vs.img.gz

# Edit sonic-vs.xml file and change the following

<source file='/PATH/TO/sonic-vs.img'/>
              ^^^^^^^^^^^^^^^^^^^^^
              Replace the above with the path on your system

# Define the VM
virsh define sonic-vs.xml

# Start the VM
virsh start <vmname>

Note: The <vmname> is as defined in the sonic-vs.xml.
The factory default is specificed as "sonicvs1"

# Connect to the VM
virsh console <vmname>

# Login as admin and use YourPaSsWoRd as the password

Frequently Asked Questions:

Q. Which platforms are supported with Enterprise SONiC by Broadcom?
A. Enterprise SONiC is supported on most commonly available ODM platforms, some example includes Edgecore, Quanta, Dell etc.

Q. How can I get a access to trial image of SONiC on an ODM Platform?
A. Please reach out to "sonic-info@broadcom.com" and provide customer name, customer contact, & intended platform for SONiC.

Q. Can you please share sample SONiC configuration BGP / EVPN?
A. Please check-out the youtube video series : https://www.youtube.com/love2network for sample SONiC configurations.
