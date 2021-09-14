---
title: Analisi dei risultati dei test di carico
description: Informazioni su come visualizzare riquadri che offrono diversi modi per analizzare i risultati di un'esecuzione di test di carico, ad esempio un grafo nel tempo o tabelle dettagliate.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.pageresult
- vs.test.load.dialog.column
- vs.test.load.monitor.requestresult
- vs.test.load.monitor.testresult
- vs.test.load.monitor.table.view
- vs.test.load.monitor.agentresult
- vs.test.load.monitor.transactionresult
helpviewer_keywords:
- tables, Load Test Viewer options
- load test results, tables
- load tests, Load Test Viewer
- data [Visual Studio ALM], load test tables
- Load Test Viewer, tables
- load tests, results tables
ms.assetid: 0a84bda3-6051-45eb-9c7f-d57419e1f97d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 1b378eef2c5bb6d18d60f7680a3a4fbdf64c69fd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634276"
---
# <a name="analyze-load-test-results-and-errors-in-the-tables-view-of-the-load-test-analyzer"></a>Analizzare gli errori e i risultati dei test di carico nella visualizzazione Tabelle dell'Analizzatore test di carico

Quando si visualizzano i risultati dell'esecuzione di un test di carico, è possibile aprire riquadri diversi che consentono di analizzare i dati in vari modi. ossia in un grafico, per rilevare le modifiche nel corso del tempo, oppure in tabelle dettagliate.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Per passare alla visualizzazione tabella, scegliere Tabelle **sulla barra degli** strumenti del test **di** carico. Per passare da una tabella all'altra usare l'elenco a discesa **Tabella** nella barra degli strumenti sopra la griglia della tabella. In visualizzazione tabella è possibile visualizzare fino a cinque tabelle alla volta. Per ulteriori informazioni, vedere [Affiancare tabelle di un test di carico](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#tile-load-test-tables) in questo argomento.

La maggior parte di valori numerici visualizzata in una tabella per i contatori delle prestazioni è cumulativa per l'intera esecuzione di test di carico. Le colonne denominate **Ultimo** sono un'eccezione e rappresentano il valore dell'intervallo di campionamento più recente.

> [!NOTE]
> Le colonne denominate **Ultimo** sono disponibili solo durante l'esecuzione di un test di carico. Al termine del test di carico, non sono disponibili.

È possibile ordinare la maggior parte delle tabelle scegliendo il titolo della colonna da usare come riferimento. Per impostazione predefinita, in alcune tabelle non vengono visualizzate tutte le colonne disponibili. È possibile aggiungere colonne alle tabelle, se sono disponibili. Per aggiungere colonne, fare clic con il pulsante destro del mouse sulla tabella e scegliere **Aggiungi/Rimuovi colonne**.

> [!NOTE]
> È possibile copiare i dati da una tabella in altre applicazioni come Excel per eseguire altre analisi.

## <a name="the-load-test-tables"></a>Tabelle di test di carico

Nella tabella seguente sono elencate le tabelle disponibili per l'analisi delle esecuzioni di test di carico.

