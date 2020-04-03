---
title: Eseguire strumenti di profilatura con o senza debugger | Microsoft Docs
ms.date: 04/02/2020
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf544b3bec9b492f1d1669549ba5501a52f7d5f2
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638793"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Eseguire gli strumenti di profilatura con o senza il debugger

Visual Studio offre una vasta gamma di strumenti di misurazione delle prestazioni e di profilatura. Alcuni strumenti, come **Utilizzo CPU** e **Utilizzo memoria**, possono essere eseguiti con o senza debugger e nelle configurazioni di compilazione Release o Debug. Gli strumenti **Profiler prestazioni** come **Sequenza temporale applicazione** possono essere eseguiti nelle compilazioni Debug o Release. Gli strumenti integrati nel debugger, come la finestra **Strumenti di diagnostica** e la scheda **Eventi**, vengono eseguiti solo durante le sessioni di debug.

>[!NOTE]
>È possibile usare gli strumenti per le prestazioni non inclusi nel debugger con Windows 7 e versioni successive. Per eseguire gli strumenti di profilatura integrati nel debugger è necessario Windows 8 o versione successiva.

Il **Profiler prestazioni** non incluso nel debugger e gli **Strumenti di diagnostica** integrati nel debugger offrono informazioni ed esperienze di uso diverse. Gli strumenti integrati nel debugger indicano i punti di interruzione e i valori delle variabili. Gli strumenti non inclusi nel debugger ottengono risultati più vicini all'esperienza dell'utente finale.

Per stabilire quali strumenti e risultati usare, considerare quanto segue:

- I problemi di prestazioni esterni, come ad esempio i problemi di I/O dei file o di velocità di risposta della rete non sono visualizzati in modo molto diverso negli strumenti integrati nel debugger o negli altri.
- Per i problemi causati da chiamate a uso elevato di CPU, possono esservi differenze notevoli delle prestazioni tra le compilazioni Release e Debug. Verificare se il problema è presente nelle compilazioni Release.
- Se il problema si verifica solo durante le compilazioni Debug, probabilmente non è necessario eseguire gli strumenti non integrati nel debugger. Per problemi delle compilazioni Release, stabilire se gli strumenti del debugger possono essere utili per un'indagine più approfondita.
- Le compilazioni Release offrono funzionalità di ottimizzazione come ad esempio l'incorporamento di chiamate di funzione e di costanti, l'eliminazione di percorsi di codice non usati e l'archiviazione di variabili in modalità non utilizzabili dal debugger. I numeri relativi alle prestazioni negli strumenti integrati nel debugger sono meno accurati, perché le compilazioni Debug non offrono queste ottimizzazioni.
- Il debugger stesso modifica i tempi delle prestazioni in quanto esegue operazioni di debugger necessarie come l'intercettazione di eccezioni e di eventi di caricamento del modulo.
- I numeri relativi alle prestazioni della compilazione Release negli strumenti **Profiler prestazioni** sono i più precisi e accurati. I risultati degli strumenti integrati nel debugger sono particolarmente utili per il confronto con altre misurazioni correlate al debug.

Per Utilizzo CPU, è possibile eseguire lo strumento su un computer remoto utilizzando gli strumenti da riga di comando.

## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Raccogliere dati di profilatura durante il debug

Quando si avvia il debug in Visual Studio selezionando **Debug di** > **avvio** di debug o premendo **F5**, la finestra Strumenti di **diagnostica** viene visualizzata per impostazione predefinita. Per aprirlo manualmente, selezionare **Debug** > di**Windows** > **Mostra strumenti**di diagnostica . Nella finestra **Strumenti di diagnostica** vengono visualizzate informazioni su eventi, memoria dei processi e utilizzo della CPU.

![Strumenti di diagnostica](../profiling/media/diagnostictools-update1.png "Strumenti di diagnostica")

- Utilizzare l'icona **Impostazioni** nella barra degli strumenti per scegliere se visualizzare **Utilizzo memoria** o **Utilizzo CPU**.

- Selezionare **Impostazioni** nell'elenco a discesa **Impostazioni** per aprire **Diagnostic Tools Property Pages** (Pagine delle proprietà strumenti di diagnostica) con altre opzioni.

- Se si esegue Visual Studio Enterprise, è possibile abilitare o disabilitare IntelliTrace in**IntelliTrace delle****opzioni** >  **degli strumenti** > di Visual Studio.

