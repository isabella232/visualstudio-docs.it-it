---
title: wsl-install
description: devinit tool wsl-install.
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
ms.openlocfilehash: 448df85f9a67189d22a8d371c1d5ec30b960928a9242c05f44e07ba5eb198bc2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121418028"
---
# <a name="wsl-install"></a>wsl-install

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione a GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è rivolta alle esperienze in continua evoluzione per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro Visual Studio cloud. Nell'ambito di `devinit` questo e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Lo `wsl-install` strumento viene usato per installare le distribuzioni Linux per [sottosistema Windows per Linux](/windows/wsl/) (WSL).

> [!IMPORTANT]
> Lo `wsl-install` strumento richiede che WSL 2 sia già abilitato in Windows. Se per qualche motivo WSL 2 non è abilitato, è possibile seguire la documentazione [di installazione di WSL](https://docs.microsoft.com/windows/wsl/install-win10). È anche possibile usare lo [strumento windowsfeature-enable](tool-windowsfeature-enable.md) per abilitare le funzionalità Windows necessarie.

## <a name="usage"></a>Utilizzo

Se entrambe `input` le proprietà e vengono omesse o vuote, lo strumento seguirà `additionalOptions` il [comportamento](#default-behavior) predefinito descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                             |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà comments facoltativa. Non usato.                             |
| [**Input**](#input)                              | string | Sì      | Distribuzione da installare. Per informazioni [dettagliate,](#input) vedere Input di seguito.     |
| [**additionalOptions**](#additional-options)     | stringa | No       | Per [informazioni dettagliate, vedere](#additional-options) Opzioni aggiuntive di seguito.  |

### <a name="input"></a>Input

URI per il pacchetto di distribuzione dell'applicazione AppX ( `.appx` ) contenente la distribuzione da distribuire. L'URI deve puntare a un archivio che contiene un singolo nella radice dell'archivio `.appx` o all'interno di un archivio `install.tar.gz` `.appx` interno. Di seguito sono riportati alcuni esempi di distribuzione supportate:

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
> Le distribuzioni Arm Linux non sono attualmente supportate GitHub Codespaces.

### <a name="additional-options"></a>Opzioni aggiuntive

Sono supportate più opzioni aggiuntive:

| Nome                      | Tipo      | Obbligatoria | valore                                                                                                                                                                                    |
|---------------------------|-----------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --wsl-version             | stringa    | No       | Versione di WSL da usare. Il valore predefinito è 2.                                                                                                                                  |
| --post-create-command     | stringa    | No       | Comando da eseguire all'interno della distribuzione Linux al termine dell'installazione. Il comando deve essere formattato come singola parola o racchiuso tra virgolette. Il valore predefinito è nessun comando.  |

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `wsl-install` strumento è l'errore perché la proprietà , la distribuzione da `input` installare, è obbligatoria.

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito sono riportati esempi di come eseguire `wsl-install` usando `.devinit.json` un oggetto .

#### <a name="devinitjson-that-will-install-ubuntu-2004"></a>.devinit.jsin verrà installato Ubuntu 20.04:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-ubuntu-2004-and-perform-a-post-create-command"></a>.devinit.jsche installerà Ubuntu 20.04 ed eseguirà un comando post-creazione:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'echo Hello from Ubuntu!'"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-ubuntu-2004-and-perform-a-post-create-command-that-configures-the-packages-listed"></a>.devinit.jsin verrà installato Ubuntu 20.04 e verrà eseguito un comando post-creazione che configura i pacchetti elencati:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'apt-get update && apt-get install g++ gcc g++-9 gcc-9 cmake gdb ninja-build zip rsync -y'"
        }
    ]
}
```