|Nome tabella|Descrizione|
|-|-|
|Errors|Visualizza un elenco di errori generati durante l'esecuzione del test di carico. Per altre informazioni, vedere [La tabella Errori](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-errors-table) in questo argomento e Analizzare i risultati del test di [carico.](../test/analyze-load-test-results-using-the-load-test-analyzer.md)|
|Pagine|Visualizza un elenco di pagine visitate durante l'esecuzione di un test di carico. Alcuni dati di questa tabella sono disponibili solo al termine di un test di carico. Per altre informazioni, vedere [Procedura: Visualizzare la risposta della pagina Web.](../test/how-to-view-web-page-response-time-in-a-load-test.md)|
|Requests|Visualizza dettagli relativi alle singole richieste emesse durante un test di carico, tra cui tutte le richieste HTTP e le richieste dipendenti, ad esempio immagini. Per altre informazioni, vedere [la tabella Requests](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-requests-table) in questo argomento.|
|Traccia SQL|Visualizza i risultati della traccia SQL. Questa tabella è disponibile solo al termine di un test di carico e soltanto se durante il test è stata usata la traccia SQL. Per altre informazioni, vedere [La tabella SQL dati di traccia](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table) in questo argomento.|
|Test|Visualizza dettagli relativi ai singoli test eseguiti durante un test di carico. Per altre informazioni, vedere [la tabella Test](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-tests-table) in questo argomento.|
|Soglie|Visualizza un elenco di violazioni delle regole di soglia verificatesi durante l'esecuzione del test di carico. Per altre informazioni, vedere [Analisi delle violazioni delle regole di soglia.](../test/analyze-threshold-rule-violations-in-load-tests.md)|
|Transazioni|Visualizza un elenco delle transazioni effettuate durante un'esecuzione di test di carico. Per altre informazioni, vedere [la tabella Transactions](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-transactions-table) in questo argomento.|
|Agenti|Vengono visualizzati dettagli solo se per il test di carico vengono usati un controller di test e agenti di test. Viene visualizzato un elenco degli agenti usati durante l'esecuzione dei test di carico. Nella tabella Agenti è incluso il numero di richieste testate dall'agente nonché, di tali richieste, il numero che non ha superato il test. Nella tabella Agenti è anche incluso il numero di test della combinazione dei test di carico completato dall'agente nonché, di tali test, il numero che non ha avuto esito positivo.|
|Dettagli test|Vengono visualizzati i dettagli per i test inclusi nella combinazione di test per il test di carico. Tra i dettagli sono inclusi il nome del test, lo scenario in cui ha avuto luogo il test, l'ora di avvio, il tempo impiegato per l'esecuzione e i risultati dell'operazione con l'indicazione del superamento o meno del test. Se il test non è stato superato, viene visualizzato un collegamento nella colonna **Dettagli**. È possibile scegliere il collegamento per visualizzare l'Editor test prestazioni Web con la richiesta non riuscita evidenziata.|

## <a name="collect-percentile-data"></a>Raccogliere i dati percentili

Alcune tabelle di test di carico possono contenere colonne aggiuntive, che includono i dati percentili e i tempi di risposta suddivisi in gruppi in base all'emulazione della rete. Per impostazione predefinita, questi dati non vengono raccolti. I dai percentili sono disponibili solo quando si salvano i risultati in un database e non quando si esegue il salvataggio in locale. Per altre informazioni, vedere [Gestione dei risultati del test di carico in Load Risultati test Repository](../test/manage-load-test-results-in-the-load-test-results-repository.md). Inoltre, per raccogliere questi dati, nell'**editor test di carico**, sotto il nodo **Impostazioni di esecuzione**, selezionare il nodo dell'impostazione di esecuzione specifico da modificare. Nella finestra **Proprietà**, per la proprietà **Intervallo archiviazione dettagli**, selezionare **StatisticsOnly** o **AllIndividualDetails**. Per altre informazioni, vedere [Procedura: Visualizzare la risposta della pagina Web.](../test/how-to-view-web-page-response-time-in-a-load-test.md)

## <a name="the-requests-table"></a>Tabella Richieste

Nella tabella **Richieste** vengono visualizzati i dettagli relativi alle singole richieste emesse durante un test di carico, tra cui tutte le richieste HTTP e le richieste dipendenti, ad esempio immagini. Le richieste sono elencate in base a test e scenario, perché una richiesta può essere inclusa in diversi test e scenari.

Nella tabella seguente sono elencate le colonne della tabella **Richieste**:

