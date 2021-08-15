---
title: Tutti gli strumenti
description: Esempio di uso di tutti gli strumenti devinit.
ms.date: 02/08/2021
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 32f8fee439bad53145e31d98f437df8805547220f79c459486288ccebb8e710b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121418019"
---
# <a name="all-tools"></a>Tutti gli strumenti

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è incentrata sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di Visual Studio di lavoro. Come parte di questo `devinit` e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community per sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Questo esempio include un oggetto `devinit.json` , che installa tutti gli strumenti devinit disponibili.

## <a name="devinitjson"></a>.devinit.json

```json
{
  "$schema": "./devinit.schema-6.0.json",
  "comments": "A sample dot-devinit file",
  "run": [
    {
      "tool": "azurecli-login",
      "comments": "Logs in to Azure Cli."
    },
    {
      "tool": "choco-install",
      "input": "kubernetes-cli",
      "additionalOptions": "--version 1.18.1",
      "comments": "Additional options are appended to the 'choco install' command line. In this case, we pass in the specific package version to install."
    },
    {
      "tool": "choco-upgrade",
      "input": "kubernetes-cli",
      "additionalOptions": "--version 1.18.2",
      "comments": "Additional options are appended to the 'choco upgrade' command line. In this case, we pass in the specific package version to install."
    },
    {
      "tool": "dotnet-restore",
      "input": "C:\\app1\\app1.csproj",
      "comments": "Restores the dependencies and tools of a project using .NET Core. Input can be used to provide .sln path or project file path."
    },
    {
      "tool": "dotnet-toolinstall",
      "input": "dotnet-ef",
      "additionalOptions": "--global",
      "comments": "Installs a .NET Core tool."
    },
    {
      "tool": "enable-iis",
      "comments": "Enables IIS features and installs the latest ASP.NET hosting bundle."
    },
    {
      "tool": "msi-install",
      "input": "https://www.7-zip.org/a/7z1900.msi",
      "comments": "Installs the 7-Zip MSI",
    },
    {
      "tool": "npm-install",
      "input": "some-package",
      "additionalOptions": "--some-additional-options",
      "comments": "Installs an NPM package"
    },
    {
      "tool": "nuget-restore",
      "comments": "Restores nuget packages to current directory 'Packages' folder. Input is optional and used for packages.config path.",
      "input": "C:\\packages.config"
    },
    {
      "tool": "require-azureartifactscredentialprovider",
      "comments": "Installs Azure Artifacts Credential Provider."
    },
    {
      "tool": "require-azurecli",
      "comments": "Always installs latest of Azure CLI for Windows."
    },
    {
      "tool": "require-choco",
      "input": "0.10.15"
    },
    {
      "tool": "require-dotnetcoresdk",
      "comments": "If input is null, the sdk version is from global.json if it exists; otherwise, current LTS version."
    },
    {
      "tool": "require-dotnetcoresdk",
      "input": "3.1.200",
      "comments": "Input specifies an explicit SDK version."
    },
    {
      "tool": "require-dotnetframeworksdk",
      "input": "4.8.0",
      "comments": "Input specifies an explicit SDK version."
    },
    {
      "tool": "require-mssql",
      "input": "install",
      "comments": "Installs MS SQL."
    },
    {
      "tool": "require-nodejs",
      "input": "12.16.3",
      "comments": "Installs Node.js."
    },
    {
      "tool": "require-npm",
      "input": "6.14.4",
      "comments": "Installs NPM."
    },
    {
      "tool": "require-nuget",
      "input": "5.5.1",
      "comments": "Installs NuGet for given input version. If no input given, then installs latest."
    },
    {
      "tool": "require-psmodule",
      "input": "PowerShellGet",
      "additionalOptions": "-Repository PSGallery",
      "comments": "Installs specified PS module mentioned in input from PSGallery, unless repository mentioned in additional options."
    },
    {
      "tool": "require-vcpkg",
      "comments": "Installs vcpkg."
    },
    {
      "tool": "require-vscomponent",
      "input": "C:\\.vsconfig",
      "comments": "Imports .vsconfig file which is passed as input to Visual Studio."
    },
    {
      "tool": "require-winget",
      "comments": "Installs winget",
    },
    {
      "tool": "set-env",
      "input": "Foo=Bar",
      "comments": "Set-env can set, display or delete individual variables and can display all variables."
    },
    {
      "tool": "vcpkg-install",
      "input": "some-package",
      "additionalOptions": "--some-additional-options",
      "comments": "Installs a package using vcpkg."
    },
    {
      "comments": "Enables the .NET Framework 3.5 feature.",
      "tool": "windowsfeature-enable",
      "input": "Microsoft-Windows-NetFx3-OC-Package"
    },
    {
      "comments": "Disables the IIS Asp.Net 4.5 feature.",
      "tool": "windowsfeature-disable",
      "input": "IIS-ASPNET45"
    },
    {
      "comments": "Lists the state of all Windows features.",
      "tool": "windowsfeature-list"
    },
    {
      "comments": "Installs the package defined in winget-manifest.yml.",
      "tool": "winget-install",
      "additionalOptions": "--manifest winget-manifest.yml"
    },
    {
      "tool": "wsl-install",
      "input": "https://aka.ms/wslubuntu2004",
      "additionalOptions": "--wsl-version 1 --post-create-command some-post-create-command",
      "comments": "Installs distro from target URL using Windows Subsystem for Linux."
    }
  ]
}
```

## <a name="devcontainerjson"></a>.devcontainer.jssu

Contenuto del _.devcontainer.jsnel_ file nella radice del repo.

```json
{
  "postCreateCommand": "devinit init"
}
```
