---
title: Registrazione e annullamento della registrazione di VSPackage | Microsoft Docs
description: Informazioni sulla registrazione e l'annullamento della registrazione dei pacchetti VSPackage, inclusi gli attributi in uso e il file con estensione pkgdef.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0f3f0182ee7cb696fea33aa41df076f6579e7db948b7f6113fc46d419f53989f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121237852"
---
# <a name="register-and-unregister-vspackages"></a>Registrare e annullare la registrazione di VSPackage
Gli attributi vengono utilizzati per registrare un vspackage, ma

## <a name="register-a-vspackage"></a>Registrare un VSPackage
 È possibile usare gli attributi per controllare la registrazione di VSPackage gestiti. Tutte le informazioni di registrazione sono contenute in un file *con estensione pkgdef.* Per altre informazioni sulla registrazione basata su file, vedere [Utilità CreatePkgDef](../extensibility/internals/createpkgdef-utility.md).

 Il codice seguente illustra come usare gli attributi di registrazione standard per registrare il pacchetto VSPackage.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>Annullamento della registrazione di un'estensione
 Se sono stati sperimentando molti VSPackage diversi e si vuole rimuoverli dall'istanza sperimentale, è sufficiente eseguire il **comando Reimposta.** Cercare Reset **the Visual Studio Experimental Instance** (Reimposta istanza sperimentale) nella pagina iniziale del computer oppure eseguire questo comando dalla riga di comando:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 Se si vuole disinstallare un'estensione installata nell'istanza di sviluppo di Visual Studio, passare a Estensioni e aggiornamenti degli strumenti, trovare l'estensione e fare clic  >  su **Disinstalla**.

 Se per qualche motivo nessuno di questi metodi riesce a disinstallare l'estensione, è possibile annullare la registrazione dell'assembly VSPackage dalla riga di comando come segue:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Usare un attributo di registrazione personalizzato per registrare un'estensione

In alcuni casi potrebbe essere necessario creare un nuovo attributo di registrazione per l'estensione. È possibile usare gli attributi di registrazione per aggiungere nuove chiavi del Registro di sistema o per aggiungere nuovi valori alle chiavi esistenti. Il nuovo attributo deve derivare da <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> e deve eseguire l'override dei <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> metodi e <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> .

### <a name="create-a-custom-attribute"></a>Creare un attributo personalizzato

Il codice seguente illustra come creare un nuovo attributo di registrazione.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 Viene usato nelle classi di attributi per specificare l'elemento di programma (classe, metodo e così via) a cui si riferiscono l'attributo, se può essere usato più di una volta e se può essere <xref:System.AttributeUsageAttribute> ereditato.

### <a name="create-a-registry-key"></a>Creare una chiave del Registro di sistema

Nel codice seguente l'attributo personalizzato crea una **sottochiave Custom** sotto la chiave per il pacchetto VSPackage che viene registrato.

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

### <a name="create-a-new-value-under-an-existing-registry-key"></a>Creare un nuovo valore in una chiave del Registro di sistema esistente

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

## <a name="see-also"></a>Vedi anche
- [VSPackages](../extensibility/internals/vspackages.md)
