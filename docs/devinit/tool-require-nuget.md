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
ms.openlocfilehash: e4f08e8c3f5967eb2e9db53633a12b304ac23bfb
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671760"
---
# <a name="require-nuget"></a>require-nuget

Lo strumento per scaricare l'interfaccia della riga di comando di `require-nuget` NuGet e aggiunge alla variabile Path. L'interfaccia della riga di comando di NuGet offre l'estensione completa della funzionalità NuGet per installare, creare, pubblicare e gestire i pacchetti senza apportare modifiche ai file di progetto. Scopri di più [sull'interfaccia della](/nuget/reference/nuget-exe-cli-reference)riga di comando di NuGet.

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