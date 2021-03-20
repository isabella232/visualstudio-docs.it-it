---
title: require-dotnetframeworksdk
description: per lo strumento devinit è necessario dotnetframeworksdk.
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
ms.openlocfilehash: 0c40ebfd2a8b665a1421ba70c0f785774e97d3df
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672151"
---
# <a name="require-dotnetframeworksdk"></a>require-dotnetframeworksdk

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione agli spazi dei codebase di GitHub da Visual Studio 2019 non sarà più supportata e l'anteprima privata è stata conclusa. Ci stiamo concentrando sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e per le soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro di Visual Studio. Come parte di questo `devinit` e gli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio per informazioni sulle future anteprime e informazioni di roadmap.

Lo `require-dotnetframeworksdk` strumento viene usato per installare il [.NET Framework SDK](https://dotnet.microsoft.com/) tramite i [programmi di installazione forniti](https://dotnet.microsoft.com/download/visual-studio-sdks).

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria  | valore                                                                                    |
|--------------------------------------------------|--------|-----------|------------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No        | Proprietà commenti facoltativi. Non usato.                                                    |
| [**input**](#input)                              | stringa | No        | Versione di .NET Framework SDK da installare. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito. |
| [**additionalOptions**](#additional-options)     | stringa | No        | Non usato. Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.               |

### <a name="input"></a>Input

La `input` proprietà viene usata per specificare la versione di .NET Framework SDK da installare. È possibile trovare un elenco di versioni nel [sito DotNet-Framework](https://dotnet.microsoft.com/download/visual-studio-sdks).

### <a name="additional-options"></a>Opzioni aggiuntive

Non usato.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `require-dotnetframeworksdk` strumento prevede l'installazione della versione più recente. Vedere i [programmi di installazione forniti](https://dotnet.microsoft.com/download/visual-studio-sdks) per la versione più recente.

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito sono riportati alcuni esempi di come eseguire `require-dotnetframeworksdk` usando un `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-latest-net-framework"></a>.devinit.jsin che installerà la versione più recente .NET Framework:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetframeworksdk"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-the-net-framework"></a>.devinit.jssu che installerà una versione specifica del .NET Framework:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetframeworksdk",
            "input": "4.8.0"
        }
    ]
}
```