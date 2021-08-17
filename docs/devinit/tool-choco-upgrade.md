---
title: choco-upgrade
description: devinit tool choco-upgrade.
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
ms.openlocfilehash: 63ea33101bbd0062ebab9dc74925ac98d7d206984d3ffdb256644618afbb86da
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390669"
---
# <a name="choco-upgrade"></a>choco-upgrade

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è incentrata sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di Visual Studio di lavoro. Come parte di questo `devinit` e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community per sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Lo `choco-upgrade` strumento può essere usato per installare e aggiornare pacchetti [chocolatey.](https://chocolatey.org/docs/commandsupgrade)

## <a name="usage"></a>Utilizzo

Se `input` entrambe le `additionalOptions` proprietà e vengono omesse o vuote, lo strumento non farà nulla.

| Nome                                             | Tipo   | Obbligatoria  | valore                                                                                                          |
|--------------------------------------------------|--------|-----------|----------------------------------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No        | Proprietà comments facoltativa. Non usato.                                                                          |
| [**Input**](#input)                              | string | Sì       | Pacchetto da aggiornare. Per [informazioni dettagliate,](#input) vedere Input di seguito.                                                 |
| [**additionalOptions**](#additional-options)     | stringa | No        | Opzioni aggiuntive da passare all'oggetto . Per [informazioni dettagliate, vedere](#additional-options) Opzioni aggiuntive di seguito.       |

### <a name="input"></a>Input

La proprietà viene utilizzata per specificare il nome del pacchetto da aggiornare ,ad esempio 'mongodb', o il percorso di un file di configurazione dei formati `input` _seguentipackages.config_, _nuspec_ e _nupkg_. Il valore di verrà aggiunto a un comando (ad esempio ) insieme agli argomenti specifici in e alle opzioni predefinite `input` `choco upgrade` `choco upgrade mongodb` [`additionalOptions`](#additional-options) `choco` (definite di [seguito).](#built-in-options) I pacchetti sono disponibili nella [raccolta di pacchetti Chocolatey.](https://chocolatey.org/packages) Quando si usa un file di configurazione, è possibile passare il percorso di tale file nella `input` proprietà , ad esempio: `"input":"packages.config"` .

### <a name="additional-options"></a>Opzioni aggiuntive

È possibile passare opzioni di configurazione aggiuntive come valore di `additionalOptions` . Questi argomenti sono pass-through diretto agli argomenti usati da [`choco upgrade`](https://chocolatey.org/docs/commands-upgrade) e sono definiti nella documentazione di Chocolatey.

### <a name="built-in-options"></a>Opzioni predefinite

Lo strumento imposta una serie di argomenti della riga di comando `choco-upgrade` per garantire che possano essere `choco` `choco` eseguiti senza testa. Questi argomenti sono elencati di seguito e la relativa documentazione è disponibile nella documentazione [di chocolatey](https://chocolatey.org/docs/).

| Nome                  | Descrizione                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **--yes**             | Conferma tutte le richieste: sceglie una risposta affermativa invece di chiedere conferma. Implica `--accept-license` . |
| **--no-progress**     | Non mostrare lo stato: le percentuali di stato non vengono visualizzate.                                         |
| **--skip-powershell** | Ignora PowerShell: chocolateyInstall.ps1 non verrà eseguito.                                              |

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `choco-upgrade` strumento è l'errore perché `input` la proprietà è obbligatoria.

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito sono riportati esempi di come eseguire `choco-upgrade` usando `.devinit.json` un oggetto .

#### <a name="devinitjson-that-will-update-packages-listed-in-packagesconfig"></a>.devinit.jssu che aggiornerà i pacchetti elencati in packages.config:
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

#### <a name="devinitjson-that-will-upgrade-mongodb"></a>.devinit.jssu che a upgraderà MongoDB:
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

#### <a name="devinitjson-that-will-upgrade-to-a-specific-version-of-mongodb"></a>.devinit.jssu verrà eseguito l'aggiornamento a una versione specifica di MongoDB:
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