---
title: choco-install
description: devinit tool choco-install per installare i pacchetti Chocolatey.
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
ms.openlocfilehash: 075d085e12926f30ea9e71512decb2fb77b7456cdfb3502295e7a40b6dff39b9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390711"
---
# <a name="choco-install"></a>choco-install

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione a GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è rivolta alle esperienze in continua evoluzione per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro Visual Studio cloud. Nell'ambito di `devinit` questo e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Lo `choco-install` strumento può essere usato per installare e aggiornare i pacchetti [chocolatey.](https://chocolatey.org/)

## <a name="usage"></a>Utilizzo

Se entrambe `input` le proprietà e vengono `additionalOptions` omesse o vuote, lo strumento non farà nulla.

| Nome                                             | Tipo   | Obbligatoria  | valore                                                                                                          |
|--------------------------------------------------|--------|-----------|----------------------------------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No        | Proprietà comments facoltativa. Non usato.                                                                          |
| [**Input**](#input)                              | string | Sì       | Pacchetto da installare. Per informazioni [dettagliate,](#input) vedere Input di seguito.                                                 |
| [**additionalOptions**](#additional-options)     | stringa | No        | Opzioni aggiuntive da passare agli strumenti. Per [informazioni dettagliate, vedere](#additional-options) Opzioni aggiuntive di seguito.       |

### <a name="input"></a>Input

La proprietà viene usata per specificare il nome del pacchetto da installare (ad esempio 'mongodb') o il percorso di un file di configurazione dei formati `input` _seguentipackages.config_, _nuspec_ e _nupkg_. Il valore di verrà aggiunto a un comando (ad esempio ) insieme a qualsiasi argomento specifico in e alle opzioni predefinite `input` `choco install` `choco install mongodb` [`additionalOptions`](#additional-options) `choco` (definite di [seguito).](#built-in-options) I pacchetti sono disponibili nella [raccolta di pacchetti Chocolatey.](https://chocolatey.org/packages) Quando si usa un file di configurazione, è possibile passare il percorso del file nella `input` proprietà , ad esempio `"input":"packages.config"` .

### <a name="additional-options"></a>Opzioni aggiuntive

È possibile passare opzioni di configurazione aggiuntive come valore di `additionalOptions` . Questi argomenti sono pass-through diretti agli argomenti usati da [`choco install`](https://chocolatey.org/docs/commands-install) e sono definiti nella documentazione di chocolatey.

#### <a name="adding-new-feeds-to-chocolatey"></a>Aggiunta di nuovi feed a Chocolatey
Se si vuole aggiungere un nuovo feed a Chocolatey, in modo simile a un comando, è possibile passare `choco source add` `additionalOptions` a tale scopo. Un esempio di aggiunta di un nuovo feed è in [Esempio di utilizzo di](#example-usage). Se si vuole aggiungere un feed privato, è consigliabile eseguire lo strumento nel prompt dei comandi perché richiede credenziali. Ad esempio, `devinit run -t choco-install -i {package} -s "{feed link}" -u {user} -p {password}` , dove , , e fanno riferimento al `{package}` `{feed link}` `{user}` `{password}` pacchetto, al collegamento al feed, al nome utente e alla password specifici. Per altre informazioni, vedere la documentazione di Chocolatey a cui si fa riferimento in precedenza. 

### <a name="built-in-options"></a>Opzioni predefinite

Lo `choco-install` strumento imposta una serie di argomenti della riga di comando per garantire `choco` `choco` l'esecuzione headless. Questi argomenti sono elencati di seguito e la relativa documentazione è disponibile nella [documentazione di chocolatey.](https://chocolatey.org/docs/)

| Nome                  | Descrizione                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **--yes**             | Conferma tutte le richieste: sceglie una risposta affermativa invece di chiedere conferma. Implica `--accept-license.` |
| **--no-progress**     | Non mostrare lo stato di avanzamento: le percentuali di avanzamento non vengono visualizzate.                                         |
| **--skip-powershell** | Ignora PowerShell: chocolateyInstall.ps1 non verrà eseguito.                                              |

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `choco-install` strumento è l'errore perché la `input` proprietà è obbligatoria.

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito sono riportati esempi di come eseguire `choco-install` usando `.devinit.json` un oggetto .

#### <a name="devinitjson-that-will-install-packages-listed-in-packagesconfig"></a>.devinit.jsin verranno installati i pacchetti elencati in packages.config:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "packages.config",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-mongodb"></a>.devinit.jsin verrà installato MongoDB:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "mongodb"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-mongodb"></a>.devinit.jsin verrà installata una versione specifica di MongoDB:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "mongodb",
            "additionalOptions": "--version 4.2.7"
        }
    ]
}
```

#### <a name="devinitjson-that-adds-a-new-feed-to-chocolatey"></a>.devinit.jssu che aggiunge un nuovo feed a Chocolatey:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "packages.config",
            "additionalOptions": "-s '{feed link}'"
        }
    ]
}
```