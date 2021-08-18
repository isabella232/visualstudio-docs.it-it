---
title: OpenCV
description: Esempio di personalizzazione con devinit per usare sia Linux che Windows per il repository OpenCV.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 2d7750d6a77965527b4bf396afd8de094762821923c543a06d184509c238b205
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452832"
---
# <a name="opencv"></a>OpenCV

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione a GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è rivolta alle esperienze in continua evoluzione per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro Visual Studio cloud. Nell'ambito di `devinit` questo e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Questo esempio illustra come personalizzare GitHub [codespace per](https://github.com/features/codespaces) sviluppare con progetti multipiattaforma, ad esempio [opencv/OpenCV.](https://github.com/opencv/opencv)

Le personalizzazioni seguenti sono già applicate al fork [microsoft/OpenCV](https://github.com/microsoft/opencv) e consentono di compilare con destinazione Windows e Ubuntu.

## <a name="customization-with-devcontainerjson-and-devinitjson"></a>Personalizzazione con devcontainer.json e devinit.json

La `.devcontainer` directory deve contenere i file seguenti:

* devcontainer.json
* devinit.jssu

### <a name="devcontainerjson"></a>devcontainer.json

Di seguito è riportato il contenuto del _devcontainer.jsnel_ file .

```json
{
  "postCreateCommand": "devinit init"
}
```

avvia `postCreateCommand` lo strumento  [devinit,](devinit-and-codespaces.md) che usadevinit.js _in_.

### <a name="devinitjson"></a>devinit.jssu

Di seguito è riportato il contenuto del [_devinit.jsnel_](devinit-json.md) file .

```json
{
    "run": [
        {
            "comments": "Example that will install Ubuntu 20.04 using WSL2, and configure it with various packages useful for C++ development.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'apt-get update && apt-get install g++ gcc g++-9 gcc-9 cmake gdb ninja-build zip rsync -y'"
        }
    ]
}
```

Il _devinit.jsè_ il file utilizzato dallo strumento [devinit](devinit-and-codespaces.md) e deve essere nella stessa directory di _devcontainer.jsin_.

In questo esempio viene usato lo strumento [wsl-install](tool-wsl-install.md) per creare un'istanza di WSL che esegue Ubuntu 20.04 ed eseguire il provisioning con strumenti di sviluppo C++ essenziali.
## <a name="targeting-windows-or-linux"></a>Destinazione Windows o Linux

Viene sempre creata una configurazione di compilazione Windows predefinita denominata `x64-Debug` .

Aggiungendo i file indicati in precedenza, al momento della creazione dell'istanza di Codespace, Visual Studio effettua il provisioning di una nuova connessione SSH nel [Gestione connessioni](/cpp/linux/connect-to-your-remote-linux-computer)e crea una nuova configurazione nella selezione configurazione destinata all'istanza di Ubuntu tramite la connessione SSH.

![Configurazione per Ubuntu](media/wsl-ssh-linux-configuration.png).

Selezionando la configurazione evidenziata destinata a WSL, è possibile compilare ed eseguire il debug delle destinazioni di compilazione di OpenCV.
