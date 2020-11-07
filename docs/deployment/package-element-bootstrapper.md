---
title: '&lt;Elemento del pacchetto &gt; (programma di avvio automatico) | Microsoft Docs'
description: L'elemento del pacchetto è l'elemento XML di primo livello all'interno di un file di pacchetto. L'elemento del pacchetto è obbligatorio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <package> element [bootstrapper]
ms.assetid: ecd06658-ad02-4440-bccd-88437b7fb816
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7645731cf5b955601541a122f2fdb3fa3d794cc3
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350738"
---
# <a name="ltpackagegt-element-bootstrapper"></a>&lt;Elemento del pacchetto &gt; (programma di avvio automatico)
L' `Package` elemento è l'elemento XML di primo livello all'interno di un file di pacchetto.

## <a name="syntax"></a>Sintassi

```xml
<Package
    Culture
    Name
    LicenseAgreement
>
    <InstallChecks>
        <AssemblyCheck
            Property
            Name
            PublicKeyToken
            Version
            Language
            ProcessorArchitecture
        />
        <RegistryCheck
            Property
            Key
            Value
        />
        <ExternalCheck
            PackageFile
            Property
            Arguments
            Log
        />
        <FileCheck
            Property
            FileName
            SearchPath
            SpecialFolder
            SearchDepth
        />
        <MsiProductCheck
            Property
            Product
            Feature
        />
        <RegistryFileCheck
            Property
            Key
            Value
            File
            SearchDepth
        />
    </InstallChecks>

    <Commands
        Reboot
    >
        <Command
            PackageFile
            Arguments
            EstimatedInstallSeconds
            EstimatedDiskBytes
            EstimatedTempBytes
            Log
        >
            <InstallConditions>
                <BypassIf
                    Property
                    Compare
                    Value
                    Schedule
                />
                <FailIf
                    Property
                    Compare
                    Value
                    String
                    Schedule
                />
            </InstallConditions>
            <ExitCodes>
                <ExitCode
                    Value
                    Result
                    String
                />
            </ExitCodes>
        </Command>
    </Commands>

    <PackageFiles
        CopyAllComponents
    >
        <PackageFile
            Name
            Path
            HomeSite
            PublicKey
        />
    </PackageFiles>

    <Strings>
        <String
            Name
        >
        </String>
    </Strings>

    <Schedules>
        <Schedule
            Name
        >
           <BuildList />
           <BeforePackage />
           <AfterPackage />
        </Schedule>
    </Schedules>
</Package>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 L' `Package` elemento è obbligatorio. Ha gli attributi seguenti.

| Attributo | Descrizione |
|--------------------| - |
| `Culture` | Obbligatorio. Definisce le impostazioni cultura per questo pacchetto, che determina il linguaggio da utilizzare. Questo attributo è una chiave dell' `Strings` elemento, che elenca le stringhe specifiche delle impostazioni cultura per i nomi dei prodotti e i messaggi di errore durante l'installazione. |
| `Name` | Obbligatorio. Nome del pacchetto visualizzato allo sviluppatore all'interno di uno strumento, ad esempio [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Questo attributo è una chiave nell' `Strings` elemento, che deve contenere un `String` elemento con le `Name` proprietà e `Culture` impostate in modo da corrispondere alle `Name` `Culture` proprietà e di `Package` . |
| `LicenseAgreement` | facoltativo. Specifica il nome del file nel pacchetto di distribuzione che contiene il contratto di licenza End-User (EULA).  Questo file può essere in formato testo normale (con *estensione txt* ) o RTF. ( *RTF* ) |

## <a name="example"></a>Esempio
 Nell'esempio di codice riportato di seguito viene illustrato un file di pacchetto completo per ridistribuire il .NET Framework 2,0.

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Package
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
  Name="DisplayName"
  Culture="Culture"
  LicenseAgreement="eula.rtf"
>

    <PackageFiles>
        <PackageFile Name="eula.rtf"/>
    </PackageFiles>

    <!-- Defines a localizable string table for error messages-->
    <Strings>
        <String Name="DisplayName">.NET Framework 2.0</String>
        <String Name="Culture">en</String>
        <String Name="AdminRequired">Administrator permissions are required to install the .NET Framework 2.0. Contact your administrator.</String>
        <String Name="InvalidPlatformWin9x">Installation of the .NET Framework 2.0 is not supported on Windows 95. Contact your application vendor.</String>
        <String Name="InvalidPlatformWinNT">Installation of the .NET Framework 2.0 is not supported on Windows NT 4.0. Contact your application vendor.</String>
        <String Name="InvalidPlatformIE">Installation of the .NET Framework 2.0 requires Internet Explorer 5.01 or greater. Contact your application vendor.</String>
        <String Name="InvalidPlatformArchitecture">This version of the .NET Framework 2.0 is not supported on a 64-bit operating system. Contact your application vendor.</String>
        <String Name="WindowsInstallerImproperInstall">Due to an error with Windows Installer, the installation of the .NET Framework 2.0 cannot proceed.</String>
        <String Name="AnotherInstanceRunning">Another instance of setup is already running. The running instance must complete before this setup can proceed.</String>
        <String Name="BetaNDPFailure">A beta version of the .NET Framework was detected on the computer. Uninstall any previous beta versions of .NET Framework before continuing.</String>
        <String Name="GeneralFailure">A failure occurred attempting to install the .NET Framework 2.0.</String>
        <String Name="DotNetFXExe">http://go.microsoft.com/fwlink/?LinkId=37283</String>
        <String Name="InstMsiAExe">http://go.microsoft.com/fwlink/?LinkId=37285</String>
        <String Name="Msi30Exe">http://go.microsoft.com/fwlink/?LinkId=37287</String>
    </Strings>

</Package>
```

## <a name="see-also"></a>Vedere anche
- [Riferimento allo schema del prodotto e del pacchetto](../deployment/product-and-package-schema-reference.md)