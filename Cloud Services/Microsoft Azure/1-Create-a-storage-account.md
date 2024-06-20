# Create a storage account

1. Log in with your Azure account (username@mydomain.com), credentials and OTP.
Under Azure services, select Storage accounts. Or, type "Storage" in the search field, select Storage accounts under Services

![](https://github.com/sysadminrepo/Procedures/blob/main/Cloud%20Services/Microsoft%20Azure/Assets/1-storage-service.png)

Click on + Create

![](https://github.com/sysadminrepo/Procedures/blob/main/Cloud%20Services/Microsoft%20Azure/Assets/2-create_account.png)

## Basics tab
1. Select a subscription and a resource group 
2. Enter a storage account name (The name must be unique across all existing storage account names in Azure. It must be 3 to 24 characters long, and can contain only lowercase letters and numbers.)
3. Select a region, performance and redundancy.

![](https://github.com/sysadminrepo/Procedures/blob/main/Cloud%20Services/Microsoft%20Azure/Assets/3-enter_infos.png)

## Advanced tab
1. By default, secure transfer and storage account key access are enabled. The minimum TLS version is 1.2 and copy operations are permitted from any storage account.

![](https://github.com/sysadminrepo/Procedures/blob/main/Cloud%20Services/Microsoft%20Azure/Assets/4-advanced_tab1.png)

2. Under Blob storage, select Access tier (Hot or Cool)

![](https://github.com/sysadminrepo/Procedures/blob/main/Cloud%20Services/Microsoft%20Azure/Assets/5-advanced_tab_blobcooltier.png)

3. For a blob storage which will be mounted on a local machine with NFSv3 protocol, enable hierarchical namespace and NFSv3

![](https://github.com/sysadminrepo/Procedures/blob/main/Cloud%20Services/Microsoft%20Azure/Assets/6-advanced_tab_nfsv3.png)

## Networking tab
1. By default, Enable public access from all network is selected.

![](https://github.com/sysadminrepo/Procedures/blob/main/Cloud%20Services/Microsoft%20Azure/Assets/7-Screenshot%20from%202024-04-05%2010-58-36.png)

2. If you have enabled NFSv3, the connectivity method must be set to "public endpoint (selected networks)" or "private endpoint":

2.1 Select Enable public access from selected virtual networks and IP addresses
2.2 Select a virtual network in the drop down menu

![](https://github.com/sysadminrepo/Procedures/blob/main/Cloud%20Services/Microsoft%20Azure/Assets/8-Screenshot-from-2024-04-05%2011-35-56.png)

2.3 If none created yet, click on Create virtual network under the drop down menu
2.4 Enter a name
2.5 Select default address space and subnets
2.6 Click OK

![](https://github.com/sysadminrepo/Procedures/blob/main/Cloud%20Services/Microsoft%20Azure/Assets/9-create-virtual-network.png)

##Review + Create
Review the settings
Click Create