|Colonna|Descrizione|Visibile per impostazione predefinita|
|-|-|-|
|**Richiesta**|URL della richiesta. ad esempio *home.html* o *orange-arrow.gif*.|Sì|
|**Scenario**|Nome dello scenario.|Sì|
|**Test**|Nome del test.|Sì|
|**Totale**|Numero totale relativo a questa richiesta di test delle prestazioni Web emessa durante l'esecuzione del test di carico. Il totale include le richieste riuscite e non riuscite, ma non le richieste memorizzate nella cache, perché non vengono inviate al server Web.|Sì|
|**Riuscito**|Numero di volte in cui la richiesta è stata emessa ed è riuscita.|No|
|**Operazione non riuscita**|Numero di volte in cui la richiesta è stata emessa e non è riuscita. Le voci di questa colonna vengono visualizzate come collegamenti ipertestuali. È possibile scegliere un collegamento ipertestuale per visualizzare un elenco dei singoli errori nella finestra di dialogo **Errori test di carico**. Per altre informazioni, vedere [Analizzare i risultati del test di carico.](../test/analyze-load-test-results-using-the-load-test-analyzer.md)|Sì|
|**Richieste nella cache**|Numero totale di volte in cui la richiesta è già stata memorizzata nella cache.|No|
|**Richieste/sec**|Frequenza al secondo della richiesta durante l'esecuzione del test di carico.|No|
|**Richieste riuscite/sec**|Frequenza al secondo di questa richiesta durante l'esecuzione del test di carico, per le istanze della richiesta che sono riuscite.|No|
|**Richieste non riuscite/sec**|Frequenza al secondo di questa richiesta durante l'esecuzione del test di carico, per le istanze della richiesta che non sono riuscite.|No|
|**Tempo primo byte**|Tempo medio impiegato per ricevere il primo byte della risposta, misurato dal momento in cui la richiesta è stata inviata al server Web. Le unità sono espresse in secondi.|No|
|**Tempo di risposta**|Tempo medio impiegato per ricevere l'intera risposta a una richiesta, misurato dal momento in cui la richiesta è stata inviata al server Web. Le unità sono espresse in secondi.|Sì|
|**Lunghezza del contenuto**|Lunghezza media del contenuto della risposta alla richiesta. Le unità sono espresse in byte.|Sì|

## <a name="the-tests-table"></a>Tabella Test

Nella tabella **Test** vengono visualizzati i dettagli relativi ai singoli test durante un test di carico. I test sono elencati in base a test e scenario, perché un test può essere incluso in diversi scenari.

Nella tabella seguente sono elencate le colonne della tabella **Test**.

|Colonna|Descrizione|Visibile per impostazione predefinita|
|-|-|-|
|**Test**|Nome del test.|Sì|
|**Scenario**|Nome dello scenario.|Sì|
|**Totale**|Numero totale di volte in cui il test è stato eseguito nello scenario. Include il numero di volte in cui il test è stato superato e non superato.|Sì|
|**Riuscito**|Numero totale di volte in cui il test è stato eseguito nello scenario ed è stato superato.|Sì|
|**Operazione non riuscita**|Numero totale di volte in cui il test è stato eseguito nello scenario e non è stato superato. Le voci di questa colonna vengono visualizzate come collegamenti ipertestuali. È possibile scegliere un collegamento ipertestuale per visualizzare un elenco dei singoli errori nella finestra di dialogo **Errori test di carico**. Per altre informazioni, vedere [Analizzare i risultati del test di carico.](../test/analyze-load-test-results-using-the-load-test-analyzer.md)|Sì|
|**Test/sec**|Frequenza al secondo del test durante l'esecuzione del test di carico.|Sì|
|**Richieste riuscite/sec**|Frequenza al secondo di questo test durante l'esecuzione del test di carico, per le istanze del test che sono state superate.|No|
|**Richieste non riuscite/sec**|Frequenza al secondo di questo test durante l'esecuzione del test di carico, per le istanze del test che non sono state superate.|No|
|**Ora test**|Tempo medio impiegato per eseguire il test durante il test di carico. Le unità sono espresse in secondi.|Sì|
|**Tempo test 90%**|Il novantesimo valore percentile per Tempo test.|No|
|**Tempo test 95%**|Il novantacinquesimo valore percentile per Tempo test.|Sì|
|**Richieste/Test**|Numero medio di richieste nel test se si tratta di un test delle prestazioni Web.|No|

