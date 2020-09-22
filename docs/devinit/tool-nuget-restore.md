---
title: NuGet-ripristino
description: strumento devinit NuGet-Restore.
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
ms.openlocfilehash: 446498f77d7f9a26c9876f6a163d819a97df1ff9
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810919"
---
# <a name="nuget-restore"></a>NuGet-ripristino

Lo `nuget-restore` strumento Ripristina le dipendenze e gli strumenti specifici del progetto specificati nel file di progetto. Per altre informazioni sul ripristino di NuGet, vedere [qui](https://docs.microsoft.com/nuget/reference/cli-reference/cli-ref-restore).

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

Il comportamento predefinito dello `nuget-restore` strumento consiste nell'eseguire ' NuGet Restore ' nella directory corrente.

## <a name="example-usage"></a>Esempio di utilizzo

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "A sample dot-devinit file that restores NuGet pacakges.",
    "run": [
        {
            "tool": "nuget-restore",
            "comments": "Restores the dependencies and tools of a project using nuget restore.",
            "input": "C:\\nuget\\Nuget.config"
        }
    ]
}
```
