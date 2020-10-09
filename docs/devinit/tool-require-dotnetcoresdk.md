---
title: require-dotnetcoresdk
description: per lo strumento devinit è necessario dotnetcoresdk.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 1a85268eb71ece1f06dc8d71d018d16206902130
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91860829"
---
# <a name="require-dotnetcoresdk"></a>require-dotnetcoresdk

Lo `require-dotnetcoresdk` strumento viene usato per installare il [.NET Core SDK](https://dotnet.microsoft.com/) e il runtime condiviso tramite lo script [DotNet-install](/dotnet/core/tools/dotnet-install-script) .

## <a name="usage"></a>Uso

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                               |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.                                               |
| [**input**](#input)                              | stringa | No       | Versione del .NET Core SDK da installare. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito. |
| [**additionalOptions**](#additional-options)     | stringa | No       | Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.                    |

### <a name="input"></a>Input

La `input` proprietà viene utilizzata per specificare la versione di .NET Core SDK da installare. È possibile trovare un elenco di versioni nel [sito DotNet-Core](https://dotnet.microsoft.com/download/dotnet-core).

### <a name="additional-options"></a>Opzioni aggiuntive

Altre opzioni di configurazione possono essere passate come valore di `additionalOptions` . Questi argomenti sono un passthrough diretto per gli argomenti usati nello script [DotNet-install](/dotnet/core/tools/dotnet-install-script) . Per ulteriori informazioni sui parametri disponibili, vedere la [documentazione](/dotnet/core/tools/dotnet-install-script) per lo script [DotNet-install](/dotnet/core/tools/dotnet-install-script) . Quando `additionalOptions` si usa, assicurarsi di usare i nomi e il formato degli argomenti di PowerShell.

> [!NOTE]
> Qualsiasi valore aggiuntivo a un argomento che include uno spazio deve includere una coppia aggiuntiva di virgolette precedute (usando la barra rovesciata). Un esempio può essere visualizzato nell' [esempio di utilizzo](#example-usage) usando `-InstallDir` .

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `require-dotnetcoresdk` strumento prevede l'installazione della versione della .NET Core SDK specificata in un `global.json` file [(documentazione)](/dotnet/core/tools/global-json?tabs=netcore3x) nella directory di lavoro corrente. Se non `global.json` viene trovato alcun file, `require-dotnetcoresdk` installerà la versione corrente più recente del .NET Core SDK e il runtime condiviso.

## <a name="example-usage"></a>Esempio di utilizzo

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of installing latest or, if present, the SDK version from a global.json file.",
            "tool": "require-dotnetcoresdk"
        },
        {
            "comments": "Example that will install a specific version.",
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0"
        },
        {
            "comments": "Example that will install a specific version and the aspnetcore runtime.",
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0",
            "additionalOptions": "-Runtime aspnetcore"
        },
        {
            "comments": "Example that will install in a specific directory.",
            "tool": "require-dotnetcoresdk",
            "additionalOptions": "-InstallDir \"C:\\Program Files\\dotnet\""
        }
    ]
}
```