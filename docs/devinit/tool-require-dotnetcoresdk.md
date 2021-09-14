---
title: require-dotnetcoresdk
description: devinit tool require-dotnetcoresdk.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709844"
---
# <a name="require-dotnetcoresdk"></a>require-dotnetcoresdk

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è incentrata sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di Visual Studio di lavoro. Come parte di questo `devinit` e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community per sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Lo `require-dotnetcoresdk` strumento viene usato per installare il [.NET Core SDK](https://dotnet.microsoft.com/) e il runtime condiviso tramite lo script [dotnet-install.](/dotnet/core/tools/dotnet-install-script)

## <a name="usage"></a>Utilizzo

Se `input` entrambe le proprietà e vengono omesse o vuote, lo strumento seguirà `additionalOptions` il [comportamento](#default-behavior) predefinito descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                               |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà comments facoltativa. Non usato.                                               |
| [**Input**](#input)                              | stringa | No       | Versione del .NET Core SDK da installare. Per [informazioni dettagliate,](#input) vedere Input di seguito. |
| [**additionalOptions**](#additional-options)     | stringa | No       | Per [informazioni dettagliate, vedere](#additional-options) Opzioni aggiuntive di seguito.                    |

### <a name="input"></a>Input

La `input` proprietà viene usata per specificare la versione .NET Core SDK da installare. Un elenco di versioni è disponibile nel sito [dotnet-core](https://dotnet.microsoft.com/download/dotnet-core).

### <a name="additional-options"></a>Opzioni aggiuntive

È possibile passare opzioni di configurazione aggiuntive come valore di `additionalOptions` . Questi argomenti sono un pass-through diretto agli argomenti usati nello script [dotnet-install.](/dotnet/core/tools/dotnet-install-script) Per altre informazioni sui parametri disponibili, vedere la [documentazione](/dotnet/core/tools/dotnet-install-script) per lo script [dotnet-install.](/dotnet/core/tools/dotnet-install-script) Quando si usa , assicurarsi di usare i nomi e il `additionalOptions` formato degli argomenti di PowerShell.

> [!NOTE]
> Qualsiasi valore aggiuntivo di un argomento che include uno spazio deve includere una coppia aggiuntiva di virgolette precedute da caratteri di escape (usando la barra rovesciata). È possibile vedere un esempio in [Utilizzo di esempio](#example-usage) usando `-InstallDir` .

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello strumento è installare la versione del .NET Core SDK specificata in un `require-dotnetcoresdk` file `global.json` [(documentazione)](/dotnet/core/tools/global-json?tabs=netcore3x) nella directory di lavoro corrente. Se non viene trovato alcun file, verrà installata la versione corrente più recente del .NET Core SDK `global.json` `require-dotnetcoresdk` e del runtime condiviso.

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito sono riportati esempi di come eseguire `require-dotnetcoresdk` usando `.devinit.json` un oggetto .

#### <a name="devinitjson-that-will-install-the-latest-version-of-net-core"></a>.devinit.json che installerà la versione più recente di .NET Core:
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

#### <a name="devinitjson-that-will-install-a-specific-version-of-net-core"></a>.devinit.json che installerà una versione specifica di .NET Core:
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

#### <a name="devinitjson-that-will-install-a-specific-version-of-net-core-and-aspnet-core"></a>.devinit.json che installerà una versione specifica di .NET Core e ASP.NET Core:
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

#### <a name="devinitjson-that-will-install-net-core-in-a-specific-directory"></a>.devinit.json che installerà .NET Core in una directory specifica:
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