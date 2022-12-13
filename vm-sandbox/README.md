# Accessing the Unreal Sandbox Environment for Store Visualization

- [Accessing the Unreal Sandbox Environment for Store Visualization](#accessing-the-unreal-sandbox-environment-for-store-visualization)
  - [Requirements](#requirements)
  - [Useful commands](#useful-commands)
  - [Accessing the Sandbox VM](#accessing-the-sandbox-vm)
  - [Using the Sandbox VM](#using-the-sandbox-vm)

## Requirements

* Azure cli which you can install from [here](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)
* Access to the resource group `unibremen-sandbox-infrastructure` inside the `uhbiai` subscription

## Useful commands

```Bash

# login to azure account
az login

# start the virtual machine
az vm start --resource-group unibremen-sandbox-infrastructure --name k4r-sandbox-vm

# stop the virtual machine
az vm stop --resource-group unibremen-sandbox-infrastructure --name k4r-sandbox-vm

# list ip addresses to connect to the virtual machine
az vm list-ip-addresses --resource-group unibremen-sandbox-infrastructure --name k4r-sandbox-vm

# restart the virtual machine
az vm restart --resource-group unibremen-sandbox-infrastructure --name k4r-sandbox-vm

# activate the Nvidia Gpu Driver Extension
az vm extension set \
 --resource-group unibremen-sandbox-infrastructure \
 --vm-name k4r-sandbox-vm --name NvidiaGpuDriverWindows \
 --publisher Microsoft.HpcCompute \
 --version 1.4 \
 --settings '{}'
```

## Accessing the Sandbox VM

after starting the virtual machine, you can connect to it via the public ip address you can get from the command above.
Then you can rdp to the virtual machine with `windows remote desktop` application.

username: `k4r`

password: You get this via a separate mail/instruction.

## Using the Sandbox VM

Using remote desktop you can access the sandbox vm as any other windows machine.

__Important__ You must shutdown the virtual machine as soon as you are done with it.
