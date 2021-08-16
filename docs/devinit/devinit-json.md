---
title: File di configurazione devinit
description: Documentazione per l'.devinit.jssul file manifesto per devinit.
ms.date: 11/02/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 84c9123ea117b1a215473be8e804b8122e2c49364e5f570a131b0c93333e952d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378389"
---
# <a name="devinit-configuration-file"></a>File di configurazione devinit

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione a GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è rivolta alle esperienze in continua evoluzione per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro Visual Studio cloud. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Il `.devinit.json` file definisce le dipendenze a livello di sistema necessarie all'applicazione per l'esecuzione e la compilazione. Le dipendenze a livello di sistema sono elementi come Node.js, SQL Server, IIS, RabbitMQ, Docker e così via. Questi sono gli elementi che normalmente si installano nella casella di sviluppo che non vengono installati da un determinato repo. Non è possibile definire le dipendenze specifiche dell'applicazione come si farebbe in gestori di pacchetti, ad esempio NuGet o NPM. Si tratta, tuttavia, di una posizione in cui definire che sono necessari gli gestori di pacchetti.

## <a name="file-location"></a>Percorso del file

Il `devinit init` comando viene guidato tramite il file `.devinit.json` . Per impostazione predefinita, `devinit` cerca il file nei percorsi seguenti:

* {current-directory} \\.devinit.jssu
* {current-directory} \\devinit.jssu
* {current-directory} \\ . devinit \\.devinit.json
* {current-directory} \\ . devinit \\devinit.json
* {current-directory} \\ devinit \\.devinit.json
* {current-directory} \\ devinit \\devinit.json
* {current-directory} \\ . devcontainer \\.devinit.json
* {current-directory} \\ . devcontainer \\devinit.json

> [!NOTE]
> Se vengono trovati più file predefiniti, devinit userà il file visualizzato per primo nell'elenco precedente.

Il `.devinit.json` file può anche essere specificato in modo esplicito tramite l'opzione `--file` / `-f` .

### <a name="directories-and-relative-paths"></a>Directory e percorsi relativi

I percorsi sono relativi alla posizione in cui devinit è in esecuzione. Si tratta in genere della directory di lavoro corrente da cui è `devinit` stato eseguito .

## <a name="file-format"></a>Formato file
In `.devinit.json` un è possibile specificare più di uno strumento da eseguire. Nella sezione `run` è possibile inserire qualsiasi numero di oggetti. Un esempio è illustrato nell'esempio.devinit.js[ su](sample-all-tool.md) con tutti gli strumenti.

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "string",
    "run": [
        {
            "comments": "string",
            "tool": "string",
            "input": "string|null|undefined",
            "additionalOptions": "string|null|undefined"
        }
    ]
}
```

### <a name="property-values"></a>Valori delle proprietà

| Nome         | Tipo   | Obbligatoria | valore                              |
|--------------|--------|----------|------------------------------------|
| **Commenti** | stringa | No       | Commenti per il file.             |
| **Correre**      | array  | Sì      | [Oggetto RunTool](#run-tool-object) |

#### <a name="run-tool-object"></a>Eseguire l'oggetto strumento

| Nome                  | Tipo   | Obbligatoria | valore                                                                                                      |
|-----------------------|--------|----------|------------------------------------------------------------------------------------------------------------|
| **Commenti**          | stringa | No       | Commenti per la voce dello strumento.                                                                               |
| **Strumento**              | string | Sì      | Nome dello strumento. Per un `devinit list` elenco degli strumenti disponibili, vedere il comando .                            |
| **input**             | stringa | No       | Input dello strumento. Varia a seconda dello strumento. Ad esempio, la versione richiesta, l'ID del pacchetto, il nome file o la cartella.|
| **additionalOptions** | stringa | No       | Argomenti aggiuntivi della riga di comando da passare agli strumenti.                                                |

## <a name="examples"></a>Esempio

Per altri esempi sull'uso di devinit, vedere la [sezione Esempi](sample-readme.md).
