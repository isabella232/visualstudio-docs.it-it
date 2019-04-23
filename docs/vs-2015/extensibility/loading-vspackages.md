---
title: Caricamento di pacchetti VSPackage | Microsoft Docs
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
ms.openlocfilehash: 6c9de9c90840c01b37b99d813fbf23b7c2be3eea
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60066572"
---
# <a name="loading-vspackages"></a>Caricamento di pacchetti VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I pacchetti VSPackage vengono caricati in Visual Studio solo quando è richiesta la funzionalità. Ad esempio, un pacchetto VSPackage viene caricato quando Visual Studio Usa un servizio che implementa il pacchetto VSPackage o una factory progetto. Questa funzionalità è denominata il caricamento ritardato, che viene usato ogni volta che è possibile migliorare le prestazioni.  
  
> [!NOTE]
>  Visual Studio può determinare determinate informazioni VSPackage, ad esempio i comandi che offre un pacchetto VSPackage, senza caricare il pacchetto VSPackage.  
  
 I pacchetti VSPackage impostabili per caricare automaticamente in un contesto dell'interfaccia utente specifico, ad esempio, quando è aperta una soluzione. Il <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> questo contesto viene impostato dall'attributo.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>Caricamento automatico un pacchetto VSPackage in un contesto specifico  
  
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
  
## <a name="forcing-a-vspackage-to-load"></a>Utilizzo forzato di un pacchetto VSPackage da caricare  
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
  
     Il caricamento force non deve essere utilizzato per la comunicazione di VSPackage. Uso [sull'utilizzo e la fornitura di servizi](../extensibility/using-and-providing-services.md) invece.  
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>Uso di un attributo personalizzato per registrare un VSPackage  
 In alcuni casi potrebbe essere necessario creare un nuovo attributo di registrazione per l'estensione. È possibile usare gli attributi di registrazione per aggiungere nuove chiavi del Registro di sistema o per aggiungere nuovi valori per le chiavi esistenti. Il nuovo attributo deve derivare da <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, e deve eseguire l'override di <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> e <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> metodi.  
  
## <a name="creating-a-registry-key"></a>Creazione di una chiave del Registro di sistema  
 Nel codice seguente, l'attributo personalizzato viene creato un **personalizzato** sottochiave sotto la chiave per il pacchetto VSPackage in fase di registrazione.  
  
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
  
## <a name="creating-a-new-value-under-an-existing-registry-key"></a>Creazione di un nuovo valore in una chiave del Registro di sistema esistente  
 È possibile aggiungere i valori personalizzati a una chiave esistente. Il codice seguente viene illustrato come aggiungere un nuovo valore a una chiave di registrazione del pacchetto VSPackage.  
  
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
 [Pacchetti VSPackage](../extensibility/internals/vspackages.md)
