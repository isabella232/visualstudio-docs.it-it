---
title: require-nuget
description: per lo strumento devinit è necessario-NuGet.
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
ms.openlocfilehash: dd5c85e6bff00433903a1e9e472f567401ada70c
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440496"
---
# <a name="require-nuget"></a>require-nuget

Lo `require-nuget` strumento Scarica l'interfaccia della riga di comando di NuGet e la aggiunge a `PATH` . L'interfaccia della riga di comando di NuGet offre l'estensione completa della funzionalità NuGet per installare, creare, pubblicare e gestire i pacchetti senza apportare modifiche ai file di progetto. Scopri di più [sull'interfaccia della](/nuget/reference/nuget-exe-cli-reference)riga di comando di NuGet.

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Type   | Obbligatoria | valore                                                                                |
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
Di seguito è riportato un esempio di come eseguire `require-nuget` usando un `.devinit.json` .

#### <a name="devinitjson-that-will-install-a-specified-version-of-nuget"></a>.devinit.json che installerà una versione specificata di NuGet:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-nuget",
            "input": "5.5.1",
        }
    ]
}
```