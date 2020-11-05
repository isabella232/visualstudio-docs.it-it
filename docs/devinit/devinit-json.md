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
ms.openlocfilehash: 2b6cc27d2614f71c85988457ab9bb64228bbaebb
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399966"
---
# <a name="devinit-configuration-file"></a>file di configurazione di devinit

## <a name="file-location"></a>Percorso del file

Il `devinit.exe init` comando viene gestito tramite il _.devinit.jssu_ file. Per impostazione predefinita, `devinit.exe` Cerca il file nei percorsi seguenti:

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

È anche possibile specificare in modo esplicito il _.devinit.jssu_ file tramite l' `--file` / `-f` opzione.

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

| Nome         | Type   | Obbligatoria | valore                              |
|--------------|--------|----------|------------------------------------|
| **Commenti** | stringa | No       | Commenti per il file.             |
| **Correre**      | array  | Sì      | [Oggetto RunTool](#run-tool-object) |

#### <a name="run-tool-object"></a>Esegui oggetto strumento

| Nome                  | Type   | Obbligatoria | valore                                                                                                      |
|-----------------------|--------|----------|------------------------------------------------------------------------------------------------------------|
| **Commenti**          | stringa | No       | Commenti per la voce dello strumento.                                                                               |
| **strumento**              | string | Sì      | Nome dello strumento. Vedere il `devinit list` comando per un elenco di strumenti disponibili.                            |
| **input**             | stringa | No       | Input dello strumento. Varia in base allo strumento. Ad esempio, la versione richiesta, l'ID del pacchetto, il nome file o la cartella.|
| **additionalOptions** | stringa | No       | Argomenti aggiuntivi della riga di comando da passare allo strumento.                                                |

## <a name="examples"></a>Esempi

Per altri esempi sull'uso di devinit, vedere la [sezione Esempi](sample-readme.md).
