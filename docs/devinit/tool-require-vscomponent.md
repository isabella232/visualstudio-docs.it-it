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
ms.openlocfilehash: e88f1b58308d0c81d17f9337f0a1a1d5e253c6ba
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862823"
---
# <a name="require-vscomponent"></a>require-vscomponent

Lo `require-vscomponent` strumento viene usato per importare le configurazioni di Visual Studio in Visual Studio esistente. Per altre informazioni `.vsconfig` , vedere [qui](../install/import-export-installation-configurations.md).

## <a name="usage"></a>Uso

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                     | Tipo   | Obbligatoria | valore                                                                |
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

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "A sample dot-devinit file.",
    "run": [
        {
            "tool": "require-vscomponent",
            "comments": "Imports .vsconfig file which is passed as input to Visual Studio.",
            "input": "C:\\.vsconfig"
        }
    ]
}
```