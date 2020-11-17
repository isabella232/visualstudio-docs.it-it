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
ms.openlocfilehash: b521009affbc1db81676481e33640a69e619aaf3
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671712"
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
