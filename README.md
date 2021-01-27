# ARM Template playbook

Deploy an multi resource infrastructure on azure using azure ARM Templates:

- 3 Virtual Machines
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

Deploy
```powershell
New-AzResourceGroupDeployment -name deploy -ResourceGroupName armtemplate -TemplateFile ./playbook.json -TemplateParameterFile .\playbook.parameters.json -verbose
```

## Next 

Make it modular...
