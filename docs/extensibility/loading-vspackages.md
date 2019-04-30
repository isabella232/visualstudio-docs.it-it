---
title: Caricamento di pacchetti VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 92d6605f85aff7cd99abd4046999f484332a2faa
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431334"
---
# <a name="load-vspackages"></a>Caricare i pacchetti VSPackage
I pacchetti VSPackage vengono caricati in Visual Studio solo quando è richiesta la funzionalità. Ad esempio, un pacchetto VSPackage viene caricato quando Visual Studio Usa un servizio che implementa il pacchetto VSPackage o una factory progetto. Questa funzionalità è denominata il caricamento ritardato, che viene usato ogni volta che è possibile migliorare le prestazioni.

> [!NOTE]
> Visual Studio può determinare determinate informazioni VSPackage, ad esempio i comandi che offre un pacchetto VSPackage, senza caricare il pacchetto VSPackage.

 I pacchetti VSPackage impostabili per caricare automaticamente in un contesto dell'interfaccia utente specifico, ad esempio, quando è aperta una soluzione. Il <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> questo contesto viene impostato dall'attributo.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>Caricare automaticamente un VSPackage in un contesto specifico

- Aggiungere il `ProvideAutoLoad` gli attributi di VSPackage dell'attributo:

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     Visualizzare i campi enumerati di <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> per un elenco di contesti dell'interfaccia utente e i relativi valori GUID.

- Impostare un punto di interruzione il <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> (metodo).

- Compilare il pacchetto VSPackage e avviare il debug.

- Caricare una soluzione oppure crearne uno.

     Il pacchetto VSPackage viene caricato e si arresta in corrispondenza del punto di interruzione.

## <a name="force-a-vspackage-to-load"></a>Forzare un pacchetto VSPackage da caricare
 In alcune circostanze un pacchetto VSPackage potrebbe essere necessario forzare un altro VSPackage da caricare. Ad esempio, un pacchetto VSPackage leggero potrebbe caricare un pacchetto VSPackage di dimensioni maggiori in un contesto che non è disponibile come un CMDUIContext.

 È possibile usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> metodo per forzare un pacchetto VSPackage da caricare.

- Inserire questo codice nel <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo del pacchetto VSPackage che forza un altro VSPackage da caricare:

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     Quando viene inizializzato il pacchetto VSPackage, forzerà `PackageToBeLoaded` da caricare.

     Il caricamento force non deve essere utilizzato per la comunicazione di VSPackage. Uso [usare e forniscono i servizi](../extensibility/using-and-providing-services.md) invece.

## <a name="see-also"></a>Vedere anche
- [Pacchetti VSPackage](../extensibility/internals/vspackages.md)
