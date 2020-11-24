---
title: require-dotnetframeworksdk
description: per lo strumento devinit è necessario dotnetframeworksdk.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: ed1d9ee019d96ebf93362db6907646ceb52b8f64
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441657"
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