---
title: windowsfeature-enable
description: strumento devinit WindowsFeature-Enable.
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
ms.openlocfilehash: 6e3d2fdaf6be019cae504d4f71258d410d232ff5
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400205"
---
# <a name="windowsfeature-enable"></a>windowsfeature-enable

Lo `windowsfeature-enable` strumento viene usato per abilitare le funzionalità di Windows.

## <a name="usage"></a>Utilizzo

| Nome                                             | Type   | Obbligatoria | valore                                                                    |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.                                    |
| [**input**](#input)                              | string | Sì      | Funzionalità di Windows da installare. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito.   |
| [**additionalOptions**](#additional-options)     | stringa | No       | Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.         |

### <a name="input"></a>Input

La `input` proprietà deve essere `name` della proprietà dell'oggetto `windows feature` da installare. È possibile trovare un elenco delle funzionalità disponibili eseguendo il `Get-WindowsFeature` comando PowerShell cmd.

### <a name="additional-options"></a>Additional-Options

Nessuno.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `windowsfeature-enable` strumento è l'errore, come `input` richiesto.

## <a name="example-usage"></a>Esempio di utilizzo

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "comments": "Installs IIS.",
            "tool": "windowsfeature-enable",
            "input": "web-server",
        },
        {
            "comments": "Installs the .NET Framework 3.5.",
            "tool": "windowsfeature-enable",
            "input": "net-framework-features"
        },
        {
            "comments": "Installs the .NET Framework 4.5.",
            "tool": "windowsfeature-enable",
            "input": "net-framework-45-features"
        },
        {
            "comments": "Installs Windows Subsystem for Linux 2.0.",
            "tool": "windowsfeature-enable",
            "input": "Microsoft-Windows-Subsystem-Linux"
        }
    ]
}
```
