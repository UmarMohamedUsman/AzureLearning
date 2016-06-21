# Connecting to Azure using Azure PowerShell

[ Microsoft Official Article ](https://azure.microsoft.com/en-us/documentation/articles/powershell-install-configure/)

To login to your AzureRM SubscriptionName
```
# To login to Azure Resource Manager
PS C:\> Login-AzureRmAccount

# You can also use a specific Tenant if you would like a faster login experience
# Login-AzureRmAccount -TenantId xxxx
```
To view your AzureRM SubscriptionName

```
# To view all subscriptions for your account
PS C:\> Get-AzureRmSubscription

# To select a default subscription for your current session
PS C:\> Get-AzureRmSubscription –SubscriptionName “your sub” | Select-AzureRmSubscription
```

To see Location that can be  under your subscriptions
```
Get-AzureRmLocation | select Location, DisplayName
```
To check the AzureRM Subscription Context
```
# View your current Azure PowerShell session context
# This session state is only applicable to the current session and will not affect other sessions
PS C:\> Get-AzureRmContext

Environment           : AzureCloud
Account               : abhanand@microsoft.com
TenantId              : 72f988bf-86f1-41af-91ab-2d7cd011db47
SubscriptionId        : 6b6a59a6-e367-4913-bea7-34b6862095bf
SubscriptionName      : Microsoft Azure Internal Consumption
CurrentStorageAccount :
```
Hint : [How to create a StorageAccount using PowerShell](https://github.com/abhishekanand/AzureLearning/blob/master/Module%20I/CreateStorageAccount.md)

```
# To select the default storage context for your current session
PS C:\> Set-AzureRmCurrentStorageAccount –ResourceGroupName “your resource group” –StorageAccountName “your storage account name”

# View your current Azure PowerShell session context
# Note: the CurrentStorageAccount is now set in your session context
PS C:\> Get-AzureRmContext

# To list all of the blobs in all of your containers in all of your accounts
PS C:\> Get-AzureRmStorageAccount | Get-AzureStorageContainer | Get-AzureStorageBlob
```

To check Available AzureRmResourceProvider
```
# To see Registered AzureRmResourceProvider
C:\> Get-AzureRmResourceProvider

# To see Available (Registered + NotRegistered) AzureRmResourceProvider
C:\> Get-AzureRmResourceProvider -ListAvailable
```
