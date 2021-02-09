---
title: require-vcpkg
description: per lo strumento devinit è necessario vcpkg.
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
ms.openlocfilehash: 2e660c46ce4e77c9ebbb8c4587952970d38d6f3f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862227"
---
# <a name="require-vcpkg"></a>require-vcpkg

Lo `require-vcpkg` strumento viene usato per installare [vcpkg](https://github.com/microsoft/vcpkg).

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                      |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.                                      |
| [**input**](#input)                              | stringa | No       | Non usato. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito.                           |
| [**additionalOptions**](#additional-options)     | stringa | No       | Non usato. Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti. |

### <a name="input"></a>Input

Non usato.

### <a name="additional-options"></a>Opzioni aggiuntive

Non usato.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `require-vcpkg` strumento prevede l'installazione di vcpkg e la relativa aggiunta a `PATH` .

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito è riportato un esempio di come eseguire `require-vcpkg` usando un `.devinit.json` .

#### <a name="devinitjson-that-will-install-vcpkg"></a>.devinit.json che installerà vcpkg:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-vcpkg"
        }
    ]
}
```
