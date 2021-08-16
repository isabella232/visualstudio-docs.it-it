---
title: require-psmodule
description: devinit tool require-psmodule.
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
ms.openlocfilehash: 4aac45dfe7d23be35962a126fe995867cede7df9b4a27b12a6eed03bd5dbefe1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378341"
---
# <a name="require-psmodule"></a>require-psmodule

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione a GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è rivolta alle esperienze in continua evoluzione per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro Visual Studio cloud. Nell'ambito di `devinit` questo e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.


Lo strumento viene usato per installare un modulo `require-psmodule` [di PowerShell](/powershell/scripting/developer/module/understanding-a-windows-powershell-module?view=powershell-7&preserve-view=true) dal [PowerShell Gallery](https://www.powershellgallery.com/) tramite [Install-Module](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true), in modo che possa essere usato negli script di PowerShell.

> [!TIP]
> Dopo aver installato un modulo, sarà comunque necessario importarlo in uno script usando [Import-Module.](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7&preserve-view=true)

## <a name="usage"></a>Utilizzo

Se entrambe `input` le proprietà e vengono omesse o vuote, lo strumento seguirà `additionalOptions` il [comportamento](#default-behavior) predefinito descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà comments facoltativa. Non usato.                                                   |
| [**Input**](#input)                              | string | Sì      | Pacchetti da installare. Per informazioni [dettagliate,](#input) vedere Input di seguito.                       |
| [**additionalOptions**](#additional-options)     | stringa | No       | Non usato. Per [informazioni dettagliate, vedere](#additional-options) Opzioni aggiuntive di seguito.              |

### <a name="input"></a>Input

La `input` proprietà deve essere del modulo di `Name` PowerShell da installare. È possibile trovare un elenco dei moduli di PowerShell disponibili eseguendo una [PowerShell Gallery](https://www.powershellgallery.com/).

### <a name="additional-options"></a>Opzioni aggiuntive

Le opzioni aggiuntive vengono passate direttamente [al comando Install-Module](/powershell/module/powershellget/install-module?preserve-view=true&view=powershell-7) e sono documentate in [Microsoft Docs](/powershell/module/powershellget/install-module?preserve-view=true&view=powershell-7).

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello strumento `require-psmodule` è l'errore `input` necessario.

### <a name="built-in-options"></a>Opzioni predefinite

Lo `require-psmodule` strumento imposta una serie di argomenti della riga di comando per garantire `Install-Module` `Install-Module` l'esecuzione headless. Questi argomenti sono elencati di seguito e la relativa documentazione è disponibile in [Install-Module](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true).

| Nome         | Descrizione                                                                                                                                                                                                                                                                                                                                                               |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **-Force**   | Installa un modulo ed esegue l'override dei messaggi di avviso relativi ai conflitti di installazione del modulo. Se nel computer esiste già un modulo con lo stesso nome, Force consente l'installazione di più versioni. Sovrascriverà il modulo se esiste un modulo esistente con lo stesso nome e la stessa versione. Force e AllowClobber possono essere usati insieme in un Install-Module comando. |
| **-WhatIf**  | Il flag -WhatIf viene aggiunto quando viene passata l'esecuzione di tipo dry per il `devinit` comando .                                                                                                                                                                                                                                                                                                       |
| **-Verbose** | Il flag -Verbose viene aggiunto quando viene passato verbose per il `devinit` comando .                                                                                                                                                                                                                                                                                                      |


## <a name="example-usage"></a>Esempio di utilizzo
Di seguito sono riportati esempi di come eseguire `require-psmodule` usando `.devinit.json` un oggetto .

#### <a name="devinitjson-that-will-install-the-powershellget-module"></a>.devinit.jsin verrà installato il modulo PowerShellGet:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-psmodule",
            "input": "PowerShellGet",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-powershellget-module-from-a-specific-repository"></a>.devinit.jsin verrà installato il modulo PowerShellGet da un repository specifico:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-psmodule",
            "input": "PowerShellGet",
            "additionalOptions": "-Repository PSGallery"
        }
    ]
}
```