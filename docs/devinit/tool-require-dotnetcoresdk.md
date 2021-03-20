---
title: require-dotnetcoresdk
description: per lo strumento devinit è necessario dotnetcoresdk.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 1963ad8dfe1bd31eb3f98ec6fdf57524a274cfb6
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671791"
---
# <a name="require-dotnetcoresdk"></a>require-dotnetcoresdk

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione agli spazi dei codebase di GitHub da Visual Studio 2019 non sarà più supportata e l'anteprima privata è stata conclusa. Ci stiamo concentrando sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e per le soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro di Visual Studio. Come parte di questo `devinit` e gli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio per informazioni sulle future anteprime e informazioni di roadmap.

Lo `require-dotnetcoresdk` strumento viene usato per installare il [.NET Core SDK](https://dotnet.microsoft.com/) e il runtime condiviso tramite lo script [DotNet-install](/dotnet/core/tools/dotnet-install-script) .

## <a name="usage"></a>Utilizzo

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
Di seguito sono riportati alcuni esempi di come eseguire `require-dotnetcoresdk` usando un `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-latest-version-of-net-core"></a>.devinit.jssu che installerà la versione più recente di .NET Core:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetcoresdk"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-net-core"></a>.devinit.jssu che installerà una versione specifica di .NET Core:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-net-core-and-aspnet-core"></a>.devinit.jssu che installerà una versione specifica di .NET Core e ASP.NET Core:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0",
            "additionalOptions": "-Runtime aspnetcore"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-net-core-in-a-specific-directory"></a>.devinit.jssu che installerà .NET Core in una directory specifica:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetcoresdk",
            "additionalOptions": "-InstallDir \"C:\\Program Files\\dotnet\""
        }
    ]
}
```