## <a name="the-transactions-table"></a>Tabella Transazioni

Nella tabella **Transazioni** viene visualizzato un elenco delle transazioni effettuate durante l'esecuzione di un test di carico. Le transazioni si riferiscono alle transazioni definite in un test delle prestazioni Web o ai timer definiti in uno unit test. Non si riferiscono alle transazioni di database.

Nella tabella seguente sono elencate le colonne della tabella **Transazioni**.

> [!NOTE]
> Per visualizzare tutte le colonne, è necessario abilitare la proprietà Intervallo archiviazione dettagli associata all'impostazione esecuzione test attiva. Per altre informazioni, vedere [Procedura: Specificare la proprietà Timing Details Archiviazione](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

|Colonna|Descrizione|Visibile senza i dettagli dell'intervallo|
|-|-|-|
|**Transazione**|Nome della transazione.|Sì|
|**Scenario**|Nome dello scenario.|Sì|
|**Test**|Nome del test.|Sì|
|**Totale**|Numero totale di transazioni eseguite durante il test di carico.|Sì|
|**Tempo transazione**|Tempo impiegato per eseguire la transazione durante un'esecuzione dei test di carico. Per i test delle prestazioni Web, il tempo interazione utente è incluso nel calcolo. Le unità sono espresse in secondi.|No|
|**Tempo di risposta**|Tempo di risposta per la transazione del test delle prestazioni Web nell'esecuzione di un test di carico. Tempo di risposta è diverso da Tempo transazione, in quanto il primo non include gli eventuali tempi interazione utente presenti durante la transazione. Le unità sono espresse in secondi.|No|
|**Ave. Transaction Time**|Tempo medio della transazione. Sono inclusi i tempi di interazione utente. Ad esempio, se si dispone di tre richieste, ognuna con un tempo di interazione utente, nella durata saranno inclusi tali tempi di interazione utente nonché l'ora effettiva di esecuzione delle richieste.|No|
|**Ave. Tempo di risposta**|Tempo di risposta medio per la transazione di un test delle prestazioni Web nell'esecuzione di un test di carico. Tempo di risposta è diverso da Tempo transazione, in quanto il primo non include gli eventuali tempi interazione utente presenti durante la transazione. Le unità sono espresse in secondi.|No|
|**Tempo di risposta minimo**|Non sono inclusi i tempi di interazione utente.|No|
|**Tempo di risposta massimo**|Non sono inclusi i tempi di interazione utente.|No|
|**Mediana tempo di risposta**|Non sono inclusi i tempi di interazione utente.|No|
|**Tempo di risposta 90%**|Il novantesimo valore percentile per Tempo transazione. Non sono inclusi i tempi di interazione utente. **Nota**: è un valore diverso da quello usato in Visual Studio Team System 2008 Test Load Agent, cioè **Tempo transazione 90%**.|No|
|**Tempo di risposta 95%**|Il novantacinquesimo valore percentile per Tempo transazione. Non sono inclusi i tempi di interazione utente. **Nota**: è un valore diverso da quello usato in Visual Studio Team System 2008 Test Load Agent, cioè **Tempo transazione 95%**.|No|
|**Tempo di risposta 99%**|Il novantanovesimo valore percentile per Tempo transazione. Non sono inclusi i tempi di interazione utente.|No|
|**Deviazione standard tempo di risposta**|Non sono inclusi i tempi di interazione utente.|No|

## <a name="the-errors-table"></a>Tabella degli errori

Quando si esegue un test di carico, è possibile analizzare gli errori che si verificano. L'analisi degli errori e la modifica dei test rappresentano una parte importante del processo di test di carico. Se si verificano errori, sulla barra di stato del test di carico viene visualizzato il collegamento ipertestuale **errori** che ne specifica il numero. Per visualizzare la tabella degli errori, scegliere il collegamento ipertestuale.

