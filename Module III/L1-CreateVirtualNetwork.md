# Create a virtual network by using PowerShell

Original Article : [Click Here](https://azure.microsoft.com/en-us/documentation/articles/virtual-networks-create-vnet-arm-ps/)


####
```
New-AzureRmResourceGroup -Name TestRG -Location centralus
```
####
```
New-AzureRmVirtualNetwork -ResourceGroupName TestRG -Name TestVNet -AddressPrefix 192.168.0.0/16 -Location centralus
```
####
```
Get-AzureRmVirtualNetwork -ResourceGroupName TestRG -Name TestVNet
```
####
```
$vnet = Get-AzureRmVirtualNetwork -ResourceGroupName TestRG -Name TestVNet
```
####
```
Add-AzureRmVirtualNetworkSubnetConfig -Name FrontEnd -VirtualNetwork $vnet -AddressPrefix 192.168.1.0/24
```
####
```
Add-AzureRmVirtualNetworkSubnetConfig -Name BackEnd  -VirtualNetwork $vnet -AddressPrefix 192.168.2.0/24
```
####
```
Get-AzureRmVirtualNetwork -ResourceGroupName TestRG -Name TestVNet
```
####
```
Set-AzureRmVirtualNetwork -VirtualNetwork $vnet
```
####
```
Get-AzureRmVirtualNetwork -ResourceGroupName TestRG -Name TestVNet
```
####
```
Remove-AzureRmVirtualNetwork -ResourceGroupName TestRG -Name TestVNet -Verbose -Debug
```
