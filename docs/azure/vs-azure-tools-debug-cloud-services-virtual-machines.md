---
title: Debug di un servizio cloud o di una macchina virtuale di Azure
description: Debug di un servizio cloud o di una macchina virtuale in Visual Studio
author: mikejo5000
manager: jmartens
ms.topic: how-to
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.technology: vs-ide-debug
ms.openlocfilehash: aeaa6bf6230833a350fb2fe8d55178d6c838a5f1d014a5dcdbe959daf6d01838
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121364153"
---
# <a name="debugging-an-azure-cloud-service-or-virtual-machine-in-visual-studio"></a>Debug di un servizio cloud o di una macchina virtuale di Azure in Visual Studio

Visual Studio offre diverse opzioni per il debug dei servizi cloud e delle macchine virtuali di Azure.

## <a name="debug-your-cloud-service-on-your-local-computer"></a>Eseguire il debug del servizio cloud sul computer locale

È possibile risparmiare tempo e denaro usando il Calcolo di Azure Emulator per eseguire il debug del servizio cloud in un computer locale. Eseguendo il debug di un servizio in locale prima della distribuzione, è possibile migliorare l'affidabilità e le prestazioni senza pagare per il tempo di calcolo. Tuttavia, potrebbero verificarsi alcuni errori solo quando si esegue un servizio cloud in Azure stesso. È possibile eseguire il debug di questi errori se si abilita il debug remoto quando si pubblica il servizio e poi si collega il debugger a un'istanza del ruolo.

L'emulatore simula il servizio di calcolo di Azure e viene eseguito nell'ambiente locale in modo da poter testare ed eseguire il debug del servizio cloud prima della distribuzione. L'emulatore gestisce il ciclo di vita delle istanze del ruolo e fornisce l'accesso alle risorse simulate, ad esempio l'archiviazione locale. Durante il debug o l’esecuzione del servizio da Visual Studio, esso avvia automaticamente l’emulatore come applicazione in background e il servizio viene distribuito all'emulatore. È possibile usare l'emulatore per visualizzare il servizio quando è in esecuzione nell'ambiente locale. È possibile eseguire la versione completa o la versione express dell'emulatore. A partire da Azure 2.3, la versione rapida dell'emulatore è l'impostazione predefinita. Vedere [Uso di Emulator Express per l'esecuzione e il debug di un servizio cloud in locale.](vs-azure-tools-emulator-express-debug-run.md)

### <a name="to-debug-your-cloud-service-on-your-local-computer"></a>Per eseguire il debug del servizio cloud nel computer locale

1. Nella barra dei menu selezionare **Debug**  >  **Avvia debug per** eseguire il progetto di servizio cloud di Azure. In alternativa, è possibile premere F5. Verrà visualizzato un messaggio che indica l'avvio dell'emulatore di calcolo. Quando l'emulatore viene avviato, l'icona della barra delle applicazioni conferma l'operazione.

    ![Emulatore di Azure nella barra delle applicazioni](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC783828.png)

2. Per visualizzare l'interfaccia utente dell'emulatore di calcolo, aprire il menu di scelta rapida dell'icona di Azure nell'area di notifica e selezionare **Show Compute Emulator UI**(Mostra interfaccia emulatore di calcolo).

    Il riquadro sinistro dell'interfaccia utente mostra i servizi attualmente distribuiti nell'emulatore di calcolo e le istanze del ruolo in esecuzione in ogni servizio. È possibile scegliere il servizio o i ruoli per visualizzare le informazioni di diagnostica, registrazione e ciclo di vita nel riquadro di destra. Se si seleziona il margine superiore di una finestra inclusa, essa si espande per riempire il riquadro destro.

3. Scorrere l'applicazione scegliendo i comandi dal menu Debug e **impostando** i punti di interruzione nel codice. Mentre si esegue l'applicazione un'istruzione alla volta nel debugger, i riquadri vengono aggiornati con lo stato corrente dell'applicazione. Quando si arresta il debug, la distribuzione dell'applicazione viene eliminata. Se l'applicazione include un ruolo Web e la proprietà dell'azione di avvio è stata impostata per l'avvio del Web browser, Visual Studio avvia l'applicazione Web nel browser. Se si modifica il numero di istanze di un ruolo nella configurazione del servizio, è necessario arrestare il servizio cloud e quindi riavviare il debug perché sia possibile eseguire il debug delle nuove istanze del ruolo.

    > [!NOTE]
    > quando si arresta l'esecuzione o il debug del servizio, l'emulatore di calcolo locale e l'emulatore di archiviazione non vengono arrestati. È necessario arrestarli in modo esplicito dall'area di notifica.

