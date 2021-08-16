---
title: Eseguire strumenti di profilatura con o senza debugger | Microsoft Docs
description: Informazioni sulle differenze tra le diverse modalità disponibili per gli strumenti di profilatura
ms.date: 5/26/2020
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0d207fd29eb77a5e90c1aae2fb60f0672d3769ab57cfcd7ad0e4a3035bd6332c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121441821"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Eseguire gli strumenti di profilatura con o senza il debugger

Visual Studio offre una vasta gamma di strumenti di misurazione delle prestazioni e di profilatura. Alcuni strumenti, ad esempio Utilizzo CPU e Utilizzo memoria, possono essere eseguiti con o senza il debugger e nelle configurazioni della build di rilascio o di debug. Gli strumenti visualizzati nella finestra [Strumenti di diagnostica vengono](../profiling/profiling-feature-tour.md#measure-performance-while-debugging) eseguiti solo durante una sessione di debug. Gli strumenti visualizzati nel [Profiler prestazioni](../profiling/profiling-feature-tour.md#post_mortem) vengono eseguiti senza il debugger e si analizzano i risultati dopo aver scelto di arrestare e raccogliere i dati (per l'analisi post-mortem).

>[!NOTE]
>È possibile usare gli strumenti per le prestazioni non inclusi nel debugger con Windows 7 e versioni successive. Per eseguire gli strumenti di profilatura integrati nel debugger è necessario Windows 8 o versione successiva.

Il Profiler prestazioni non incluso nel debugger e gli Strumenti di diagnostica integrati nel debugger offrono informazioni ed esperienze di uso diverse. Gli strumenti integrati nel debugger mostrano i valori delle variabili e consentono di usare i punti di interruzione. Gli strumenti non inclusi nel debugger ottengono risultati più vicini all'esperienza dell'utente finale.

Per decidere quali strumenti e risultati usare, tenere presente quanto segue:

- Strumento integrato nel debugger e strumento non debugger
  - I problemi di prestazioni esterni, come ad esempio i problemi di I/O dei file o di velocità di risposta della rete non sono visualizzati in modo molto diverso negli strumenti integrati nel debugger o negli altri.
  - Il debugger stesso modifica i tempi di prestazioni, in quanto esegue le operazioni del debugger necessarie, ad esempio l'intercettazione di eccezioni e gli eventi di caricamento dei moduli.
  - I numeri di prestazioni della build di Profiler prestazioni sono i più precisi e accurati. I risultati dello strumento integrato nel debugger sono particolarmente utili per confrontarli con altre misurazioni correlate al debug o per usare le funzionalità del debugger.
  - Alcuni strumenti, ad esempio lo strumento di allocazione di oggetti .NET, sono disponibili solo per scenari non di debugger.
- Debug e build di rilascio
  - Per i problemi causati da chiamate a elevato utilizzo di CPU, potrebbero esserci notevoli differenze di prestazioni tra le build di rilascio e di debug. Verificare se il problema esiste nelle build di rilascio.
  - Se il problema si verifica solo durante le compilazioni di debug, probabilmente non è necessario eseguire gli strumenti non del debugger. Per i problemi della build di rilascio, decidere se le funzionalità fornite dagli strumenti integrati nel debugger consentono di individuare il problema.
  - Le compilazioni Release offrono funzionalità di ottimizzazione come ad esempio l'incorporamento di chiamate di funzione e di costanti, l'eliminazione di percorsi di codice non usati e l'archiviazione di variabili in modalità non utilizzabili dal debugger. I numeri delle prestazioni nelle build di debug sono meno accurati, perché le build di debug non dispongono di queste ottimizzazioni.

## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Raccogliere dati di profilatura durante il debug

Quando si avvia il debug in Visual Studio debug selezionando Debug Avvia debug o premendo  >   **F5,** la finestra Strumenti di diagnostica visualizzata per impostazione predefinita.  Per aprirlo manualmente, selezionare **Debug**  >  **Windows**  >  **Mostra Strumenti di diagnostica**. Nella finestra **Strumenti di diagnostica** vengono visualizzate informazioni su eventi, memoria dei processi e utilizzo della CPU.

![Screenshot della finestra Strumenti di diagnostica](../profiling/media/diagnostictoolswindow.png " Finestra Strumenti di diagnostica")

- Usare l'icona **Impostazioni** sulla barra degli strumenti per scegliere se visualizzare **Utilizzo memoria**, **Analisi interfaccia utente** o **Utilizzo CPU**.

- Selezionare **Impostazioni** nell'elenco **Impostazioni** a discesa per aprire le pagine **Strumenti di diagnostica con** altre opzioni.

- Se si esegue Visual Studio Enterprise, è possibile abilitare o disabilitare IntelliTrace selezionando Strumenti  >  **Opzioni**  >  **IntelliTrace.**

La sessione di diagnostica termina quando si interrompe il debug.

Per altre informazioni, vedere:

- [Misurare le prestazioni dell'applicazione analizzando l'utilizzo della CPU](../profiling/beginners-guide-to-performance-profiling.md)
- [Misurare l'utilizzo della memoria in Visual Studio](../profiling/memory-usage.md)

### <a name="the-events-tab"></a>Scheda Eventi

Durante una sessione di debug, la scheda Eventi della finestra Strumenti di diagnostica elenca gli eventi di diagnostica che si verificano. La categoria *prefissi Punto* di interruzione, *File* e altri, consente di analizzare rapidamente l'elenco per individuare una categoria o ignorare le categorie di cui non si è a cui si è a cui non si è a cui si è a favore.

Usare **l'elenco** a discesa Filtro per filtrare gli eventi in e fuori dalla visualizzazione, selezionando o deselezionando categorie specifiche di eventi.

![Screenshot del filtro eventi di diagnostica](../profiling/media/diagnosticeventfilter.png "Filtro eventi di diagnostica")

Usare la casella di ricerca per trovare una stringa specifica nell'elenco di eventi. Ecco i risultati di una ricerca del nome della stringa *corrispondente* a quattro eventi:

![Screenshot della ricerca di eventi di diagnostica](../profiling/media/diagnosticseventsearch.png "Ricerca di eventi di diagnostica")

Per altre informazioni, vedere l'articolo relativo a come [eseguire ricerche e applicare filtri nella scheda Eventi della finestra Strumenti di diagnostica](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

## <a name="collect-profiling-data-without-debugging"></a>Raccogliere dati di profilatura senza il debug

Per raccogliere dati sulle prestazioni senza debug, è possibile eseguire gli strumenti Profiler prestazioni.

1. Con un progetto aperto in Visual Studio, impostare la configurazione della soluzione su **Rilascio** e selezionare Debugger **Windows** locale (o **Computer** locale) come destinazione della distribuzione.

1. Selezionare **Debug**  >  **Profiler prestazioni** o premere **ALT** + **F2.**

1. Nella pagina di avvio degli strumenti di diagnostica selezionare uno o più strumenti da eseguire. Vengono visualizzati solo gli strumenti applicabili al tipo di progetto, al sistema operativo e al linguaggio di programmazione. Selezionare **Mostra tutti gli strumenti** per vedere anche gli strumenti che sono disabilitati per la sessione di diagnostica.

   ![Screenshot degli strumenti di diagnostica](../profiling/media/diaghubsummarypage.png "DIAG_SelectTool")

1. Per avviare la sessione di diagnostica, fare clic su **Avvia**.

   Durante l'esecuzione della sessione, alcuni strumenti mostrano grafici dei dati in tempo reale nella pagina degli strumenti di diagnostica, nonché controlli per sospendere e riprendere la raccolta dei dati.

    ![Screenshot della raccolta dati nel Profiler prestazioni](../profiling/media/diaghubcollectdata.png "Raccolta dati nell'hub")

1. Per terminare la sessione di diagnostica, scegliere **Arrestare raccolta**.

   I dati analizzati vengono visualizzati nella **pagina Report.**

È possibile salvare i report e aprirli dall'elenco **Sessioni aperte di** recente nella Strumenti di diagnostica di avvio.

![Screenshot dell'Strumenti di diagnostica di sessioni aperte di recente](../profiling/media/diaghubopenexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

Per altre informazioni, vedere:

- [Analizzare l'utilizzo della CPU](../profiling/cpu-usage.md)
- [Analizzare l'utilizzo della memoria per il codice .NET](../profiling/dotnet-alloc-tool.md)
- [Analizzare l'utilizzo della memoria](../profiling/memory-usage-without-debugging2.md)
- [Analizzare le prestazioni del codice asincrono .NET](../profiling/analyze-async.md)
- [Analizzare le prestazioni del database](../profiling/analyze-database.md)
- [Analizzare l'utilizzo della GPU](../profiling/gpu-usage.md)

## <a name="collect-profiling-data-from-the-command-line"></a>Raccogliere dati di profilatura dalla riga di comando

Per misurare i dati sulle prestazioni dalla riga di comando, è possibile usare VSDiagnostics.exe, incluso in Visual Studio o nella Strumenti remoti. Ciò è utile per acquisire tracce delle prestazioni nei sistemi in Visual Studio non è installato o per creare script per la raccolta di tracce delle prestazioni. Per istruzioni dettagliate, vedere Misurare [le prestazioni dell'applicazione dalla riga di comando.](../profiling/profile-apps-from-command-line.md)