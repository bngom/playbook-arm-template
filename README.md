# ARM Template playbook

Deploy an multi resource infrastructure on azure using azure ARM Templates:

- 2 Virtual Machines
- Virtual Networks
- Network Securiy Groups
- Network Interfaces
- Storage account

## Deploy your template using powershell

Connect to your account
```powershell
connect-azaccount
```

Get your subscription
```powershell
get-azsubscription
```

Select your subcription
```powershell
select-azsubscription <subscription-id>
```

Create a resource group
```powershell
new-azresourcegroup -name armtemplate -location westeurope
```



Check your deployment
```powershell
New-AzResourceGroupDeployment -name deploy -ResourceGroupName armtemplate -TemplateFile playbook.json -TemplateParameterFile playbook.parameters.json -whatif

...
 ]
      tags.displayName:         "mytestvm-vnet"
      type:                     "Microsoft.Network/virtualNetworks"

  + Microsoft.Storage/storageAccounts/mytestvmsa [2019-06-01]

      apiVersion:       "2019-06-01"
      id:               "/subscriptions/67630563-efe1-4f5b-bede-6775f812225d/resourceGroups/armtemplate/providers/Microsoft.Storage/storageAccounts/mytestvmsa"
      kind:             "Storage"
      location:         "westeurope"
      name:             "mytestvmsa"
      sku.name:         "Standard_LRS"
      tags.displayName: "mytestvmsa"
      type:             "Microsoft.Storage/storageAccounts"

  * Microsoft.Storage/storageAccounts/techbngomstorage
  * Microsoft.Storage/storageAccounts/techbngomstoragetest

Resource changes: 12 to create, 2 to ignore.
```

Deploy

```powershell
New-AzResourceGroupDeployment -name deploy -ResourceGroupName armtemplate -TemplateFile playbook.json -TemplateParameterFile playbook.parameters.json -verbose

...
DeploymentName          : deploy
ResourceGroupName       : armtemplate        
ProvisioningState       : Succeeded
Timestamp               : 27/01/2021 18:25:27
Mode                    : Incremental        
TemplateLink            :
Parameters              :
                          Name             Type                       Value
                          ===============  =========================  ==========
                          vMname           String                     mytestvm
                          oSusername       String                     uname
                          oSpassword       SecureString
                          vMcount          Int                        2
                          vMsize           String                     Standard_A2_v2
                          storageSKU       String                     Standard_LRS

Outputs                 :
DeploymentDebugLogLevel :

```



## Next 

Make it modular...
