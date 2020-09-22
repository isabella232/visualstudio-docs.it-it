---
title: vcpkg-install
description: strumento devinit vcpkg-install.
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
ms.openlocfilehash: 7c974b5747c38231ff4115aba17a8e3728672851
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005988"
---
# <a name="vcpkg-install"></a>vcpkg-install

Lo `vcpkg-install` strumento viene usato per acquisire le librerie C/C++, denominate porte, usando [vcpkg](https://github.com/microsoft/vcpkg).

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.                                                   |
| [**input**](#input)                              | string | Sì      | Pacchetti da installare. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito.                       |
| [**additionalOptions**](#additional-options)     | stringa | No       | Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.                        |

### <a name="input"></a>Input

La `input` proprietà deve essere dell'oggetto `name` `vcpkg` da installare o di un elenco di nomi separati da spazi per installare più pacchetti. Un elenco delle porte disponibili è reperibile nel [repository GitHub vcpkg](https://github.com/microsoft/vcpkg/tree/master/ports).

### <a name="additional-options"></a>Opzioni aggiuntive

Le opzioni aggiuntive vengono passate direttamente al comando [vcpkg](https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true) e sono documentate nel [repository GitHub vcpkg](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md).

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `vcpkg-install` strumento è l'errore, come `input` richiesto.

## <a name="example-usage"></a>Esempio di utilizzo

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs the sdl2 port.",
            "tool": "vcpkg-install",
            "input": "sdl2",
        },
        {
            "comments": "Installs the sdl2 and sqlite3 ports.",
            "tool": "vcpkg-install",
            "input": "sdl2 sqlite3"
        }
    ]
}
```
