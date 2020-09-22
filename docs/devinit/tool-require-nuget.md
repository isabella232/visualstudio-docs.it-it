---
title: require-nuget
description: per lo strumento devinit è necessario-NuGet.
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
ms.openlocfilehash: ef5de2d8358dae0f5f29b815cfa2dca26a3f1cef
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005176"
---
# <a name="require-nuget"></a>require-nuget

Lo strumento per scaricare l'interfaccia della riga di comando di `require-nuget` NuGet e aggiunge alla variabile Path. L'interfaccia della riga di comando di NuGet offre l'estensione completa della funzionalità NuGet per installare, creare, pubblicare e gestire i pacchetti senza apportare modifiche ai file di progetto. Scopri di più [sull'interfaccia della](https://docs.microsoft.com/nuget/reference/nuget-exe-cli-reference)riga di comando di NuGet.

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.                                                |
| [**input**](#input)                              | stringa | No       | Versione dell'interfaccia della riga di comando NuGet da installare. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito. |
| [**additionalOptions**](#additional-options)     | stringa | No       | Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.                     |

### <a name="input"></a>Input

`input`È una proprietà facoltativa usata per specifica la versione dell'interfaccia della riga di comando di NuGet da installare. Se `input` viene omesso, verrà installata la versione più recente dell'interfaccia della riga di comando.

### <a name="additional-options"></a>Opzioni aggiuntive

Non usato.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `require-nuget` strumento consiste nell'installare la versione più recente dell'interfaccia della riga di comando di NuGet.

## <a name="example-usage"></a>Esempio di utilizzo

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "A sample dot-devinit file that downloads NuGet CLI and adds to PATH variable.'",
    "run": [
        {
            "tool": "require-nuget",
            "input": "5.5.1",
            "comments": "Installs NuGet for given input version. If no input given, then installs latest."
        }
    ]
}
```
