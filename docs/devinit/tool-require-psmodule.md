---
title: require-psmodule
description: per lo strumento devinit è necessario PSModule.
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
ms.openlocfilehash: b855d8f3e9827d7b88f6d95bdf426cfb470b2bda
ms.sourcegitcommit: 3e05bd4bfac6f0b8b3534d8c013388f67e288651
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2020
ms.locfileid: "91959786"
---
# <a name="require-psmodule"></a>require-psmodule

Lo `require-psmodule` strumento viene usato per installare un [modulo di PowerShell](/powershell/scripting/developer/module/understanding-a-windows-powershell-module?view=powershell-7&preserve-view=true) dal [PowerShell Gallery](https://www.powershellgallery.com/) tramite [install-module](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true), in modo che possa essere usato negli script di PowerShell.

> [!TIP]
> Dopo l'installazione di un modulo, sarà comunque necessario importarlo in uno script con [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7&preserve-view=true).

## <a name="usage"></a>Uso

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Type   | Obbligatoria | valore                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.                                                   |
| [**input**](#input)                              | Stringa | Sì      | Pacchetti da installare. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito.                       |
| [**additionalOptions**](#additional-options)     | stringa | No       | Non usato. Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.              |

### <a name="input"></a>Input

La `input` proprietà deve essere il `Name` del modulo PowerShell da installare. Per trovare un elenco dei moduli di PowerShell disponibili, è possibile eseguire una ricerca nell' [PowerShell Gallery](https://www.powershellgallery.com/).

### <a name="additional-options"></a>Opzioni aggiuntive

Le opzioni aggiuntive vengono passate direttamente al comando [install-module](/powershell/module/powershellget/install-module?preserve-view=true&view=powershell-7) e sono documentate in [Microsoft docs](/powershell/module/powershellget/install-module?preserve-view=true&view=powershell-7).

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `require-psmodule` strumento è l'errore, come `input` richiesto.

## <a name="builtin-options"></a>Opzioni predefinite

Lo `require-psmodule` strumento imposta un numero di `Install-Module` argomenti della riga di comando per garantire che sia `Install-Module` possibile eseguire l'intestazione. Questi argomenti sono elencati di seguito e la relativa documentazione è disponibile in [install-module](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true).

| Nome         | Descrizione                                                                                                                                                                                                                                                                                                                                                               |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **-Force**   | Installa un modulo ed esegue l'override dei messaggi di avviso relativi ai conflitti di installazione del modulo. Se nel computer esiste già un modulo con lo stesso nome, Force consente l'installazione di più versioni. Sovrascriverà il modulo se è presente un modulo esistente con lo stesso nome e la stessa versione. Force e AllowClobber possono essere usati insieme in un comando Install-Module. |
| **-WhatIf**  | Il flag-WhatIf viene aggiunto quando viene passata l'esecuzione a secco per il `devinit` comando.                                                                                                                                                                                                                                                                                                       |
| **-Verbose** | Il flag-Verbose viene aggiunto quando viene passato verbose per il `devinit` comando.                                                                                                                                                                                                                                                                                                      |


## <a name="example-usage"></a>Esempio di utilizzo

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs the PowerShellGet module.",
            "tool": "require-psmodule",
            "input": "PowerShellGet",
        },
        {
            "comments": "Installs the PowerShellGet module from a specific repository.",
            "tool": "require-psmodule",
            "input": "PowerShellGet",
            "additionalOptions": "-Repository PSGallery"
        }
    ]
}
```