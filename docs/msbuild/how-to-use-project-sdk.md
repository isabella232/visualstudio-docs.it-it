---
title: 'Procedura: Fare riferimento a un SDK di progetto MSBuild | Microsoft Docs'
ms.date: 01/25/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74ccc29417cdee7a9f93c39509c0f7d06a5c72ff
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "76826471"
---
# <a name="how-to-use-msbuild-project-sdks"></a>Procedura: Usare SDK di progetto MSBuild

MSBuild 15.0 ha introdotto il concetto di "SDK del progetto", che semplifica l'utilizzo di kit di sviluppo software che richiedono l'importazione di proprietà e destinazioni.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```

Durante la valutazione del progetto, MSBuild aggiunge importazioni implicite nella parte superiore e inferiore del file di progetto:

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

    Un'importazione implicita viene aggiunta nella parte superiore e inferiore del progetto come descritto in precedenza.
    
    Per specificare una versione specifica dell'SDK, aggiungerla all'attributo: `Sdk`

    ```xml
    <Project Sdk="My.Custom.Sdk/1.2.3">
        ...
    </Project>
    ```

    > [!NOTE]
    > Questo è al momento l'unico metodo supportato per fare riferimento a un progetto SDK in Visual Studio per Mac.

- Usare l'elemento di primo livello `<Sdk/>`:

    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```

   Un'importazione implicita viene aggiunta nella parte superiore e inferiore del progetto come descritto in precedenza.
   
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

Durante la valutazione dell'importazione, MSBuild risolve dinamicamente il percorso dell'SDK del progetto in base al nome e alla versione specificati.  MSBuild dispone inoltre di un elenco di resolver SDK registrati, ovvero plug-in che individuano gli SDK del progetto nel computer. Questi plug-in includono:

- Un resolver basato su NuGet che recupera i feed di pacchetto configurati per i pacchetti NuGet corrispondenti all'ID e alla versione dell'SDK specificati.

   Questo sistema di risoluzione è attivo solo se è stata specificata una versione facoltativa. Può essere utilizzato per qualsiasi SDK di progetto personalizzato.
   
- Un resolver dell'interfaccia della riga di comando .NET che risolve gli SDK installati con [l'interfaccia della riga](/dotnet/core/tools/)di comando di .NET.

   Questo sistema di risoluzione individua `Microsoft.NET.Sdk` `Microsoft.NET.Sdk.Web` gli SDK del progetto, ad esempio e che fanno parte del prodotto.
   
- Un resolver predefinito che risolve gli SDK che sono stati installati con MSBuild.

Il resolver SDK basato su NuGet supporta la specifica di una versione nel file [global.json,](/dotnet/core/tools/global-json) che consente di controllare la versione SDK del progetto in un'unica posizione anziché in ogni singolo progetto:

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

Durante una compilazione, è possibile usare una sola versione di ogni SDK di progetto. Se si fa riferimento a due versioni diverse dello stesso SDK del progetto, MSBuild genera un avviso. Si consiglia di **non** specificare una versione nei progetti se una versione è specificata nel file *global.json.*

## <a name="see-also"></a>Vedere anche

- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
- [Personalizzare la compilazione](../msbuild/customize-your-build.md)
- [Pacchetti, metapacchetti e framework](/dotnet/core/packages)
- [Aggiunte al formato csproj per .NET Core](/dotnet/core/tools/csproj)
