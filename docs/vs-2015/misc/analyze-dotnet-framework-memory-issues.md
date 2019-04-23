---
title: Analizzare i problemi di memoria di .NET Framework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.diagnostics.managedmemoryanalysis
ms.assetid: 43341928-9930-48cf-a57f-ddcc3984b787
caps.latest.revision: 9
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 75a51cbe851b6566ab210a3c8ae12a9b7c2e0d2b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60107658"
---
# <a name="analyze-net-framework-memory-issues"></a>Analizzare i problemi relativi alla memoria .NET Framework
L'analizzatore di memoria gestita di Visual Studio permette di rilevare perdite di memoria e uso non efficiente della memoria nel codice .NET. La versione minima di .NET Framework per il codice di destinazione è .NET Framework 4.5.  
  
 Lo strumento di analisi della memoria analizza le informazioni in *file dump con dati di heap* che una copia degli oggetti nella memoria di un'app. È possibile raccogliere file di dump (con estensione dmp) dall'IDE di Visual Studio oppure usando altri strumenti di sistema.  
  
- È possibile analizzare un singolo snapshot per ottenere informazioni sull'impatto relativo dei tipi di oggetto sull'uso della memoria e per trovare nell'app il codice che usa la memoria in modo non efficiente.  
  
- È anche possibile confrontare (*diff*) due snapshot di un'app per individuare le aree del codice che provocano la memoria utilizzo aumenti nel corso del tempo.  
  
  Per una procedura dettagliata dell'analizzatore di memoria gestita, vedere [usando Visual Studio 2013 per diagnosticare i problemi di memoria .NET in produzione](http://blogs.msdn.com/b/visualstudioalm/archive/2013/06/20/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production.aspx) in Visual Studio blog di ALM e Team Foundation Server.  
  
