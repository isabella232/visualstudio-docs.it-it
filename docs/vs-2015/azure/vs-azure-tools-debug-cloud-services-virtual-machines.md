---
title: Debug di un servizio cloud di Azure o una macchina virtuale in Visual Studio | Microsoft Docs
description: Debug di un servizio cloud o di una macchina virtuale in Visual Studio
author: mikejo5000
manager: douge
ms.assetid: 945e06e0-2100-41af-b218-72347367ddab
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.openlocfilehash: b2c67ce81a42df4a17761fcee2dcd2f8a67c4941
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002941"
---
# <a name="debugging-an-azure-cloud-service-or-virtual-machine-in-visual-studio"></a>Debug di un servizio cloud di Azure o una macchina virtuale in Visual Studio

Visual Studio offre diverse opzioni per il debug di servizi cloud di Azure e macchine virtuali.

## <a name="debug-your-cloud-service-on-your-local-computer"></a>Il debug del servizio cloud nel computer locale

È possibile risparmiare tempo e denaro usando Azure compute emulator per il debug del servizio cloud in un computer locale. Dal debug di un servizio in locale prima di distribuirla, è possibile migliorare affidabilità e prestazioni senza pagare per tempo di calcolo. Tuttavia, potrebbero verificarsi alcuni errori solo quando si esegue un servizio cloud in Azure stesso. È possibile eseguire il debug di questi errori se si abilita il debug remoto quando si pubblica il servizio e quindi collegare il debugger a un'istanza del ruolo.

