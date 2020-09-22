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
ms.openlocfilehash: 115fda00f880e9c2fa1782735dd471fc3df68936
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005974"
---
# <a name="windowsfeature-enable"></a>windowsfeature-enable

Lo `windowsfeature-enable` strumento viene usato per abilitare le funzionalità di Windows.

## <a name="usage"></a>Utilizzo

| Nome                                             | Tipo   | Obbligatoria | valore                                                                    |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.                                    |
| [**input**](#input)                              | string | Sì      | Funzionalità di Windows da installare. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito.   |
| [**additionalOptions**](#additional-options)     | stringa | No       | Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.         |

### <a name="input"></a>Input

La `input` proprietà deve essere `name` della proprietà dell'oggetto `windows feature` da installare. È possibile trovare un elenco delle funzionalità disponibili eseguendo il `Get-WindowsFeature` comando PowerShell cmd.

### <a name="additional-options"></a>Opzioni aggiuntive

Nessuno.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `windowsfeature-enable` strumento è l'errore, come `input` richiesto.

## <a name="example-usage"></a>Esempio di utilizzo

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
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
