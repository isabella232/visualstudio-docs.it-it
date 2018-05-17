---
title: Controllo della versione di Team Foundation
description: Connessione a Team Foundation Server o a Visual Studio Team Services con il controllo della versione di Team Foundation.
author: asb3993
ms.author: amburns
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: f892209faeb06ca703d28016457e9ba4ab86ccda
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/08/2018
---
# <a name="connecting-to-team-foundation-version-control"></a>Connessione al controllo della versione di Team Foundation 

Visual Studio Team Services (VSTS) e Team Foundation Server (TFS) mettono a disposizione due modelli di controllo della versione: Git, un controllo della versione distribuito, e il controllo della versione di Team Foundation (TFVC), un controllo della versione centralizzato. Questo articolo offre una panoramica del controllo della versione di Team Foundation con Visual Studio per Mac e rappresenta un punto di partenza per l'uso di questo strumento.

> [!NOTE]
> **Nota**: il controllo della versione di Team Foundation Version è attualmente in anteprima e alcune funzionalità non sono ancora completamente operative. Presto saranno disponibili altre modifiche.

## <a name="requirements"></a>Requisiti

* Visual Studio per Mac versione 7.5 o successiva.
* Visual Studio Team Server o Team Foundation Server 2013 o versione successiva
* Un progetto in Visual Studio Team Services o Team Foundation Server configurato per l'uso del controllo della versione di Team Foundation.

## <a name="installation"></a>Installazione

Da Visual Studio per Mac scegliere il menu **Visual Studio > Estensioni**. Cercare "Controllo della versione di Team Foundation" e installare l'estensione **Controllo della versione di Team Foundation**. Quando richiesto, riavviare l'IDE.

## <a name="using-the-add-in"></a>Uso del componente aggiuntivo

Dopo aver installato l'estensione, selezionare il menu **Controllo della versione > VSTS/TFS > Connetti a Controllo della versione di Team Foundation**. 

![Aggiungere un server del controllo della versione di Team Foundation](media/tfvc-add-remove-server.png)


Per iniziare, scegliere Visual Studio Team Services o Team Foundation Server:

![Connettersi a un server del controllo della versione di Team Foundation](media/tfvc-choose-server-type.png)

Immettere le credenziali: 

![Accedere a un server del controllo della versione di Team Foundation](media/tfvc-login.png)

Scegliere quindi i progetti a cui si vuole accedere: 

![Scegliere i progetti](media/tfvc-choose-projects.png)

Per continuare, chiudere le finestre di dialogo e quindi usare il menu **Controllo della versione > TFS/VSTS > Esplora controllo codice sorgente** per cercare il codice sorgente.

> [!WARNING]
> **Problema noto**: in questa versione di anteprima, la prima volta che si apre Esplora controllo codice sorgente è necessario creare una nuova area di lavoro.

![Esplora origini](media/tfvc-source-explorer.png)

Da Esplora origini è possibile cercare il codice sorgente nel server ed eseguire le azioni seguenti:

- Gestione di aree di lavoro (creazione, modifica o eliminazione).
- Spostamento all'interno della struttura del progetto.
- Eseguire il mapping di progetti.
- Acquisizione di progetti.
- Blocco e sblocco di file.
- Ridenominazione di file.
- Eliminazione di file.
- Aggiunta di un nuovo file.
- Estrazione.
- Archiviazione.
- Visualizzazione della cronologia delle modifiche.
- Confronto delle modifiche.

## <a name="creating-a-new-workspace"></a>Creazione di una nuova area di lavoro

In Esplora controllo codice sorgente fare clic sul pulsante **Gestisci aree di lavoro**. 

![Gestisci aree di lavoro](media/tfvc-manage-workspaces.png)

Fare clic su **Aggiungi** per creare una nuova area di lavoro.

![Crea l'area di lavoro](media/tfvc-create-workspace.png)

Specificare un nome per l'area di lavoro e quindi fare clic su **Aggiungi Cartella di lavoro**  per eseguire il mapping del progetto in una cartella locale nel computer.

Al termine, fare clic su **OK** e quindi chiudere la finestra di dialogo Gestisci aree di lavoro. È ora possibile acquisire file tramite Esplora origini e iniziare.