## <a name="debug-a-cloud-service-in-azure"></a>Debug di un servizio cloud in Azure

Per eseguire il debug di un servizio cloud da un computer remoto, è necessario abilitare tale funzionalità in modo esplicito quando si distribuisce il servizio cloud, in modo che i servizi richiesti (ad esempio msvsmon.exe) siano installati nelle macchine virtuali che eseguono le istanze del ruolo. Se si non abilita il debug remoto quando il servizio è pubblicato, è necessario ripubblicare il servizio con il debug remoto abilitato.

Se si abilita il debug remoto per un servizio cloud, esso non produce una riduzione delle prestazioni o costi aggiuntivi. Non usare il debug remoto in un servizio di produzione, poiché i client che usano il servizio potrebbero essere compromessi.

> [!NOTE]
> Quando si pubblica un servizio cloud da Visual Studio, è possibile abilitare **IntelliTrace** per qualsiasi ruolo del servizio destinato a .NET Framework 4 o .NET Framework 4.5. Tramite **IntelliTrace** è possibile esaminare gli eventi verificatisi in un'istanza del ruolo in passato e riprodurre il contesto da quel momento. Vedere [Debug di un servizio cloud pubblicato con IntelliTrace e Visual Studio](vs-azure-tools-IntelliTrace-debug-published-cloud-services.md) e [Uso di IntelliTrace](../debugger/intellitrace.md).

### <a name="to-enable-remote-debugging-for-a-cloud-service"></a>Per abilitare il debug remoto per un servizio cloud

1. Aprire il menu di scelta rapida per il progetto Azure e quindi selezionare **Pubblica**.

2. Selezionare l'ambiente di **Gestione temporanea** e la configurazione di **Debug**.

    Questa è solo un'indicazione. È possibile scegliere di eseguire ambienti di test in un ambiente di produzione. Tuttavia, possono verificarsi effetti negativi per gli utenti se si abilita il debug remoto nell'ambiente di produzione. È possibile scegliere la configurazione di rilascio, ma la configurazione di debug semplifica il debug.

    ![Scegliere la configurazione di debug](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746717.gif)

3. Seguire la procedura consueta, ma selezionare la casella di controllo **Abilita debug remoto per tutti i ruoli** nella scheda **Impostazioni avanzate**.

    ![Configurazione di debug](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746718.gif)

### <a name="to-attach-the-debugger-to-a-cloud-service-in-azure"></a>Per collegare il debugger a un servizio cloud in Azure

1. In Esplora server espandere il nodo del servizio cloud.

2. Aprire il menu di scelta rapida per il ruolo o l'istanza del ruolo a cui si vuole collegarlo, quindi selezionare **Collega debugger**.

    Se si esegue il debug di un ruolo, il debugger di Visual Studio si connette a ogni istanza di tale ruolo. Il debugger si interrompe in un punto di interruzione per la prima istanza del ruolo che esegue la riga di codice e soddisfa le condizioni del punto di interruzione. Se si esegue il debug di un'istanza, il debugger si collega solo a tale istanza e si interrompe in un punto di interruzione solo quando l’istanza specifica esegue la riga di codice e soddisfa le condizioni del punto di interruzione.

    ![Collega debugger](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746719.gif)

