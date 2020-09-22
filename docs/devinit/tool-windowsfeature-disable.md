---
title: windowsfeature-disable
description: strumento devinit WindowsFeature-Disable.
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
ms.openlocfilehash: 8a649cec23a8f0090500a493fe577b3ba41788f9
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005981"
---
# <a name="windowsfeature-disable"></a>windowsfeature-disable

Lo `windowsfeature-disable` strumento viene usato per acquisire le funzionalità di Windows.

## <a name="usage"></a>Utilizzo

| Nome                                             | Tipo   | Obbligatoria | valore                                                                  |
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
