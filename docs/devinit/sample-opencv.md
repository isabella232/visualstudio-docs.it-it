---
title: OpenCV
description: Personalizzazione di esempio con la devinilt per la destinazione sia di Linux che di Windows per il repository OpenCV.
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
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672467"
---
# <a name="opencv"></a>OpenCV

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione agli spazi dei codebase di GitHub da Visual Studio 2019 non sarà più supportata e l'anteprima privata è stata conclusa. Ci stiamo concentrando sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e per le soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro di Visual Studio. Come parte di questo `devinit` e gli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio per informazioni sulle future anteprime e informazioni di roadmap.

Questo esempio illustra come personalizzare gli spazi dei nomi di [GitHub per lo](https://github.com/features/codespaces) sviluppo con progetti multipiattaforma, ad esempio [OpenCV/OpenCV](https://github.com/opencv/opencv).

Le seguenti personalizzazioni sono già state applicate alla divisione [Microsoft/OpenCV](https://github.com/microsoft/opencv) e consentono a di compilare come destinazione Windows e Ubuntu.

## <a name="customization-with-devcontainerjson-and-devinitjson"></a>Personalizzazione con devcontainer.json e devinit.json

La `.devcontainer` Directory deve contenere i file seguenti:

* devcontainer.json
* devinit.js

### <a name="devcontainerjson"></a>devcontainer.json

Di seguito è riportato il contenuto del _devcontainer.jssu_ file.

```json
{
  "postCreateCommand": "devinit init"
}
```

Il `postCreateCommand` Avvia lo strumento  [devinit](devinit-and-codespaces.md) , che utilizza _devinit.js_.

### <a name="devinitjson"></a>devinit.js

Di seguito è riportato il contenuto del [_devinit.jssu_](devinit-json.md) file.

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

Il _devinit.jsin_ è il file utilizzato dallo strumento [devinit](devinit-and-codespaces.md) e deve trovarsi nella stessa directory di _devcontainer.jsin_.

In questo esempio, lo strumento [WSL-install](tool-wsl-install.md) viene usato per creare un'istanza di WSL che esegue Ubuntu 20,04 e provisioning con gli strumenti di sviluppo C++ essenziali.
## <a name="targeting-windows-or-linux"></a>Destinazione di Windows o Linux

Una configurazione di compilazione predefinita destinata A Windows viene sempre creata denominata `x64-Debug` .

Se si aggiungono i file menzionati in precedenza, durante la creazione dell'istanza di codespace, Visual Studio effettua il provisioning di una nuova connessione SSH nella [gestione connessione](/cpp/linux/connect-to-your-remote-linux-computer)e crea una nuova configurazione nella selezione configurazione che ha come destinazione l'istanza di Ubuntu tramite la connessione SSH.

![Configurazione destinata a Ubuntu](media/wsl-ssh-linux-configuration.png).

Selezionando la configurazione evidenziata destinata a WSL, è possibile compilare ed eseguire il debug delle destinazioni di compilazione di OpenCV.
