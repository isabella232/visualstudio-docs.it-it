---
title: windowsfeature-list
description: WindowsFeature-list dello strumento devinit.
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
ms.openlocfilehash: 3030ddaaa3cc19b8719b067d9bd5e3572957b84f
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400198"
---
# <a name="windowsfeature-list"></a>windowsfeature-list

Lo `windowsfeature-list` strumento viene usato per elencare lo stato di abilitazione/disabilitazione di tutte le funzionalità di Windows.

| Nome                                             | Type   | Obbligatoria | valore                                      |
|--------------------------------------------------|--------|----------|--------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.      |
| [**input**](#input)                              | stringa | No       | Non usato. Ignorato.                         |
| [**additionalOptions**](#additional-options)     | stringa | No       | Non usato. Ignorato.                         |

### <a name="input"></a>Input

Non usato. Ignorato.

#### <a name="additional-options"></a>Opzioni aggiuntive

Non usato. Ignorato.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `windowsfeature-list` strumento consiste nell'elencare lo stato di abilitazione/disabilitazione di tutte le funzionalità di Windows.

## <a name="example-usage"></a>Esempio di utilizzo

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "comments": "Lists the state of all Windows features.",
            "tool": "windowsfeature-list"
        }
    ]
}
```
