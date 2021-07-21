# Steps to move one VM from one VNet to other

## Using Same resourcegroup and Same region

1) Collect the disk information.

2) Stop VM and delete Source VM. Causion: Check the vnet whether you are in right place.

3) Expand RG resources --> select the Previous VM disk --> click on create VM from this disk option under Disk blade.

4) Fill the details and push to next step. You need to select the destination VNet and subnet if required.

5) in final window, Please click on create. 

6) check the progress of VM creation. If all went good, then login with the username and password given to previous VM. then check the application status and perform test for application if needed.


# Using same resourcegroup and Different region.