3. Dopo che il debugger si connette a un'istanza, eseguire il debug come di consueto. Il debugger si connette automaticamente al processo host appropriato per il ruolo. In base al ruolo, il debugger si collega a w3wp.exe, WaWorkerHost.exe o WaIISHost.exe. Per verificare il processo a cui è collegato il debugger, espandere il nodo dell'istanza in Esplora server. Vedere [Architettura del ruolo di Azure](/archive/blogs/kwill/windows-azure-role-architecture) per altre informazioni sui processi di Azure.

    ![Finestra di dialogo Seleziona tipo di codice](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

4. Per identificare i processi a cui è collegato il debugger, sulla barra dei menu selezionare Debug   >  **Windows**  >  **Processie** aprire la **finestra di dialogo** Processi . (Tastiera: CTRL+ALT+Z) Per disconnettere un processo specifico, aprire il menu di scelta rapida e quindi selezionare **Disconnetti processo**. In alternativa, individuare il nodo dell'istanza in Esplora server, individuare il processo, aprire il relativo menu di scelta rapida e quindi selezionare **Disconnetti processo**.

    ![Debug di processi](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC690787.gif)

> [!WARNING]
> Evitare interruzioni prolungate in corrispondenza dei punti di interruzione durante il debug remoto. Azure considera un processo che è stato arrestato per più di pochi minuti come processo che non risponde e interrompe l'invio di traffico a tale istanza. Se si arresta per troppo tempo, msvsmon.exe si disconnette dal processo.

Per disconnettere il debugger da tutti i processi nell'istanza o nel ruolo, aprire il menu di scelta rapida per il ruolo o l'istanza di cui si esegue il debug e quindi selezionare **Scollega debugger**.

## <a name="limitations-of-remote-debugging-in-azure"></a>Limitazioni del debug remoto in Azure

Da Azure SDK 2.3, il debug remoto presenta le limitazioni seguenti:

* Con il debug remoto abilitato, non è possibile pubblicare un servizio cloud in cui un ruolo contiene più di 25 istanze.
* Il debugger usa le porte da 30400 a 30424, da 31400 a 31424e da 32400 a 32424. Se prova a usare una di queste porte, non sarà possibile pubblicare il servizio e verrà visualizzato uno dei seguenti messaggi di errore nel log delle attività per Azure:

  * Errore durante la convalida del file con estensione cscfg in base al file con estensione csdef.
    L'intervallo di porte riservate 'intervallo' per l’endpoint Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector del ruolo 'ruolo' si sovrappone con una porta o un intervallo già definiti.
  * Allocazione non riuscita. Riprovare più tardi, provare a ridurre la dimensione della VM o il numero di istanze del ruolo oppure provare a distribuire in un'area diversa.

## <a name="debugging-azure-virtual-machines"></a>Debug di macchine virtuali di Azure

È possibile eseguire il debug di programmi in esecuzione su macchine virtuali di Azure tramite Esplora server in Visual Studio. Quando si abilita il debug remoto su una macchina virtuale di Azure, Azure installa l'estensione di debug remoto nella macchina virtuale. Quindi, è possibile connettersi a processi sulla macchina virtuale ed eseguire il debug come di consueto.

> [!NOTE]
> Il debug di macchine virtuali create tramite lo stack di gestione risorse di Azure può essere eseguito in modalità remota usando Esplora cloud in Visual Studio 2015. Per altre informazioni, vedere [Gestione delle risorse di Azure con Cloud Explorer](vs-azure-tools-resources-managing-with-cloud-explorer.md).

### <a name="to-debug-an-azure-virtual-machine"></a>Per eseguire il debug di una macchina virtuale di Azure.

1. In Esplora server espandere il nodo Macchine virtuali e selezionare il nodo della macchina virtuale di cui si desidera eseguire il debug.

2. Aprire il menu di scelta rapida e selezionare **Abilita debug**. Quando viene chiesto se si è certi di voler abilitare il debug nella macchina virtuale, selezionare **Sì**.

    Azure installa l'estensione di debug remoto nella macchina virtuale per abilitare il debug.

    ![Comando di debug di abilitazione della macchina virtuale](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Finestra Log attività di Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

3. Al termine dell'installazione dell'estensione di debug remoto, aprire il menu di scelta rapida della macchina virtuale e selezionare **Collega debugger...**

    Azure ottiene un elenco dei processi nella macchina virtuale e li visualizza nella finestra di dialogo **Connetti a processo**.

    ![Comando Collega debugger](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

4. Nella finestra di dialogo **Connetti a processo** scegliere **Seleziona** per limitare l'elenco di risultati in modo che visualizzi solo i tipi di codice da sottoporre a debug. È possibile eseguire il debug di codice gestito, codice nativo o entrambi a 32 o 64 bit.

    ![Finestra di dialogo Seleziona tipo di codice](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

5. Scegliere i processi di cui si vuole eseguire il debug nella macchina virtuale e quindi selezionare **Collega.** Ad esempio, è possibile scegliere il processo w3wp.exe se si desidera eseguire il debug di un'applicazione Web nella macchina virtuale. Per altre informazioni, vedere [Debug di uno o più processi in Visual Studio](../debugger/debug-multiple-processes.md) e [Architettura del ruolo di Azure](/archive/blogs/kwill/windows-azure-role-architecture).

## <a name="create-a-web-project-and-a-virtual-machine-for-debugging"></a>Creare un progetto Web e una macchina virtuale per il debug

Prima di pubblicare il progetto Azure, può risultare utile per eseguire il test in un ambiente indipendente che supporti scenari di debug e di test e in cui sia possibile installare programmi di test e di controllo. Per avviare tale test, eseguire il debug remoto dell'app in una macchina virtuale.

I progetti ASP.NET di Visual Studio offrono un'opzione per creare una macchina virtuale utile che è possibile usare per il test delle applicazioni. La macchina virtuale include endpoint comunemente necessari, come PowerShell, Desktop remoto e WebDeploy.

### <a name="to-create-a-web-project-and-a-virtual-machine-for-debugging"></a>Per creare un progetto Web e una macchina virtuale per il debug

1. Creare un'applicazione Web ASP.NET in Visual Studio.

2. Nella sezione Azure della finestra di dialogo Nuovo ASP.NET Project selezionare **Macchina virtuale** nella casella di riepilogo a discesa. Lasciare deselezionata la casella di controllo **Crea risorse remote**. Selezionare **OK** per procedere.

    Verrà visualizzata la finestra di dialogo per la creazione di una macchina virtualein Azure.

    ![Finestra di dialogo Crea progetto Web ASP.NET](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746723.png)

    > [!NOTE]
    > verrà chiesto di accedere all'account Azure, se non è ancora stato eseguito l'accesso.

3. Scegliere le varie impostazioni per la macchina virtuale e quindi selezionare **OK.** Per altre informazioni, vedere [Macchine virtuali](/azure/virtual-machines/) .

    Il valore specificato per il nome DNS sarà il nome della macchina virtuale.

    ![Finestra di dialogo Crea macchina virtuale di Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746724.png)

    Azure crea la macchina virtuale e quindi effettua il provisioning e la configurazione degli endpoint, ad esempio Desktop remoto e Distribuzione Web.

4. Dopo aver configurato completamente la macchina virtuale, selezionare il relativo nodo in Esplora server.

5. Aprire il menu di scelta rapida e selezionare **Abilita debug**. Quando viene chiesto se si è certi di voler abilitare il debug nella macchina virtuale, selezionare **Sì**.

    Azure installa l'estensione di debug remoto nella macchina virtuale per abilitare il debug.

    ![Comando di debug di abilitazione della macchina virtuale](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Finestra Log attività di Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

6. Pubblicare il progetto come descritto in [Procedura: Distribuire un progetto Web tramite la pubblicazione con un clic in Visual Studio](/previous-versions/aspnet/dd465337(v=vs.110)). Poiché si intende eseguire il debug nella macchina virtuale, nella pagina **Impostazioni** della configurazione guidata **Pubblica sito Web** selezionare **Debug** come configurazione. Ciò assicura che i simboli del codice siano disponibili durante il debug.

    ![Impostazioni di pubblicazione](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718349.png)

7. In **Opzioni pubblicazione file** selezionare **Rimuovi file aggiuntivi nella destinazione** se il progetto è già stato distribuito in precedenza.

8. Dopo la pubblicazione del progetto, selezionare **Collega debugger...**

    Azure ottiene un elenco dei processi nella macchina virtuale e li visualizza nella finestra di dialogo **Connetti a processo**.

    ![Comando Collega debugger](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

9. Nella finestra di dialogo **Connetti a processo** scegliere **Seleziona** per limitare l'elenco di risultati in modo che visualizzi solo i tipi di codice da sottoporre a debug. È possibile eseguire il debug di codice gestito, codice nativo o entrambi a 32 o 64 bit.

    ![Finestra di dialogo Seleziona tipo di codice](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

10. Scegliere i processi di cui si vuole eseguire il debug nella macchina virtuale e quindi selezionare **Collega.** Ad esempio, è possibile scegliere il processo w3wp.exe se si desidera eseguire il debug di un'applicazione Web nella macchina virtuale. Per altre informazioni, vedere [Debug di uno o più processi in Visual Studio](../debugger/debug-multiple-processes.md) .

## <a name="next-steps"></a>Passaggi successivi

* Usare **IntelliTrace** per raccogliere un log di chiamate ed eventi da un server di rilascio. Vedere [Debug di un servizio cloud pubblicato con IntelliTrace e Visual Studio](vs-azure-tools-IntelliTrace-debug-published-cloud-services.md).

* Usare **Diagnostica di Azure** per registrare informazioni dettagliate dal codice eseguito all'interno dei ruoli, sia che essi siano eseguiti nell'ambiente di sviluppo o in Azure. Vedere [Raccogliere dati di registrazione usando Diagnostica di Azure](/azure/cloud-services/cloud-services-dotnet-diagnostics).
