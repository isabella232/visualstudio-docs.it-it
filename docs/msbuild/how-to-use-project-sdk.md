---
title: 'Procedura: Fare riferimento a un SDK di progetto MSBuild | Microsoft Docs'
description: Informazioni su come usare MSBuild SDK di progetto per semplificare l'uso di software development kit che richiedono l'importazione di proprietà e destinazioni.
ms.custom: SEO-VS-2020
ms.date: 01/25/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: b26c8704be6770954849a440f15683be68ce82aa
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625679"
---
# <a name="how-to-use-msbuild-project-sdks"></a>Procedura: Usare SDK di progetto MSBuild

MSBuild 15.0 ha introdotto il concetto di "SDK di progetto", che semplifica l'uso di software development kit che richiedono l'importazione di proprietà e destinazioni.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```

Durante la valutazione del progetto, MSBuild le importazioni implicite nella parte superiore e inferiore del file di progetto:

```xml
<Project>
    <!-- Implicit top import -->
    <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>

    <!-- Implicit bottom import -->
    <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

## <a name="reference-a-project-sdk"></a>Fare riferimento a un SDK di progetto

Esistono tre modi per fare riferimento a un SDK di progetto:

- Usare l'attributo `Sdk` per l'elemento `<Project/>`:

    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```

    Un'importazione implicita viene aggiunta all'inizio e alla fine del progetto, come descritto in precedenza.
    
    Per specificare una versione specifica dell'SDK, accodarla `Sdk` all'attributo :

    ```xml
    <Project Sdk="My.Custom.Sdk/1.2.3">
        ...
    </Project>
    ```

- Usare l'elemento di primo livello `<Sdk/>`:

    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```

   Un'importazione implicita viene aggiunta all'inizio e alla fine del progetto, come descritto in precedenza.
   
   L'attributo `Version` non è obbligatorio.

- Usare l'elemento `<Import/>` in un punto qualsiasi nel progetto:

    ```xml
    <Project>
        <PropertyGroup>
            <MyProperty>Value</MyProperty>
        </PropertyGroup>
        <Import Project="Sdk.props" Sdk="My.Custom.Sdk" />
        ...
        <Import Project="Sdk.targets" Sdk="My.Custom.Sdk" />
    </Project>
   ```

   L'inclusione esplicita delle importazioni nel progetto consente il controllo completo sull'ordine.

   Quando si usa l'elemento `<Import/>` è possibile specificare anche un attributo `Version` facoltativo. Ad esempio, è possibile specificare `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />`.

## <a name="how-project-sdks-are-resolved"></a>Come vengono risolti gli SDK di progetto

Quando si valuta l'importazione, MSBuild risolve dinamicamente il percorso dell'SDK del progetto in base al nome e alla versione specificati.  MSBuild include anche un elenco di resolver SDK registrati, che sono plug-in che individuano gli SDK di progetto nel computer. Questi plug-in includono:

- Un resolver basato su NuGet che recupera i feed di pacchetto configurati per i pacchetti NuGet corrispondenti all'ID e alla versione dell'SDK specificati.

   Questo sistema di risoluzione è attivo solo se è stata specificata una versione facoltativa. Può essere usato per qualsiasi SDK di progetto personalizzato.
   
- Resolver di .NET SDK che risolve MSBuild SDK installati con [.NET SDK.](/dotnet/core/sdk/)

   Questo sistema di risoluzione individua gli SDK del progetto, ad `Microsoft.NET.Sdk` esempio e che fanno parte del `Microsoft.NET.Sdk.Web` prodotto.
   
- Un resolver predefinito che risolve gli SDK che sono stati installati con MSBuild.

Il NuGet SDK basato su NuGet supporta la specifica di una versione nel file [global.json,](/dotnet/core/tools/global-json) che consente di controllare la versione dell'SDK del progetto in un'unica posizione anziché in ogni singolo progetto:

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

Durante una compilazione, è possibile usare una sola versione di ogni SDK di progetto. Se si fa riferimento a due versioni diverse dello stesso SDK del progetto, MSBuild genera un avviso. È consigliabile **non specificare** una versione nei progetti se viene specificata una versione nel file *global.json.*

## <a name="see-also"></a>Vedi anche

- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
- [Personalizzare la compilazione](../msbuild/customize-your-build.md)
- [Pacchetti, metapacchetti e framework](/dotnet/core/packages)
- [Aggiunte al formato csproj per .NET Core](/dotnet/core/tools/csproj)
