---
title: require-nuget
description: devinit tool require-nuget.
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
ms.openlocfilehash: fe907e78b694022a39768edf38c0f869234d51e7e1b6bdbbab62b1c797ac682d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121343226"
---
# <a name="require-nuget"></a>require-nuget

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione a GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è rivolta alle esperienze in continua evoluzione per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro Visual Studio cloud. Nell'ambito di `devinit` questo e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Lo `require-nuget` strumento scarica NuGet'interfaccia della riga di comando e la aggiunge a `PATH` . NuGet L'interfaccia della riga di comando offre NuGet funzionalità per installare, creare, pubblicare e gestire pacchetti senza apportare modifiche ai file di progetto. Altre informazioni sull'interfaccia NuGet comando [qui.](/nuget/reference/nuget-exe-cli-reference)

## <a name="usage"></a>Utilizzo

Se entrambe `input` le proprietà e vengono omesse o vuote, lo strumento seguirà `additionalOptions` il [comportamento](#default-behavior) predefinito descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà comments facoltativa. Non usato.                                                |
| [**Input**](#input)                              | stringa | No       | NuGet Versione dell'interfaccia della riga di comando da installare. Per informazioni [dettagliate,](#input) vedere l'input seguente. |
| [**additionalOptions**](#additional-options)     | stringa | No       | Per [informazioni dettagliate, vedere](#additional-options) Opzioni aggiuntive di seguito.                     |

### <a name="input"></a>Input

è `input` una proprietà facoltativa usata per specificare la versione dell'interfaccia della NuGet riga di comando da installare. Se `input` viene omesso, verrà installata la versione più recente dell'interfaccia della riga di comando.

### <a name="additional-options"></a>Opzioni aggiuntive

Non usato.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello strumento è `require-nuget` l'installazione della versione più recente dell'interfaccia della NuGet comando.

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito è riportato un esempio di come eseguire `require-nuget` usando `.devinit.json` un oggetto .

#### <a name="devinitjson-that-will-install-a-specified-version-of-nuget"></a>.devinit.jsin verrà installata una versione specificata di NuGet:
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