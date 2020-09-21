---
title: require-dotnetframeworksdk
description: per lo strumento devinit è necessario dotnetframeworksdk.
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
ms.openlocfilehash: c9e27883bda455794429221af436af1fe39229fc
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809686"
---
# <a name="require-dotnetframeworksdk"></a>require-dotnetframeworksdk

Lo `require-dotnetframeworksdk` strumento viene usato per installare il [.NET Framework SDK](https://dotnet.microsoft.com/) tramite i [programmi di installazione forniti](https://dotnet.microsoft.com/download/visual-studio-sdks).

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Type   | Obbligatoria  | valore                                                                                    |
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

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will install a specific version of the .NET Framework SDK.",
            "tool": "require-dotnetframeworksdk",
            "input": "4.8.0"
        },
        {
            "comments": "Example that will install the latest version of the .NET Framework SDK.",
            "tool": "require-dotnetframeworksdk"
        }
    ]
}
```
