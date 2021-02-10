---
title: Caricamento dei pacchetti VSPackage | Microsoft Docs
description: Informazioni sul caricamento dei pacchetti VSPackage in Visual Studio, incluso il caricamento ritardato, che viene usato quando possibile per migliorare le prestazioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f87b5bcc94ed11e18de763bd1db7c59bdc4796fc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966383"
---
# <a name="load-vspackages"></a>Carica VSPackage
I pacchetti VSPackage vengono caricati in Visual Studio solo quando sono necessarie le relative funzionalità. Ad esempio, un pacchetto VSPackage viene caricato quando Visual Studio usa una factory del progetto o un servizio implementato dal pacchetto VSPackage. Questa funzionalità è denominata caricamento ritardato, che viene usato quando possibile per migliorare le prestazioni.

> [!NOTE]
> Visual Studio è in grado di determinare determinate informazioni VSPackage, ad esempio i comandi offerti da un pacchetto VSPackage, senza caricare il pacchetto VSPackage.

 I pacchetti VSPackage possono essere impostati per l'autoload in un particolare contesto dell'interfaccia utente, ad esempio quando una soluzione è aperta. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>Questo contesto viene impostato dall'attributo.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>Autoload di un VSPackage in un contesto specifico

- Aggiungere l' `ProvideAutoLoad` attributo agli attributi VSPackage:

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     Vedere i campi enumerati di <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> per un elenco dei contesti dell'interfaccia utente e i relativi valori GUID.

- Impostare un punto di interruzione nel <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo.

- Compilare il pacchetto VSPackage e avviare il debug.

- Caricare una soluzione o crearne una.

     Il pacchetto VSPackage viene caricato e arrestato in corrispondenza del punto di interruzione.

## <a name="force-a-vspackage-to-load"></a>Forzare il caricamento di un pacchetto VSPackage
 In alcune circostanze, un pacchetto VSPackage potrebbe dover forzare il caricamento di un altro pacchetto VSPackage. Ad esempio, un pacchetto VSPackage leggero potrebbe caricare un pacchetto VSPackage di dimensioni maggiori in un contesto non disponibile come CMDUIContext.

 È possibile usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> metodo per forzare il caricamento di un pacchetto VSPackage.

- Inserire questo codice nel <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo del pacchetto VSPackage che impone il caricamento di un altro pacchetto VSPackage:

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     Quando il pacchetto VSPackage viene inizializzato, il caricamento verrà forzato `PackageToBeLoaded` .

     Impossibile utilizzare il caricamento forzato per la comunicazione VSPackage. Usare invece [e fornire i servizi](../extensibility/using-and-providing-services.md) .

## <a name="see-also"></a>Vedi anche
- [VSPackages](../extensibility/internals/vspackages.md)
