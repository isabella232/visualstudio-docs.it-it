---
title: Pubblicare un'app Node.js nel Servizio app Linux
description: È possibile pubblicare applicazioni Node.js create in Visual Studio nel Servizio app Linux in Azure
ms.date: 11/22/2019
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-javascript
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 397374c1df912707d308acdf5df9fcdbc9d5221b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625793"
---
# <a name="publish-a-nodejs-application-to-azure-linux-app-service"></a>Pubblicare un'applicazione Node.js in Azure (Servizio app Linux)

Questa esercitazione illustra l'attività di creazione di una semplice applicazione Node.js e della pubblicazione in Azure.

Nella pubblicazione di un'applicazione Node.js in Azure, sono disponibili diverse opzioni, tra cui il Servizio app di Azure, una macchina virtuale con un sistema operativo scelto dall'utente, il servizio Azure Container per la gestione con Kubernetes, un'istanza di contenitore con Docker e altro ancora. Per altre informazioni su ognuna di queste opzioni, vedere [Calcolo](https://azure.microsoft.com/product-categories/compute/).

Per questa esercitazione, l'app viene distribuita nel [Servizio app Linux](/azure/app-service/containers/app-service-linux-intro).
Il Servizio app Linux consente di distribuire un contenitore Docker di Linux per eseguire l'applicazione Node.js (anziché il Servizio app di Windows, che esegue le app Node.js su IIS in Windows).

Questa esercitazione mostra come creare un'applicazione Node.js partendo da un template installato con gli strumenti Node.js per Visual Studio, eseguire il push del codice in un repository su GitHub, quindi effettuare il provisioning di un Servizio App Azure tramite il portale web di Azure in modo da poterlo distribuire a partire dal repository GitHub. Per usare la riga di comando per effettuare il provisioning del Servizio app di Azure ed eseguire il push del codice da un repository Git locale, vedere [Creare un'app Node.js](/azure/app-service/containers/quickstart-nodejs).

In questa esercitazione verranno illustrate le procedure per:
> [!div class="checklist"]
> * Creare un progetto Node.js
> * Creare un repository GitHub per il codice
> * Creare un Servizio app Linux in Azure
> * Distribuire in Azure

## <a name="prerequisites"></a>Prerequisiti

* È necessario che siano installati Visual Studio e il carico di lavoro di sviluppo Node.js.

    ::: moniker range=">=vs-2019"
    Se non è ancora stato installato Visual Studio 2019, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Se Visual Studio 2017 non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente.
    ::: moniker-end

    Se è necessario installare il carico di lavoro ma Visual Studio, passare a Strumenti Ottieni strumenti e  >  **funzionalità...**, che apre il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo Node.js**, quindi scegliere **Modifica**.

    ![Carico di lavoro Node.js nel programma di installazione di Visual Studio](../ide/media/quickstart-nodejs-workload.png)