La sessione di diagnostica termina quando si interrompe il debug.

### <a name="the-events-tab"></a>Scheda Eventi

Durante una sessione di debug, la scheda **Eventi** della finestra **Strumenti di diagnostica** elenca gli eventi di diagnostica che si verificano. I prefissi di categoria come ad esempio **Punto di interruzione**, **File** e altri, consentono di esaminare rapidamente l'elenco per individuare una categoria, o ignorare le categorie non si è interessati.

Usare l'elenco a discesa **Filtra** per filtrare gli eventi da visualizzare, selezionando o deselezionando categorie di eventi specifiche.

![Filtro eventi di diagnostica](../profiling/media/diagnosticeventfilter.png "Filtro eventi di diagnostica")

Usare la casella di ricerca per trovare una stringa specifica nell'elenco di eventi. Di seguito vengono illustrati i risultati di una ricerca per la stringa "name" per cui sono stati trovati quattro eventi corrispondenti:

![Ricerca eventi di diagnostica](../profiling/media/diagnosticseventsearch.png "Ricerca eventi di diagnostica")

Per altre informazioni, vedere l'articolo relativo a come [eseguire ricerche e applicare filtri nella scheda Eventi della finestra Strumenti di diagnostica](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

## <a name="collect-profiling-data-without-debugging"></a>Raccogliere dati di profilatura senza il debug

Per raccogliere dati sulle prestazioni senza debug, è possibile eseguire gli strumenti **Profiler prestazioni**. Per l'esecuzione di alcuni strumenti di profilatura, è necessario avere i privilegi di amministratore. È possibile aprire Visual Studio come amministratore oppure eseguire gli strumenti come amministratore quando si avvia la sessione di diagnostica.

1. Con un progetto aperto in Visual Studio, impostare la configurazione della soluzione su **Release** e selezionare **Debugger Windows locale** (o Computer **locale)** come destinazione di distribuzione.

1. Selezionare **Debug** > **Performance Profiler**oppure premere **ALT**+**F2**.

1. Nella pagina di avvio di diagnostica selezionare uno o più strumenti da eseguire. Vengono visualizzati solo gli strumenti applicabili al tipo di progetto, al sistema operativo e al linguaggio di programmazione. Selezionare **Mostra tutti gli strumenti** per vedere anche gli strumenti che sono disabilitati per la sessione di diagnostica. Ecco le possibili scelte per un'app UWP C#:

   ![Selezionare gli strumenti di diagnostica](../profiling/media/diag_selecttool.png "DIAG_SelectTool")

