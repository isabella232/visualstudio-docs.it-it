---
title: Controllo della versione di Team Foundation
description: Connessione a Team Foundation Server o a Visual Studio Team Services con il controllo della versione di Team Foundation.
author: asb3993
ms.author: amburns
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 58d0fc5c31b02574661f8b86a4ae8bcaf393be3a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693773"
---
# <a name="connecting-to-team-foundation-version-control"></a>Connessione al controllo della versione di Team Foundation 

> [!NOTE]
> **Nota**: il controllo della versione di Team Foundation Version è attualmente in anteprima e alcune funzionalità non sono ancora completamente operative. Inviare il proprio feedback su eventuali problemi riscontrati alla [community degli sviluppatori](https://developercommunity.visualstudio.com/spaces/41/index.html). Presto saranno disponibili altre modifiche.

Visual Studio Team Services (VSTS) e Team Foundation Server (TFS) mettono a disposizione due modelli di controllo della versione: Git, un controllo della versione distribuito, e il controllo della versione di Team Foundation (TFVC), un controllo della versione centralizzato. Questo articolo offre una panoramica del controllo della versione di Team Foundation con Visual Studio per Mac e rappresenta un punto di partenza per l'uso di questo strumento.

## <a name="requirements"></a>Requisiti

* Visual Studio per Mac versione 7.5 o successiva.
* Visual Studio Team Services o Team Foundation Server 2013 e versioni successive
* Un progetto in Visual Studio Team Services o Team Foundation Server configurato per l'uso del controllo della versione di Team Foundation.

## <a name="installation"></a>Installazione

In Visual Studio per Mac scegliere **Visual Studio > Estensioni...** dal menu. Nella scheda **Raccolta** selezionare **Controllo della versione > Controllo della versione di Team Foundation per TFS e VSTS** e fare clic su **Installa…**:

  ![Gestione estensioni](media/tfvc-install.png) 

Seguire i prompt per installare l'estensione. Al termine dell'installazione, riavviare l'IDE.

## <a name="using-the-add-in"></a>Uso del componente aggiuntivo

Dopo aver installato l'estensione, selezionare la voce di menu **Controllo della versione > TFS/VSTS > Connetti a Controllo della versione di Team Foundation**. Fare clic su **Aggiungi** per aggiungere un nuovo account: 

![Aggiungere un server del controllo della versione di Team Foundation](media/tfvc-add-remove-server.png)

Per iniziare, scegliere Visual Studio Team Services o Team Foundation Server:

![Connettersi a un server del controllo della versione di Team Foundation](media/tfvc-choose-server-type.png)

Immettere le credenziali e fare clic su **Accedi**: 

![Accedere a un server del controllo della versione di Team Foundation](media/tfvc-login.png)

Dopo l'accesso, selezionare i progetti a cui si vuole accedere e premere **OK**: 

![Scegliere i progetti](media/tfvc-choose-projects.png)

Selezionare la voce di menu **Controllo della versione > TFS/VSTS > Esplora controllo codice sorgente** per aprire lo strumento che consente di esplorare il codice sorgente.

> [!IMPORTANT]
> **Problema noto**: in questa versione di anteprima, la prima volta che si apre Esplora controllo codice sorgente è necessario [creare una nuova area di lavoro](#creating-a-new-workspace).

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

Per creare una nuova area di lavoro, fare clic sul pulsante **Aggiungi**.

![Crea l'area di lavoro](media/tfvc-create-workspace.png)

Specificare un nome per l'area di lavoro e quindi fare clic su **Aggiungi Cartella di lavoro**  per eseguire il mapping del progetto in una cartella locale nel computer.

Al termine, fare clic su **OK** e quindi chiudere la finestra di dialogo Gestisci aree di lavoro. È ora possibile acquisire file tramite Esplora origini e iniziare.

## <a name="troubleshooting"></a>Risoluzione dei problemi

### <a name="problems-using-basic-authentication"></a>Problemi relativi all'uso dell'autenticazione di base

Per eseguire l'autenticazione con un server sono disponibili diverse opzioni:

- Oauth
- Basic
- Ntlm

Per usare l'autenticazione di base è necessario abilitare **credenziali di autenticazione alternative** in VSTS seguendo questa procedura:

1. Accedere all'account VSTS come proprietario dell'account (https://{account}.visualstudio.com).
2. Nella barra degli strumenti dell'account, selezionare l'icona a forma di ingranaggio e quindi **Criteri**:  ![Opzione delle impostazioni dei criteri selezionata](media/tfvc-auth2.png) 
3. Verificare le impostazioni di connessione dell'applicazione. Modificare queste impostazioni in base ai propri criteri di sicurezza: ![Opzione delle impostazioni dei criteri selezionata](media/tfvc-auth.png)  

### <a name="i-do-not-see-anything-in-tfvc"></a>Nel controllo della versione di Team Foundation non viene visualizzato nulla

Per configurare il controllo della versione di Team Foundation nel computer di sviluppo, è **necessario** creare un'area di lavoro, come descritto nella sezione [Creazione di una nuova area di lavoro](#creating-a-new-workspace).

In Esplora controllo codice sorgente premere il pulsante **Gestisci aree di lavoro**. Seguire i passaggi per eseguire il mapping del progetto team a una cartella sul computer di sviluppo.

### <a name="i-do-not-see-any--all-of-my-projects"></a>Non viene visualizzato alcun progetto

Dopo l'autenticazione viene visualizzato l'elenco dei progetti. Per impostazione predefinita, vengono visualizzati solo i progetti Team Foundation Server. Per visualizzare altri tipi di progetti, selezionare la casella "See all projects" (Visualizza tutti i progetti).

Tenere presente che i progetti contenuti nel server non verranno visualizzati se non si hanno i privilegi corretti.

#### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Viene visualizzato l'errore "Cannot create the workspace. Please, try again" (Impossibile creare l'area di lavoro. Riprovare.)

Quando si tenta di [creare una nuova area di lavoro](#creating-a-new-workspace), verificare che siano soddisfatte le condizioni seguenti:

- Il nome dell'area di lavoro non deve contenere caratteri non validi.
- Il nome deve essere composto da un massimo di 64 caratteri.
- Il percorso locale non può essere usato da altre aree di lavoro.