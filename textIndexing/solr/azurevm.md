# Creating an Azure VM
I decided to create a Vm on Azure.  I have an Azure allowance that can host many VMs

# Creating the VM
## Create SSH Keys

- Open the Settings app and go to Apps -> Apps & features.
- On the right, click Manage optional features.
- On the next page, click the button Add a feature.
- In the list of features, select OpenSSH Client and click on the Install button.
- Open the Windows Terminal
```C:\Users\clyde\.ssh> ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/clyde/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in c:\users\clyde\azureubuntu.
Your public key has been saved in c:\users\clyde\azureubuntu.pub.
The key fingerprint is:
SHA256:t6xGQ+4K/499h3ZexWTI0OmDs1yzoIwbZzWZXdGxq+Q clyde@AUGUSTUS
The key's randomart image is:
+---[RSA 2048]----+
|            .. ++|
|             oo.+|
|             *ooo|
|        .   O *+.|
|       oSo.+ B =o|
|        *o=.= o .|
|    .  o *o  E  .|
|     o  ++  + o. |
|      o++.oo +.  |
+----[SHA256]-----+
```

## Create the server
- Create a resourcegorup `openVirus`
- Create a VM openvirus

Standard D2s v3
2 vcpus, 8 GiB memory (£63.11/month)

To display the public key for VM creation, type `cat id_rsa.pub`.

- allow ports, 80, 22 and 443
- Use a Premium SSD for the storage
- select the remaining defaults for the machine
- when the machine is created, click **Networking** on the sidebar then **Add Inbound port rule**. Open the 8983 port.
# Connect to the box
- Open a command prompt or terminal and type `ssh <username>@<ip address>`
- [Install PowerShell](https://linuxhint.com/install_powershell_ubuntu/)
- Follow the [instructions](instructions.md) to build the server

# Create a data drive
You can create an Azure virtual data disk to hold large amounts of data.  The standard size is 1Tb.  This is a good idea as the OS disk is only 30Gb in size and can quickly fill up.

- First, create the data disk when creating the VM in the Azure portal.  You can always add a data disk later

- Then [format and mount](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/attach-disk-portal) the disk.  This is a tricky operation which should be done carefully.

You can now store the data files on this disk and keep the OS drive free.

