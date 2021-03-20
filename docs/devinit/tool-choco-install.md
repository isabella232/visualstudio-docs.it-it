---
title: choco-install
description: strumento devinit Choco-install per installare i pacchetti di cioccolato.
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
ms.openlocfilehash: c1f5b1c587ea8d1d6335e19b2e7303cc12ad9783
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671658"
---
# <a name="choco-install"></a>choco-install

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione agli spazi dei codebase di GitHub da Visual Studio 2019 non sarà più supportata e l'anteprima privata è stata conclusa. Ci stiamo concentrando sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e per le soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro di Visual Studio. Come parte di questo `devinit` e gli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio per informazioni sulle future anteprime e informazioni di roadmap.

Lo `choco-install` strumento può essere usato per installare e aggiornare i pacchetti di [cioccolato](https://chocolatey.org/) .

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento non eseguirà alcuna operazione.

| Nome                                             | Tipo   | Obbligatoria  | valore                                                                                                          |
|--------------------------------------------------|--------|-----------|----------------------------------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No        | Proprietà commenti facoltativi. Non usato.                                                                          |
| [**input**](#input)                              | string | Sì       | Pacchetto da installare. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito.                                                 |
| [**additionalOptions**](#additional-options)     | stringa | No        | Opzioni aggiuntive da passare allo strumento. Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.       |

### <a name="input"></a>Input

La `input` proprietà viene utilizzata per specificare il nome del pacchetto da installare, ad esempio ' MongoDB ', oppure il percorso di un file di configurazione con i formati seguenti _packages.config_, _NuSpec_ e _. nupkg_. Il valore di `input` verrà accodato a un `choco install` comando (ad esempio `choco install mongodb` ) insieme a eventuali argomenti specifici di [`additionalOptions`](#additional-options) e alle `choco` opzioni predefinite (definite di [seguito](#built-in-options)). I pacchetti sono disponibili nella [raccolta di pacchetti di cioccolato](https://chocolatey.org/packages). Quando si usa un file di configurazione, ad esempio, è possibile passare il percorso del file nella `input` proprietà `"input":"packages.config"` .

### <a name="additional-options"></a>Opzioni aggiuntive

Altre opzioni di configurazione possono essere passate come valore di `additionalOptions` . Questi argomenti sono il pass-through diretto agli argomenti utilizzati da [`choco install`](https://chocolatey.org/docs/commands-install) e sono definiti nella documentazione di cioccolato.

#### <a name="adding-new-feeds-to-chocolatey"></a>Aggiunta di nuovi feed a Chocolate
Se si desidera aggiungere un nuovo feed alla cioccolata, in modo simile a un `choco source add` comando, è possibile passare `additionalOptions` a tale scopo. Un esempio di aggiunta di un nuovo feed è nell' [uso di esempio](#example-usage). Se si desidera aggiungere un feed privato, è consigliabile eseguire lo strumento nel prompt dei comandi perché richiede le credenziali. Ad esempio, `devinit run -t choco-install -i {package} -s "{feed link}" -u {user} -p {password}` , dove `{package}` , `{feed link}` , `{user}` e `{password}` fanno riferimento al pacchetto specifico, al collegamento al feed, al nome utente e alla password. Per ulteriori informazioni, fare riferimento alla documentazione di cioccolato. 

### <a name="built-in-options"></a>Opzioni predefinite

Lo `choco-install` strumento imposta un numero di `choco` argomenti della riga di comando per garantire che sia `choco` possibile eseguire l'intestazione. Questi argomenti sono elencati di seguito e la relativa documentazione è disponibile nella [documentazione di cioccolato](https://chocolatey.org/docs/).

| Nome                  | Descrizione                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **--Sì**             | Conferma tutti i prompt: sceglie una risposta affermativa anziché richiedere. Implica `--accept-license.` |
| **--No-Progress**     | Non visualizzare lo stato di avanzamento: le percentuali di avanzamento non verranno visualizzate.                                         |
| **--Skip-PowerShell** | Ignorare PowerShell-chocolateyInstall.ps1 non verrà eseguito.                                              |

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `choco-install` strumento è l'errore perché la `input` proprietà è obbligatoria.

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito sono riportati alcuni esempi di come eseguire `choco-install` usando un `.devinit.json` .

#### <a name="devinitjson-that-will-install-packages-listed-in-packagesconfig"></a>.devinit.jsin che installerà i pacchetti elencati in packages.config:
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

#### <a name="devinitjson-that-will-install-mongodb"></a>.devinit.jssu che installerà MongoDB:
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

#### <a name="devinitjson-that-will-install-a-specific-version-of-mongodb"></a>.devinit.jssu che installerà una versione specifica di MongoDB:
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

#### <a name="devinitjson-that-adds-a-new-feed-to-chocolatey"></a>.devinit.jssu che aggiunge un nuovo feed alla cioccolata:
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