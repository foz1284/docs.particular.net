---
title: Licensing ServiceControl
reviewed: 2018-10-10
tags:
 - license
---

There are a few options to add a license to ServiceControl.

include: registry-licensing

## ServiceControl Management app

ServiceControl has a license user interface which can be accessed in ServiceControl Management. ServiceControl Management is installed together with ServiceControl and can be found in the Windows Start Menu.

The designated license file will be imported into the registry. The license file is added to the `HKEY_LOCAL_MACHINE` registry hive so it is available to all instances of ServiceControl regardless of the service account used.

![](managementutil-addlicense.png 'width=500')


## ServiceControl PowerShell

To import a license using PowerShell:

 * Start PowerShell from the start menu, ensure [ServiceControl Powershell Module](/servicecontrol/powershell.md) is loaded
 * Execute the following cmdlet with the path to the license file.

```ps
Import-ServiceControlLicense <LicenseFile>
```

## Using other platform tools

See the [ServiceInsight licensing page](/serviceinsight/license.md) or the [instructions for licensing manually using the registry](/nservicebus/licensing/?version=core_6#license-management-using-the-registry) for more information.

## Instance licensing

In Versions 1.17 and below, a license can be applied to an individual instance rather than using a license installed in the registry. To do this, copy the `license.xml` file to a `license` directory under the installation path of the instance.

NOTE: Instance Licensing is deprecated in Version 1.18 and above. Use ServiceControl Management or the ServiceControl PowerShell module to install the license file to the registry.

## Troubleshooting

### ServiceControl license was updated, but ServicePulse reports the license has expired

License information is read at service startup and cached. Once a new license is applied the ServiceControl instance must be restarted to detect the license change, until then the license status shown in ServicePulse is based on the cached state.