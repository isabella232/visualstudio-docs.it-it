---
title: choco-upgrade
description: strumento devinit Choco-upgrade.
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
ms.openlocfilehash: fab2a3f2893ba79874b6909b3d19ccf939f8b14a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906317"
---
# <a name="choco-upgrade"></a>choco-upgrade

Lo `choco-upgrade` strumento può essere usato per installare e aggiornare i pacchetti di [cioccolato](https://chocolatey.org/docs/commandsupgrade) .

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento non eseguirà alcuna operazione.

| Nome                                             | Tipo   | Obbligatoria  | valore                                                                                                          |
|--------------------------------------------------|--------|-----------|----------------------------------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No        | Proprietà commenti facoltativi. Non usato.                                                                          |
| [**input**](#input)                              | string | Sì       | Pacchetto da aggiornare. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito.                                                 |
| [**additionalOptions**](#additional-options)     | stringa | No        | Opzioni aggiuntive da passare allo strumento. Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.       |

### <a name="input"></a>Input

La `input` proprietà viene utilizzata per specificare il nome del pacchetto da aggiornare, ad esempio ' MongoDB ', oppure il percorso di un file di configurazione con i formati seguenti _packages.config_, _NuSpec_ e _. nupkg_. Il valore di `input` verrà accodato a un `choco upgrade` comando (ad esempio `choco upgrade mongodb` ) insieme a eventuali argomenti specifici di [`additionalOptions`](#additional-options) e alle `choco` opzioni predefinite (definite di [seguito](#built-in-options)). I pacchetti sono disponibili nella [raccolta di pacchetti di cioccolato](https://chocolatey.org/packages). Quando si usa un file di configurazione, è possibile passare il percorso del file nella `input` proprietà, ad esempio: `"input":"packages.config"` .

### <a name="additional-options"></a>Opzioni aggiuntive

Altre opzioni di configurazione possono essere passate come valore di `additionalOptions` . Questi argomenti sono il pass-through diretto agli argomenti utilizzati da [`choco upgrade`](https://chocolatey.org/docs/commands-upgrade) e sono definiti nella documentazione di cioccolato.

### <a name="built-in-options"></a>Opzioni predefinite

Lo `choco-upgrade` strumento imposta un numero di `choco` argomenti della riga di comando per garantire che sia `choco` possibile eseguire l'intestazione. Questi argomenti sono elencati di seguito e la relativa documentazione è disponibile nella [documentazione di cioccolato](https://chocolatey.org/docs/).

| Nome                  | Descrizione                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **--Sì**             | Conferma tutti i prompt: sceglie una risposta affermativa anziché richiedere. Implica `--accept-license` . |
| **--No-Progress**     | Non visualizzare lo stato di avanzamento: le percentuali di avanzamento non verranno visualizzate.                                         |
| **--Skip-PowerShell** | Ignorare PowerShell-chocolateyInstall.ps1 non verrà eseguito.                                              |

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `choco-upgrade` strumento è l'errore perché la `input` proprietà è obbligatoria.

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito sono riportati alcuni esempi di come eseguire `choco-upgrade` usando un `.devinit.json` .

#### <a name="devinitjson-that-will-update-packages-listed-in-packagesconfig"></a>.devinit.jssu in grado di aggiornare i pacchetti elencati in packages.config:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-upgrade",
            "input": "packages.config",
        }
    ]
}
```

#### <a name="devinitjson-that-will-upgrade-mongodb"></a>.devinit.jssu che aggiornerà MongoDB:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-upgrade",
            "input": "mongodb"
        }
    ]
}
```

#### <a name="devinitjson-that-will-upgrade-to-a-specific-version-of-mongodb"></a>.devinit.jssu che eseguirà l'aggiornamento a una versione specifica di MongoDB:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-upgrade",
            "input": "mongodb",
            "additionalOptions": "--version 4.2.7"
        }
    ]
}
```