---
title: Uso dei dati IntelliTrace salvati | Microsoft Docs
description: Usare un file IntelliTrace (.iTrace) per avviare il debug in un punto specifico dell'esecuzione. Il file contiene informazioni registrate da Intellitrace da un'esecuzione dell'app.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.norepro
helpviewer_keywords:
- iTrace files
- IntelliTrace, log files
- IntelliTrace log files
- .iTrace files
ms.assetid: 9f2cce86-345a-4e22-84ba-91542d81e67a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a62e0714da65552eedc6ca989a5035cdcf655b8d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122096830"
---
# <a name="using-saved-intellitrace-data-c-visual-basic-c"></a>Uso dei dati IntelliTrace salvati (C#, Visual Basic, C++)

Passare a specifici punti nell'esecuzione di un'applicazione quando si avvia il debug da un file di log IntelliTrace (.iTrace). Questo file può contenere eventi di prestazioni, eccezioni, thread, passi del test, moduli e altre informazioni di sistema che IntelliTrace ha raccolto durante l'esecuzione dell'applicazione.

 Assicurarsi di disporre degli elementi seguenti:

- File di origine e file di simboli (.pdb) corrispondenti per il codice dell'applicazione. In caso contrario, Visual Studio non consente di risolvere i percorsi di origine e verrà visualizzato il messaggio "Simboli non trovati". Vedere [Specificare i file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) e [Diagnosticare i problemi dopo la distribuzione.](../debugger/diagnose-problems-after-deployment.md)

- Visual Studio Enterprise (ma non edizioni Professional o Community) in un computer di sviluppo o in un altro computer per aprire i file .iTrace

- Un file .iTrace da una di queste origini:

    |**Origine**|**Vedere**|
    |----------------|-------------|
    |Una sessione di IntelliTrace in Visual Studio Visual Studio Enterprise (ma non edizioni Professional o Community)|[Funzionalità di IntelliTrace](../debugger/intellitrace-features.md)|
    |Microsoft Monitoring Agent, in modalità autonoma o con System Center 2012 R2 Operations Manager, per app Web ASP.NET e applicazioni SharePoint in esecuzione in fase di distribuzione|-   [Diagnosticare i problemi dopo la distribuzione](../debugger/diagnose-problems-after-deployment.md)<br />-   [Novità di System Center 2012 R2 Operations Manager](/previous-versions/system-center/system-center-2012-R2/dn249700(v=sc.12))|

## <a name="what-do-you-want-to-do"></a><a name="GetStarted"></a> Cosa si vuole fare?

