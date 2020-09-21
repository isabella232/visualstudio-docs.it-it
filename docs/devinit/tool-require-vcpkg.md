---
title: require-vcpkg
description: per lo strumento devinit è necessario vcpkg.
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
ms.openlocfilehash: 42d21f4d5a2faa4eb7ecf39883475160d0cacaba
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810435"
---
# <a name="require-vcpkg"></a>require-vcpkg

Lo `require-vcpkg` strumento viene usato per installare [vcpkg](https://github.com/microsoft/vcpkg).

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Type   | Obbligatoria | valore                                                                      |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.                                      |
| [**input**](#input)                              | stringa | No       | Non usato. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito.                           |
| [**additionalOptions**](#additional-options)     | stringa | No       | Non usato. Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti. |

### <a name="input"></a>Input

Non usato.

### <a name="additional-options"></a>Opzioni aggiuntive

Non usato.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `require-vcpkg` strumento prevede l'installazione di vcpkg e la relativa aggiunta al percorso (solo Windows).

## <a name="example-usage"></a>Esempio di utilizzo

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs vcpkg.",
            "tool": "require-vcpkg"
        }
    ]
}
```