## <a name="BKMK_Contents"></a> Contenuto  
 [Uso della memoria nelle app .NET Framework](#BKMK_Memory_use_in__NET_Framework_apps)  
  
 [Identificare un problema di memoria in un'app](#BKMK_Identify_a_memory_issue_in_an_app)  
  
 [Raccogliere snapshot di memoria](#BKMK_Collect_memory_snapshots)  
  
 [Analizzare il consumo di memoria](#BKMK_Analyze_memory_use)  
  
## <a name="BKMK_Memory_use_in__NET_Framework_apps"></a> Uso della memoria nelle app .NET Framework  
 .NET Framework è un runtime con Garbage Collection. Nella maggior parte delle app, quindi, l'uso della memoria non costituisce un problema. Nelle applicazioni con esecuzione prolungata, ad esempio servizi e applicazioni Web, e nei dispositivi con quantità limitata di memoria l'accumulo di oggetti in memoria può influire negativamente sulle prestazioni dell'app e del dispositivo in cui è eseguita. L'uso eccessivo di memoria può privare di risorse l'applicazione e la macchina, nel caso in cui l'esecuzione del Garbage Collector sia troppo frequente o se il sistema operativo deve spostare memoria tra la RAM e il disco. Nel caso peggiore, è possibile che un'app si arresti in modo anomalo, con un'eccezione di tipo "Memoria insufficiente".  
  
 .NET *heap gestito* è un'area di memoria virtuale in cui sono archiviati gli oggetti di riferimento creati da un'app. La durata degli oggetti è gestita dal Garbage Collector (GC), che usa i riferimenti per tenere traccia degli oggetti che occupano blocchi di memoria. Un riferimento viene creato quando si crea un oggetto e lo si assegna a una variabile. Un singolo oggetto può avere più riferimenti. Ad esempio, è possibile creare riferimenti aggiuntivi a un oggetto tramite l'aggiunta dell'oggetto a una classe, una raccolta o un'altra struttura di dati oppure tramite l'assegnazione dell'oggetto a una seconda variabile. Un riferimento può essere creato anche, in modo meno ovvio, da un oggetto che aggiunge un gestore a un evento di un altro oggetto. In questo caso il secondo oggetto conserva il riferimento al primo oggetto fino alla rimozione esplicita del gestore o all'eliminazione del secondo oggetto.  
  
 Il Garbage Collector mantiene per ogni applicazione un albero dei riferimenti, che tiene traccia degli oggetti a cui l'applicazione fa riferimento. Il *nell'albero dei riferimenti* dispone di un insieme di radici, che include gli oggetti globali e statici, nonché gli stack di thread associato e in modo dinamico istanze degli oggetti. Un oggetto contiene una radice se è presente almeno un oggetto padre che include un riferimento all'oggetto. Il Garbage Collector può recuperare la memoria di un oggetto solo quando nessun altro oggetto o variabile dell'applicazione include riferimenti a tale oggetto.  
  
 ![Torna all'inizio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommario](#BKMK_Contents)  
  
## <a name="BKMK_Identify_a_memory_issue_in_an_app"></a> Identificare un problema di memoria in un'app  
 Il sintomo più evidente di problemi di memoria è individuabile nelle prestazioni dell'app, in particolare in caso di peggioramento delle prestazioni nel tempo. Anche il peggioramento delle prestazioni di altre app durante l'esecuzione dell'app specifica potrebbe indicare un problema di memoria. Se si sospetta un problema di memoria, usare uno strumento quale Gestione attività o [Windows Performance Monitor](http://technet.microsoft.com/library/cc749249.aspx) per analizzare ulteriormente il problema. Una possibile origine della perdita di memoria potrebbe essere, ad esempio, un incremento inspiegabile nella dimensione totale della memoria:  
  
 ![Aumento della memoria uniforme in Monitoraggio di risorse](../misc/media/mngdmem-resourcemanagerconsistentgrowth.png "MNGDMEM_ResourceManagerConsistentGrowth")  
  
 È anche possibile che si notino picchi di memoria superiori a quanto suggerito dalle proprie conoscenze del codice e che potrebbero indicare un uso non efficiente della memoria in una procedura:  
  
 ![Picchi di memoria di Resource Manager](../misc/media/mngdmem-resourcemanagerspikes.png "MNGDMEM_ResourceManagerSpikes")  
  
## <a name="BKMK_Collect_memory_snapshots"></a> Raccogliere snapshot di memoria  
 Lo strumento di analisi della memoria analizza le informazioni in *file di dump* che contengono informazioni sull'heap. È possibile creare file dump in Visual Studio, oppure è possibile usare uno strumento quale [ProcDump](http://technet.microsoft.com/sysinternals/dd996900.aspx) dalla [Windows Sysinternals](http://technet.microsoft.com/sysinternals). Visualizzare [che cos'è un dump e come crearne uno?](http://blogs.msdn.com/b/debugger/archive/2009/12/30/what-is-a-dump-and-how-do-i-create-one.aspx) sul blog di Visual Studio Debugger Team.  
  
> [!NOTE]
>  La maggior parte degli strumenti può raccogliere informazioni sui file di dump con o senza dati di memoria heap completi. L'analizzatore di memoria di Visual Studio richiede informazioni complete sull'heap.  
  
 **Per raccogliere un dump da Visual Studio**  
  
1. È possibile creare un file di dump per un processo avviato da un progetto di Visual Studio oppure collegare il debugger a un processo in esecuzione. Visualizzare [Collega a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
2. Arrestare l'esecuzione. Il debugger si arresta quando si sceglie **Interrompi tutto** nel **Debug** dal menu o a un'eccezione o a un punto di interruzione  
  
3. Nel **Debug** menu, scegliere **Salva Dump con nome**. Nel **Salva Dump con nome** finestra di dialogo specificare un percorso e assicurarsi che **Minidump con Heap** (predefinito) viene selezionato nel **Salva come tipo** elenco.  
  
   **Per confrontare due snapshot di memoria**  
  
   Per analizzare l'incremento nell'uso di memoria di un'app, raccogliere due file di dump da una singola istanza dell'app.  
  
   ![Torna all'inizio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommario](#BKMK_Contents)  
  
## <a name="BKMK_Analyze_memory_use"></a> Analizzare il consumo di memoria  
 [Filtrare l'elenco di oggetti](#BKMK_Filter_the_list_of_objects) **&#124;** [analizzare i dati di memoria in da un singolo snapshot](#BKMK_Analyze_memory_data_in_from_a_single_snapshot) **&#124;** [confrontare due memoria snapshot](#BKMK_Compare_two_memory_snapshots)  
  
 Per analizzare un file di dump alla ricerca di problemi di uso della memoria:  
  
1. In Visual Studio, scegliere **File**, **Open** e specificare il file di dump.  
  
2. Nel **riepilogo File Minidump** pagina, scegliere **Debug della memoria gestita**.  
  
    ![Pagina di riepilogo file di dump](../misc/media/mngdmem-dumpfilesummary.png "MNGDMEM_DumpFileSummary")  
  
   L'analizzatore di memoria avvia una sessione di debug per analizzare il file e mostra i risultati nella pagina Visualizza heap:  
  
   ![Torna all'inizio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommario](#BKMK_Contents)  
  
### <a name="BKMK_Filter_the_list_of_objects"></a> Filtrare l'elenco di oggetti  
 Per impostazione predefinita, l'analizzatore di memoria filtra l'elenco di oggetti in uno snapshot di memoria per mostrare solo i tipi e le istanze che corrispondono a codice utente e per mostrare solo i tipi la cui dimensione inclusiva totale supera una percentuale di soglia della dimensione totale dell'heap. È possibile modificare queste opzioni nel **le impostazioni di visualizzazione** elenco:  
  
|||  
|-|-|  
|**Abilitare Just My Code**|Just My Code nasconde la maggior parte degli oggetti di sistema più comuni, in modo che nell'elenco siano visualizzati solo i tipi creati dall'utente.<br /><br /> È anche possibile impostare l'opzione Just My Code in Visual Studio **opzioni** nella finestra di dialogo. Scegliere **Opzioni e impostazioni** dal menu **Debug**. Nel **Debugging**/**generali** scheda, selezionare o deselezionare **Just My Code**.|  
|**Comprimi oggetti piccoli**|**Comprimi oggetti piccoli** nasconde tutti i tipi la cui dimensione inclusiva totale è minore dello 0,5% della dimensione totale dell'heap.|  
  
 È anche possibile filtrare l'elenco di tipo immettendo una stringa nel **ricerca** casella. L'elenco mostra solo i tipi i cui nomi includono la stringa.  
  
 ![Torna all'inizio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommario](#BKMK_Contents)  
  
### <a name="BKMK_Analyze_memory_data_in_from_a_single_snapshot"></a> Analizzare i dati di memoria in da un singolo snapshot  
 Visual Studio avvia una nuova sessione di debug per analizzare il file, quindi mostra i dati della memoria in una finestra Visualizza heap.  
  
 ![L'elenco di tipo Object](../misc/media/dbg-mma-objecttypelist.png "DBG_MMA_ObjectTypeList")  
  
 ![Torna all'inizio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommario](#BKMK_Contents)  
  
#### <a name="object-type-table"></a>Tabella Tipo di oggetto  
 Nella tabella in alto sono elencati tutti i tipi di oggetti conservati in memoria.  
  
- **Conteggio** Mostra il numero di istanze del tipo nello snapshot.  
  
- **Dimensione (byte)** è la dimensione di tutte le istanze del tipo, esclusa la dimensione degli oggetti a cui include riferimenti a. Alla classe  
  
- **Dimensione inclusiva (byte)** include le dimensioni degli oggetti di riferimento.  
  
  È possibile scegliere l'icona delle istanze (![icona dell'istanza nella colonna tipo di oggetto](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) nella **tipo di oggetto** colonna per visualizzare un elenco delle istanze del digitare.  
  
#### <a name="instance-table"></a>Tabella Istanza  
 ![Tabella delle istanze](../misc/media/dbg-mma-instancestable.png "DBG_MMA_InstancesTable")  
  
- **Istanza** è la posizione di memoria dell'oggetto che funge da identificatore di oggetto dell'oggetto  
  
- **Valore** Mostra il valore effettivo dei tipi di valore. È possibile passare il puntatore del mouse sul nome di un tipo di riferimento per visualizzarne i valori di dati in un suggerimento relativo ai dati.  
  
   ![I valori in un suggerimento dati dell'istanza](../misc/media/dbg-mma-instancevaluesindatatip.png "DBG_MMA_InstanceValuesInDataTip")  
  
- **Dimensione (byte)** è la dimensione dell'oggetto, esclusa la dimensione degli oggetti a cui include riferimenti a. Alla classe  
  
- **Dimensione inclusiva (byte)** include le dimensioni degli oggetti di riferimento.  
  
  Per impostazione predefinita, i tipi e le istanze vengono ordinati in base **dimensione inclusiva (byte)**. Per cambiare l'ordinamento, scegliere un'intestazione di colonna dell'elenco.  
  
#### <a name="paths-to-root"></a>Percorsi della radice  
  
- Per un tipo selezionato dal **ObjectType** tabella, il **percorsi della radice** tabella mostra le gerarchie univoche di tipo che conducono agli oggetti radice per tutti gli oggetti del tipo, insieme al numero di riferimenti al tipo che si trova nella gerarchia.  
  
- Per un oggetto selezionato dall'istanza di un tipo **percorsi della radice** Visualizza un grafico degli oggetti effettivi che contengono un riferimento all'istanza. È possibile passare il puntatore del mouse sul nome dell'oggetto per visualizzarne i valori di dati in un suggerimento relativo ai dati.  
  
#### <a name="referenced-types--referenced-objects"></a>Tipi a cui si fa riferimento / Oggetti a cui si fa riferimento  
  
- Per un tipo selezionato dal **ObjectType** tabella, il **tipi di cui viene fatto riferimento** scheda Mostra le dimensioni e numero di tipi di cui viene fatto riferimento da tutti gli oggetti del tipo selezionato.  
  
- Per un'istanza di un tipo, selezionata **gli oggetti cui viene fatto riferimento** Mostra gli oggetti contenuti nell'istanza selezionata. È possibile passare il puntatore del mouse sul nome per visualizzarne i valori di dati in un suggerimento relativo ai dati.  
  
  **Riferimenti circolari**  
  
  Un oggetto può fare riferimento a un secondo oggetto che contiene in modo diretto o indiretto un riferimento al primo oggetto. Quando l'analizzatore di memoria incontra questa situazione, interrompe l'espansione il percorso di riferimento e aggiunge un **[rilevato ciclo]** annotazione per il listato del primo oggetto, quindi si arresta.  
  
  **Tipi radice**  
  
  L'analizzatore di memoria aggiunge annotazioni agli oggetti radice che descrivono il tipo di riferimento incluso:  
  
|Annotazione|Descrizione|  
|----------------|-----------------|  
|**Variabile statica** `VariableName`|Una variabile statica. `VariableName` è il nome della variabile.|  
|**Handle finalizzazione**|Un riferimento dalla coda del finalizzatore.|  
|**Variabile locale**|Una variabile locale.|  
|**Handle sicuro**|Un handle per un riferimento sicuro dalla tabella di handle degli oggetti.|  
|**Async. Handle bloccato**|Un oggetto bloccato asincrono dalla tabella di handle degli oggetti.|  
|**Handle dipendente**|Un oggetto dipendente dalla tabella di handle degli oggetti.|  
|**Handle bloccato**|Un riferimento sicuro bloccato dalla tabella di handle degli oggetti.|  
|**Handle RefCount**|Un oggetto con conteggio dei riferimenti dalla tabella di handle degli oggetti.|  
|**Handle SizedRef**|Un handle sicuro che conserva una dimensione approssimativa della chiusura collettiva di tutti gli oggetti e di tutte le radici di oggetto in fase di Garbage Collection.|  
|**Variabile locale bloccata**|Una variabile locale bloccata.|  
  
### <a name="BKMK_Compare_two_memory_snapshots"></a> Confrontare due snapshot di memoria  
 È possibile confrontare due file di dump di un processo per individuare oggetti che potrebbero essere la causa di perdite di memoria. L'intervallo tra la raccolta del primo file (precedente) e del secondo file (successivo) deve essere sufficientemente ampio da rendere chiaramente evidente l'incremento del numero di oggetti persi. Per confrontare i due file:  
  
1. Aprire il file di dump secondo e quindi scegliere **eseguire il Debug della memoria gestita** nel **riepilogo File Minidump** pagina.  
  
2. Nella pagina del report di analisi di memoria, aprire il **linea di base Select** elenco e quindi scegliere **Sfoglia** per specificare il primo file di dump.  
  
   L'analizzatore aggiunge colonne nel riquadro superiore del report che consentono di visualizzare la differenza tra il **conteggio**, **Size**, e **dimensione inclusiva** dei tipi rispetto ai valori nel snapshot precedente.  
  
   ![Colonne diff nell'elenco dei tipi](../misc/media/mngdmem-diffcolumns.png "MNGDMEM_DiffColumns")  
  
   Oggetto **Diff. conteggio riferimenti** viene anche aggiunta la **percorsi della radice** tabella.  
  
   ![Torna all'inizio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommario](#BKMK_Contents)  
  
## <a name="see-also"></a>Vedere anche  
 [Blog VS ALM TFS: Con Visual Studio 2013 per diagnosticare i problemi di memoria .NET in produzione](http://blogs.msdn.com/b/visualstudioalm/archive/2013/06/20/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production.aspx)   
 [Channel 9 &#124; Visual Studio TV &#124; analisi memoria gestita](http://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Managed-Memory-Analysis)   
 [Channel 9 &#124; casella degli strumenti di Visual Studio &#124; gestito l'analisi della memoria in Visual Studio 2013](http://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Managed-Memory-Analysis-in-Visual-Studio-2013)