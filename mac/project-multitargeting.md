---
title: Progetti multitargeting
description: Questo documento fornisce una panoramica su come configurare progetti con più target in Visual Studio per Mac.This document provides an overview of how to setup multi-targeted projects in Visual Studio for Mac.
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 12/12/2019
ms.assetid: 2a561af4-f1fe-493e-9a53-aa6d77d15498
ms.openlocfilehash: 3d1372ab5bd08ce164352293ec9d341ca567e3d5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451440"
---
# <a name="projects-with-multiple-target-frameworks"></a>Progetti con più framework di destinazioneProjects with multiple target frameworks
In Visual Studio per Mac è possibile configurare un progetto Xamarin o .NET Core per l'esecuzione in una delle diverse versioni di .NET Framework e in una delle diverse piattaforme di sistema. Ad esempio, è possibile scegliere come destinazione un progetto per l'esecuzione sia in .NET Framework 4.6 che in .NET Core 3.1.For example, you could target a project to run on both .NET Framework 4.6 and .NET Core 3.1. 

Per altre informazioni sui framework di destinazione, vedere [Framework di destinazione](/dotnet/standard/frameworks).

> [!NOTE] 
> Questo argomento si applica a Visual Studio per Mac. Per Visual Studio in Windows, vedere [Panoramica della destinazione Framework](/visualstudio/ide/visual-studio-multi-targeting-overview).

## <a name="targeting-multiple-frameworks"></a>Targeting di più frameworkTargeting multiple frameworks

I framework di destinazione vengono specificati nel file di progetto, che è possibile modificare facendo clic con il pulsante destro del mouse sul progetto e scegliendo il comando **Strumenti > Modifica file.** Quando viene specificato un singolo framework di destinazione, usare l'elemento TargetFramework. Il file di progetto dell'app console seguente illustra come scegliere come destinazione .NET Core 3.0 come destinazione:The following console app project file demonstrates how to target .NET Core 3.0:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Usare l'elemento TargetFrameworks plurale con più framework di destinazione:Use the plural TargetFrameworks element with multiple target frameworks:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>
```

Ulteriori informazioni su come [impostare come destinazione più framework](/dotnet/standard/frameworks#how-to-specify-target-frameworks).

## <a name="working-with-code-in-a-multi-target-project"></a>Utilizzo del codice in un progetto con più destinazioneWorking with code in a multi-target project
Quando si sta modificando un file di C , in un progetto con più framework di destinazione, è possibile specificare il framework di destinazione che si desidera utilizzare per guidare l'esperienza dell'editor (ad esempio, mostrando avvisi se si utilizza un'API non supportata da tale framework). È possibile modificare il framework di destinazione utilizzando il selettore **Framework** di destinazione nell'angolo superiore sinistro della finestra dell'editor.

![Utilizzo del selettore del framework di destinazione per modificare il framework di destinazione, che si trova nella parte superiore della finestra dell'editorUsing the target framework selector to change the target framework, located in the top of the editor window](media/project-multitargeting-framework-selector.png)

A volte è necessario chiamare API diverse a seconda della piattaforma di destinazione dell'applicazione. A tale scopo, è possibile scrivere codice condizionale per compilare il codice per una piattaforma specifica:To do this, you can write conditional code to compile code for a specific platform:

```C#
public class MyClass
{
    static void Main()
    {
#if NET40
        Console.WriteLine("Target framework: .NET Framework 4.0");
#elif NET45  
        Console.WriteLine("Target framework: .NET Framework 4.5");
#else
        Console.WriteLine("Target framework: .NET Standard 1.4");
#endif
    }
}
```

Quando si scrive il codice, verranno visualizzati avvisi nei suggerimenti di completamento automatico IntelliSense, che consentono di sapere se mancano API specifiche per uno dei framework di destinazione supportati dall'applicazione.

![Un messaggio di avviso visualizzato in IntelliSense, un'API non funzionerà per un framework di destinazione specificato. Testo di esempio: spazio dei nomi System.Buffers, SharedUtils (netstandard2.0) - Non disponibile. È possibile utilizzare la barra di spostamento per cambiare contesto.](media/project-multitargeting-intellisense-warnings.png)

## <a name="see-also"></a>Vedere anche

- [Panoramica del targeting per framework (Windows)Framework targeting overview (Windows)](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [Framework di destinazione nei progetti in stile SDKTarget frameworks in SDK-style projects](/dotnet/standard/frameworks#how-to-specify-target-frameworks)
