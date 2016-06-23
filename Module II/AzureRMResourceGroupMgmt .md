
* Creation of Empty Azure Resource group
* Creation of Empty Azure Resource group with tags
* Cleaning Tags from Azure Resource group
* Updating Tags for Azure Resource group


##### To create a new resource group, provide a name and location for your resource group.
```
New-AzureRmResourceGroup -Name FTResourceGroup -Location "West US"

Output :
ResourceGroupName : FTResourceGroup
Location          : westus
ProvisioningState : Succeeded
Tags              :
ResourceId        : /subscriptions/6b6a59a6-e367-4913-bea7-34b6862095bf/resourceGroups/FTResourceGroup
```

##### To create a new resource group, provide a name and location for your resource group with Tag .
This command creates a new empty resource group. This command  assigns tags to the resource group. The first tag, named "Empty," could be used to identify resource groups that have no resources.
The second tag is named "Department" and has a value of "IT". You can use a tag like this one to categorize resource groups for administration or budgeting.
```
New-AzureRmResourceGroup -Location "West US" -Name FTResourceGroupTagged -Tag @{Name="Empty"}, @{Name="Department";Value="IT"} -Verbose -Debug

Output :

ResourceGroupName : FTResourceGroupTagged
Location          : westus
ProvisioningState : Succeeded
Tags              :
                    Name        Value
                    ==========  =====
                    Empty            
                    Department  IT   

ResourceId        : /subscriptions/6b6a59a6-e367-4913-bea7-34b6862095bf/resourceGroups/FTResourceGroupTagged
```

##### Get all tags of a resource group  
```
(Get-AzureRmResourceGroup -Name FTResourceGroupTagged).Tags

Output :

Name                           Value                                                                                                           
----                           -----                                                                                                                 
Value                                                                                                                                                
Name                           Empty                                                                                                                 
Value                          IT                                                                                                                    
Name                           Department  
```

##### This command deletes all tags from the resource group. It uses the Tag parameter with an empty hash table value.
```
Set-AzureRmResourceGroup -Name FTResourceGroupTagged -Tag @{}

Output :

ResourceGroupName : FTResourceGroupTagged
Location          : westus
ProvisioningState : Succeeded
Tags              :
ResourceId        : /subscriptions/6b6a59a6-e367-4913-bea7-34b6862095bf/resourceGroups/FTResourceGroupTagged

```

##### Apply a tag to a resource group   
```
Set-AzureRmResourceGroup -Name FTResourceGroupTagged -Tag @{Name="Department";Value="IT"}

output :
ResourceGroupName : FTResourceGroupTagged
Location          : westus
ProvisioningState : Succeeded
Tags              :
                    Name        Value
                    ==========  =====
                    Department  IT   

ResourceId        : /subscriptions/6b6a59a6-e367-4913-bea7-34b6862095bf/resourceGroups/FTResourceGroupTagged
```

##### Add tags to a resource group  
```
$tags = (Get-AzureRmResourceGroup -Name FTResourceGroupTagged).Tags
$tags += @{Name="Status";Value="Approved"}
Set-AzureRmResourceGroup -Name FTResourceGroupTagged -Tag $tags

Output :
ResourceGroupName : FTResourceGroupTagged
Location          : westus
ProvisioningState : Succeeded
Tags              :
                    Name        Value   
                    ==========  ========
                    Department  IT      
                    Status      Approved

ResourceId        : /subscriptions/6b6a59a6-e367-4913-bea7-34b6862095bf/resourceGroups/FTResourceGroupTagged
```
##### Remove a resource group  
```
Remove-AzureRmResourceGroup -Name FTResourceGroupTagged -verbose
```
##### Caution : DON'T USE THIS - Remove all resource groups  
```
Get-AzureRmResourceGroup | Remove-AzureRmResourceGroup -Verbose
```
