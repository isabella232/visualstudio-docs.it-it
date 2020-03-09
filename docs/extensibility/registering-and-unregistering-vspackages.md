---
title: Registrazione e annullamento della registrazione di pacchetti VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 701700ba9d5c6db1e5858a2419e1b2c0fa950ae5
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409144"
---
# <a name="register-and-unregister-vspackages"></a>Registrare e annullare la registrazione di pacchetti VSPackage
Usare gli attributi per registrare un pacchetto VSPackage, ma

## <a name="register-a-vspackage"></a>Registrare un pacchetto VSPackage
 È possibile usare gli attributi per controllare la registrazione dei pacchetti VSPackage gestiti. Tutte le informazioni di registrazione sono contenute in un file con *estensione pkgdef* . Per ulteriori informazioni sulla registrazione basata su file, vedere [CreatePkgDef Utility](../extensibility/internals/createpkgdef-utility.md).

 Il codice seguente illustra come usare gli attributi di registrazione standard per registrare il pacchetto VSPackage.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>Annullamento della registrazione di un'estensione
 Se si è verificato un numero elevato di VSPackage diversi e si desidera rimuoverli dall'istanza sperimentale, è possibile eseguire semplicemente il comando **Reset** . Cercare **Reimposta l'istanza sperimentale di Visual Studio** nella pagina iniziale del computer oppure eseguire questo comando dalla riga di comando:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 Se si desidera disinstallare un'estensione installata nell'istanza di sviluppo di Visual Studio, passare a **strumenti** > **estensioni e aggiornamenti**, trovare l'estensione e fare clic su **Disinstalla**.

 Se per qualche motivo nessuno di questi metodi riesce a disinstallare l'estensione, è possibile annullare la registrazione dell'assembly VSPackage dalla riga di comando nel modo seguente:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Usare un attributo di registrazione personalizzato per registrare un'estensione

In alcuni casi potrebbe essere necessario creare un nuovo attributo di registrazione per l'estensione. È possibile usare gli attributi di registrazione per aggiungere nuove chiavi del registro di sistema o per aggiungere nuovi valori alle chiavi esistenti. Il nuovo attributo deve derivare da <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>e deve eseguire l'override dei metodi <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> e <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A>.

### <a name="create-a-custom-attribute"></a>Creare un attributo personalizzato

Nel codice seguente viene illustrato come creare un nuovo attributo di registrazione.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 Il <xref:System.AttributeUsageAttribute> viene usato nelle classi Attribute per specificare l'elemento Program (classe, metodo e così via) a cui appartiene l'attributo, se può essere usato più di una volta e se può essere ereditato.

### <a name="create-a-registry-key"></a>Creare una chiave del registro di sistema

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

### <a name="create-a-new-value-under-an-existing-registry-key"></a>Crea un nuovo valore in una chiave del registro di sistema esistente

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
- [Pacchetti VSPackage](../extensibility/internals/vspackages.md)