Nella tabella degli errori sono raggruppati gli errori, in base al tipo e al sottotipo, che si sono verificati durante un test di carico. Nella tabella è anche presente una riga **totale** che specifica il totale di tutti gli errori che si sono verificati.

La tabella degli errori contiene le seguenti colonne:

|Colonna|Descrizione|Visibile per impostazione predefinita|
|-|-|-|
|Tipo|Il tipo di errore, ad esempio HttpError.|Sì|
|Sottotipo|Il sottotipo di errore, ad esempio LoadTestException.|Sì|
|Conteggio|Il numero di errori di questo tipo che si sono verificati durante il test di carico. Le voci di questa colonna vengono visualizzate come collegamenti ipertestuali. È possibile fare clic su qualsiasi collegamento ipertestuale per visualizzare un elenco dei singoli errori.|Sì|
|Ultimo messaggio|Messaggio in cui viene descritto l'errore, ad esempio 404 - NotFound.|Sì|

Per altre informazioni, vedere [Uso delle tabelle dei test di carico.](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)

### <a name="drill-down-to-the-error-list"></a>Drill-down nell'elenco degli errori

Nella tabella degli errori sono raggruppati gli errori per tipo e sottotipo. Per visualizzare una tabella dei singoli errori, aprire la finestra di dialogo **Errori test di carico**. Per visualizzare la finestra di dialogo, scegliere un collegamento ipertestuale nella colonna **Conteggio** della tabella degli errori. È anche possibile fare clic con il pulsante destro del mouse su una riga della tabella degli errori popolata e quindi scegliere **Errori**.

> [!NOTE]
> Vengono raccolte solo le prime 1.000 istanze di qualsiasi combinazione di tipo e sottotipo di errore. Quando si apre la finestra di dialogo **Errori test di carico** verranno visualizzate al massimo le prime 1.000 istanze di tale errore.

La tabella **Errori test di carico** contiene le seguenti colonne:

|Colonna|Descrizione|
|-|-|
|**Time**|L'ora durante il test di carico in cui si è verificato l'errore.|
|**Agent**|Il nome del computer agente in cui si è verificato l'errore. Questo è importante quando si eseguono test di carico usando controller di test e agenti di test. Per altre informazioni, vedere [Installare e configurare agenti di test](../test/lab-management/install-configure-test-agents.md).|
|**Test**|Nome del test delle prestazioni Web in cui si è verificato l'errore.|
|**Scenario**|Il nome dello scenario in cui si è verificato l'errore.|
|**Richiesta**|L'URL della richiesta in cui si è verificato l'errore.|
|**Tipo**|Il tipo di errore, ad esempio HttpError.|
|**Sottotipo**|Il sottotipo di errore, ad esempio LoadTestException.|
|**Text**|Il testo del messaggio di errore, ad esempio 404 - NotFound.|
|**Tra elementi sovrapposti**|Le voci di questa colonna sono vuote o contengono la parola **Stack** in formato collegamento ipertestuale. È possibile scegliere il collegamento ipertestuale per visualizzare la traccia dello stack dell'errore.|
|**Dettagli**|Le voci di questa colonna sono vuote o contengono la parola **TestLog** in formato collegamento ipertestuale. Questo collegamento può consentire di isolare errori nel test di carico. Ad esempio, se si sceglie il collegamento **TestLog** in un errore di richiesta di test delle prestazioni Web, i risultati per il test delle prestazioni Web verranno visualizzati nel visualizzatore prestazioni Web Risultati test Ed evidenziare l'errore della richiesta.|

> [!NOTE]
> È possibile ordinare la tabella scegliendo le intestazioni delle colonne.

## <a name="the-sql-trace-data-table"></a>Tabella dei dati di Traccia SQL

