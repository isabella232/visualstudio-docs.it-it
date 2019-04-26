---
title: Eseguire strumenti di profilatura con o senza debugger | Microsoft Docs
ms.date: 11/04/2018
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 273dc6770f2928ed65d6a473b7f1986bc353687e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62999419"
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

## <a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Raccogliere dati di profilatura durante il debug

Quando si avvia il debug in Visual Studio selezionando **Debug** > **Avvia debug** oppure premendo **F5**, la finestra **Strumenti di diagnostica** viene visualizzata per impostazione predefinita. Per aprirla manualmente, selezionare **Debug** > **Finestre** > **Mostra strumenti di diagnostica**. Nella finestra **Strumenti di diagnostica** vengono visualizzate informazioni su eventi, memoria dei processi e utilizzo della CPU.

![Strumenti di diagnostica](../profiling/media/diagnostictools-update1.png "Strumenti di diagnostica")

- Usare l'icona **Impostazioni** sulla barra degli strumenti per scegliere se visualizzare **Utilizzo memoria**, **Analisi interfaccia utente** o **Utilizzo CPU**.

- Selezionare **Impostazioni** nell'elenco a discesa **Impostazioni** per aprire **Diagnostic Tools Property Pages** (Pagine delle proprietà strumenti di diagnostica) con altre opzioni.

- Se si usa Visual Studio Enterprise, è possibile abilitare o disabilitare IntelliTrace in **Strumenti** > **Opzioni** > **IntelliTrace** in Visual Studio.

La sessione di diagnostica termina quando si interrompe il debug.

È anche possibile visualizzare **Strumenti di diagnostica** per destinazioni di debug in remoto. Per il debug e la profilatura remoti, è necessario installare il debugger remoto di Visual Studio ed eseguirlo nella destinazione remota.
- Per il debug e la profilatura remoti di progetti di app desktop, vedere [Remote debugging](../debugger/remote-debugging.md) (Debug remoto).
- Per il debug e la profilatura remoti di app UWP, vedere [Eseguire il debug di app UWP in un computer remoto da Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md).

### <a name="the-events-tab"></a>Scheda Eventi

Durante una sessione di debug, la scheda **Eventi** della finestra **Strumenti di diagnostica** elenca gli eventi di diagnostica che si verificano. I prefissi di categoria, come ad esempio **Punto di interruzione**, **File** e altri, consentono di esaminare rapidamente l'elenco per individuare una categoria o ignorare le categorie non si è interessati.

Usare l'elenco a discesa **Filtra** per filtrare gli eventi da visualizzare, selezionando o deselezionando categorie di eventi specifiche.

![Filtro eventi di diagnostica](../profiling/media/diagnosticeventfilter.png "Filtro eventi di diagnostica")

Usare la casella di ricerca per trovare una stringa specifica nell'elenco di eventi. Di seguito vengono illustrati i risultati di una ricerca per la stringa "name" per cui sono stati trovati quattro eventi corrispondenti:

![Ricerca di eventi di diagnostica](../profiling/media/diagnosticseventsearch.png "Ricerca di eventi di diagnostica")

Per altre informazioni, vedere l'articolo relativo a come [eseguire ricerche e applicare filtri nella scheda Eventi della finestra Strumenti di diagnostica](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

## <a name="collect-profiling-data-without-debugging"></a>Raccogliere dati di profilatura senza il debug

Per raccogliere dati sulle prestazioni senza debug, è possibile eseguire gli strumenti **Profiler prestazioni**. Per l'esecuzione di alcuni strumenti di profilatura, è necessario avere i privilegi di amministratore. È possibile aprire Visual Studio come amministratore oppure eseguire gli strumenti come amministratore quando si avvia la sessione di diagnostica.

1. Con un progetto aperto in Visual Studio, selezionare **Debug** > **Profiler prestazioni**, oppure premere **ALT**+**F2**.

1. Nella pagina di avvio di diagnostica selezionare uno o più strumenti da eseguire. Vengono visualizzati solo gli strumenti applicabili al tipo di progetto, al sistema operativo e al linguaggio di programmazione. Selezionare **Mostra tutti gli strumenti** per vedere anche gli strumenti che sono disabilitati per la sessione di diagnostica. Ecco le possibili scelte per un'app UWP C#:

   ![Selezionare gli strumenti di diagnostica](../profiling/media/diag_selecttool.png "DIAG_SelectTool")

