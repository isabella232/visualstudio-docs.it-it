---
title: alette-installazione
description: strumento devinit per Winger.
ms.date: 02/08/2021
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 4a2ad1ef30692d7d23f2d450f0ba32d6f38f8262
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672624"
---
# <a name="winget-install"></a>alette-installazione

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione agli spazi dei codebase di GitHub da Visual Studio 2019 non sarà più supportata e l'anteprima privata è stata conclusa. Ci stiamo concentrando sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e per le soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro di Visual Studio. Come parte di questo `devinit` e gli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio per informazioni sulle future anteprime e informazioni di roadmap.

Lo `winget-install` strumento viene usato per installare i [pacchetti di wingt](https://docs.microsoft.com/windows/package-manager/winget/).

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento restituirà un errore.

| Nome                                         | Tipo   | Obbligatoria | valore                                                                             |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------------|
| **Commenti**                                 | stringa | No       | Proprietà commenti facoltativi. Non usato.                                             |
| [**input**](#input)                          | stringa | No       | Pacchetto da installare. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito.                    |
| [**additionalOptions**](#additional-options) | stringa | No       | Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.                  |

### <a name="input"></a>Input

La proprietà input viene utilizzata per specificare `Id` o `Name` del pacchetto da installare, ad esempio "MongoDB. Server". Il valore di input verrà accodato a un `winget install` comando (ad esempio `winget install MongoDB.Server` ). Se il nome del pacchetto non è univoco e corrisponde agli altri pacchetti, è possibile specificare il `Id` del pacchetto e aggiungere il `--exact` flag a `additionalOptions` per assicurarsi che l'identità del pacchetto corrisponda esattamente a. `Id`Per trovare un pacchetto, è possibile eseguire il `winget search` comando e utilizzare il `Id` parametro per un pacchetto.  

### <a name="additional-options"></a>Opzioni aggiuntive

Le opzioni di configurazione aggiuntive possono essere passate come valore di additionalOptions. Questi argomenti sono il pass-through diretto agli argomenti utilizzati da `winget install` e sono definiti nella `winget install` [documentazione](https://docs.microsoft.com/windows/package-manager/winget/install).

#### <a name="manifests"></a>Manifesti

Un ulteriore facoltativo che `winget` supporta è la possibilità di fornire un [file manifesto](https://docs.microsoft.com/windows/package-manager/winget/install#local-install) per il dettaglio del pacchetto da installare. Per usare questa funzionalità con devinit `input` , il parametro deve essere vuoto e la `additionalOptions` proprietà deve includere l' `--manifest` opzione seguita dal percorso del manifesto (ad esempio `--manifest path.to.manifest.yml` ).

### <a name="built-in-options"></a>Opzioni predefinite

Lo strumento wingt-install imposta un numero di argomenti della riga di comando di wingt per garantire che il wingt possa essere eseguito. Questi argomenti sono elencati di seguito e la relativa documentazione si trova nella `winget install` [documentazione](https://docs.microsoft.com/windows/package-manager/winget/install)di.

| Nome     | Descrizione                                                                                                                       |
|----------|-----------------------------------------------------------------------------------------------------------------------------------|
| --invisibile all'utente | Esegue il programma di installazione in modalità invisibile all'utente, senza visualizzare alcuna interfaccia utente. L'esperienza predefinita mostra lo stato del programma di installazione.                       | 

## <a name="example-usage"></a>Esempio di utilizzo

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-6.0",
    "run": [
        {
            "comments": "Installs Microsoft PowerToys.",
            "tool": "winget-install",
            "input": "Microsoft.PowerToys",
            "additionalOptions": "--version 0.15.2",
        },
        {
            "comments": "Installs PostgreSQL.",
            "tool": "winget-install",
            "input": "PostgreSQL.PostgreSQL",
            "additionalOptions": "--exact"
        },
        {
            "comments": "Installs the package defined in winget-manifest.yml.",
            "tool": "winget-install",
            "additionalOptions": "--manifest winget-manifest.yml"
        }
    ]
}
```
