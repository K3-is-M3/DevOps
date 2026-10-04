# Connect to a storage account using an Azure Private Endpoint

## Purpose & Scope
This article provides a tutorial for creating a private endpoint in Azure to enable secure communication between Azure resources, such as virtual machines and Azure Storage, without public access.

## Value Proposition
Following this tutorial helps users establish a secure and private connection to Azure Storage, enhancing data security and compliance by eliminating public access.

## Quick Summary of Content
- Create a virtual network and bastion host for secure access.
- Set up an Azure Storage account and disable public access.
- Create a private endpoint for the storage account.
- Deploy a virtual machine within the virtual network.
- Test connectivity to the storage account via the private endpoint using Azure Storage Explorer.
- Instructions for managing resources, including creating a blob container and retrieving the storage access key.
- Guidance on deleting the resource group and its resources after use.

## Since I will be explaining by doing, I will be combining multiple tasks together in an easy-to-understand way
Deployment Tips:
- Region Selection: For optimal performance, place all your resources in a single region that is physically closest to your location.
- Free Account Limits: If you are using the $200 Azure free credit, Microsoft enforces strict regional quota limits.
- The Fix: If you run into quota errors, workaround the restriction by spreading your resources (e.g., virtual networks) across multiple different regions.
- **Also, the settings I use here are only for testing purposes. For production environments, requirements might be different**

### Step 1
Here we will:
- Create a resource group
- Create a virtual network
### Walkthrough
<video src="https://youtu.be/z7YDLZ68ZRc?si=fsEHK7uyfcwPez0v" controls width="650" height="450"></video>

<hr>

### Step 2
Here we will:
- Create a NAT gateway for our virtual network created in step one. This will enable the VMs in our network to access the internet without exposing our IP address, which would be the case if we just assigned a public IP address.
- ### I missed a crucial step here, which is assigning an outbound IP to our gateway, without which we cannot access the internet from our VM. But not to worry! I have covered it in step 5, but you can make the correction in this step too. That's good as well.
### Walkthrough
<video src="https://youtu.be/2HrytHgXKwM?si=gC5ilhULWmqKYpkT" controls width="650" height="450"></video>

<hr>

### Step 3
Here we will:
- Create a Virtual Machine (Windows)
### Walkthrough
<video src="https://youtu.be/1gP2RZIKBLo?si=WNytxD2L6iqR8xMI" controls width="650" height="450"></video>

<hr>

### Step 4
Here we will **Create a storage account**. From there, we will:
- disable public access on the storage account
- create a private endpoint

From your storage account, you will also need to obtain a storage access key from your storage account (this will be required for later steps)

Finally, we will:
- Add a blob container to your storage account
### Walkthrough
<video src="https://youtu.be/YBVwkTBx8Ik?si=_XLsBJxBQQvXIego" controls width="650" height="450"></video>

<hr>

### Step 5
- Access Windows VM through Bastion
- Sign in with the credentials you set during VM creation
- Open browser and google [Microsoft Azure Storage Explorer](https://www.microsoft.com/en-us/download/details.aspx?id=108134). Download and Install it.
- Open select resource dialog box (power plug symbol) 
    -> select resource -> storage account or service -> connection method = Connection String -> paste your connection string -> Next -> Connect
    -> Expand your storage acc and select blob containers
- You should see your newly created container

- **And you have successfully connected to a storage account using an Azure Private Endpoint**
### Walkthrough
<video src="https://youtu.be/ZKAz7vfHaMs?si=g_YEtyNjsP4aEUXZ" controls width="650" height="450"></video>

<hr>

### Step 6
- Clean up. Time to clear all our resources to prevent our credits from being drained.
- **ALWAYS** make sure you have deleted all the resources you provisioned. Double check if need be.
### Walkthrough
<video src="https://youtu.be/wujk-VDj5kE?si=QgJ5tvhJkIMpwHO9" controls width="650" height="450"></video>