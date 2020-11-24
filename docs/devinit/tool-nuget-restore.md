---
title: nuget-restore
description: strumento devinit NuGet-Restore.
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
ms.openlocfilehash: 8e525451ffcd691b0dab1260584946ad3d0a561c
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440368"
---
# <a name="nuget-restore"></a>nuget-restore

Lo `nuget-restore` strumento Ripristina le dipendenze e gli strumenti specifici del progetto specificati nel file di progetto. Per altre informazioni sul ripristino di NuGet, vedere [qui](/nuget/reference/cli-reference/cli-ref-restore).

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

Le opzioni aggiuntive vengono passate così come sono al comando di ripristino NuGet.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `nuget-restore` strumento viene eseguito `NuGet restore` nella directory corrente.

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito è riportato un esempio di come eseguire `nuget-restore` usando un `.devinit.json` .

#### <a name="devinitjson-that-will-restore-dependencies-and-tools-of-a-project"></a>.devinit.jssu per ripristinare le dipendenze e gli strumenti di un progetto:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "nuget-restore",
            "input": "C:\\nuget\\Nuget.config"
        }
    ]
}
```