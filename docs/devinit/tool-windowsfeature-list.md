---
title: elenco di WindowsFeature
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
ms.openlocfilehash: 6c4c20fb92e0d854eb7745a598efabd7ac426bfc
ms.sourcegitcommit: 417ea66a8b07ec102ece2fa00e07b88edc404c00
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/23/2020
ms.locfileid: "91127834"
---
# <a name="windowsfeature-list"></a>elenco di WindowsFeature

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
    "$schema": "./devinit.schema-2.0.json",
    "run": [
        {
            "comments": "Lists the state of all Windows features.",
            "tool": "windowsfeature-list"
        }
    ]
}
```
