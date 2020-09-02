---
title: Progetti multitargeting
description: In questo documento viene fornita una panoramica su come configurare progetti multitargeting in Visual Studio per Mac.
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 12/12/2019
ms.assetid: 2a561af4-f1fe-493e-9a53-aa6d77d15498
ms.openlocfilehash: 3d1372ab5bd08ce164352293ec9d341ca567e3d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75451440"
---
# <a name="projects-with-multiple-target-frameworks"></a>Progetti con più framework di destinazione
In Visual Studio per Mac, è possibile configurare un progetto Novell o .NET Core per l'esecuzione in una delle diverse versioni del .NET Framework e in una qualsiasi delle diverse piattaforme di sistema. È ad esempio possibile fare riferimento a un progetto da eseguire sia in .NET Framework 4,6 che in .NET Core 3,1. 

Per altre informazioni sui framework di destinazione, vedere [Framework di destinazione](/dotnet/standard/frameworks).

> [!NOTE] 
> Questo argomento si applica a Visual Studio per Mac. Per Visual Studio in Windows, vedere [Panoramica della destinazione del Framework](/visualstudio/ide/visual-studio-multi-targeting-overview).

## <a name="targeting-multiple-frameworks"></a>Selezione di più Framework come destinazione

I Framework di destinazione vengono specificati nel file di progetto, che è possibile modificare facendo clic con il pulsante destro del mouse sul progetto e scegliendo il comando **strumenti > modifica file** . Quando viene specificato un singolo framework di destinazione, usare l'elemento TargetFramework. Il file di progetto di app console seguente illustra come definire come destinazione .NET Core 3,0:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Usare l'elemento plural TargetFrameworks con più framework di destinazione:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>
```

Altre informazioni su come definire la [destinazione per più Framework](/dotnet/standard/frameworks#how-to-specify-target-frameworks).

## <a name="working-with-code-in-a-multi-target-project"></a>Utilizzo del codice in un progetto con più destinazioni
Quando si modifica un file C# in un progetto con più framework di destinazione, è possibile specificare il Framework di destinazione che si vuole usare per guidare l'esperienza dell'editor (ad esempio, mostrando gli avvisi se si usa un'API non supportata da tale Framework). È possibile modificare il Framework di destinazione usando il selettore del **Framework di destinazione** nell'angolo superiore sinistro della finestra dell'editor.

![Uso del selettore del Framework di destinazione per modificare il Framework di destinazione, situato nella parte superiore della finestra dell'editor](media/project-multitargeting-framework-selector.png)

In alcuni casi è necessario chiamare API diverse a seconda della piattaforma di destinazione dell'applicazione. A tale scopo, è possibile scrivere codice condizionale per compilare il codice per una piattaforma specifica:

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

Quando si scrive il codice, verranno visualizzati avvisi nei suggerimenti per il completamento automatico di IntelliSense, in cui è possibile sapere se mancano API specifiche per i Framework di destinazione supportati dall'applicazione.

![Un messaggio di avviso visualizzato in IntelliSense, un'API non funzionerà per un Framework di destinazione specificato. Testo di esempio: spazio dei nomi System. buffers, SharedUtils (netstandard 2.0)-non disponibile. Per cambiare contesto, è possibile usare la barra di spostamento.](media/project-multitargeting-intellisense-warnings.png)

## <a name="see-also"></a>Vedere anche

- [Cenni preliminari sul Framework targeting (Windows)](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [Framework di destinazione nei progetti di tipo SDK](/dotnet/standard/frameworks#how-to-specify-target-frameworks)
