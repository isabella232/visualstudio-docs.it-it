---
title: Richiedi-NPM
description: lo strumento devinit richiede-NPM.
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
ms.openlocfilehash: 56c8bc0d277427d235396671f446a44125aa0165
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809679"
---
# <a name="require-npm"></a>Richiedi-NPM

Lo `require-npm` strumento viene usato per installare [NPM](https://www.npmjs.com/).

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Type   | Obbligatoria | valore                                                                                       |
|--------------------------------------------------|--------|----------|---------------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.                                                       |
| [**input**](#input)                              | string | Sì      | Specifica la versione di NPM. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito.                           |
| [**additionalOptions**](#additional-options)     | stringa | No       | Non usato. Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.                  |

### <a name="input"></a>Input

La `input` proprietà viene usata per specificare la versione di NPM.

### <a name="additional-options"></a>Opzioni aggiuntive

Non utilizzato.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `require-nodejs` strumento consiste nell'installare la versione LTS più recente di NPM.

## <a name="example-usage"></a>Esempio di utilizzo

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of installing latest LTS of NPM.",
            "tool": "require-npm"
        },
        {
            "comments": "Example that will install a specific version.",
            "tool": "require-npm",
            "input": "6.14.6"
        }
    ]
}
```
