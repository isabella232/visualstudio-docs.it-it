---
title: OpenCV
description: Esempio di personalizzazione che usa devinit per usare sia Linux che Windows per il repository OpenCV.
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
ms.openlocfilehash: 319f560e4661f12acbef941692e5fd2c257c25ee
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710345"
---
# <a name="opencv"></a>OpenCV

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è incentrata sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di Visual Studio di lavoro. Come parte di questo `devinit` e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community per sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Questo esempio illustra come personalizzare GitHub [Codespace per](https://github.com/features/codespaces) sviluppare con progetti multipiattaforma, ad esempio [opencv/OpenCV.](https://github.com/opencv/opencv)

Le personalizzazioni seguenti sono già applicate al fork [microsoft/OpenCV](https://github.com/microsoft/opencv) e consentono di compilare la destinazione Windows e Ubuntu.

## <a name="customization-with-devcontainerjson-and-devinitjson"></a>Personalizzazione con devcontainer.json e devinit.json

La `.devcontainer` directory deve contenere i file seguenti:

* devcontainer.json
* devinit.json

### <a name="devcontainerjson"></a>devcontainer.json

Di seguito è riportato il contenuto del file _devcontainer.json._

```json
{
  "postCreateCommand": "devinit init"
}
```

Avvia `postCreateCommand` lo strumento [devinit,](devinit-and-codespaces.md) che usa _devinit.json._

### <a name="devinitjson"></a>devinit.json

Di seguito è riportato il contenuto del file [_devinit.json._](devinit-json.md)

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

_Devinit.json_ è il file utilizzato dallo strumento [devinit](devinit-and-codespaces.md) e deve essere nella stessa directory _di devcontainer.json._

In questo esempio, lo strumento [wsl-install](tool-wsl-install.md) viene usato per creare un'istanza WSL che esegue Ubuntu 20.04 e per il provisioning con strumenti di sviluppo C++ essenziali.
## <a name="targeting-windows-or-linux"></a>Destinazione Windows o Linux

Viene sempre creata una configurazione di Windows predefinita denominata `x64-Debug` .

Aggiungendo i file indicati in precedenza, al momento della creazione dell'istanza di Codespace, Visual Studio effettua il provisioning di una nuova connessione SSH nel [Gestione connessioni](/cpp/linux/connect-to-your-remote-linux-computer)e crea una nuova configurazione nel selettore di configurazione destinato all'istanza di Ubuntu tramite la connessione SSH.

![Configurazione per Ubuntu](media/wsl-ssh-linux-configuration.png).

Selezionando la configurazione evidenziata destinata a WSL, è possibile compilare ed eseguire il debug delle destinazioni di compilazione di OpenCV.
