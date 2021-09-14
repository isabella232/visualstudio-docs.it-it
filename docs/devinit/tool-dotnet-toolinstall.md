---
title: dotnet-toolinstall
description: devinit tool dotnet-toolinstall.
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
ms.openlocfilehash: 4daa3722abd169c03656adec39aafc29d5e7e435
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709861"
---
# <a name="dotnet-toolinstall"></a>dotnet-toolinstall

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è incentrata sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di Visual Studio di lavoro. Come parte di questo `devinit` e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community per sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Lo `dotnet-toolinstall` strumento viene usato per installare [.NET Core Tools](https://dotnet.microsoft.com/) tramite il comando `dotnet tool update` .

## <a name="usage"></a>Utilizzo

Se `input` entrambe le proprietà e vengono omesse o vuote, lo strumento seguirà `additionalOptions` il [comportamento](#default-behavior) predefinito descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                 |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà comments facoltativa. Non usato.                                 |
| [**Input**](#input)                              | string | Sì      | Strumento .NET Core da installare. Per [informazioni dettagliate,](#input) vedere Input di seguito. |
| [**additionalOptions**](#additional-options)     | stringa | No       | Per [informazioni dettagliate, vedere](#additional-options) Opzioni aggiuntive di seguito.      |

### <a name="input"></a>Input

La `input` proprietà viene usata per specificare lo strumento .NET Core da installare. È disponibile un elenco non ufficiale di strumenti in [https://github.com/natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) .

### <a name="additional-options"></a>Opzioni aggiuntive

È possibile passare opzioni di configurazione aggiuntive come valore di `additionalOptions` . Questi argomenti sono un pass-through diretto agli argomenti usati dal [`dotnet tool update`](/dotnet/core/tools/global-tools#update-a-tool) comando.

Il `dotnet tool update` comando viene usato per gestire in modo sicuro il caso in cui uno strumento è già installato.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `dotnet-toolinstall` strumento è l'errore come `input` richiesto.

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito sono riportati esempi di come eseguire `dotnet-toolinstall` usando `.devinit.json` un oggetto .

#### <a name="devinitjson-that-will-install-the-dotnet-trace-tool"></a>.devinit.json che installerà lo strumento dotnet-trace:
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

#### <a name="devinitjson-that-will-install-the-dotnet-trace-tool-as-a-global-tool"></a>.devinit.json che installerà lo strumento dotnet-trace come strumento globale:
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