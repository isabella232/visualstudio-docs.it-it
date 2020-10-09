---
title: wsl-install
description: strumento devinit WSL-install.
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
ms.openlocfilehash: 950ca7f1e9c43123b206893dbc6a07da7c3743ec
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862860"
---
# <a name="wsl-install"></a>wsl-install

Lo `wsl-install` strumento viene usato per installare le distribuzioni di Linux per il [sottosistema Windows per Linux](/windows/wsl/) (WSL).

Lo `wsl-install` strumento richiede che WSL 2 sia già abilitato in Windows. Se per qualche motivo WSL2 non è abilitato, è possibile abilitare WSL2 usando lo strumento [WindowsFeature-Enable](tool-windowsfeature-enable.md) e il nome della funzionalità `Microsoft-Windows-Subsystem-Linux` .

## <a name="usage"></a>Uso

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                             |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.                             |
| [**input**](#input)                              | string | Sì      | Distro da installare. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito.     |
| [**additionalOptions**](#additional-options)     | stringa | No       | Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.  |

### <a name="input"></a>Input

URI del pacchetto di distribuzione dell'applicazione AppX ( `.appx` ) che contiene la distribuzione da distribuire. L'URI deve puntare a un `.appx` archivio che contiene un singolo oggetto `install.tar.gz` nella radice dell'archivio o all'interno di un `.appx` archivio interno. Esempi di distribuzioni supportate includono:

| Distribuzione                          | Uri                                                           |
|---------------------------------|---------------------------------------------------------------|
| Ubuntu 20.04                    | https://aka.ms/wslubuntu2004                                  |
| Ubuntu 18.04                    | https://aka.ms/wsl-ubuntu-1804                                |
| Ubuntu 16.04                    | https://aka.ms/wsl-ubuntu-1604                                |
| Debian GNU/Linux                | https://aka.ms/wsl-debian-gnulinux                            |
| Kali Linux                      | https://aka.ms/wsl-kali-linux-new                             |
| OpenSUSE Leap 42                | https://aka.ms/wsl-opensuse-42                                |
| SUSE Linux Enterprise Server 12 | https://aka.ms/wsl-sles-12                                    |

> [!NOTE]
> Le distribuzioni Linux ARM non sono attualmente supportate negli spazi di codespace di GitHub.

### <a name="additional-options"></a>Opzioni aggiuntive

Sono supportate più opzioni aggiuntive:

| Nome                      | Tipo      | Obbligatoria | valore                                                                                                                                                                                    |
|---------------------------|-----------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --WSL-Version             | stringa    | No       | Versione di WSL da usare. Il valore predefinito è 2.                                                                                                                                  |
| --Post-creazione-comando     | stringa    | No       | Comando da eseguire all'interno della distribuzione di Linux una volta completata l'installazione. Il comando deve essere formattato come una singola parola o racchiuso tra virgolette. Il valore predefinito è no Command.  |

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `wsl-install` strumento è l'errore come la `input` proprietà, la distro da installare, è obbligatoria.

## <a name="example-usage"></a>Esempio di utilizzo

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will install Ubuntu 20.04.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004"
        },
        {
            "comments": "Example that will install Ubuntu 20.04 using WSL2, and echo 'Hello from Ubuntu!' after installing.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'echo Hello from Ubuntu!'"
        },
        {
            "comments": "Example that will install Ubuntu 20.04 using WSL2, and configure it with various packages.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'apt-get update && apt-get install g++ gcc g++-9 gcc-9 cmake gdb ninja-build zip rsync -y'"
        }
    ]
}
```