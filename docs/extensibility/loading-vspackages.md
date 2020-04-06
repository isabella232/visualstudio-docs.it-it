---
title: Caricamento di pacchetti VSPackage . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1c221bf06ef3b7e37e2afc1856f3e54fe5ad95e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702957"
---
# <a name="load-vspackages"></a>Caricare VSPackage
I package VS vengono caricati in Visual Studio solo quando è richiesta la relativa funzionalità. Ad esempio, un pacchetto VSPackage viene caricato quando Visual Studio utilizza una factory del progetto o un servizio che implementa il pacchetto VSPackage.For example, a VSPackage is loaded when Visual Studio uses a project factory or a service that the VSPackage implements. Questa funzionalità è denominata caricamento ritardato, che viene utilizzato quando possibile per migliorare le prestazioni.

> [!NOTE]
> Visual Studio visual E Visual Studio può determinare alcune informazioni VSPackage, ad esempio i comandi che offre un VSPackage, senza caricare il pacchetto VSPackage.

 VSPackage possono essere impostati per il caricamento automatico in un particolare contesto dell'interfaccia utente (UI), ad esempio, quando una soluzione è aperta. L'attributo <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> imposta questo contesto.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>Caricamento automatico di un pacchetto VSPackage in un contesto specificoAutoload a VSPackage in a specific context

- Aggiungere `ProvideAutoLoad` l'attributo agli attributi VSPackage:Add the attribute to the VSPackage attributes:

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     Vedere i campi <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> enumerati di per un elenco dei contesti dell'interfaccia utente e dei relativi valori GUID.

- Impostare un <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> punto di interruzione nel metodo .

- Compilare il pacchetto VSPackage e avviare il debug.

- Caricare una soluzione o crearne una.

     Il pacchetto VSPackage carica e si arresta in corrispondenza del punto di interruzione.

## <a name="force-a-vspackage-to-load"></a>Forzare il caricamento di un pacchetto VSPackage
 In alcune circostanze un VSPackage potrebbe essere necessario forzare un altro VSPackage da caricare. Ad esempio, un VSPackage leggero potrebbe caricare un VSPackage più grande in un contesto che non è disponibile come CMDUIContext.For example, a lightweight VSPackage might load a larger VSPackage in a context that is not available as a CMDUIContext.

 È possibile <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> utilizzare il metodo per forzare un VSPackage da caricare.

- Inserire questo codice <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> nel metodo del pacchetto VSPackage che forza il caricamento di un altro VSPackage:Insert this code into the method of the VSPackage that forces another VSPackage to load:

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     Quando il pacchetto VSPackage viene `PackageToBeLoaded` inizializzato, verrà forzata il caricamento.

     Il caricamento forzato non deve essere utilizzato per la comunicazione VSPackage.Force loading should not be used for VSPackage communication. Utilizzare [e fornire](../extensibility/using-and-providing-services.md) servizi invece.

## <a name="see-also"></a>Vedere anche
- [Pacchetti VSPackage](../extensibility/internals/vspackages.md)
