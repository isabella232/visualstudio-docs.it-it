---
title: WindowsFeature-Disabilita
description: strumento devinit WindowsFeature-Disable.
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
ms.openlocfilehash: bae1dffee275b1ae7f05daf411814d2d288fc086
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810407"
---
# <a name="windowsfeature-disable"></a>WindowsFeature-Disabilita

Lo `windowsfeature-disable` strumento viene usato per acquisire le funzionalità di Windows.

## <a name="usage"></a>Utilizzo

| Nome                                             | Type   | Obbligatoria | valore                                                                  |
|--------------------------------------------------|--------|----------|------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.                                  |
| [**input**](#input)                              | string | Sì      | Funzionalità di Windows da installare. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito. |
| [**additionalOptions**](#additional-options)     | stringa | No       | Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.       |

### <a name="input"></a>Input

La `input` proprietà deve essere `name` della proprietà dell'oggetto `windows feature` da disabilitare.

### <a name="additional-options"></a>Opzioni aggiuntive

Nessuno.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `windowsfeature-disable` strumento è l'errore, come `input` richiesto.

## <a name="example-usage"></a>Esempio di utilizzo

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs IIS.",
            "tool": "require-windowsfeature",
            "input": "web-server",
        }
    ]
}
```
