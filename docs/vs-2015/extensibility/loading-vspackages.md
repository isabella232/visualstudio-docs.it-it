---
title: Caricamento dei pacchetti VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e20caff476e116ad59430692719bdbbe22c4914c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839632"
---
# <a name="loading-vspackages"></a>Caricamento di pacchetti VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I pacchetti VSPackage vengono caricati in Visual Studio solo quando sono necessarie le relative funzionalità. Ad esempio, un pacchetto VSPackage viene caricato quando Visual Studio usa una factory del progetto o un servizio implementato dal pacchetto VSPackage. Questa funzionalità è denominata caricamento ritardato, che viene usato quando possibile per migliorare le prestazioni.  
  
> [!NOTE]
> Visual Studio è in grado di determinare determinate informazioni VSPackage, ad esempio i comandi offerti da un pacchetto VSPackage, senza caricare il pacchetto VSPackage.  
  
 I pacchetti VSPackage possono essere impostati per l'autoload in un particolare contesto dell'interfaccia utente, ad esempio quando una soluzione è aperta. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>Questo contesto viene impostato dall'attributo.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>Caricamento di un pacchetto VSPackage in un contesto specifico  
  
- Aggiungere l' `ProvideAutoLoad` attributo agli attributi VSPackage:  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     Vedere i campi enumerati di <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> per un elenco dei contesti dell'interfaccia utente e i relativi valori GUID.  
  
- Impostare un punto di interruzione nel <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo.  
  
- Compilare il pacchetto VSPackage e avviare il debug.  
  
- Caricare una soluzione o crearne una.  
  
     Il pacchetto VSPackage viene caricato e arrestato in corrispondenza del punto di interruzione.  
  
## <a name="forcing-a-vspackage-to-load"></a>Forzare il caricamento di un pacchetto VSPackage  
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
  
     Impossibile utilizzare il caricamento forzato per la comunicazione VSPackage. Utilizzare [e fornire i servizi](../extensibility/using-and-providing-services.md) .  
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>Uso di un attributo personalizzato per registrare un pacchetto VSPackage  
 In alcuni casi potrebbe essere necessario creare un nuovo attributo di registrazione per l'estensione. È possibile usare gli attributi di registrazione per aggiungere nuove chiavi del registro di sistema o per aggiungere nuovi valori alle chiavi esistenti. Il nuovo attributo deve derivare da <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> ed è necessario eseguire l'override dei <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> metodi e.  
  
## <a name="creating-a-registry-key"></a>Creazione di una chiave del registro di sistema  
 Nel codice seguente, l'attributo custom crea una sottochiave **personalizzata** sotto la chiave per il pacchetto VSPackage registrato.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
  
```  
  
## <a name="creating-a-new-value-under-an-existing-registry-key"></a>Creazione di un nuovo valore in una chiave del registro di sistema esistente  
 È possibile aggiungere valori personalizzati a una chiave esistente. Il codice seguente illustra come aggiungere un nuovo valore a una chiave di registrazione VSPackage.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPackages](../extensibility/internals/vspackages.md)
