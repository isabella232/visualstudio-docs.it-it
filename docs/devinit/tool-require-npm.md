---
title: require-npm
description: lo strumento devinit richiede-NPM.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 29ec1819317329985e0ea3210a56038fb2284c0f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862262"
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
Di seguito sono riportati alcuni esempi di come eseguire `require-npm` usando un `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-lts-of-npm"></a>.devinit.jssu che installerà il LTS di NPM:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-npm"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-npm"></a>.devinit.jssu che installerà una versione specifica di NPM:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-npm",
            "input": "6.14.6"
        }
    ]
}
```