---
ms.topic: include
ms.openlocfilehash: dbf7482acb02c6347c9c0d0765ef962cfb43a050
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2018
---
## <a name="initialize-debug-assets-with-the-vs-code-extension"></a>Inizializzare gli asset di debug con l'estensione di Visual Studio Code
È prima di tutto necessario configurare il progetto del codice in modo che Visual Studio Code possa comunicare con l'ambiente di sviluppo in Azure. L'estensione di Visual Studio Code per Connected Environment fornisce un comando helper per impostare la configurazione di debug. 

Aprire il **Riquadro comandi** (tramite il menu **Visualizza | Riquadro comandi**) e usare il completamento automatico per digitare e selezionare questo comando: `Connected Environment: Create configuration files for connected development`. 

Viene così aggiunta la configurazione di debug per Connected Environment nella cartella `.vscode`.

![](../media/vsce-command-palette.png)

> [!Note]
> **IMPORTANTE**: a causa di un bug, chiudere e riaprire Visual Studio Code prima di procedere.