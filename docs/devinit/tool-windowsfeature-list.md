---
title: windowsfeature-list
description: WindowsFeature-list dello strumento devinit.
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
ms.openlocfilehash: 43370389aaffdb4395248fed6ec83de39f16c86d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874505"
---
# <a name="windowsfeature-list"></a>windowsfeature-list

Lo `windowsfeature-list` strumento viene usato per elencare lo stato di abilitazione/disabilitazione di tutte le funzionalità di Windows.

| Nome                                             | Tipo   | Obbligatoria | valore                                      |
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
Di seguito è riportato un esempio di come eseguire `windowsfeature-list` usando un `.devinit.json` .

#### <a name="devinitjson-that-will-list-the-state-of-all-windows-features"></a>.devinit.jssu in cui è possibile elencare lo stato di tutte le funzionalità di Windows:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "tool": "windowsfeature-list"
        }
    ]
}
```
