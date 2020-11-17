---
title: dotnet-toolinstall
description: strumento devinit DotNet-toolinstall.
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
ms.openlocfilehash: 85a8beafdc9b19a807becabb459baa5de88169e2
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672219"
---
# <a name="dotnet-toolinstall"></a>dotnet-toolinstall

Lo `dotnet-toolinstall` strumento viene usato per installare gli [strumenti di .NET Core](https://dotnet.microsoft.com/) tramite il `dotnet tool update` comando.

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Type   | Obbligatoria | valore                                                                 |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.                                 |
| [**input**](#input)                              | string | Sì      | Strumento .NET Core da installare. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito. |
| [**additionalOptions**](#additional-options)     | stringa | No       | Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.      |

### <a name="input"></a>Input

La `input` proprietà viene usata per specificare lo strumento .NET Core da installare. In è disponibile un elenco di strumenti non ufficiale [https://github.com/natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) .

### <a name="additional-options"></a>Opzioni aggiuntive

Altre opzioni di configurazione possono essere passate come valore di `additionalOptions` . Questi argomenti sono un passthrough diretto per gli argomenti usati dal [`dotnet tool update`](/dotnet/core/tools/global-tools#update-a-tool) comando. 

Il `dotnet tool update` comando viene usato per gestire in modo sicuro il caso in cui è già installato uno strumento.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `dotnet-toolinstall` strumento è l'errore, come `input` richiesto.

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito sono riportati alcuni esempi di come eseguire `dotnet-toolinstall` usando un `.devinit.json` . 

#### <a name="devinitjson-that-will-install-the-dotnet-trace-tool"></a>.devinit.jssu che installerà lo strumento DotNet-Trace:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-trace"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-dotnet-trace-tool-as-a-global-tool"></a>.devinit.jssu che installerà lo strumento DotNet-Trace come strumento globale:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-trace",
            "additionalOptions": "--global"
        }
    ]
}
```