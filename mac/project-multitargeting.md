---
title: Progetti multitargeting
description: Questo documento offre una panoramica di come configurare progetti multi-target in Visual Studio per Mac.
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 12/12/2019
ms.assetid: 2a561af4-f1fe-493e-9a53-aa6d77d15498
ms.openlocfilehash: 3d1372ab5bd08ce164352293ec9d341ca567e3d5
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964589"
---
# <a name="projects-with-multiple-target-frameworks"></a>Progetti con più framework di destinazione
In Visual Studio per Mac è possibile configurare un progetto Xamarin o .NET Core per l'esecuzione in una delle diverse versioni del .NET Framework e in una qualsiasi delle diverse piattaforme di sistema. Ad esempio, è possibile impostare come destinazione un progetto per l'esecuzione in .NET Framework 4.6 e .NET Core 3.1. 

Per altre informazioni sui framework di destinazione, vedere [Framework di destinazione](/dotnet/standard/frameworks).

> [!NOTE] 
> Questo argomento si applica a Visual Studio per Mac. Per Visual Studio su Windows, vedere [Panoramica della destinazione del framework](/visualstudio/ide/visual-studio-multi-targeting-overview).

## <a name="targeting-multiple-frameworks"></a>Destinazione di più framework

I framework di destinazione vengono specificati nel file di progetto, che è possibile modificare facendo clic con il pulsante destro del mouse sul progetto e scegliendo strumenti > Comando Modifica **file.** Quando viene specificato un singolo framework di destinazione, usare l'elemento TargetFramework. Il file di progetto dell'app console seguente illustra come impostare come destinazione .NET Core 3.0:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Usare l'elemento TargetFrameworks plurale con più framework di destinazione:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>
```

Altre informazioni su come impostare [come destinazione più framework](/dotnet/standard/frameworks#how-to-specify-target-frameworks).

## <a name="working-with-code-in-a-multi-target-project"></a>Uso del codice in un progetto multi-destinazione
Quando si modifica un file C# in un progetto con più framework di destinazione, è possibile specificare il framework di destinazione da usare per guidare l'esperienza dell'editor, ad esempio visualizzando avvisi se si usa un'API non supportata da tale framework. È possibile modificare il framework di destinazione usando il **selettore Framework** di destinazione nell'angolo superiore sinistro della finestra dell'editor.

![Uso del selettore del framework di destinazione per modificare il framework di destinazione, che si trova nella parte superiore della finestra dell'editor](media/project-multitargeting-framework-selector.png)

A volte è necessario chiamare API diverse a seconda della piattaforma di destinazione dell'applicazione. A tale scopo, è possibile scrivere codice condizionale per compilare il codice per una piattaforma specifica:

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

Quando si scrive codice, verranno visualizzati avvisi nei suggerimenti di completamento automatico intelliSense, che informano se sono mancanti API specifiche per uno dei framework di destinazione supportati dall'applicazione.

![Un messaggio di avviso visualizzato in IntelliSense, un'API non funzionerà per un framework di destinazione specificato. Testo di esempio: spazio dei nomi System.Buffers, SharedUtils (netstandard2.0) - Non disponibile. È possibile usare la barra di spostamento per cambiare contesto.](media/project-multitargeting-intellisense-warnings.png)

## <a name="see-also"></a>Vedi anche

- [Panoramica della destinazione del framework (Windows)](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [Framework di destinazione nei progetti in stile SDK](/dotnet/standard/frameworks#how-to-specify-target-frameworks)
