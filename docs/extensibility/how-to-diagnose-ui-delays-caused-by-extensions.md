---
title: Consente di ritardare la diagnosi di estensione dell'interfaccia utente in Visual Studio | Microsoft Docs
ms.date: 01/26/2018
ms.topic: conceptual
author: PooyaZv
ms.author: pozandev
manager: jillfra
ms.workload: multiple
ms.openlocfilehash: 00266fd8fbc881707652247e08b093ca4b15a88d
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2019
ms.locfileid: "58324344"
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>Procedura: Diagnosticare i ritardi dell'interfaccia utente causati dalle estensioni

Quando l'interfaccia utente smette di rispondere, Visual Studio esamina lo stack di chiamate del thread dell'interfaccia utente, partire dal nodo foglia e procedendo verso la base. Se Visual Studio determina che un frame dello stack di chiamate appartiene a un modulo che fa parte di un'estensione installata e abilitata, visualizza una notifica.

![Ritardo dell'interfaccia utente (blocco) notifica](media/ui-delay-notification-in-vs.png)

La notifica informa l'utente che il ritardo dell'interfaccia utente (vale a dire, il problema del blocco dell'interfaccia utente) deve essere il risultato del codice da un'estensione. Fornisce inoltre l'utente con le opzioni per disabilitare l'estensione o le notifiche future per l'estensione.

Questo documento descrive come eseguire la diagnostica nel codice dell'estensione causa notifiche ritardo dell'interfaccia utente.

> [!NOTE]
> Non utilizzare l'istanza sperimentale di Visual Studio per diagnosticare i ritardi dell'interfaccia utente. Alcune parti dell'analisi dello stack di chiamate necessaria per le notifiche di ritardo dell'interfaccia utente sono state disabilitate quando si usa l'istanza sperimentale, vale a dire che le notifiche di ritardo dell'interfaccia utente potrebbero non essere visualizzate.

Di seguito è fornita una panoramica del processo di diagnostica:
1. Identificare lo scenario di trigger.
2. Riavviare Visual Studio con l'attività di accesso.
3. Avviare l'analisi ETW.
4. Attivare la notifica venga visualizzato anche in questo caso.
5. Arrestare la traccia eventi ETW.
6. Esaminare il registro attività per ottenere l'ID di ritardo.
7. Analizzare la traccia ETW usando un ID di ritardo nel passaggio 6.

Nelle sezioni seguenti verranno esaminate in dettaglio questi passaggi.

## <a name="identify-the-trigger-scenario"></a>Identificare lo scenario di trigger

Per diagnosticare un ritardo dell'interfaccia utente, è necessario prima identificare quale (sequenza di azioni) fa in modo che Visual Studio per visualizzare la notifica. Si tratta affinché è in grado di attivare la notifica in un secondo momento con la registrazione attivata.

## <a name="restart-vs-with-activity-logging-on"></a>Riavviare Visual Studio con l'attività di accesso

Visual Studio può generare un log di attività"" che fornisce informazioni utili durante il debug di un problema. Per abilitare la registrazione in Visual Studio delle attività, aprire Visual Studio con il `/log` opzione della riga di comando. Dopo l'avvio di Visual Studio, il log attività verrà archiviato nel percorso seguente:

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

Per altre informazioni su come è possibile trovare il VS ID istanza, vedere [strumenti per il rilevamento e la gestione di istanze di Visual Studio](../install/tools-for-managing-visual-studio-instances.md). Si userà questo log di attività in un secondo momento per trovare altre informazioni sui ritardi dell'interfaccia utente e le notifiche correlate.

## <a name="starting-etw-tracing"></a>Avvio di ETW tracing

È possibile usare [PerfView](https://github.com/Microsoft/perfview/) per raccogliere una traccia ETW. PerfView fornisce un'interfaccia facile da usare per raccogliere una traccia ETW e per eseguire l'analisi. Per raccogliere una traccia, usare il comando seguente:

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

In questo modo il provider "Microsoft-VisualStudio", ovvero il provider di che Visual Studio utilizza per gli eventi correlati alle notifiche di ritardo dell'interfaccia utente. Specifica anche la parola chiave per il provider del kernel che è possibile usare PerfView per generare il **stack in fase di Thread** visualizzazione.

## <a name="trigger-the-notification-to-appear-again"></a>Attivare la notifica verrà nuovamente visualizzato

Una volta PerfView ha avviato la raccolta di traccia, è possibile utilizzare la sequenza di azioni di trigger (dal passaggio 1) per la notifica venga visualizzato anche in questo caso. Quando viene visualizzata la notifica, è possibile arrestare una raccolta delle tracce di PerfView elaborare e generare il file di output di traccia.

## <a name="stop-etw-tracing"></a>Arrestare la traccia eventi ETW

Per interrompere la raccolta delle tracce, è sufficiente usare il **arrestare la raccolta** pulsante nella finestra di PerfView. Dopo aver interrotto la raccolta delle tracce, PerfView automaticamente elaborerà gli eventi ETW e genera un file di output di traccia.

## <a name="examine-the-activity-log-to-get-the-delay-id"></a>Esaminare il log attività per ottenere l'ID di ritardo

Come accennato in precedenza, è possibile trovare il log attività *%APPDATA%\Microsoft\VisualStudio\<vs_instance_id > \ActivityLog.xml*. Ogni volta che Visual Studio rileva una ritardo dell'interfaccia utente di estensione, scrive un nodo nel log attività con `UIDelayNotifications` come origine. Questo nodo contiene quattro tipi di informazione per il ritardo dell'interfaccia utente:

- L'ID del ritardo dell'interfaccia utente, un numero sequenziale che identifica in modo univoco un ritardo dell'interfaccia utente in una sessione di Visual Studio
- L'ID di sessione, che identifica in modo univoco la sessione di Visual Studio dall'inizio alla chiusura
- Se è stata visualizzata una notifica per il ritardo dell'interfaccia utente
- L'estensione che probabilmente causa il ritardo dell'interfaccia utente

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
> Non tutti i risultati di ritardi dell'interfaccia utente in una notifica. Di conseguenza, è necessario verificare sempre il **notifica illustrata?** valore per identificare correttamente il ritardo dell'interfaccia utente a destra.

Dopo avere individuato il ritardo dell'interfaccia utente corretto nel log attività, annotare l'ID di ritardo dell'interfaccia utente specificato nel nodo. Si userà l'ID per cercare l'evento ETW corrispondente nel passaggio successivo.

## <a name="analyze-the-etw-trace"></a>Analizzare la traccia ETW

Successivamente, aprire il file di traccia. È possibile eseguire questa operazione usando la stessa istanza di PerfView o avviando una nuova istanza e impostando il percorso della cartella corrente nella parte superiore sinistra della finestra nel percorso del file di traccia.

![Impostare il percorso della cartella in Perfview](media/perfview-set-path.png)

Quindi, selezionare il file di traccia nel riquadro a sinistra e aprirlo scegliendone **aprire** dal menu di scelta rapida.

> [!NOTE]
> Per impostazione predefinita PerfView restituisce un archivio Zip. Quando si apre *trace.zip*, viene automaticamente decomprime l'archivio e verrà visualizzata la traccia. È possibile saltare questo passaggio se si deseleziona il **Zip** finestra durante la raccolta delle tracce. Tuttavia, se si prevede di trasferire e utilizzo delle tracce in diversi computer, è consigliabile evitare se si deseleziona il **Zip** casella. Senza questa opzione, PDB obbligatorio per gli assembly Ngen di accompagnamento non la traccia e pertanto i simboli da assembly Ngen non verranno risolti in computer di destinazione. (Vedere [questo post di blog](https://devblogs.microsoft.com/devops/creating-ngen-pdbs-for-profiling-reports/) per altre informazioni sui file PDB per gli assembly Ngen.)

Può richiedere diversi minuti prima che PerfView elaborare e aprire la traccia. Dopo aver aperta la traccia, viene visualizzato un elenco delle varie "visualizzazioni" sotto di esso.

![Visualizzazione Riepilogo traccia PerfView](media/perfview-summary-view-events-selected.png)

Si userà innanzitutto le **eventi** visualizzazione per ottenere l'intervallo di tempo del ritardo dell'interfaccia utente:

1. Aprire il **eventi** visualizzazione selezionando `Events` nodo nella traccia e scegliendo **Open** dal menu di scelta rapida o.
2. Selezionare "`Microsoft-VisualStudio/ExtensionUIUnresponsiveness`" nel riquadro sinistro.
3. Premere INVIO

La selezione venga applicata e all `ExtensionUIUnresponsiveness` gli eventi vengono visualizzati nel riquadro di destra.

![Selezione degli eventi nella visualizzazione eventi](media/perfview-event-selection.png)

Ogni riga nel riquadro di destra corrisponde a un ritardo dell'interfaccia utente. L'evento include un valore "ID ritardo" che deve corrispondere all'ID di ritardo nel log attività nel passaggio 6. Poiché `ExtensionUIUnresponsiveness` viene generato alla fine del ritardo dell'interfaccia utente, il timestamp dell'evento (approssimativamente) segni l'ora di fine del ritardo dell'interfaccia utente. L'evento contiene anche la durata del ritardo. È possibile sottrarre la durata dal timestamp finale per ottenere il timestamp di quando il ritardo dell'interfaccia utente avviata.

![Calcolare l'intervallo di tempo di ritardo dell'interfaccia utente](media/ui-delay-time-range.png)

Nello screenshot precedente, ad esempio, il timestamp dell'evento è 12,125.679 e la durata del ritardo è 6,143.085 (ms). Pertanto
* L'inizio di ritardo è 12,125.679 6,143.085 = 5,982.594.
* L'intervallo di tempo di ritardo dell'interfaccia utente è 5,982.594 a 12,125.679.

Dopo aver ottenuto l'intervallo di tempo, è possibile chiudere fuori il **eventi** consente di visualizzare e aprire il **gli stack di Thread di esecuzione (con le attività StartStop)** visualizzazione. Questa visualizzazione è particolarmente utile poiché spesso le estensioni che bloccano il thread dell'interfaccia utente sono semplicemente in attesa di un'operazione O-associate ai / o di altri thread. Di conseguenza, il **CPU Stack** visualizzazione, ovvero l'opzione ideale per la maggior parte dei casi, non può acquisire il tempo trascorso dal thread di blocco perché senza l'uso della CPU durante tale periodo. Il **stack in fase di Thread** risolve questo problema, correttamente bloccato che Mostra ora.

![Nodo ora (con le attività StartStop) gli stack di thread nella visualizzazione Riepilogo PerfView](media/perfview-thread-time-with-startstop-activities-stacks.png)

Durante l'apertura **stack in fase di Thread** consente di visualizzare, scegliere il **devenv** processo per avviare l'analisi.

![Visualizzazione stack di tempo per l'analisi di ritardo dell'interfaccia utente del thread](media/ui-delay-thread-time-stacks.png)

Nel **stack in fase di Thread** visualizzazione, in alto a sinistra della pagina, è possibile impostare l'intervallo di tempo per i valori sono calcolati nel passaggio precedente e premere **invio** in modo che gli stack vengono adattati per l'intervallo di tempo.

> [!NOTE]
> Determinare quale thread è l'interfaccia utente di thread (avvio) può essere illogico se la raccolta di traccia viene avviata dopo che Visual Studio è già aperto. Tuttavia, i primi elementi nello stack del thread dell'interfaccia utente (avvio) sono più probabile sempre le DLL di sistema operativo (*Ntdll. dll* e *kernel32.dll*) seguito da `devenv!?` e quindi `msenv!?` . Questa sequenza consente di identificare il thread dell'interfaccia utente.

 ![Che identifica il thread di avvio](media/ui-delay-startup-thread.png)

È inoltre possibile filtrare ulteriormente questa visualizzazione includendo solo gli stack che contengono i moduli dal pacchetto.

* Impostare **GroupPats** al testo vuoto per rimuovere qualsiasi forma di raggruppamento aggiunta per impostazione predefinita.
* Impostare **IncPats** includere parte del nome dell'assembly, oltre a filtro processo esistente. In questo caso, deve essere **devenv; UIDelayR2**.

![Impostazione GroupPath e IncPath in visualizzazione finestra Stack in fase di Thread](media/perfview-tts-group-path-inc-path.png)

PerfView ha dettagliate sotto il **aiutare** menu che è possibile usare per identificare i colli di bottiglia delle prestazioni nel codice. Inoltre, i collegamenti seguenti forniscono altre informazioni su come usare Visual Studio, le API per ottimizzare il codice di threading:

* [https://aka.ms/vsthreading](https://aka.ms/vsthreading)
* [https://aka.ms/vsthreadingcookbook](https://aka.ms/vsthreadingcookbook)

È anche possibile usare gli analizzatori statici di Visual Studio nuove per le estensioni (mobileengagement [qui](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers)), che forniscono informazioni aggiuntive sulle procedure consigliate per la scrittura di estensioni efficiente. Visualizzare un elenco delle [analizzatori di Visual Studio SDK](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md) e [threading analizzatori](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md).

> [!NOTE]
> Se non si riesce a risolvere il problema del blocco a causa di dipendenze non prevedono un controllo (ad esempio, se l'estensione deve chiamare i servizi di Visual Studio sincroni sul thread UI), vorremmo saperlo. Se sei un membro del programma Partner Visual Studio, è possibile contattare Microsoft inviando una richiesta di supporto per gli sviluppatori. In caso contrario, utilizzare lo strumento "Segnala un problema" per inviare commenti e suggerimenti e includere `"Extension UI Delay Notifications"` nel titolo. Includere anche una descrizione dettagliata dell'analisi.