1. Per avviare la sessione di diagnostica, fare clic su **Avvia**.

   Durante l'esecuzione della sessione, alcuni strumenti visualizzano grafici dei dati in tempo reale nella pagina degli strumenti di diagnostica.

    ![Raccogliere dati nell'hub Prestazioni e diagnosticaCollect data on the Performance and Diagnostic Hub](../profiling/media/pdhub_collectdata.png "Hub raccogliere dati")

1. Per terminare la sessione di diagnostica, scegliere **Arrestare raccolta**.

   I dati analizzati vengono visualizzati nella pagina **Report**.

È possibile salvare i report e aprirli dall'elenco **Sessioni aperte di recente** nella pagina di avvio degli strumenti di diagnostica.

![Aprire una file delle sessioni di diagnostica salvato](../profiling/media/pdhub_openexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

### <a name="the-profiling-report"></a>Rapporto di profilatura
 ![Report di strumenti di diagnostica](../profiling/media/diag_report.png "DIAG_Report")

|||
|-|-|
|![Passaggio 1](../profiling/media/procguid_1.png "ProcGuid_1")|La sequenza temporale mostra la durata della sessione di profilatura, gli eventi di attivazione del ciclo di vita dell'app e i contrassegni utente.|
|![Passaggio 2](../profiling/media/procguid_2.png "ProcGuid_2")|Puoi limitare il rapporto a una parte della sequenza temporale trascinando le barre blu per selezionare un'area della stessa.|
|![Passaggio 3](../profiling/media/procguid_3.png "ProcGuid_3")|In ogni strumento di diagnostica viene visualizzato uno o più grafici master. Se la sessione di diagnostica ha più di uno strumento, vengono visualizzati tutti i grafici master.|
|![Fase 4](../profiling/media/procguid_4.png "ProcGuid_4")|È possibile comprimere ed espandere i singoli grafici di ogni strumento.|
|![Fase 5](../profiling/media/procguid_6.png "ProcGuid_6")|Quando i dati includono più di uno strumento, i dettagli dello strumento sono raccolti in schede.|
|![Passaggio 6](../profiling/media/procguid_6a.png "ProcGuid_6a")|La metà inferiore del report include una o più viste di dettagli per ogni strumento. È possibile filtrare la vista selezionando le aree della sequenza temporale.|

## <a name="run-diagnostic-sessions-on-installed-or-running-apps"></a>Eseguire sessioni di diagnostica per le app installate o in esecuzione

Prima di avviare l'app dal progetto di Visual Studio, è anche possibile eseguire sessioni di diagnostica su destinazioni alternative. Ad esempio, potrebbe essere necessario diagnosticare problemi di prestazioni in un'app installata dall'Archivio applicazioni di Windows. Nel profiler prestazioni selezionare dall'elenco a discesa in **Modifica destinazione**.

![Scegliere la destinazione di analisi degli strumenti diagnostici](../profiling/media/pdhub_chooseanalysistarget.png "PDHUB_ChooseAnalysisTarget")

È possibile avviare app già installate oppure collegare gli strumenti di diagnostica ad app e processi già in esecuzione.

Se si sceglie **Eseguibile** come destinazione dell'analisi, è possibile immettere il percorso di un *file con estensione exe* in un computer locale o remoto. In entrambi i casi, il *file .exe* viene eseguito localmente. Tuttavia, è consigliabile profilare l'app aprendo la soluzione in Visual Studio.However, we recommend that you profile your app by opening the solution in Visual Studio.

Per un'app UWP, quando si seleziona **App in esecuzione** o App **installata**, si seleziona l'app da un elenco che trova le app nella destinazione di distribuzione specificata. La destinazione può essere un computer locale o remoto. Per profilare un'app UWP in un computer remoto, è necessario selezionare **Universale (protocollo non crittografato)** nella finestra di dialogo **Connessioni remote.**

![Scegliere un'app in esecuzione o installata per la diagnostica](../profiling/media/pdhub_selectrunningapp.png "PDHUB_SelectRunningApp")

> [!NOTE]
> Per altri scenari che richiedono l'utilizzo remoto degli strumenti di profilatura, vedere [Misurare le prestazioni dell'applicazione dalla riga](../profiling/profile-apps-from-command-line.md)di comando. È possibile utilizzare gli strumenti della riga di comando con Utilizzo CPU e lo strumento .NET Object Allocation.

## <a name="see-also"></a>Vedere anche

Di seguito vengono elencati post di blog e articoli MSDN a cura del team di sviluppo di diagnostica:
- [MSDN Magazine: Analyze Performance While Debugging in Visual Studio 2015](https://msdn.microsoft.com/magazine/dn973013.aspx) (Analizzare le prestazioni durante il debug in Visual Studio 2015)

- [MSDN Magazine: Use IntelliTrace to Diagnose Issues Faster](https://msdn.microsoft.com/magazine/dn973014.aspx) (Usare IntelliTrace per diagnosticare i problemi più velocemente)

- [Post di blog: Diagnosing Event Handler Leaks with the Memory Usage Tool in Visual Studio 2015](https://devblogs.microsoft.com/devops/diagnosing-event-handler-leaks-with-the-memory-usage-tool-in-visual-studio-2015/) (Diagnosi delle perdite di memoria del gestore eventi con lo strumento Utilizzo memoria in Visual Studio 2015)

- [Video: Debug cronologico con IntelliTrace in Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/Events/Ignite/2015/BRK3716)

- [Video: Problemi di prestazioni di debug in Visual Studio 2015](https://channel9.msdn.com/Events/Build/2015/3-731)

- [PerfTips: Performance Information at-a-glance while Debugging with Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/) (Informazioni immediate sulle prestazioni durante il debug in Visual Studio)

- [Finestra del debugger degli strumenti di diagnostica in Visual Studio 2015](https://devblogs.microsoft.com/devops/diagnostic-tools-debugger-window-in-visual-studio-2015/)

- [IntelliTrace in Visual Studio Enterprise 2015](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)