* Il runtime di Node.js deve essere installato.

    Se il runtime non è installato, installare la versione LTS dal sito Web [Node.js](https://nodejs.org/en/download/). In generale, Visual Studio rileva automaticamente il runtime di Node.js installato. Se non viene rilevato un runtime installato, è possibile usare la pagina delle proprietà per configurare il progetto in modo che faccia riferimento al runtime installato (dopo aver creato un progetto, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Proprietà**).

## <a name="create-a-nodejs-project-to-run-in-azure"></a>Creare un progetto Node.js da eseguire in Azure

1. Aprire Visual Studio.

1. Creare una nuova app Express TypeScript.

    ::: moniker range=">=vs-2019"
    Premere **ESC** per chiudere la finestra iniziale. Premere **CTRL+Q** per aprire la casella di ricerca, digitare **Node.js** e scegliere **Create new Basic Azure Node.js Express 4 application** (Crea nuova applicazione Basic Azure Node.js Express 4) (TypeScript). Nella finestra di dialogo visualizzata scegliere **Crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Nella barra dei menu superiore scegliere **File**  >  **Nuovo**  >  **Project**. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **TypeScript** e quindi selezionare **Node.js**. Nel riquadro centrale scegliere **Applicazione Express 4 Node.js Azure di base** e quindi scegliere **OK**.

    ![Creare una nuova app rapida TypeScript](../javascript/media/azure-ts-express-app.png)
    ::: moniker-end
    Se non viene visualizzato il modello di progetto **Applicazione Express 4 Node.js Azure di base** è necessario aggiungere il carico di lavoro **Sviluppo Node.js**. Per istruzioni dettagliate, vedere i [Prerequisiti](#prerequisites).

    Visual Studio crea il progetto e lo apre in Esplora soluzioni (riquadro destro).

1. Premere **F5** per compilare ed eseguire l'app e assicurarsi che tutto funzioni come previsto.

1. Selezionare **File**  >  **Aggiungi al controllo del codice sorgente** per creare un repository Git locale per il progetto.

    A questo punto, è in esecuzione e viene archiviata nel controllo del codice sorgente locale un'app Node.js che usa il framework Express ed è scritta in TypeScript.

1. Modificare il progetto nel modo desiderato prima di procedere con i passaggi successivi.

## <a name="push-code-from-visual-studio-to-github"></a>Eseguire il push del codice da Visual Studio a GitHub

Per configurare GitHub per Visual Studio:

1. Assicurarsi che sia installata l'[Estensione GitHub per Visual Studio](https://visualstudio.github.com/) e abilitata tramite la voce di menu **Strumenti** > **Estensioni e aggiornamenti**.

2. Scegliere Visualizza altri elementi **dal** menu  >  **Windows**  >  **GitHub**.

    Viene visualizzata la finestra di GitHub.

3. Se non viene visualizzato il pulsante **Inizia** nella finestra di GitHub, fare clic su **File** > **Aggiungi al controllo del codice sorgente** e attendere che l'interfaccia utente si aggiorni.

    ![Aprire la finestra di GitHub](../javascript/media/azure-github-get-started.png)

4. Fare clic su **Inizia**.

    Se si è già connessi a GitHub, viene visualizzata la casella degli strumenti simile alla figura seguente.

    ![Impostazioni del repository GitHub](../javascript/media/azure-github-publish.png)

5. Completare i campi del nuovo repository da pubblicare e quindi fare clic su **Pubblica**.

    Dopo alcuni istanti, viene visualizzato un banner indicante "Il repository è stato creato".

    La sezione successiva descrive come pubblicare da questo repository a un Servizio app di Azure in Linux.

## <a name="create-a-linux-app-service-in-azure"></a>Creare un Servizio app Linux in Azure

1. Accedere al [portale di Azure](https://portal.azure.com).

2. Selezionare **Servizi app** dall'elenco dei servizi a sinistra, quindi fare clic su **Aggiungi**.

3. Se necessario, creare un nuovo gruppo di risorse e piano del servizio app in cui includere la nuova app.

4. Assicurarsi di impostare il **sistema operativo** su **Linux** e impostare lo **Stack di runtime** nella versione di Node.js necessaria, come illustrato nella figura.

    ![Creare un Servizio app Linux](../javascript/media/azure-create-appservice-annotated.png)

5. Fare clic su **Crea** per creare il servizio app.

    La distribuzione potrebbe richiedere alcuni minuti.

6. Dopo la distribuzione, passare alla sezione **Impostazioni applicazione** e aggiungere un'impostazione con un nome per `SCM_SCRIPT_GENERATOR_ARGS` e un valore per `--node`.

    ![Impostazioni applicazione](../javascript/media/azure-script-generator-args.png)

    > [!WARNING]
    > Il processo di distribuzione del Servizio app usa una serie di regole euristiche per determinare il tipo di applicazione da provare ed eseguire. Se viene rilevato un file .*sln* nel contenuto distribuito, processo presuppone che venga distribuito un progetto basato su MSBuild. L'impostazione aggiunta in precedenza sostituisce questa logica e specifica esplicitamente che si tratta di un'applicazione Node.js. Senza questa impostazione, l'applicazione Node.js non verrà distribuita se il file .*sln* fa parte del repository distribuito al Servizio app.

7. In **Impostazioni applicazione** aggiungere un'altra impostazione con il nome e il valore `WEBSITE_NODE_DEFAULT_VERSION` `8.9.0` .

8. Dopo la distribuzione, aprire il Servizio app e selezionare **Opzioni di distribuzione**.

    ![Opzioni di distribuzione](../javascript/media/azure-deployment-options.png)

9. Fare clic su **Scegli origine**, quindi scegliere **GitHub** e quindi configurare le autorizzazioni necessarie.

    ![Autorizzazioni GitHub](../javascript/media/azure-choose-source.png)

10. Selezionare il repository e il ramo da cui eseguire la pubblicazione, quindi selezionare **OK**.

    ![Pubblicare nel servizio app di Linux](../javascript/media/azure-repo-and-branch.png)

    Durante la sincronizzazione viene visualizzata la pagina **Opzioni di distribuzione**.

    ![Distribuzione e sincronizzazione con GitHub](../javascript/media/azure-deployment-options-sync.png)

    Una volta che la sincronizzazione è stata completata, verrà visualizzato un segno di spunta.

    Il sito esegue ora l'applicazione Node.js dal repository GitHub ed è accessibile all'URL creato per il Servizio app di Azure (per impostazione predefinita, il nome assegnato al Servizio app di Azure seguito da ".azurewebsites.net").

## <a name="modify-your-app-and-push-changes"></a>Modificare le app ed eseguire il push delle modifiche

1. Aggiungere il codice visualizzato di seguito in *app.ts* dopo la riga `app.use('/users', users);`. Verrà aggiunta un'API REST nell'URL */api*.

    ```typescript
    app.use('/api', (req, res, next) => {
        res.json({"result": "success"});
    });
    ```

2. Compilare il codice e provarlo in locale, quindi archiviarlo ed eseguirne il push in GitHub.

    Nel portale di Azure, sono necessari alcuni minuti per rilevare le modifiche nel repository GitHub, quindi viene avviata una nuova sincronizzazione della distribuzione. Sarà simile alla figura riportata di seguito.

    ![Modifica e sincronizzazione](../javascript/media/azure-changes-detected.png)

3. Al termine della distribuzione, passare al sito pubblico e accodare */api* all'URL. Viene restituita la risposta JSON.

## <a name="troubleshooting"></a>Risoluzione dei problemi

* Se il processo node.exe smette di funzionare (ovvero si verifica un'eccezione non gestita), il contenitore viene riavviato.
* Durante l'avvio del contenitore, viene eseguito tramite varie regole euristiche che determinano come avviare il processo Node.js. È possibile visualizzare i dettagli dell'implementazione in [generateStartupCommand.js](https://github.com/Azure/app-service-builtin-images/blob/master/node/8.9.4/startup/generateStartupCommand.js).
* È possibile connettersi al contenitore in esecuzione tramite SSH per le indagini. Questa operazione viene eseguita agevolmente tramite il portale di Azure. Selezionare il Servizio app e scorrere verso il basso nell'elenco di strumenti fino a raggiungere **SSH** nella sezione **Strumenti di sviluppo**.
* Per facilitare la risoluzione dei problemi, passare alle impostazioni dei **log di diagnostica** per il Servizio app e modificare l'impostazione **Registrazione del contenitore Docker** da **Off** a **File system**. I log vengono creati nel contenitore in */home/LogFiles/* _docker.log* e sono accessibili nella scheda tramite SSH o FTP (S).
* È possibile assegnare un nome di dominio personalizzato al sito, anziché l'URL *.azurewebsites.net URL assegnato per impostazione predefinita. Per altre informazioni, vedere l'argomento [Eseguire il mapping di un dominio personalizzato](/azure/app-service/app-service-web-tutorial-custom-domain).
* È consigliabile eseguire la distribuzione in un sito di gestione temporanea per altri test prima di passare in produzione. Per informazioni dettagliate su come configurare questa opzione, vedere l'argomento [Creare ambienti di staging](/azure/app-service/web-sites-staged-publishing).
* Vedere le [Domande frequenti sul Servizio app in Linux ](/azure/app-service/containers/app-service-linux-faq) per le domande più comuni.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come creare un Servizio app di Linux e distribuire un'applicazione Node.js al servizio. Sono disponibili anche altre informazioni sul Servizio app di Linux.

> [!div class="nextstepaction"]
> [Servizio app di Linux](/azure/app-service/containers/app-service-linux-intro)
