---
title: require-vscomponent
description: per lo strumento devinit è necessario vscomponent.
ms.date: 02/08/2021
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 50172f96a49e2384553a372ded0c889b30a23fff
ms.sourcegitcommit: e262f4c2a147c3fa2d27de666aae3a0497317867
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2021
ms.locfileid: "100006390"
---
# <a name="require-vscomponent"></a>require-vscomponent

Lo `require-vscomponent` strumento viene usato per importare le configurazioni di Visual Studio in Visual Studio esistente. Per altre informazioni `.vsconfig` , vedere [qui](../install/import-export-installation-configurations.md).

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                     | Tipo   | Obbligatoria | valore                                                                |
|------------------------------------------|--------|----------|----------------------------------------------------------------------|
| **Commenti**                             | stringa | No       | Proprietà commenti facoltativi. Non usato.                                |
| [**input**](#input)                      | stringa | No       | Percorso completo dell'oggetto `.vsconfig` . Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito. |
| [additionalOptions](#additional-options) | stringa | No       | Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.     |

### <a name="input"></a>Input

La `input` proprietà viene utilizzata per specificare il percorso completo del `.vsconfig` file. Se non è indicato, lo strumento cercherà un `.vsconfig` nella directory corrente e passerà il valore al programma di installazione di Visual Studio.

### <a name="additional-options"></a>Opzioni aggiuntive

Altre opzioni di configurazione possono essere passate come valore di `additionalOptions` . 

| Nome                      | Tipo      | Obbligatoria | valore                                                                                                                                                                                    |
|---------------------------|-----------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --installPath             | stringa    | No       | Percorso di installazione dell'istanza di Visual Studio che si desidera modificare.                                                                                                                       |

Se non viene specificato alcun percorso di installazione, lo strumento modificherà il meno recente installato in Visual Studio nel computer se sono presenti più istanze nel computer. 

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `require-vscomponent` strumento consiste nel cercare un `.vsconfig` file nella directory corrente ed eseguire il programma di installazione di Visual Studio con questi dettagli in modalità non interattiva. `require-vscomponent` supporta solo la modifica di un'installazione esistente di Visual Studio. 

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito è riportato un esempio di come eseguire `require-vscomponent` usando un `.devinit.json` .

#### <a name="devinitjson-that-will-import-the-configurations-of-a-given-vsconfig-file-path"></a>.devinit.json che importerà le configurazioni di un percorso di file con estensione vsconfig specificato:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "A sample dot-devinit file.",
    "run": [
        {
            "tool": "require-vscomponent",
            "input": "C:\\.vsconfig"
        }
    ]
}
```

#### <a name="devinitjson-that-will-import-the-configurations-of-a-given-vsconfig-file-path-to-the-visual-studio-instance-specified-via-an-install-path"></a>.devinit.json che importerà le configurazioni di un determinato percorso del file con estensione vsconfig nell'istanza di Visual Studio specificata tramite un percorso di installazione:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "A sample dot-devinit file.",
    "run": [
        {
            "tool": "require-vscomponent",
            "input": "C:\\.vsconfig",
            "additionalOptions": "--installPath 'C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\Enterprise'"
        }
    ]
}
```