L'emulatore simula il servizio di calcolo di Azure e viene eseguito nell'ambiente locale in modo che sia possibile testare e il debug del servizio cloud prima di distribuirlo. L'emulatore gestisce il ciclo di vita delle istanze del ruolo e fornisce l'accesso alle risorse simulate, ad esempio l'archivio locale. Durante il debug o esegue il servizio da Visual Studio, avvia automaticamente l'emulatore come applicazione in background e quindi distribuisce il servizio nell'emulatore. È possibile usare l'emulatore per visualizzare il servizio quando è in esecuzione nell'ambiente locale. È possibile eseguire la versione completa o la versione express dell'emulatore. (A partire da Azure 2.3, la versione express dell'emulatore è l'impostazione predefinita). Visualizzare [tramite l'emulatore Express per eseguire e il Debug di un servizio Cloud localmente](vs-azure-tools-emulator-express-debug-run.md).

### <a name="to-debug-your-cloud-service-on-your-local-computer"></a>Per il debug del servizio cloud nel computer locale

1. Nella barra dei menu, scegliere **Debug**, **Avvia debug** per eseguire il progetto servizio cloud di Azure. In alternativa, è possibile premere F5. Si verrà visualizzato un messaggio di avvio nell'emulatore di calcolo. Quando l'emulatore viene avviato, l'icona sulla barra delle applicazioni conferma l'operazione.

    ![Nell'emulatore di Azure nell'area di notifica](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC783828.png)

2. Visualizzare l'interfaccia utente dell'emulatore di calcolo, aprire il menu di scelta rapida dell'icona di Azure nell'area di notifica e quindi selezionare **Mostra interfaccia emulatore di calcolo**.

    Il riquadro sinistro dell'interfaccia utente mostra i servizi attualmente distribuiti nell'emulatore di calcolo e le istanze del ruolo che ogni servizio è in esecuzione. È possibile scegliere il servizio o i ruoli per visualizzare le informazioni di diagnostica, registrazione e ciclo di vita nel riquadro di destra. Se si seleziona il margine superiore di una finestra inclusa, si espande per riempire il riquadro destro.

3. Passaggio tramite l'applicazione selezionando i comandi di **Debug** menu e impostando punti di interruzione nel codice. Mentre si procede attraverso l'applicazione nel debugger, i riquadri vengono aggiornati con lo stato corrente dell'applicazione. Quando si arresta il debug, la distribuzione dell'applicazione viene eliminata. Se l'applicazione include un ruolo web ed è stata impostata la proprietà azione di avvio per avviare il web browser, Visual Studio avvia l'applicazione web nel browser. Se si modifica il numero di istanze di un ruolo nella configurazione del servizio, è necessario arrestare il servizio cloud e quindi riavviare il debug in modo che è possibile eseguire il debug di queste nuove istanze del ruolo.

    **Nota:** quando si arresta l'esecuzione o debug del servizio, l'emulatore di calcolo locale e l'emulatore di archiviazione non vengono arrestati. È necessario arrestarli in modo esplicito dall'area di notifica.

## <a name="debug-a-cloud-service-in-azure"></a>Eseguire il debug di un servizio cloud in Azure

Per eseguire il debug di un servizio cloud da un computer remoto, è necessario abilitare tale funzionalità in modo esplicito quando si distribuisce il servizio cloud in modo che i servizi richiesti (ad esempio, msvsmon.exe) vengono installati nelle macchine virtuali che eseguono le istanze del ruolo. Se si non abilita il debug remoto quando il servizio è pubblicato, è necessario ripubblicare il servizio con il debug remoto abilitato.

Se si abilita il debug remoto per un servizio cloud, non avere prestazioni rallentate o sono previsti addebiti aggiuntivi. Non usare il debug remoto in un servizio di produzione, poiché i client che usano il servizio potrebbero essere compromessi.

> [!NOTE]
> Quando si pubblica un servizio cloud da Visual Studio, è possibile abilitare **IntelliTrace** per qualsiasi ruolo del servizio destinate a .NET Framework 4 o .NET Framework 4.5. Usando **IntelliTrace**, è possibile esaminare gli eventi generati in un'istanza del ruolo in passato e riprodurre il contesto da quel momento. Visualizzare [debug di un servizio cloud pubblicato con IntelliTrace e Visual Studio](http://go.microsoft.com/fwlink/?LinkID=623016) e [utilizzo di IntelliTrace](https://msdn.microsoft.com/library/dd264915.aspx).

### <a name="to-enable-remote-debugging-for-a-cloud-service"></a>Per abilitare il debug remoto per un servizio cloud

1. Aprire il menu di scelta rapida per il progetto Azure e quindi selezionare **pubblica**.

2. Selezionare il **Staging** ambiente e il **Debug** configurazione.

    Questo è solo un'indicazione. È possibile scegliere di eseguire ambienti di test in un ambiente di produzione. Tuttavia, si potrebbero influire negativamente sulle utenti se si abilita il debug remoto nell'ambiente di produzione. È possibile scegliere la configurazione di rilascio, ma la configurazione di Debug semplifica il debug.

    ![Scegliere la configurazione di Debug](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746717.gif)

3. Seguire la procedura consueta, ma selezionare la **Abilita Debugger remoto per tutti i ruoli** casella di controllo la **impostazioni avanzate** scheda.

    ![Configurazione di debug](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746718.gif)

### <a name="to-attach-the-debugger-to-a-cloud-service-in-azure"></a>Per collegare il debugger a un servizio cloud in Azure

1. In Esplora Server espandere il nodo per il servizio cloud.

2. Aprire il menu di scelta rapida per il ruolo o l'istanza del ruolo a cui si desidera collegare e quindi selezionare **collega Debugger**.

    Se si esegue il debug di un ruolo, il debugger di Visual Studio si connette a ogni istanza di tale ruolo. Il debugger si interrompe in un punto di interruzione per la prima istanza di ruolo che esegue la riga di codice e soddisfa qualsiasi condizione del punto di interruzione. Se si esegue il debug di un'istanza, il debugger si collega solo tale istanza e si interrompe in un punto di interruzione solo quando quell'istanza specifica esegue la riga di codice e soddisfa le condizioni del punto di interruzione.

    ![Collega debugger](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746719.gif)

3. Dopo che il debugger si connette a un'istanza, eseguire il debug come di consueto. Il debugger si connette automaticamente al processo host appropriato per il ruolo. A seconda che cos'è il ruolo, il debugger si connette a w3wp.exe, WaWorkerHost.exe o WaIISHost.exe. Per verificare il processo a cui è collegato il debugger, espandere il nodo dell'istanza in Esplora Server. Visualizzare [Azure Role Architecture](http://blogs.msdn.com/b/kwill/archive/2011/05/05/windows-azure-role-architecture.aspx) per altre informazioni sui processi di Azure.

    ![Selezionare una finestra di dialogo tipo di codice](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

4. Per identificare i processi a cui è collegato il debugger, aprire la finestra di dialogo processi, nella barra dei menu, scegliendo Debug, Windows, i processi. (Tastiera: Ctrl + Alt + Z) Per disconnettere un processo specifico, aprire il menu di scelta rapida e quindi selezionare **Disconnetti processo**. In alternativa, individuare il nodo dell'istanza in Esplora Server, individuare il processo, aprire il menu di scelta rapida e quindi selezionare **Disconnetti processo**.

    ![Debug di processi](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC690787.gif)

> [!WARNING]
> Evitare interruzioni prolungate in corrispondenza di punti di interruzione quando remote debug. Azure considera un processo viene arrestato per più di qualche minuto che non risponde e interrompe l'invio di traffico a tale istanza. Se si arresta per troppo tempo, msvsmon.exe si disconnette dal processo.

Per disconnettere il debugger da tutti i processi nell'istanza o nel ruolo, aprire il menu di scelta rapida per il ruolo o l'istanza che sta eseguendo il debug e quindi selezionare **Scollega Debugger**.

## <a name="limitations-of-remote-debugging-in-azure"></a>Limitazioni del debug remoto in Azure

Da Azure SDK 2.3, il debug remoto presenta le limitazioni seguenti:

* Con il debug remoto abilitato, è possibile pubblicare un servizio cloud in cui un ruolo contiene più di 25 istanze.
* Il debugger usa le porte da 30400 a 30424, da 31400 a 31424e da 32400 a 32424. Se si prova a usare una di queste porte, sarà possibile pubblicare il servizio e uno dei seguenti messaggi di errore verrà visualizzato nel log attività per Azure:

  * Errore di convalida del file con estensione cscfg in base al file con estensione csdef.
    L'intervallo di porte riservate 'intervallo' per l'endpoint Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector del ruolo 'ruolo' si sovrappone con una porta già definita o un intervallo.
  * Allocazione non riuscita. Riprovare più tardi, provare a ridurre le dimensioni della macchina virtuale o il numero di istanze del ruolo oppure provare a distribuire in un'area diversa.

## <a name="debugging-azure-virtual-machines"></a>Debug di macchine virtuali di Azure

È possibile eseguire il debug di programmi in esecuzione su macchine virtuali di Azure usando Esplora Server in Visual Studio. Quando si abilita il debug remoto in una macchina virtuale di Azure, Azure installa l'estensione di debug remoto nella macchina virtuale. Quindi, è possibile connettersi a processi sulla macchina virtuale e il debug come di consueto.

> [!NOTE]
> Macchine virtuali create tramite lo stack di gestione risorse di Azure può eseguire in modalità remota il debug usando Cloud Explorer in Visual Studio 2015. Per altre informazioni, vedere [gestione delle risorse di Azure con Cloud Explorer](http://go.microsoft.com/fwlink/?LinkId=623031).

### <a name="to-debug-an-azure-virtual-machine"></a>Eseguire il debug di una macchina virtuale di Azure

1. In Esplora Server espandere il nodo macchine virtuali e selezionare il nodo della macchina virtuale che si desidera eseguire il debug.

2. Aprire il menu di scelta rapida e selezionare **Abilita debug**. Quando viene richiesto se si è certi se si desidera abilitare il debug nella macchina virtuale, seleziona **Sì**.

    Azure installa l'estensione di debug remoto nella macchina virtuale per abilitare il debug.

    ![Macchina virtuale attiva comando di debug](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Log attività di Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

3. Dopo che l'estensione di debug remoto al termine dell'installazione, aprire il menu di scelta rapida della macchina virtuale e selezionare **collega Debugger...**

    Azure Ottiene un elenco dei processi nella macchina virtuale e li visualizza nella finestra di dialogo Connetti a processo.

    ![Comando Collega debugger](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

4. Nel **Connetti a processo** finestra di dialogo **seleziona** per limitare l'elenco di risultati per visualizzare solo i tipi di codice da sottoporre a debug. È possibile eseguire il debug di codice gestito a 32 o 64 bit, il codice nativo o entrambi.

    ![Selezionare una finestra di dialogo tipo di codice](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

5. Selezionare i processi che si desidera eseguire il debug nella macchina virtuale e quindi selezionare **Attach**. Ad esempio, è possibile scegliere il processo w3wp.exe se si desidera eseguire il debug di un'app web nella macchina virtuale. Visualizzare [Debug di uno o più processi in Visual Studio](https://msdn.microsoft.com/library/jj919165.aspx) e [Azure Role Architecture](http://blogs.msdn.com/b/kwill/archive/2011/05/05/windows-azure-role-architecture.aspx) per altre informazioni.

## <a name="create-a-web-project-and-a-virtual-machine-for-debugging"></a>Creare un progetto web e una macchina virtuale per il debug

Prima di pubblicare il progetto Azure, si potrebbe risultare utile per eseguire il test in un ambiente indipendente che supporta il debug e scenari di test e in cui è possibile installare il test e i programmi di controllo. Un modo per eseguire tali test è in modalità remota il debug dell'applicazione in una macchina virtuale.

I progetti di Visual Studio ASP.NET offrono un'opzione per creare una macchina virtuale utile che è possibile usare per il test di app. La macchina virtuale include endpoint comunemente necessari, ad esempio PowerShell, Desktop remoto e WebDeploy.

### <a name="to-create-a-web-project-and-a-virtual-machine-for-debugging"></a>Per creare un progetto web e una macchina virtuale per il debug

1. In Visual Studio, creare una nuova applicazione Web ASP.NET.

2. Nella finestra di dialogo Nuovo progetto ASP.NET, nella sezione Azure, scegliere **macchina virtuale** nella casella di riepilogo a discesa. Lasciare il **crea risorse remote** casella di controllo selezionata. Selezionare **OK** per procedere.

    Il **crea macchina virtuale in Azure** verrà visualizzata la finestra di dialogo.

    ![Creare una finestra di dialogo di progetto web ASP.NET](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746723.png)

    **Nota:** viene chiesto di accedere all'account di Azure se non è già stato effettuato.

3. Selezionare le varie impostazioni per la macchina virtuale e quindi selezionare **OK**. Visualizzare [macchine virtuali](http://go.microsoft.com/fwlink/?LinkId=623033) per altre informazioni.

    Il nome che immesso per il nome DNS sarà il nome della macchina virtuale.

    ![Creare una macchina virtuale nella finestra di dialogo di Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746724.png)

    Azure crea la macchina virtuale e quindi esegue il provisioning e la configurazione degli endpoint, ad esempio Desktop remoto e distribuzione Web

4. Dopo che la macchina virtuale è completamente configurata, selezionare il nodo della macchina virtuale in Esplora Server.

5. Aprire il menu di scelta rapida e selezionare **Abilita debug**. Quando viene richiesto se si è certi se si desidera abilitare il debug nella macchina virtuale, seleziona **Sì**.

    Azure installa l'estensione di debug remoto alla macchina virtuale per abilitare il debug.

    ![Macchina virtuale attiva comando di debug](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Log attività di Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

6. Pubblicare il progetto come descritto nel [procedura: distribuire un Web progetto tramite un solo clic la pubblicazione in Visual Studio](https://msdn.microsoft.com/library/dd465337.aspx). Poiché si desidera eseguire il debug nella macchina virtuale, sul **impostazioni** pagina del **Pubblica sito Web** procedura guidata, selezionare **Debug** come la configurazione. Ciò assicura che i simboli del codice sono disponibili durante il debug.

    ![Impostazioni di pubblicazione](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718349.png)

7. Nel **Opzioni pubblicazione File**, selezionare **Rimuovi file aggiuntivi nella destinazione** se il progetto è già stato distribuito in precedenza.

8. Dopo la pubblicazione del progetto, nel menu di scelta rapida della macchina virtuale in Esplora Server selezionare **collega Debugger...**

    Azure Ottiene un elenco dei processi nella macchina virtuale e li visualizza nella finestra di dialogo Connetti a processo.

    ![Comando Collega debugger](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

9. Nel **Connetti a processo** finestra di dialogo **seleziona** per limitare l'elenco di risultati per visualizzare solo i tipi di codice da sottoporre a debug. È possibile eseguire il debug di codice gestito a 32 o 64 bit, il codice nativo o entrambi.

    ![Selezionare una finestra di dialogo tipo di codice](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

10. Selezionare i processi che si desidera eseguire il debug nella macchina virtuale e quindi selezionare **Attach**. Ad esempio, è possibile scegliere il processo w3wp.exe se si desidera eseguire il debug di un'app web nella macchina virtuale. Visualizzare [Debug di uno o più processi in Visual Studio](https://msdn.microsoft.com/library/jj919165.aspx) per altre informazioni.

## <a name="next-steps"></a>Passaggi successivi

* Uso **Intellitrace** per raccogliere un log di eventi e chiamate da un server di rilascio. Visualizzare [debug di un servizio Cloud pubblicato con IntelliTrace e Visual Studio](http://go.microsoft.com/fwlink/?LinkID=623016).

* Uso **diagnostica di Azure** per registrare informazioni dettagliate dal codice eseguito all'interno dei ruoli, sia che essi siano eseguiti nell'ambiente di sviluppo o in Azure. Visualizzare [raccogliere dati di registrazione utilizzando diagnostica Azure](http://go.microsoft.com/fwlink/p/?LinkId=400450).
