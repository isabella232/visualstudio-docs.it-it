---
title: require-vscomponent
description: per lo strumento devinit è necessario vscomponent.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: e9d2f546e99f83b4c53d0b76abfdaf8ec91868ac
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672111"
---
# <a name="require-vscomponent"></a>require-vscomponent

Lo `require-vscomponent` strumento viene usato per importare le configurazioni di Visual Studio in Visual Studio esistente. Per altre informazioni `.vsconfig` , vedere [qui](../install/import-export-installation-configurations.md).

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                     | Type   | Obbligatoria | valore                                                                |
|------------------------------------------|--------|----------|----------------------------------------------------------------------|
| **Commenti**                             | stringa | No       | Proprietà commenti facoltativi. Non usato.                                |
| [**input**](#input)                      | stringa | No       | Percorso completo dell'oggetto `.vsconfig` . Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito. |
| [additionalOptions](#additional-options) | stringa | No       | Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.     |

### <a name="input"></a>Input

La `input` proprietà viene utilizzata per specificare il percorso completo del `.vsconfig` file. Se non è indicato, lo strumento cercherà un `.vsconfig` nella directory corrente e passerà il valore al programma di installazione di Visual Studio.

### <a name="additional-options"></a>Opzioni aggiuntive

Non usato.

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