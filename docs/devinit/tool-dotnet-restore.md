---
title: dotnet-restore
description: strumento di devinizzazione DotNet-Restore.
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
ms.openlocfilehash: 647748acc3eb45e2eca6ab4ca1e48a8bda3a563b
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440395"
---
# <a name="dotnet-restore"></a>dotnet-restore

Lo `dotnet-restore` strumento Ripristina le dipendenze e gli strumenti specifici del progetto specificati nel file di progetto. Scopri di più su dotnet restore [qui](/dotnet/core/tools/dotnet-restore).

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Type   | Obbligatoria | valore                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.                                                |
| [**input**](#input)                              | stringa | No       | Percorso del file di progetto/soluzione da ripristinare. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito. |
| [**additionalOptions**](#additional-options)     | stringa | No       | Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.                     |

### <a name="input"></a>Input

Percorso del file di progetto/soluzione da ripristinare.

### <a name="additional-options"></a>Opzioni aggiuntive

Le opzioni aggiuntive vengono passate così come sono al comando dotnet restore.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `dotnet-restore` strumento viene eseguito `dotnet restore` nella directory corrente.

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito è riportato un esempio di come eseguire `dotnet-restore` usando un `.devinit.json` .

#### <a name="devinitjson-that-will-restore-dependencies-and-tools-of-a-project"></a>.devinit.jssu per ripristinare le dipendenze e gli strumenti di un progetto:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "dotnet-restore",
            "input": "C:\\app1\\app1.csproj"
        }
    ]
}
```