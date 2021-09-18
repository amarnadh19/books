# Steps to move one VM from one VNet to other

## Change subnet of VM (under same VNet)

1) Login to portal. 
2) click on VM’s virtual network interface card (vNIC).Select the device and left side,IP configurations and choose the subnet where to move the server.

  ![](https://github.com/amarnadh19/books/blob/main/images/az_vm_move_subnet_1.png?)

## Using Same resourcegroup and Same region - VNet1 to VNet2 

1) Collect the disk information.

2) Stop VM and delete Source VM. Causion: Check the vnet whether you are in right place.

3) Expand RG resources --> select the Previous VM disk --> click on create VM from this disk option under Disk blade.

4) Fill the details and push to next step. You need to select the destination VNet and subnet if required.

5) in final window, Please click on create. 

6) check the progress of VM creation. If all went good, then login with the username and password given to previous VM. then check the application status and perform test for application if needed.


# Move Azure VMs across regions