È possibile raccogliere dati di traccia SQL durante un'esecuzione dei test di carico da analizzare in un secondo momento. Grazie alla raccolta dei dati di traccia, è possibile identificare le query e le stored procedure che vengono eseguite con maggiore lentezza nel database SQL Server sottoposto a test.

Se la traccia SQL è attivata, durante l'esecuzione del test di carico viene creato un file contenente i dati della traccia. Tali dati vengono automaticamente salvati nell'archivio dei risultati del test di carico alla fine dell'esecuzione del test, mentre il file della traccia viene eliminato. Per analizzare i dati di traccia, aprire la tabella **Traccia SQL** al termine del test di carico.

### <a name="to-view-sql-trace-data"></a>Per visualizzare i dati di traccia SQL

1. Nell'analizzatore test di carico scegliere **Tabelle** sulla barra degli strumenti per assicurarsi che la griglia della tabella sia visualizzata.

2. Nella casella di riepilogo **Tabella** selezionare **Traccia SQL**.

3. I dati di traccia raccolti durante l'esecuzione verranno visualizzati nella griglia. Nella tabella sono elencate le operazioni SQL eseguite più lentamente, ordinate in base alla durata, con l'operazione più lenta all'inizio dell'elenco. In genere la colonna **Durata** è la prima colonna da esaminare. I dati vengono espressi in millisecondi.

   Di seguito sono riportate le colonne visualizzate:

    - **Event Class**

    - **Duration**

    - **CPU**

    - **Reads**

    - **Writes**

    - **TextData**

    - **StartTime**

    - **EndTime**

   Se si vuole tracciare eventi SQL diversi dai dati identificati in queste colonne, è possibile configurare una traccia SQL personalizzata tramite SQL Profiler, uno strumento separato da Visual Studio.

## <a name="tile-load-test-tables"></a>Affiancare tabelle di un test di carico

Quando si visualizzano i risultati di un'esecuzione di test di carico, è possibile visualizzare i dati sotto forma di tabelle dettagliate. Per passare alla visualizzazione tabella, scegliere Tabelle **sulla barra degli** strumenti del test **di** carico. Le tabelle disponibili sono le seguenti: **Errori**, **Pagine**, **Richieste**, **Traccia SQL**, **Test**, **Soglie** e **Transazioni**. Per altre informazioni, vedere [Utilizzo di tabelle di test di carico](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

In visualizzazione tabella è possibile visualizzare fino a quattro tabelle non sovrapposte alla volta.

### <a name="to-tile-tables"></a>Per affiancare le tabelle

1. Sulla barra **degli strumenti dell'analizzatore test** di carico scegliere **Tabelle**.

     Verrà aperta la visualizzazione tabella. Il layout predefinito è costituito da due pannelli orizzontali.

2. Fare clic sul pulsante del **layout** sulla barra degli strumenti dell'**Analizzatore test di carico** e scegliere una delle seguenti opzioni:

    - **Un pannello**

    - **Due pannelli orizzontali**

    - **Tre pannelli orizzontali**

    - **Quattro pannelli orizzontali**

3. Per passare tra le diverse tabelle, usare l'elenco a discesa Tabella sulla barra degli strumenti di ciascun pannello.

    > [!NOTE]
    > Non è possibile visualizzare la stessa tabella in più di un pannello. Se si sostituisce la tabella correntemente visualizzata in uno dei pannelli con quella visualizzata in un altro, in quest'ultimo verrà visualizzata la tabella sostituita nel primo.

## <a name="see-also"></a>Vedi anche

- [Analizzare i risultati del test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Procedura: Accedere ai risultati del test di carico per l'analisi](../test/how-to-access-load-test-results-for-analysis.md)
- [Analizzare i risultati del test di carico nella visualizzazione Grafici](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Analisi delle violazioni delle regole di soglia](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Gestire i risultati del test di carico nel repository di Risultati test carico](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Cenni preliminari sul riepilogo dei risultati dei test di carico](../test/load-test-results-summary-overview.md)
