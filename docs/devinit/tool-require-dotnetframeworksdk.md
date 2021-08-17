---
title: require-dotnetframeworksdk
description: devinit tool require-dotnetframeworksdk.
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
ms.openlocfilehash: c43c6910642a47c63ce9910fdcb1aedcc7bc4075df938117a4f3f94b98cf1c97
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121343196"
---
# <a name="require-dotnetframeworksdk"></a>require-dotnetframeworksdk

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione a GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è rivolta alle esperienze in continua evoluzione per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro Visual Studio cloud. Nell'ambito di `devinit` questo e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Lo `require-dotnetframeworksdk` strumento viene usato per installare .NET Framework [SDK](https://dotnet.microsoft.com/) tramite i programmi di [installazione forniti.](https://dotnet.microsoft.com/download/visual-studio-sdks)

## <a name="usage"></a>Utilizzo

Se entrambe `input` le proprietà e vengono omesse o vuote, lo strumento seguirà `additionalOptions` il [comportamento](#default-behavior) predefinito descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria  | valore                                                                                    |
|--------------------------------------------------|--------|-----------|------------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No        | Proprietà comments facoltativa. Non usato.                                                    |
| [**Input**](#input)                              | stringa | No        | Versione dell'SDK .NET Framework da installare. Per informazioni [dettagliate,](#input) vedere Input di seguito. |
| [**additionalOptions**](#additional-options)     | stringa | No        | Non usato. Per [informazioni dettagliate, vedere](#additional-options) Opzioni aggiuntive di seguito.               |

### <a name="input"></a>Input

La `input` proprietà viene usata per specificare la versione .NET Framework SDK da installare. Un elenco delle versioni è disponibile nel sito [dotnet-framework](https://dotnet.microsoft.com/download/visual-studio-sdks).

### <a name="additional-options"></a>Opzioni aggiuntive

Non usato.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello strumento `require-dotnetframeworksdk` è l'installazione della versione più recente. Vedere i [programmi di installazione forniti per](https://dotnet.microsoft.com/download/visual-studio-sdks) la versione più recente.

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito sono riportati esempi di come eseguire `require-dotnetframeworksdk` usando `.devinit.json` un oggetto .

#### <a name="devinitjson-that-will-install-the-latest-net-framework"></a>.devinit.jsin verrà installata la versione più recente .NET Framework:
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

#### <a name="devinitjson-that-will-install-a-specific-version-of-the-net-framework"></a>.devinit.jsin verrà installata una versione specifica del .NET Framework:
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