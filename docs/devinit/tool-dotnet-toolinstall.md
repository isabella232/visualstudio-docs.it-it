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
ms.openlocfilehash: f6946afa0138dc27a61f5665a9172c231392acc1
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862242"
---
# <a name="dotnet-toolinstall"></a>dotnet-toolinstall

Lo `dotnet-toolinstall` strumento viene usato per installare gli [strumenti di .NET Core](https://dotnet.microsoft.com/) tramite il `dotnet tool update` comando.

## <a name="usage"></a>Uso

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                 |
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

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will install the dotnet-trace tool.",
            "tool": "dotnet-toolinstall",
            "input": "dotnet-trace"
        },
        {
            "comments": "Example that will install the dotnet-trace tool as a global tool.",
            "tool": "dotnet-toolinstall",
            "input": "dotnet-trace",
            "additionalOptions": "--global"
        }
    ]
}
```