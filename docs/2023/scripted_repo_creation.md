---
author: Joe Parker
date: 2023/2/27
---

# Creating Local Repository <br> Using PowerShell

---

There are various scenarios where one might want to quickly generate a local repository of Lenovo updates that can be consumed by Thin Installer or System Update in a scripted manner.  This article will describe a PowerShell script that can be leveraged to create a repository for a specified machine type and OS. A couple of scenarios where this script might be used will also be described.

The script, Get-LnvUpdatesRepo.ps1, can be found in the CDRT Library repository on GitHub [here](https://github.com/CDRT/Library).

## Scenario 1

In the first scenario, Thin Installer will be leveraged in an OS deployment task sequence to apply any applicable updates available for the machine type of the targeted system. For this approach, a PowerShell script will be executed in the task sequence to control creation of the repository for the first time which can be skipped if the repository already exists. Each machine type will have its own repository folder in this scenario.

The script used in the task sequence will be as follows:

```powershell

#script goes
#here

```

The task sequence item will be defined as follows:


### Summary

With this scenario, the repository folders for the models being deployed can be created outside of the task sequence and can be recreated on a regular basis to ensure the latest content is included. Then as each device is imaged, the Thin Installer task can apply the applicable updates to ensure the final device is current.

If BIOS and firmware updates are included which will force a reboot (reboot type 1) or force a delayed reboot (reboot type 5) then the task sequence will be interrupted. Therefore, it would be best in a task sequence scenario to exclude packages of these reboot types. This can done by using the parameter "-includerebootpackages 3" in the Thin Installer command.

