---
title: require-vscomponent
description: Devinit tool require-vscomponent.
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
ms.openlocfilehash: 5ba58bfde22ad5d6d9a7a3a2c64d95326a5e33c43adb327285ac6ba73da8390b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121418014"
---
# <a name="require-vscomponent"></a>require-vscomponent

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione a GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è rivolta alle esperienze in continua evoluzione per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro Visual Studio cloud. Nell'ambito di `devinit` questo e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Lo `require-vscomponent` strumento viene usato per importare Visual Studio configurazioni in Visual Studio. Per altre informazioni, `.vsconfig` [vedere qui](../install/import-export-installation-configurations.md).

## <a name="usage"></a>Utilizzo

Se entrambe `input` le proprietà e vengono omesse o vuote, lo strumento seguirà `additionalOptions` il [comportamento](#default-behavior) predefinito descritto di seguito.

| Nome                                     | Tipo   | Obbligatoria | valore                                                                |
|------------------------------------------|--------|----------|----------------------------------------------------------------------|
| **Commenti**                             | stringa | No       | Proprietà comments facoltativa. Non usato.                                |
| [**Input**](#input)                      | stringa | No       | Percorso completo di `.vsconfig` . Per informazioni [dettagliate,](#input) vedere l'input seguente. |
| [additionalOptions](#additional-options) | stringa | No       | Per [informazioni dettagliate, vedere](#additional-options) Opzioni aggiuntive di seguito.     |

### <a name="input"></a>Input

La `input` proprietà viene utilizzata per specificare il percorso completo del `.vsconfig` file. Se non indicato, lo strumento cerca un `.vsconfig` oggetto nella directory corrente e passa il valore al Programma di installazione di Visual Studio.

### <a name="additional-options"></a>Opzioni aggiuntive

È possibile passare opzioni di configurazione aggiuntive come valore di `additionalOptions` . 

| Nome                      | Tipo      | Obbligatoria | valore                                                                                                                                                                                    |
|---------------------------|-----------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --installPath             | stringa    | No       | Percorso di installazione dell'Visual Studio che si vuole modificare.                                                                                                                       |

Se non viene specificato alcun percorso di installazione, lo strumento modificherà il primo Visual Studio installato nel computer se sono presenti più istanze nel computer. 

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello strumento è cercare un file nella directory corrente ed eseguire il Programma di installazione di Visual Studio con questi `require-vscomponent` dettagli in modalità non `.vsconfig` interattiva. `require-vscomponent`supporta solo la modifica di un'installazione Visual Studio esistente. 

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito è riportato un esempio di come eseguire `require-vscomponent` usando `.devinit.json` un oggetto .

#### <a name="devinitjson-that-will-import-the-configurations-of-a-given-vsconfig-file-path"></a>.devinit.jsche importerà le configurazioni di un determinato percorso di file con estensione vsconfig:
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

#### <a name="devinitjson-that-will-import-the-configurations-of-a-given-vsconfig-file-path-to-the-visual-studio-instance-specified-via-an-install-path"></a>.devinit.jsin che importerà le configurazioni di un determinato percorso di file con estensione vsconfig nell'istanza Visual Studio specificata tramite un percorso di installazione:
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