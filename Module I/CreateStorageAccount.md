
### Creating your First Storage Account

For this example  :
* Region : West US
* SkuName : Standard_GRS

#### Login To your Azure Account
```
# Run Login-AzureRmAccount to login
Login-AzureRmAccount
```
#### Create a Resource Group in the desired region
```
#To create a new resource group, provide a name and location for your resource group.
New-AzureRmResourceGroup -Name MyFirstStorageRG -Location "West US"
```
#### Verify existence of ResourceGruop
```
# Verify Existence of ResourceGruop
Get-AzureRmResourceGroup -Name MyFirstStorageRG
```
#### Create a New StorageAccount
Note : Storage account name must be between 3 and 24 characters in length and use numbers and lower-case letters only.
```
# Create a new stroage Account
New-AzureRmStorageAccount -ResourceGroupName "MyFirstStorageRG" -Name "mystorageaccountft" -Location "West US" -SkuName "Standard_GRS" -Kind "Storage" -Verbose
```
#### Verify creation of StorageAccount
```
# Verify creation of StorageAccount
Get-AzureRmStorageAccount -ResourceGroupName MyFirstStorageRG -Name mystorageaccountft
```
#### Delete Storage Account
```
# Delete Storage Account
Remove-AzureRmStorageAccount -ResourceGroupName MyFirstStorageRG -Name mystorageaccountft -Verbose
```
