---
title: Distribuire un'estensione del modello di livello
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, deploying extensions
- layer models, deploying extensions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 98697642135627173c5a6f31e90bf1dd1d0caeaf
ms.sourcegitcommit: 8cdc6e2ad2341f34bd6b02859a7c975daa0c9320
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2018
ms.locfileid: "53307752"
---
# <a name="deploy-a-layer-model-extension"></a>Distribuire un'estensione del modello di livello

Altri utenti di Visual Studio possono installare estensioni di modellazione del livello creati tramite Visual Studio.

## <a name="install-your-extension"></a>Installare l'estensione

L'estensione viene compilata in un file VSIX, che è possibile installare in altri computer. È anche possibile installarla nel computer di sviluppo, per renderla disponibile nell'istanza principale di Visual Studio.

### <a name="to-install-the-extension"></a>Per installare l'estensione

1. Nel progetto che contiene **source.vsix.manifest**, aprire il *bin* directory in Esplora File.

2. Copia il  **\*VSIX** file nel computer in cui si desidera installare l'estensione.

3. Nel computer di destinazione fare doppio clic sul file con estensione VSIX in Esplora risorse.

    Verrà aperto il programma di installazione di VSIX.

### <a name="to-uninstall-the-extension"></a>Per disinstallare l'estensione

1.  In Visual Studio sul **degli strumenti** menu, fare clic su **estensioni e aggiornamenti**.

2.  Fare clic sul nome dell'estensione e quindi fare clic su **Disinstalla**.

## <a name="install-an-extension-on-team-foundation-server"></a>Installare un'estensione in Team Foundation Server

Server di Team Foundation Server non è in genere installato Visual Studio e pertanto non è possibile installare l'estensione VSIX facendovi doppio clic. È necessario installare manualmente l'estensione.

### <a name="to-install-your-layer-extension-on-a-team-foundation-server-server"></a>Per installare l'estensione del livello in un server Team Foundation Server

1.  Copia il. *vsix* file dal computer di sviluppo nel computer di Team Foundation Server (TFS).

     Inserire il file VSIX in uno dei percorsi seguenti:

    -   Per installare per tutti gli utenti e i servizi:

         %ProgramFiles%\Microsoft Visual Studio [versione]\Common7\IDE\Extensions\Microsoft

    -   Per installare solo per il servizio di rete che esegue la compilazione:

         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version]\Extensions\Microsoft

    -   Se è stata configurata la compilazione per l'esecuzione in modalità interattiva come un utente specifico, è possibile installare solo per quell'utente:

         %LocalAppData%\Microsoft\VisualStudio\\[version]\Extensions\Microsoft

2.  Espandere ogni file VSIX in una cartella nello stesso percorso:

    1.  Modificare l'estensione del file da **VSIX** al **zip**.

    2.  Estrarre il contenuto del file ZIP in una cartella.

    3.  Eliminare il file ZIP.

3.  Riavviare TFS.
