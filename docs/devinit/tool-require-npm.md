---
title: require-npm
description: lo strumento devinit richiede-NPM.
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
ms.openlocfilehash: 0af1e0561edfc4cf12ccd19f17bab2a386d0afe9
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005183"
---
# <a name="require-npm"></a>require-npm

Lo `require-npm` strumento viene usato per installare [NPM](https://www.npmjs.com/).

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                                       |
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
