---
title: Caricamento di VSPackage | Microsoft Docs
description: Informazioni sul caricamento di VSPackage in Visual Studio, incluso il caricamento ritardato, che viene usato quando possibile per migliorare le prestazioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d56192fed9138e6edd8f18753893b195c174c5b9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122041724"
---
# <a name="load-vspackages"></a>Caricare VSPackage
I pacchetti VSPackage vengono caricati in Visual Studio solo quando è necessaria la relativa funzionalità. Ad esempio, un VSPackage viene caricato quando Visual Studio una factory di progetto o un servizio implementato da VSPackage. Questa funzionalità è detta caricamento ritardato, che viene usata quando possibile per migliorare le prestazioni.

> [!NOTE]
> Visual Studio determinare determinate informazioni vspackage, ad esempio i comandi offerte da un vspackage, senza caricare il pacchetto VSPackage.

 I pacchetti VSPackage possono essere impostati per il caricamento automatico in un particolare contesto dell'interfaccia utente, ad esempio quando una soluzione è aperta. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>L'attributo imposta questo contesto.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>Caricare automaticamente un VSPackage in un contesto specifico

- Aggiungere `ProvideAutoLoad` l'attributo agli attributi VSPackage:

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     Per un elenco dei contesti dell'interfaccia utente e dei relativi valori GUID, vedere i campi <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> enumerati di .

- Impostare un punto di interruzione nel <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo .

- Compilare il pacchetto VSPackage e avviare il debug.

- Caricare una soluzione o crearne una.

     Il pacchetto VSPackage viene caricato e arrestato in corrispondenza del punto di interruzione.

## <a name="force-a-vspackage-to-load"></a>Forzare il caricamento di un vspackage
 In alcuni casi potrebbe essere necessario forzare il caricamento di un altro VSPackage. Ad esempio, un pacchetto VSPackage leggero potrebbe caricare un VSPackage più grande in un contesto non disponibile come CMDUIContext.

 È possibile usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> metodo per forzare il caricamento di un vspackage.

- Inserire questo codice nel metodo del pacchetto VSPackage che forza <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> il caricamento di un altro VSPackage:

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     Quando il pacchetto VSPackage viene inizializzato, verrà forzato `PackageToBeLoaded` il caricamento.

     Il caricamento forzato non deve essere usato per la comunicazione VSPackage. Usare [e fornire servizi.](../extensibility/using-and-providing-services.md)

## <a name="see-also"></a>Vedi anche
- [VSPackages](../extensibility/internals/vspackages.md)
