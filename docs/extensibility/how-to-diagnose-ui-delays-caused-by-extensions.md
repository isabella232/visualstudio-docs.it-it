---
title: Diagnosi dei ritardi dell'interfaccia utente di estensione in Visual Studio | Microsoft Docs
ms.date: 01/26/2018
ms.topic: conceptual
author: PooyaZv
ms.author: pozandev
manager: jillfra
ms.workload: multiple
ms.openlocfilehash: e8b35a566eb0f2457d6eb8ae3a33235df2a64cd3
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849153"
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>Procedura: diagnosticare i ritardi dell'interfaccia utente causati dalle estensioni

Quando l'interfaccia utente smette di rispondere, Visual Studio esamina lo stack di chiamate del thread dell'interfaccia utente, iniziando dalla foglia e lavorando verso la base. Se Visual Studio determina che un stack frame di chiamate appartiene a un modulo che fa parte di un'estensione installata e abilitata, viene visualizzata una notifica.

![Notifica ritardo interfaccia utente (non risposta)](media/ui-delay-notification-in-vs.png)

La notifica informa l'utente che il ritardo dell'interfaccia utente (ovvero la mancata risposta nell'interfaccia utente) potrebbe essere stato il risultato del codice di un'estensione. Fornisce inoltre all'utente le opzioni per disabilitare l'estensione o le notifiche future per tale estensione.

Questo documento descrive come è possibile diagnosticare ciò che si trova nel codice di estensione causando notifiche di ritardo dell'interfaccia utente.

> [!NOTE]
> Non usare l'istanza sperimentale di Visual Studio per diagnosticare i ritardi dell'interfaccia utente. Alcune parti dell'analisi dello stack di chiamate richieste per le notifiche di ritardo dell'interfaccia utente sono spente quando si usa l'istanza sperimentale, ovvero è possibile che le notifiche di ritardo dell'interfaccia utente non vengano visualizzate.

Una panoramica del processo di diagnostica è la seguente:
1. Identificare lo scenario di trigger.
2. Riavviare Visual Studio con l'accesso alle attività.
3. Avviare la traccia ETW.
4. Attivare la notifica per visualizzare nuovamente.
5. Arrestare la traccia ETW.
6. Esaminare il log attività per ottenere l'ID ritardo.
7. Analizzare la traccia ETW usando l'ID ritardo del passaggio 6.

Nelle sezioni seguenti verranno esaminati più dettagliatamente questi passaggi.

## <a name="identify-the-trigger-scenario"></a>Identificare lo scenario di attivazione

Per diagnosticare un ritardo dell'interfaccia utente, prima di tutto è necessario identificare quale (sequenza di azioni) fa in modo che Visual Studio visualizzi la notifica. In questo modo è possibile attivare la notifica in un secondo momento con la registrazione attivata.

## <a name="restart-vs-with-activity-logging-on"></a>Riavviare Visual Studio con accesso alle attività

Visual Studio può generare un "log attività" che fornisce informazioni utili per il debug di un problema. Per attivare la registrazione delle attività in Visual Studio, aprire Visual Studio con l'opzione della riga di comando `/log`. Dopo l'avvio di Visual Studio, il log attività viene archiviato nel percorso seguente:

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

Per altre informazioni su come trovare l'ID dell'istanza di VS, vedere [strumenti per il rilevamento e la gestione di istanze di Visual Studio](../install/tools-for-managing-visual-studio-instances.md). Questo log attività verrà usato in un secondo momento per trovare altre informazioni sui ritardi dell'interfaccia utente e le notifiche correlate.

## <a name="starting-etw-tracing"></a>Avvio della traccia ETW

È possibile utilizzare [PerfView](https://github.com/Microsoft/perfview/) per raccogliere una traccia ETW. PerfView fornisce un'interfaccia di facile utilizzo per la raccolta di una traccia ETW e per l'analisi. Usare il comando seguente per raccogliere una traccia:

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

In questo modo viene abilitato il provider "Microsoft-VisualStudio", che è il provider utilizzato da Visual Studio per gli eventi correlati alle notifiche di ritardo dell'interfaccia utente. Specifica anche la parola chiave per il provider kernel che PerfView può usare per generare la visualizzazione **stack di tempo del thread** .

## <a name="trigger-the-notification-to-appear-again"></a>Attiva la notifica per visualizzare di nuovo

Quando PerfView ha avviato la raccolta di tracce, è possibile usare la sequenza di azioni trigger (dal passaggio 1) per visualizzare di nuovo la notifica. Una volta visualizzata la notifica, è possibile arrestare la raccolta di tracce per PerfView per elaborare e generare il file di traccia di output.

## <a name="stop-etw-tracing"></a>Arresta traccia ETW

Per arrestare la raccolta di tracce, è sufficiente usare il pulsante **Interrompi raccolta** nella finestra PerfView. Dopo l'arresto della raccolta di tracce, PerfView elabora automaticamente gli eventi ETW e genera un file di traccia di output.

## <a name="examine-the-activity-log-to-get-the-delay-id"></a>Esaminare il log attività per ottenere l'ID ritardo

Come indicato in precedenza, è possibile trovare il log attività in *%APPDATA%\Microsoft\VisualStudio\<vs_instance_id > \ActivityLog.XML*. Ogni volta che Visual Studio rileva un ritardo dell'interfaccia utente dell'estensione, scrive un nodo nel log attività con `UIDelayNotifications` come origine. Questo nodo contiene quattro informazioni sul ritardo dell'interfaccia utente:

- ID ritardo dell'interfaccia utente, un numero sequenziale che identifica in modo univoco un ritardo dell'interfaccia utente in una sessione di Visual Studio
- ID sessione, che identifica in modo univoco la sessione di Visual Studio dall'inizio alla chiusura
- Indica se è stata visualizzata una notifica per il ritardo dell'interfaccia utente
- Estensione che probabilmente ha causato il ritardo dell'interfaccia utente

```xml
<entry>
  <record>271</record>
  <time>2018/02/03 12:02:52.867</time>
  <type>Information</type>
  <source>UIDelayNotifications</source>
  <description>A UI delay (Delay ID = 0) has been detected. (Session ID=16e49d4b-26c2-4247-ad1c-488edeb185e0; Blamed extension="UIDelayR2"; Notification shown? Yes.)</description>
</entry>
```

> [!NOTE]
> Non tutti i ritardi dell'interfaccia utente generano una notifica. Pertanto, è sempre necessario controllare la **notifica visualizzata?** valore per identificare correttamente il ritardo dell'interfaccia utente corretto.

Dopo aver individuato il ritardo dell'interfaccia utente corretto nel log attività, annotare l'ID ritardo dell'interfaccia utente specificato nel nodo. Si userà l'ID per cercare l'evento ETW corrispondente nel passaggio successivo.

## <a name="analyze-the-etw-trace"></a>Analizzare la traccia ETW

Successivamente, aprire il file di traccia. Questa operazione può essere eseguita usando la stessa istanza di PerfView o avviando una nuova istanza e impostando il percorso della cartella corrente nella parte superiore sinistra della finestra sul percorso del file di traccia.

![Impostazione del percorso della cartella in PerfView](media/perfview-set-path.png)

Quindi, selezionare il file di traccia nel riquadro a sinistra e aprirlo scegliendo **Apri** dal menu di scelta rapida o dal menu di scelta rapida.

> [!NOTE]
> Per impostazione predefinita, PerfView restituisce un archivio zip. Quando si apre *Trace. zip*, l'archivio viene decompresso automaticamente e viene aperta la traccia. È possibile ignorare questa operazione deselezionando la casella **zip** durante la raccolta delle tracce. Tuttavia, se si prevede di trasferire e usare tracce in computer diversi, è consigliabile evitare di deselezionare la casella **zip** . Senza questa opzione, il PDB obbligatorio per gli assembly NGEN non verrà associato alla traccia e pertanto i simboli degli assembly NGEN non verranno risolti nel computer di destinazione. Per ulteriori informazioni su PDB per gli assembly NGEN, vedere [questo post di Blog](https://devblogs.microsoft.com/devops/creating-ngen-pdbs-for-profiling-reports/) .

Possono essere necessari alcuni minuti prima che PerfView elabori e apra la traccia. Una volta aperta la traccia, viene visualizzato un elenco di diverse "visualizzazioni".

![Visualizzazione Riepilogo traccia PerfView](media/perfview-summary-view-events-selected.png)

Per ottenere l'intervallo di tempo del ritardo dell'interfaccia utente, si userà prima la visualizzazione **eventi** :

1. Aprire la visualizzazione **eventi** selezionando `Events` nodo sotto la traccia e scegliendo **Apri** dal menu di scelta rapida o dal menu di scelta rapida.
2. Selezionare "`Microsoft-VisualStudio/ExtensionUIUnresponsiveness`" nel riquadro sinistro.
3. Premere INVIO

La selezione viene applicata e tutti gli eventi `ExtensionUIUnresponsiveness` vengono visualizzati nel riquadro di destra.

![Selezione di eventi nella visualizzazione eventi](media/perfview-event-selection.png)

Ogni riga nel riquadro destro corrisponde a un ritardo dell'interfaccia utente. L'evento include un valore "ID ritardo" che deve corrispondere all'ID ritardo nel log attività del passaggio 6. Poiché `ExtensionUIUnresponsiveness` viene generato al termine del ritardo dell'interfaccia utente, il timestamp dell'evento (approssimativamente) contrassegna l'ora di fine del ritardo dell'interfaccia utente. L'evento contiene inoltre la durata del ritardo. È possibile sottrarre la durata dal timestamp finale per ottenere il timestamp di quando è stato avviato il ritardo dell'interfaccia utente.

![Calcolo dell'intervallo di tempo di ritardo dell'interfaccia utente](media/ui-delay-time-range.png)

Nella schermata precedente, ad esempio, il timestamp dell'evento è 12.125,679 e la durata del ritardo è 6.143,085 (MS). Pertanto
* Il ritardo di avvio è 12.125,679-6.143,085 = 5.982,594.
* L'intervallo di tempo di ritardo dell'interfaccia utente è compreso tra 5.982,594 e 12.125,679.

Una volta ottenuto l'intervallo di tempo, è possibile chiudere la visualizzazione **eventi** e aprire la visualizzazione **stack tempo thread (con attività startstop)** . Questa visualizzazione è particolarmente utile perché spesso le estensioni che bloccano il thread dell'interfaccia utente sono semplicemente in attesa di altri thread o di un'operazione associata a I/O. Quindi, la visualizzazione **dello stack della CPU** , che rappresenta l'opzione per la maggior parte dei casi, potrebbe non acquisire il tempo di blocco del thread poiché non sta utilizzando la CPU durante tale periodo di tempo. Lo **stack di tempo del thread** risolve questo problema visualizzando correttamente il tempo di blocco.

![Nodo stack tempo thread (con attività StartStop) in visualizzazione di riepilogo PerfView](media/perfview-thread-time-with-startstop-activities-stacks.png)

Durante l'apertura della visualizzazione **stack tempo thread** , scegliere il processo **devenv** per avviare l'analisi.

![Visualizzazione stack tempo thread per l'analisi dei ritardi dell'interfaccia utente](media/ui-delay-thread-time-stacks.png)

Nella visualizzazione **stack tempo thread** , nella parte superiore sinistra della pagina, è possibile impostare l'intervallo di tempo sui valori calcolati nel passaggio precedente e premere **invio** in modo che gli stack vengano modificati in base a tale intervallo di tempo.

> [!NOTE]
> Determinare quale thread è il thread dell'interfaccia utente (avvio) può essere intuitivo se la raccolta di tracce viene avviata dopo che Visual Studio è già aperto. Tuttavia, i primi elementi nello stack del thread dell'interfaccia utente (avvio) sono sempre le dll del sistema operativo più probabili (*ntdll. dll* e *Kernel32. dll*) seguite da `devenv!?` e quindi `msenv!?`. Questa sequenza può semplificare l'identificazione del thread dell'interfaccia utente.

 ![Identificazione del thread di avvio](media/ui-delay-startup-thread.png)

È anche possibile filtrare ulteriormente questa visualizzazione includendo solo gli stack contenenti moduli del pacchetto.

* Impostare **GroupPats** su testo vuoto per rimuovere tutti i raggruppamenti aggiunti per impostazione predefinita.
* Impostare **IncPats** in modo da includere parte del nome dell'assembly oltre al filtro di processo esistente. In questo caso, deve essere **devenv; UIDelayR2**.

![Impostazione di GroupPath e IncPath nella visualizzazione stack tempo thread](media/perfview-tts-group-path-inc-path.png)

In PerfView sono disponibili istruzioni dettagliate nel menu **Guida** che è possibile utilizzare per identificare i colli di bottiglia delle prestazioni nel codice. Inoltre, i collegamenti seguenti forniscono altre informazioni su come usare le API di threading di Visual Studio per ottimizzare il codice:

* [https://github.com/Microsoft/vs-threading/blob/master/doc/index.md](https://github.com/Microsoft/vs-threading/blob/master/doc/index.md)
* [https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md)

È anche possibile usare i nuovi analizzatori statici di Visual Studio per le estensioni (pacchetto NuGet [qui](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers)), che forniscono indicazioni sulle procedure consigliate per la scrittura di estensioni efficienti. Vedere un elenco degli analizzatori di [vs SDK](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md) e degli [analizzatori di threading](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md).

> [!NOTE]
> Se non è possibile risolvere la mancata risposta a causa delle dipendenze di cui non si ha il controllo (ad esempio, se l'estensione deve chiamare i servizi sincroni di Visual Studio nel thread dell'interfaccia utente), si vuole saperlo. Se si è membri del programma Visual Studio partner, è possibile contattarci inviando una richiesta di supporto per gli sviluppatori. In caso contrario, usare lo strumento "segnala un problema" per inviare commenti e suggerimenti e includere `"Extension UI Delay Notifications"` nel titolo. Includere anche una descrizione dettagliata dell'analisi.
