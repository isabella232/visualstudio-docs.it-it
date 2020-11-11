---
title: File di configurazione di devinit
description: Documentazione per la .devinit.jsnel file manifesto per la devinilica.
ms.date: 11/02/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: acd3b65f520a9be048fe2d0209a85a85d086df2f
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438229"
---
# <a name="devinit-configuration-file"></a>file di configurazione di devinit

Il `.devinit.json` file definisce le dipendenze a livello di sistema necessarie all'applicazione per l'esecuzione e la compilazione. Le dipendenze a livello di sistema sono elementi come Node.js, SQL Server, IIS, RabbitMQ, Docker e così via. Si tratta di un tipo di operazioni normalmente installate nella casella di sviluppo che non vengono installate da un repository specifico. Non è una posizione in cui definire dipendenze specifiche dell'applicazione come si farebbe con i gestori di pacchetti, ad esempio NuGet o NPM. Si tratta, tuttavia, di una posizione in cui è necessario definire i gestori di pacchetti.

## <a name="file-location"></a>Percorso del file

Il `devinit init` comando viene gestito tramite il `.devinit.json` file. Per impostazione predefinita, `devinit` Cerca il file nei percorsi seguenti:

* {Current-directory} \\.devinit.js
* {Current-directory} \\devinit.js
* {Current-directory} \\ ..devinit.jsdi devinit \\
* {Current-directory} \\ .devinit.jsdi devinit \\
* {Current-directory} \\.devinit.jsdi devinit \\
* {Current-directory} \\devinit.jsdi devinit \\
* {Current-directory} \\ . devcontainer \\.devinit.json
* {Current-directory} \\ . devcontainer \\devinit.json

> [!NOTE]
> Se vengono trovati più file predefiniti, il file verrà usato per primo nell'elenco precedente.

Il `.devinit.json` file può essere specificato anche in modo esplicito tramite l' `--file` / `-f` opzione.

### <a name="directories-and-relative-paths"></a>Directory e percorsi relativi

I percorsi sono relativi alla posizione in cui è in esecuzione devinit. Si tratta in genere della directory di lavoro corrente da cui `devinit` è stato eseguito.

## <a name="file-format"></a>Formato file

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

#### <a name="run-tool-object"></a>Esegui oggetto strumento

| Nome                  | Tipo   | Obbligatoria | valore                                                                                                      |
|-----------------------|--------|----------|------------------------------------------------------------------------------------------------------------|
| **Commenti**          | stringa | No       | Commenti per la voce dello strumento.                                                                               |
| **strumento**              | string | Sì      | Nome dello strumento. Vedere il `devinit list` comando per un elenco di strumenti disponibili.                            |
| **input**             | stringa | No       | Input dello strumento. Varia in base allo strumento. Ad esempio, la versione richiesta, l'ID del pacchetto, il nome file o la cartella.|
| **additionalOptions** | stringa | No       | Argomenti aggiuntivi della riga di comando da passare allo strumento.                                                |

## <a name="examples"></a>Esempi

Per altri esempi sull'uso di devinit, vedere la [sezione Esempi](sample-readme.md).