1. Per avviare la sessione di diagnostica, fare clic su **Avvia**.

   Durante l'esecuzione della sessione, alcuni strumenti visualizzano grafici dei dati in tempo reale nella pagina degli strumenti di diagnostica.

    ![Raccogliere dati nell'hub Prestazioni e diagnostica](../profiling/media/pdhub_collectdata.png "Hub raccolta dati")

1. Per terminare la sessione di diagnostica, scegliere **Arrestare raccolta**.

   I dati analizzati vengono visualizzati nella pagina **Report**.

È possibile salvare i report e aprirli dall'elenco **Sessioni aperte di recente** nella pagina di avvio degli strumenti di diagnostica.

![Aprire un file della sessione di diagnostica salvato](../profiling/media/pdhub_openexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

### <a name="the-profiling-report"></a>Rapporto di profilatura
 ![Rapporto degli strumenti di diagnostica](../profiling/media/diag_report.png "DIAG_Report")

|||
|-|-|
|![Passaggio 1](../profiling/media/procguid_1.png "ProcGuid_1")|La sequenza temporale mostra la durata della sessione di profilatura, gli eventi di attivazione del ciclo di vita dell'app e i contrassegni utente.|
|![Passaggio 2](../profiling/media/procguid_2.png "ProcGuid_2")|Puoi limitare il rapporto a una parte della sequenza temporale trascinando le barre blu per selezionare un'area della stessa.|
|![Passaggio 3](../profiling/media/procguid_3.png "ProcGuid_3")|In ogni strumento di diagnostica viene visualizzato uno o più grafici master. Se la sessione di diagnostica ha più di uno strumento, vengono visualizzati tutti i grafici master.|
|![Passaggio 4](../profiling/media/procguid_4.png "ProcGuid_4")|È possibile comprimere ed espandere i singoli grafici di ogni strumento.|
|![Passaggio 5](../profiling/media/procguid_6.png "ProcGuid_6")|Quando i dati includono più di uno strumento, i dettagli dello strumento sono raccolti in schede.|
|![Passaggio 6](../profiling/media/procguid_6a.png "ProcGuid_6a")|La metà inferiore del report include una o più viste di dettagli per ogni strumento. È possibile filtrare la vista selezionando le aree della sequenza temporale.|

## <a name="run-diagnostic-sessions-on-installed-or-running-apps"></a>Eseguire sessioni di diagnostica per le app installate o in esecuzione

 Prima di avviare l'app dal progetto di Visual Studio, è anche possibile eseguire sessioni di diagnostica su destinazioni alternative. Ad esempio, potrebbe essere necessario diagnosticare problemi di prestazioni in un'app installata dall'Archivio applicazioni di Windows.

 ![Scegliere la destinazione di analisi degli strumenti di diagnostica](../profiling/media/pdhub_chooseanalysistarget.png "PDHUB_ChooseAnalysisTarget")

 È possibile avviare app già installate oppure collegare gli strumenti di diagnostica ad app e processi già in esecuzione. Quando si sceglie **Applicazione in esecuzione** o **Applicazione installata**, è possibile selezionare l'app da un elenco che individua le app nella destinazione di distribuzione specificata. La destinazione può essere un computer locale o remoto.

 ![Scegliere un'app in esecuzione o installata per la diagnostica](../profiling/media/pdhub_selectrunningapp.png "PDHUB_SelectRunningApp")

## <a name="see-also"></a>Vedere anche

Di seguito vengono elencati post di blog e articoli MSDN a cura del team di sviluppo di diagnostica:
- [MSDN Magazine: Analizza le prestazioni durante il debug in Visual Studio 2015](https://msdn.microsoft.com/magazine/dn973013.aspx)

- [MSDN Magazine: Usa IntelliTrace per una diagnosi più rapida dei problemi](https://msdn.microsoft.com/magazine/dn973014.aspx)

- [Post di blog: Diagnosing Event Handler Leaks with the Memory Usage Tool in Visual Studio 2015](https://devblogs.microsoft.com/devops/diagnosing-event-handler-leaks-with-the-memory-usage-tool-in-visual-studio-2015/) (Diagnosi delle perdite di memoria del gestore eventi con lo strumento Utilizzo memoria in Visual Studio 2015)

- [Video: Historical Debugging with IntelliTrace in Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/Events/Ignite/2015/BRK3716) (Debug cronologico con IntelliTrace in Microsoft Visual Studio Ultimate 2015)

- [Video: Debugging Performance Issues Using Visual Studio 2015](https://channel9.msdn.com/Events/Build/2015/3-731) (Debug dei problemi di prestazioni in Visual Studio 2015)

- [PerfTips: Performance Information at-a-glance while Debugging with Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/) (PerfTips: Informazioni immediate sulle prestazioni durante il debug in Visual Studio)

- [Diagnostic Tools debugger window in Visual Studio 2015](https://devblogs.microsoft.com/devops/diagnostic-tools-debugger-window-in-visual-studio-2015/) (Finestra del debugger degli strumenti di diagnostica in Visual Studio 2015)

- [IntelliTrace in Visual Studio Enterprise 2015](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)
