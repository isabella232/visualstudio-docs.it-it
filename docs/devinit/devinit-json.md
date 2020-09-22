---
title: File di configurazione di devinit
description: Documentazione per la .devinit.jsnel file manifesto per la devinilica.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 5ba7299f90ce5f3f253a7210456053faa6bd22c0
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852202"
---
# <a name="devinit-configuration-file"></a>file di configurazione di devinit

## <a name="file-location"></a>Percorso del file

Il `devinit.exe init` comando viene gestito tramite il _.devinit.jssu_ file. Per impostazione predefinita, `devinit.exe` Cerca il file nei percorsi seguenti:

- _{Current-Directory}\\_
- _{Current-directory} \\ . devinit\\_
- _{Current-directory} \\ . devcontainer\\_

L'elemento language _._ nella directory e i nomi file possono essere omessi.

È anche possibile specificare in modo esplicito il _.devinit.jssu_ file tramite l' `--file` / `-f` opzione.

### <a name="directories-and-relative-paths"></a>Directory e percorsi relativi

I percorsi sono relativi alla posizione in cui è in esecuzione devinit. Si tratta in genere della directory di lavoro corrente da cui `devinit` è stato eseguito.

## <a name="file-format"></a>Formato file

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
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
