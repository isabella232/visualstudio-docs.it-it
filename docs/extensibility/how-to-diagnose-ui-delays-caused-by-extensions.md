---
title: Diagnosi dei ritardi dell'interfaccia utente dell'estensione Visual Studio| Microsoft Docs
description: Visual Studio notifica se i ritardi dell'interfaccia utente potrebbero essere causati da un'estensione. Informazioni su come diagnosticare ciò che nel codice dell'estensione causa ritardi dell'interfaccia utente.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload: multiple
ms.openlocfilehash: 8ddb58405125b53c955324be55ccb5eec93000e4
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2021
ms.locfileid: "123398587"
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>Procedura: Diagnosticare i ritardi dell'interfaccia utente causati dalle estensioni

Quando l'interfaccia utente non risponde, Visual Studio esamina lo stack di chiamate del thread dell'interfaccia utente, iniziando dalla foglia e lavorando verso la base. Se Visual Studio determina che un stack frame di chiamata appartiene a un modulo che fa parte di un'estensione installata e abilitata, viene visualizzata una notifica.

![Notifica del ritardo dell'interfaccia utente (non risponde)](media/ui-delay-notification-in-vs.png)

La notifica informa l'utente che il ritardo dell'interfaccia utente (ovvero il mal di risposta nell'interfaccia utente) potrebbe essere stato il risultato del codice di un'estensione. Fornisce inoltre all'utente le opzioni per disabilitare l'estensione o le notifiche future per tale estensione.

Questo documento descrive come diagnosticare ciò che nel codice dell'estensione causa notifiche di ritardo dell'interfaccia utente.

> [!NOTE]
> Non usare l'istanza sperimentale Visual Studio diagnosticare i ritardi dell'interfaccia utente. Alcune parti dell'analisi dello stack di chiamate necessarie per le notifiche di ritardo dell'interfaccia utente vengono disattivate quando si usa l'istanza sperimentale, vale a dire che le notifiche di ritardo dell'interfaccia utente potrebbero non essere visualizzate.

Una panoramica del processo di diagnostica è la seguente:
1. Identificare lo scenario di trigger.
2. Riavviare Visual Studio con la registrazione delle attività attivata.
3. Avviare la traccia ETW.
4. Attivare di nuovo la notifica per la visualizzazione.
5. Arrestare la traccia ETW.
6. Esaminare il log attività per ottenere l'ID ritardo.
7. Analizzare la traccia ETW usando l'ID ritardo del passaggio 6.

Nelle sezioni seguenti questi passaggi verranno descritti in modo più dettagliato.

## <a name="identify-the-trigger-scenario"></a>Identificare lo scenario di trigger

Per diagnosticare un ritardo dell'interfaccia utente, è prima di tutto necessario identificare ciò che (sequenza di azioni) Visual Studio visualizzare la notifica. In questo modo è possibile attivare la notifica in un secondo momento con la registrazione attivata.

## <a name="restart-vs-with-activity-logging-on"></a>Riavviare Visual Studio con la registrazione delle attività attivata

Visual Studio possibile generare un "log attività" che fornisce informazioni utili durante il debug di un problema. Per attivare la registrazione delle attività in Visual Studio, aprire Visual Studio con l'opzione `/log` della riga di comando. Dopo Visual Studio, il log attività viene archiviato nel percorso seguente:

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

Per altre informazioni su come trovare l'ID istanza di Visual Studio, vedere Strumenti per il rilevamento e la gestione Visual Studio [istanze .](../install/tools-for-managing-visual-studio-instances.md) Questo log attività verrà utilizzato più avanti per ottenere altre informazioni sui ritardi dell'interfaccia utente e sulle notifiche correlate.

## <a name="starting-etw-tracing"></a>Avvio della traccia ETW

È possibile usare [PerfView](https://github.com/Microsoft/perfview/) per raccogliere una traccia ETW. PerfView offre un'interfaccia facile da usare sia per la raccolta di una traccia ETW che per l'analisi. Usare il comando seguente per raccogliere una traccia:

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

Ciò abilita il provider "Microsoft-VisualStudio", ovvero il provider che Visual Studio per gli eventi correlati alle notifiche di ritardo dell'interfaccia utente. Specifica anche la parola chiave per il provider del kernel che PerfView può usare per generare la **visualizzazione Stack tempo thread.**

## <a name="trigger-the-notification-to-appear-again"></a>Attivare di nuovo la notifica per la visualizzazione

Dopo che PerfView ha avviato la raccolta di tracce, è possibile usare la sequenza di azione del trigger (dal passaggio 1) per visualizzare nuovamente la notifica. Dopo aver visualizzato la notifica, è possibile arrestare la raccolta di tracce per PerfView per elaborare e generare il file di traccia di output.

## <a name="stop-etw-tracing"></a>Arrestare la traccia ETW

Per arrestare la raccolta di tracce, è sufficiente usare **il pulsante Arresta** raccolta nella finestra PerfView. Dopo l'arresto della raccolta di tracce, PerfView elabora automaticamente gli eventi ETW e genera un file di traccia di output.

## <a name="examine-the-activity-log-to-get-the-delay-id"></a>Esaminare il log attività per ottenere l'ID ritardo

Come accennato in precedenza, è possibile trovare il log attività *in %APPDATA%\Microsoft\VisualStudio \<vs_instance_id>\ActivityLog.xml*. Ogni volta Visual Studio rileva un ritardo dell'interfaccia utente dell'estensione, scrive un nodo nel log attività con `UIDelayNotifications` come origine. Questo nodo contiene quattro informazioni sul ritardo dell'interfaccia utente:

- ID ritardo interfaccia utente, un numero sequenziale che identifica in modo univoco un ritardo dell'interfaccia utente in una sessione di Visual Studio
- ID sessione, che identifica in modo univoco la Visual Studio sessione dall'inizio alla chiusura
- Indica se è stata visualizzata o meno una notifica per il ritardo dell'interfaccia utente
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
> Non tutti i ritardi dell'interfaccia utente comportano una notifica. È quindi consigliabile controllare sempre il valore **Notifica visualizzata?** per identificare correttamente il ritardo corretto dell'interfaccia utente.

Dopo aver trovato il ritardo corretto dell'interfaccia utente nel log attività, annota l'ID ritardo dell'interfaccia utente specificato nel nodo. L'ID verrà utilizzato per cercare l'evento ETW corrispondente nel passaggio successivo.

## <a name="analyze-the-etw-trace"></a>Analizzare la traccia ETW

Aprire quindi il file di traccia. È possibile eseguire questa operazione usando la stessa istanza di PerfView oppure avviando una nuova istanza e impostando il percorso della cartella corrente in alto a sinistra nella finestra sul percorso del file di traccia.

![Impostazione del percorso della cartella in Perfview](media/perfview-set-path.png)

Selezionare quindi il file di traccia nel riquadro  sinistro e aprirlo scegliendo Apri dal menu di scelta rapida o dal menu di scelta rapida.

> [!NOTE]
> Per impostazione predefinita, PerfView restituisce un archivio ZIP. Quando si apre *trace.zip*, decomprime automaticamente l'archivio e apre la traccia. È possibile ignorare questo passaggio deselezionando la casella **Zip durante la** raccolta di tracce. Tuttavia, se si prevede di trasferire e usare tracce in computer diversi, è consigliabile evitare di deselezionare la **casella ZIP.** Senza questa opzione, i file PDB necessari per gli assembly Ngen non accompagnano la traccia e pertanto i simboli degli assembly Ngen non verranno risolti nel computer di destinazione. Per altre [informazioni sui file](https://devblogs.microsoft.com/devops/creating-ngen-pdbs-for-profiling-reports/) PDB per gli assembly Ngen, vedere questo post di blog.

L'elaborazione e l'apertura della traccia da parte di PerfView possono richiedere alcuni minuti. Quando la traccia è aperta, sotto di essa viene visualizzato un elenco di diverse "visualizzazioni".

![Visualizzazione di riepilogo della traccia PerfView](media/perfview-summary-view-events-selected.png)

Per prima cosa si userà **la visualizzazione Eventi** per ottenere l'intervallo di tempo del ritardo dell'interfaccia utente:

1. Aprire la **visualizzazione Eventi** selezionando il nodo sotto la traccia e scegliendo Apri dal menu di scelta rapida o dal menu di `Events` scelta rapida. 
2. Selezionare " `Microsoft-VisualStudio/ExtensionUIUnresponsiveness` " nel riquadro sinistro.
3. Premere INVIO

La selezione viene applicata e tutti `ExtensionUIUnresponsiveness` gli eventi vengono visualizzati nel riquadro destro.

![Selezione di eventi nella visualizzazione Eventi](media/perfview-event-selection.png)

Ogni riga nel riquadro destro corrisponde a un ritardo dell'interfaccia utente. L'evento include un valore "DELAY ID" che deve corrispondere all'ID ritardo nel log attività del passaggio 6. Poiché viene generato alla fine del ritardo dell'interfaccia utente, il timestamp dell'evento (approssimativamente) contrassegna l'ora di fine `ExtensionUIUnresponsiveness` del ritardo dell'interfaccia utente. L'evento contiene anche la durata del ritardo. È possibile sottrarre la durata dal timestamp di fine per ottenere il timestamp dell'avvio del ritardo dell'interfaccia utente.

![Calcolo dell'intervallo di tempo di ritardo dell'interfaccia utente](media/ui-delay-time-range.png)

Nello screenshot precedente, ad esempio, il timestamp dell'evento è 12.125.679 e la durata del ritardo è 6.143.085 (ms). Pertanto
* L'inizio del ritardo è 12.125.679 - 6.143.085 = 5.982,594.
* L'intervallo di tempo di ritardo dell'interfaccia utente è compreso tra 5.982,594 e 12.125,679.

Dopo aver creato l'intervallo di tempo, è possibile chiudere la visualizzazione Eventi e aprire la visualizzazione Stack tempo thread (con attività **StartStop).**  Questa visualizzazione è particolarmente utile perché spesso le estensioni che bloccano il thread dell'interfaccia utente sono semplicemente in attesa su altri thread o su un'operazione associata all'I/O. Di conseguenza, la **visualizzazione Stack CPU,** che è l'opzione go-to per la maggior parte dei casi, potrebbe non acquisire il tempo che il thread impiega per il blocco perché non usa la CPU durante tale periodo. Gli **stack di tempo dei thread risolvono** questo problema visualizzando correttamente il tempo di blocco.

![Nodo Stack Di tempo thread (con attività StartStop) nella visualizzazione riepilogo di PerfView](media/perfview-thread-time-with-startstop-activities-stacks.png)

Quando si apre **la visualizzazione Stack di tempo dei** thread, scegliere il processo **devenv** per avviare l'analisi.

![Visualizzazione Stack tempo di thread per l'analisi dei ritardi dell'interfaccia utente](media/ui-delay-thread-time-stacks.png)

Nella visualizzazione **Stack** di tempo thread, in alto a sinistra nella pagina, è possibile impostare l'intervallo di tempo per i valori calcolati nel passaggio precedente e premere **INVIO** in modo che gli stack siano adattati a tale intervallo di tempo.

> [!NOTE]
> Determinare quale thread è il thread dell'interfaccia utente (avvio) può essere controintuitivo se la raccolta di tracce viene avviata dopo Visual Studio è già aperta. Tuttavia, i primi elementi nello stack del thread dell'interfaccia utente (avvio) sono molto probabilmente sempre DLL del sistema operativo (*ntdll.dll* *ekernel32.dll*) seguite da e quindi `devenv!?` da `msenv!?` . Questa sequenza consente di identificare il thread dell'interfaccia utente.

 ![Identificazione del thread di avvio](media/ui-delay-startup-thread.png)

È anche possibile filtrare ulteriormente questa visualizzazione includendo solo gli stack che contengono i moduli del pacchetto.

* Impostare **GroupPats su** testo vuoto per rimuovere qualsiasi raggruppamento aggiunto per impostazione predefinita.
* Impostare **IncPats in** modo da includere parte del nome dell'assembly oltre al filtro del processo esistente. In questo caso, deve essere **devenv. UIDelayR2**.

![Impostazione di GroupPath e IncPath nella visualizzazione Stack tempo di thread](media/perfview-tts-group-path-inc-path.png)

PerfView include indicazioni dettagliate nel menu **?** che è possibile usare per identificare i colli di bottiglia delle prestazioni nel codice. Inoltre, i collegamenti seguenti forniscono altre informazioni su come usare le API di threading Visual Studio per ottimizzare il codice:

* [https://github.com/Microsoft/vs-threading/blob/master/doc/index.md](https://github.com/Microsoft/vs-threading/blob/master/doc/index.md)
* [https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md)

È anche possibile usare il nuovo Visual Studio statici per le estensioni (NuGet [pacchetto](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers)qui ), che forniscono indicazioni sulle procedure consigliate per la scrittura di estensioni efficienti. Vedere un elenco di [analizzatori di VS SDK e](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md) di [analizzatori di threading.](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md)

> [!NOTE]
> Se non si riesce a risolvere la non risposta a causa di dipendenze su cui non si ha il controllo (ad esempio, se l'estensione deve chiamare servizi sincroni di Visual Studio sul thread dell'interfaccia utente), è necessario conoscerlo. Se si è membri del programma Visual Studio Partner, è possibile contattare Microsoft inviando una richiesta di supporto per gli sviluppatori. In caso contrario, usare lo strumento "Segnala un problema" per inviare commenti e suggerimenti e `"Extension UI Delay Notifications"` includere nel titolo. Includere anche una descrizione dettagliata dell'analisi.