- [Aprire un log IntelliTrace](#Open)

- [Leggere il log IntelliTrace](#Understand)

- [Avviare il debug da un log IntelliTrace](#StartDebugging)

## <a name="open-an-intellitrace-log"></a><a name="Open"></a> Aprire un log IntelliTrace
 Aprire il file .iTrace in un computer con Visual Studio Enterprise.

- Fare doppio clic sul file .iTrace all'esterno di Visual Studio oppure aprire il file da Visual Studio.

     \- - oppure -

- Se il file .iTrace viene associato a un elemento di lavoro Team Foundation Server, seguire questi passaggi nell'elemento di lavoro:

  - In **Tutti i collegamenti** individuare il file .iTrace. Aprirlo.

    \- - oppure -

  - In **Passaggi ripetizione bug** scegliere il collegamento **IntelliTrace** .

> [!TIP]
> Se si chiude il file IntelliTrace durante il debug, è possibile riaprirlo facilmente. Scegliere **IntelliTrace** dal menu **Debug**, quindi selezionare **Mostra riepilogo log**. È inoltre possibile scegliere **Mostra riepilogo log** nella finestra **IntelliTrace** . Questo comando è disponibile solo se si esegue il debug con IntelliTrace.

## <a name="understand-the-intellitrace-log"></a><a name="Understand"></a> Informazioni sul log IntelliTrace
 Alcune delle sezioni seguenti del file con estensione iTrace vengono visualizzate solo se sono stati raccolti dati da una determinata origine, ad esempio da SharePoint applicazioni.

|**Sezione**|**Contiene**|**Origine della raccolta**|
|-----------------|------------------|---------------------------|
|[Violazioni di prestazioni](#Performance)|Eventi di prestazioni con chiamate di funzione che superano la soglia configurata|Microsoft Monitoring Agent, agente di raccolta autonomo o con System Center 2012 R2 Operations Manager per ASP.NET web ospitate in IIS|
|[Dati eccezione](#ExceptionData)|Eccezioni, incluso lo stack di chiamate completo per ogni eccezione|Tutte le origini|
|[Analisi](#Analysis)|Solo per applicazioni SharePoint 2010 e SharePoint 2013. Esaminare eventi SharePoint e IntelliTrace, ad esempio eventi del debugger, eventi ULS, eccezioni non gestite e altri dati registrati da Microsoft Monitoring Agent.|Microsoft Monitoring Agent, agente di raccolta autonomo o con System Center 2012 R2 Operations Manager|
|[Informazioni di sistema](#SystemInfo)|Impostazioni e specifiche del sistema host|Tutte le origini|
|[Elenco dei thread](#ThreadsList)|Thread eseguiti durante la raccolta|Tutte le origini|
|[Moduli](#Modules)|Moduli caricati dal processo di destinazione nell'ordine di caricamento.|Tutte le origini|
|[Richiesta Web](#Modules)|Dati delle richieste Web per applicazioni Web IIS di produzione e SharePoint 2010 e SharePoint 2013|Microsoft Monitoring Agent e l'agente di raccolta autonomo|

 Di seguito sono indicati alcuni suggerimenti per individuare informazioni in ogni sezione:

- Per ordinare i dati, selezionare un'intestazione di colonna.

- Per filtrare i dati, usare la casella di ricerca. La ricerca di testo normale funziona su tutte le colonne, ad eccezione di quelle dell'ora. È inoltre possibile filtrare le ricerche a una determinata colonna con un filtro per colonna. Digitare il nome della colonna senza spazi, due punti (**:**) e il valore di ricerca. Usare un punto e virgola (**;**) per aggiungere un'altra colonna e un altro valore di ricerca.

     Ad esempio, per trovare gli eventi di prestazioni con la parola "slow" nella colonna **Descrizione** , digitare:

     `Description:slow`

## <a name="start-debugging-from-an-intellitrace-log"></a><a name="StartDebugging"></a> Avviare il debug da un log IntelliTrace

### <a name="performance-violations"></a><a name="Performance"></a> Violazioni delle prestazioni
 Rivedere gli eventi di prestazioni registrati per l'app. È possibile nascondere gli eventi non frequenti.

##### <a name="to-start-debugging-from-a-performance-event"></a>Per avviare il debug da un evento di prestazioni

1. In **Violazioni prestazioni** esaminare gli eventi di prestazioni registrati, i relativi tempi di esecuzione totali e altre informazioni sugli eventi. Esaminare ulteriori dettagli sui metodi chiamati durante un evento di prestazioni specifico.

     ![Visualizzare i dettagli degli eventi di prestazioni](../debugger/media/ffr_itsummarypageperformance.png "FFR_ITSummaryPagePerformance")

     È inoltre sufficiente fare doppio clic sull'evento.

2. Nella pagina dell'evento rivedere i tempi di esecuzione per queste chiamate. Cercare una chiamata lenta nell'albero di esecuzione.

     Le chiamate più lente vengono visualizzate nella specifica sezione in caso di più chiamate, annidate o meno.

3. Espandere tale chiamata per rivedere tutte le chiamate e i valori di parametri annidati registrati in quel momento.

     Tastiera: per visualizzare o nascondere una chiamata annidata, premere rispettivamente **Freccia DESTRA** o **Freccia SINISTRA** . Per visualizzare e nascondere i valori dei parametri per una chiamata annidata, premere **BARRA SPAZIATRICE** .

     Avviare il debug dalla chiamata.

     ![Avviare il debug da una chiamata di metodo](../debugger/media/ffr_itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")

     È inoltre sufficiente fare doppio clic sulla chiamata o premere **INVIO** .

     Se il metodo è incluso nel codice dell'applicazione, Visual Studio passa a tale metodo.

     ![Passare al codice dell'applicazione da un evento di prestazioni](../debugger/media/ffr_itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")

     È possibile esaminare altri valori registrati, lo stack di chiamate, eseguire un'istruzione alla volta nel codice o usare la finestra **IntelliTrace** per [spostarsi in avanti o indietro tra gli altri metodi](../debugger/intellitrace.md) chiamati durante questo evento di prestazioni.

### <a name="exception-data"></a><a name="ExceptionData"></a> Dati eccezione
 Rivedere le eccezioni generate e registrate per l'app. È possibile raggruppare le eccezioni con lo stesso tipo e stack di chiamate in modo da visualizzare solo l'eccezione più recente.

##### <a name="to-start-debugging-from-an-exception"></a>Per avviare il debug da un'eccezione

1. In **Dati eccezione** esaminare gli eventi di eccezione registrati, i relativi tipi, i messaggi e il momento in cui si sono verificate le eccezioni. Per esaminare il codice in dettaglio, avviare il debug dall'evento più recente in un gruppo di eccezioni.

     ![Avviare il debug da un evento di eccezione](../debugger/media/ffr_itsummarypageexception.png "FFR_ITSummaryPageException")

     È inoltre sufficiente fare doppio clic sull'evento. Se gli eventi non sono raggruppati, scegliere **Debug evento**.

     Se l'eccezione si è verificata nel codice dell'applicazione, Visual Studio passa a questa posizione.

     ![Passare al codice dell'applicazione da un evento di eccezione](../debugger/media/ffr_itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")

     È possibile esaminare altri valori registrati, lo stack di chiamate o usare la finestra **IntelliTrace** per [spostarsi in avanti o indietro tra gli altri eventi registrati](../debugger/intellitrace.md), il codice correlato e i valori registrati in questi specifici momenti.

    |**Colonna**|**Mostra**|
    |----------------|-------------------|
    |**Tipo**|Tipo .NET dell'eccezione|
    |**Messaggio più recente** per eccezioni raggruppate o **Messaggio** per eccezioni non raggruppate|Messaggio fornito dall'eccezione|
    |**Conteggio** per eccezioni raggruppate|Numero di volte in cui è stata generata l'eccezione|
    |**ID thread** per eccezioni non raggruppate|ID del thread che ha generato l'eccezione|
    |**Ora evento più recente** oppure **Ora evento**|Timestamp registrato quando è stata generata l'eccezione|
    |**Stack**|Stack di chiamate per un'eccezione.<br /><br /> Per visualizzare lo stack di chiamate, scegliere un'eccezione dall'elenco. Lo stack di chiamate viene visualizzato sotto l'elenco di eccezioni.|

### <a name="analysis"></a><a name="Analysis"></a> Analisi
 Diagnosticare problemi con applicazioni SharePoint 2010 e SharePoint 2013 tramite un ID di correlazione SharePoint o esaminare qualsiasi eccezione non gestita individuata da Microsoft Monitoring Agent.

- Usare un ID di correlazione SharePoint per trovare gli eventi e le richieste web corrispondenti. Scegliere un evento e quindi avviare il debug nel punto e nel momento in cui si è verificato l'evento.

- Se tramite Microsoft Monitoring Agent sono state trovate eccezioni non gestite, è possibile scegliere un'eccezione e, successivamente, avviare il debug nel punto e nel momento in cui si è verificata l'eccezione.

##### <a name="start-debugging-with-a-sharepoint-correlation-id"></a>Avviare il debug con un ID correlazione di SharePoint

1. Copiare l'ID di correlazione SharePoint dalla relativa origine.

    Esempio:

    ![Errore di &#45; SharePoint IntelliTrace &#45;'ID correlazione](../debugger/media/sharepointerror_intellitrace.png "SharePointError_IntelliTrace")

2. Aprire il file .iTrace, quindi passare ad **Analisi** e immettere l'ID di correlazione SharePoint per esaminare eventi registrati e di richieste Web corrispondenti.

    ![Log IntelliTrace &#45; immettere SharePoint ID correlazione](../debugger/media/entersharepointcorrelationid.png "EnterSharePointCorrelationID")

3. In **Eventi richiesta** esaminare gli eventi. Partendo dall'alto, gli eventi vengono visualizzati nell'ordine in cui si sono verificati.

   1. Scegliere un evento per visualizzarne i dettagli.

   2. Scegliere **Avvia debug** per avviare il debug nel punto in cui si è verificato l'evento.

      ![File di log IntelliTrace &#45; eventi di richiesta Web &#43; eventi](../debugger/media/entersharepointcorrelationid2.png "EnterSharePointCorrelationID2")

   È possibile visualizzare questi tipi di eventi SharePoint insieme agli eventi IntelliTrace:

- **Eventi di profilo utente**

     Questi eventi si verificano quando SharePoint carica un profilo utente e quando le proprietà del profilo vengono lette o modificate.

- **Eventi del servizio di registrazione unificato**

     Microsoft Monitoring Agent consente di registrare un subset degli eventi del servizio di registrazione unificato SharePoint e questi campi:

    |**Campo IntelliTrace**|**Campo del servizio di registrazione unificato SharePoint**|
    |----------------------------|------------------------------|
    |**ID**|**EventID**|
    |**Level**|**Level**|
    |**ID della categoria**|**ID della categoria**|
    |**Categoria**|**Categoria**|
    |**Area**|**Prodotto**|
    |**Output**|**Messaggio**|
    |**ID correlazione**|**ID correlazione**|

##### <a name="start-debugging-from-an-unhandled-exception"></a>Avviare il debug da un'eccezione non gestita

1. Scegliere un ID di correlazione SharePoint per un'eccezione. Le eccezioni vengono raggruppate per tipo e stack di chiamate.

2. (Facoltativo) Espandere **Stack di chiamate** per visualizzare lo stack di chiamate per un gruppo di eccezioni.

3. Scegliere **Debug eccezione** per avviare il debug nel punto e nel momento in cui si è verificata l'eccezione.

    ![Eccezioni non gestite &#45; SharePoint log di IntelliTrace](../debugger/media/sharepointunhandledexceptions_intellitrace.png "SharePointUnhandledExceptions_IntelliTrace")

   Per una procedura dettagliata, vedere [Procedura dettagliata: debug di un'SharePoint tramite IntelliTrace.](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md) Per i tipi di dati che l'agente registra, vedere [Funzionalità intelliTrace](../debugger/intellitrace-features.md).

### <a name="threads-list"></a><a name="ThreadsList"></a> Elenco di thread
 Esaminare i thread registrati che sono stati eseguiti nel processo di destinazione. È possibile avviare il debug dal primo evento IntelliTrace valido in un thread selezionato.

##### <a name="to-start-debugging-from-a-specific-thread"></a>Per avviare il debug da un thread specifico

1. In **Elenco dei thread** scegliere un thread.

2. Nella parte inferiore di **Elenco dei thread** scegliere **Avvia debug**. È inoltre possibile fare doppio clic su un thread.

    Per avviare il debug dall'inizio dell'applicazione, fare doppio clic su **Thread principale**. Vedere [Funzionalità intelliTrace](../debugger/intellitrace-features.md).

   I dati dei thread creati dall'utente potrebbero essere più utili di quelli creati da un server e gestiti per applicazioni Web ospitate in IIS.

|**Colonna**|**Mostra**|
|----------------|-------------------|
|**ID**|Numero ID del thread|
|**Nome**|Nome del thread. I thread senza nome vengono visualizzati come " \<No Name> ".|
|**Start Time**|Ora di creazione del thread|
|**Ora fine**|Ora di completamento del thread|

##### <a name="to-start-debugging-from-a-specific-test-step"></a>Per avviare il debug da un passaggio di test specifico

1. Espandere **Griglia passaggi test**. Scegliere un passaggio di test.

2. Nella parte inferiore di **Griglia passaggi test** scegliere **Avvia debug**. È inoltre possibile fare doppio clic su un passaggio di test.

     Verrà avviato il debug dal primo evento IntelliTrace valido dopo il passaggio di test selezionato.

     Se sono presenti dati di test, IntelliTrace tenta di risolvere la compilazione di Team Foundation Server associata usata per l'esecuzione del test. Se la compilazione viene trovata, i simboli associati per l'app vengono risolti automaticamente.

|**Campo**|**Mostra**|
|---------------|-------------------|
|**Sessione test**|Sessioni di test registrate. In genere, ne è presente solo una. Questo elenco è vuoto se sono stati creati dati di test usando un test esplorativo manuale.|
|**Test Case**|Test case della sessione di test selezionata. Questo elenco è vuoto se sono stati creati dati di test usando un test esplorativo manuale.|
|**Griglia passaggi test**|Passaggi di test registrati con il risultato del test superato o non superato|

### <a name="system-info"></a><a name="SystemInfo"></a> Informazioni di sistema
 In questa sezione vengono mostrati i dettagli sul sistema che ha ospitato l'app, ad esempio informazioni sull'hardware, sul sistema operativo, sull'ambiente e sui singoli processi.

### <a name="modules"></a><a name="Modules"></a> Moduli
 In questa sezione vengono mostrati i moduli caricati dal processo di destinazione. I moduli vengono visualizzati nell'ordine di caricamento.

|**Colonna**|**Mostra**|
|----------------|-------------------|
|**Nome modulo**|Nome del file di modulo|
|**Percorso modulo**|Posizione sul disco in cui è stato caricato il modulo|
|**ID modulo**|Identificatore univoco del modulo specifico della versione, che contribuisce ai file dei simboli (PDB) corrispondenti. Vedere [Finding symbol (.pdb) files and source files](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).|

### <a name="where-can-i-get-more-information"></a>Dove è possibile ottenere ulteriori informazioni?
 [Uso dell'agente di raccolta autonomo IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)

 [Funzionalità di IntelliTrace](../debugger/intellitrace-features.md)

 [Raccogliere un maggior numero di dati di diagnostica durante i test manuali](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)

 [IntelliTrace](../debugger/intellitrace.md)

#### <a name="forums"></a>Forum
 [Debugger di Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home)

#### <a name="guidance"></a>Indicazioni
 [Test per il recapito continuo con Visual Studio 2012 - Capitolo 6: Casella degli strumenti di test](/previous-versions/msp-n-p/jj159337(v=pandp.10))
