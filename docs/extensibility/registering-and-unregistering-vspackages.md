---
title: Registrazione e annullamento della registrazione di VSPackage Documenti Microsoft
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303183"
---
# <a name="register-and-unregister-vspackages"></a>Registrare e annullare la registrazione di VSPackageRegister and unregister VSPackages
Utilizzare gli attributi per registrare un VSPackage, ma

## <a name="register-a-vspackage"></a>Registrare un pacchetto VSPackageRegister a VSPackage
 È possibile utilizzare gli attributi per controllare la registrazione dei pacchetti VSPackage gestiti. Tutte le informazioni di registrazione sono contenute in un file *.pkgdef.* Per ulteriori informazioni sulla registrazione basata su file, vedere [Utilità CreatePkgDef](../extensibility/internals/createpkgdef-utility.md).

 The following code shows how to use the standard registration attributes to register your VSPackage.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>Annullamento della registrazione di un'estensione
 Se si sta sperimentando con un sacco di diversi VSPackage e si desidera rimuoverli dall'istanza sperimentale, è sufficiente eseguire il comando **Reimposta.** Cercare **Reimposta l'istanza sperimentale** di Visual Studio nella pagina iniziale del computer oppure eseguire questo comando dalla riga di comando:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 Se si desidera disinstallare un'estensione installata nell'istanza di sviluppo di Visual Studio, passare a**Estensioni e aggiornamenti**degli **strumenti** > , individuare l'estensione e fare clic su **Disinstalla**.

 Se per qualche motivo nessuno di questi metodi riesce a disinstallare l'estensione, è possibile annullare la registrazione dell'assembly VSPackage dalla riga di comando come segue:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Utilizzare un attributo di registrazione personalizzato per registrare un'estensioneUse a custom registration attribute to register an extension

In alcuni casi potrebbe essere necessario creare un nuovo attributo di registrazione per l'estensione. È possibile utilizzare gli attributi di registrazione per aggiungere nuove chiavi del Registro di sistema o per aggiungere nuovi valori alle chiavi esistenti. Il nuovo attributo <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>deve derivare <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> da <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> , e deve eseguire l'override dei metodi e .

### <a name="create-a-custom-attribute"></a>Creare un attributo personalizzato

Nel codice seguente viene illustrato come creare un nuovo attributo di registrazione.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 L'oggetto <xref:System.AttributeUsageAttribute> viene utilizzato nelle classi di attributi per specificare l'elemento di programma (classe, metodo e così via) a cui si trova l'attributo, se può essere utilizzato più di una volta e se può essere ereditato.

### <a name="create-a-registry-key"></a>Creare una chiave del Registro di sistemaCreate a registry key

Nel codice seguente, l'attributo personalizzato crea una sottochiave **personalizzata** sotto la chiave per il pacchetto VSPackage che viene registrato.

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

### <a name="create-a-new-value-under-an-existing-registry-key"></a>Creare un nuovo valore in una chiave del Registro di sistema esistenteCreate a new value under an existing registry key

È possibile aggiungere valori personalizzati a una chiave esistente. Il codice seguente viene illustrato come aggiungere un nuovo valore a una chiave di registrazione VSPackage.The following code shows how to add a new value to a VSPackage registration key.

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
