---
title: DotNet-toolinstall
description: strumento devinit DotNet-toolinstall.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: afc200bca49617dff40697210ac783d18ff5f532
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810144"
---
# <a name="dotnet-toolinstall"></a>DotNet-toolinstall

Lo `dotnet-toolinstall` strumento viene usato per installare gli [strumenti di .NET Core](https://dotnet.microsoft.com/) tramite il `dotnet tool update` comando.

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Type   | Obbligatoria | valore                                                                 |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.                                 |
| [**input**](#input)                              | string | Sì      | Strumento .NET Core da installare. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito. |
| [**additionalOptions**](#additional-options)     | stringa | No       | Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.      |

### <a name="input"></a>Input

La `input` proprietà viene usata per specificare l'installazione dello strumento .NET Core. In è disponibile un elenco di strumenti non ufficiale [https://github.com/natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) .

### <a name="additional-options"></a>Opzioni aggiuntive

Altre opzioni di configurazione possono essere passate come valore di `additionalOptions` . Questi argomenti sono un passthrough diretto per gli argomenti usati dal [`dotnet tool update`](https://docs.microsoft.com/dotnet/core/tools/global-tools#update-a-tool) comando. 

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
