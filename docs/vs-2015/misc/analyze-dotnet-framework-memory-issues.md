---
title: Analizzare .NET Framework problemi di memoria | Microsoft Docs
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
ms.openlocfilehash: e89b3f04a3e0e1dcd0cc29e57e09b1c71fbc2279
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545548"
---
# <a name="analyze-net-framework-memory-issues"></a>Analizzare i problemi relativi alla memoria .NET Framework
L'analizzatore di memoria gestita di Visual Studio permette di rilevare perdite di memoria e uso non efficiente della memoria nel codice .NET. La versione minima di .NET Framework per il codice di destinazione è .NET Framework 4.5.  
  
 Lo strumento di analisi della memoria analizza le informazioni nei *file di dump con i dati dell'heap* che una copia degli oggetti nella memoria di un'app. È possibile raccogliere file di dump (con estensione dmp) dall'IDE di Visual Studio oppure usando altri strumenti di sistema.  
  
- È possibile analizzare un singolo snapshot per ottenere informazioni sull'impatto relativo dei tipi di oggetto sull'uso della memoria e per trovare nell'app il codice che usa la memoria in modo non efficiente.  
  
- È anche possibile confrontare (*diff*) due snapshot di un'app per trovare le aree del codice che provocano l'incremento dell'uso della memoria nel tempo.  
  
  Per una procedura dettagliata di managed memory Analyzer, vedere [uso di Visual Studio 2013 per diagnosticare i problemi di memoria .NET in produzione nel](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/) Blog di Visual Studio ALM + Team Foundation Server.  
  
## <a name="contents"></a><a name="BKMK_Contents"></a>Contenuto  
 [Uso della memoria nelle app .NET Framework](#BKMK_Memory_use_in__NET_Framework_apps)  
  
 [Identificare un problema di memoria in un'app](#BKMK_Identify_a_memory_issue_in_an_app)  
  
 [Raccogliere snapshot di memoria](#BKMK_Collect_memory_snapshots)  
  
 [Analizzare l'uso della memoria](#BKMK_Analyze_memory_use)  
  
## <a name="memory-use-in-net-framework-apps"></a><a name="BKMK_Memory_use_in__NET_Framework_apps"></a>Uso della memoria nelle app .NET Framework  
 .NET Framework è un runtime con Garbage Collection. Nella maggior parte delle app, quindi, l'uso della memoria non costituisce un problema. Nelle applicazioni con esecuzione prolungata, ad esempio servizi e applicazioni Web, e nei dispositivi con quantità limitata di memoria l'accumulo di oggetti in memoria può influire negativamente sulle prestazioni dell'app e del dispositivo in cui è eseguita. L'uso eccessivo di memoria può privare di risorse l'applicazione e la macchina, nel caso in cui l'esecuzione del Garbage Collector sia troppo frequente o se il sistema operativo deve spostare memoria tra la RAM e il disco. Nel caso peggiore, è possibile che un'app si arresti in modo anomalo, con un'eccezione di tipo "Memoria insufficiente".  
  
 L' *heap gestito* .NET è un'area di memoria virtuale in cui vengono archiviati gli oggetti di riferimento creati da un'app. La durata degli oggetti è gestita dal Garbage Collector (GC), che usa i riferimenti per tenere traccia degli oggetti che occupano blocchi di memoria. Un riferimento viene creato quando si crea un oggetto e lo si assegna a una variabile. Un singolo oggetto può avere più riferimenti. Ad esempio, è possibile creare riferimenti aggiuntivi a un oggetto tramite l'aggiunta dell'oggetto a una classe, una raccolta o un'altra struttura di dati oppure tramite l'assegnazione dell'oggetto a una seconda variabile. Un riferimento può essere creato anche, in modo meno ovvio, da un oggetto che aggiunge un gestore a un evento di un altro oggetto. In questo caso il secondo oggetto conserva il riferimento al primo oggetto fino alla rimozione esplicita del gestore o all'eliminazione del secondo oggetto.  
  
 Il Garbage Collector mantiene per ogni applicazione un albero dei riferimenti, che tiene traccia degli oggetti a cui l'applicazione fa riferimento. L' *albero di riferimento* dispone di un set di radici, che include oggetti globali e statici, nonché gli stack di thread associati e gli oggetti di cui è stata creata un'istanza dinamicamente. Un oggetto contiene una radice se è presente almeno un oggetto padre che include un riferimento all'oggetto. Il Garbage Collector può recuperare la memoria di un oggetto solo quando nessun altro oggetto o variabile dell'applicazione include riferimenti a tale oggetto.  
  
 ![Torna al](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [contenuto](#BKMK_Contents) principale  
  
## <a name="identify-a-memory-issue-in-an-app"></a><a name="BKMK_Identify_a_memory_issue_in_an_app"></a>Identificare un problema di memoria in un'app  
 Il sintomo più evidente di problemi di memoria è individuabile nelle prestazioni dell'app, in particolare in caso di peggioramento delle prestazioni nel tempo. Anche il peggioramento delle prestazioni di altre app durante l'esecuzione dell'app specifica potrebbe indicare un problema di memoria. Se si sospetta un problema di memoria, usare uno strumento come gestione attività o [Windows Performance Monitor](https://technet.microsoft.com/library/cc749249.aspx) per approfondire l'analisi. Una possibile origine della perdita di memoria potrebbe essere, ad esempio, un incremento inspiegabile nella dimensione totale della memoria:  
  
 ![Aumento della memoria uniforme in Monitoraggio risorse](../misc/media/mngdmem-resourcemanagerconsistentgrowth.png "MNGDMEM_ResourceManagerConsistentGrowth")  
  
 È anche possibile che si notino picchi di memoria superiori a quanto suggerito dalle proprie conoscenze del codice e che potrebbero indicare un uso non efficiente della memoria in una procedura:  
  
 ![Picchi di memoria in Gestione risorse](../misc/media/mngdmem-resourcemanagerspikes.png "MNGDMEM_ResourceManagerSpikes")  
  
## <a name="collect-memory-snapshots"></a><a name="BKMK_Collect_memory_snapshots"></a>Raccogli snapshot di memoria  
 Lo strumento di analisi della memoria analizza le informazioni nei *file di dump* contenenti informazioni sull'heap. È possibile creare file di dump in Visual Studio oppure usare uno strumento come [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx) da [Windows Sysinternals](https://technet.microsoft.com/sysinternals). Vedere [che cos'è un dump e come crearne uno?](https://blogs.msdn.microsoft.com/debugger/2009/12/30/what-is-a-dump-and-how-do-i-create-one/) nel Blog del team di Visual Studio debugger.  
  
> [!NOTE]
> La maggior parte degli strumenti può raccogliere informazioni sui file di dump con o senza dati di memoria heap completi. L'analizzatore di memoria di Visual Studio richiede informazioni complete sull'heap.  
  
 **Per raccogliere un file di dump da Visual Studio**  
  
1. È possibile creare un file di dump per un processo avviato da un progetto di Visual Studio oppure collegare il debugger a un processo in esecuzione. Vedere [Connetti a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
2. Arrestare l'esecuzione. Il debugger si interrompe quando si sceglie **Interrompi tutto** dal menu **debug** o in corrispondenza di un'eccezione o di un punto di interruzione  
  
3. Scegliere **Salva dump con nome**dal menu **debug** . Nella finestra di dialogo **Salva dump con nome** specificare un percorso e assicurarsi che il **minidump con heap** (impostazione predefinita) sia selezionato nell'elenco **Salva come** .  
  
   **Per confrontare due snapshot di memoria**  
  
   Per analizzare l'incremento nell'uso di memoria di un'app, raccogliere due file di dump da una singola istanza dell'app.  
  
   ![Torna al](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [contenuto](#BKMK_Contents) principale  
  
## <a name="analyze-memory-use"></a><a name="BKMK_Analyze_memory_use"></a>Analizzare l'uso della memoria  
 [Filtrare l'elenco di oggetti](#BKMK_Filter_the_list_of_objects) **&#124;** [analizzare i dati di memoria da un singolo snapshot](#BKMK_Analyze_memory_data_in_from_a_single_snapshot) **&#124;** [confrontare due snapshot di memoria](#BKMK_Compare_two_memory_snapshots)  
  
 Per analizzare un file di dump alla ricerca di problemi di uso della memoria:  
  
1. In Visual Studio scegliere **file**, **Apri** e specificare il file di dump.  
  
2. Nella pagina **Riepilogo file minidump** scegliere **debug memoria gestita**.  
  
    ![Pagina del riepilogo dei file dump](../misc/media/mngdmem-dumpfilesummary.png "MNGDMEM_DumpFileSummary")  
  
   L'analizzatore di memoria avvia una sessione di debug per analizzare il file e mostra i risultati nella pagina Visualizza heap:  
  
   ![Torna al](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [contenuto](#BKMK_Contents) principale  
  
### <a name="filter-the-list-of-objects"></a><a name="BKMK_Filter_the_list_of_objects"></a>Filtrare l'elenco di oggetti  
 Per impostazione predefinita, l'analizzatore di memoria filtra l'elenco di oggetti in uno snapshot di memoria per mostrare solo i tipi e le istanze che corrispondono a codice utente e per mostrare solo i tipi la cui dimensione inclusiva totale supera una percentuale di soglia della dimensione totale dell'heap. È possibile modificare queste opzioni nell'elenco **Visualizza impostazioni** :  
  
|Name|Descrizione|  
|-|-|  
|**Abilita Just My Code**|Just My Code nasconde la maggior parte degli oggetti di sistema più comuni, in modo che nell'elenco siano visualizzati solo i tipi creati dall'utente.<br /><br /> È anche possibile impostare l'opzione Just My Code nella finestra di dialogo **Opzioni** di Visual Studio. Scegliere **Opzioni e impostazioni** dal menu **Debug**. Nella scheda **debug** / **generale** scegliere o deselezionare **Just My Code**.|  
|**Comprimi oggetti piccoli**|**Comprimi oggetti piccoli** nasconde tutti i tipi la cui dimensione inclusiva totale è inferiore al 0,5% delle dimensioni totali dell'heap.|  
  
 È anche possibile filtrare l'elenco dei tipi immettendo una stringa nella casella di **ricerca** . L'elenco mostra solo i tipi i cui nomi includono la stringa.  
  
 ![Torna al](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [contenuto](#BKMK_Contents) principale  
  
### <a name="analyze-memory-data-in-from-a-single-snapshot"></a><a name="BKMK_Analyze_memory_data_in_from_a_single_snapshot"></a>Analizzare i dati di memoria in da un singolo snapshot  
 Visual Studio avvia una nuova sessione di debug per analizzare il file, quindi mostra i dati della memoria in una finestra Visualizza heap.  
  
 ![Elenco Tipo di oggetto](../misc/media/dbg-mma-objecttypelist.png "DBG_MMA_ObjectTypeList")  
  
 ![Torna al](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [contenuto](#BKMK_Contents) principale  
  
#### <a name="object-type-table"></a>Tabella Tipo di oggetto  
 Nella tabella in alto sono elencati tutti i tipi di oggetti conservati in memoria.  
  
- **Count** indica il numero di istanze del tipo nello snapshot.  
  
- **Size (bytes)** è la dimensione di tutte le istanze del tipo, esclusa la dimensione degli oggetti a cui contengono riferimenti. Alla classe  
  
- **Dimensione inclusiva (byte)** include le dimensioni degli oggetti a cui si fa riferimento.  
  
  È possibile scegliere l'icona delle istanze (![l'icona dell'istanza nella colonna tipo di oggetto](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) nella colonna **tipo di oggetto** per visualizzare un elenco delle istanze del tipo.  
  
#### <a name="instance-table"></a>Tabella Istanza  
 ![Tabella delle istanze](../misc/media/dbg-mma-instancestable.png "DBG_MMA_InstancesTable")  
  
- **Instance** è la posizione di memoria dell'oggetto che funge da identificatore di oggetto dell'oggetto.  
  
- **Valore** indica il valore effettivo dei tipi di valore. È possibile passare il puntatore del mouse sul nome di un tipo di riferimento per visualizzarne i valori di dati in un suggerimento relativo ai dati.  
  
   ![Valori di istanze in un suggerimento dati](../misc/media/dbg-mma-instancevaluesindatatip.png "DBG_MMA_InstanceValuesInDataTip")  
  
- **Dimensioni (byte)** è la dimensione dell'oggetto, esclusa la dimensione degli oggetti a cui sono contenuti i riferimenti. Alla classe  
  
- **Dimensione inclusiva (byte)** include le dimensioni degli oggetti a cui si fa riferimento.  
  
  Per impostazione predefinita, i tipi e le istanze sono ordinati in base alle **dimensioni Inclusive (byte)**. Per cambiare l'ordinamento, scegliere un'intestazione di colonna dell'elenco.  
  
#### <a name="paths-to-root"></a>Percorsi della radice  
  
- Per un tipo selezionato dalla tabella **tipo di oggetto** , la tabella **percorsi della radice** Mostra le gerarchie di tipi univoche che portano a oggetti radice per tutti gli oggetti del tipo, insieme al numero di riferimenti al tipo che si trova al di sopra della gerarchia.  
  
- Per un oggetto selezionato dall'istanza di un tipo, i **percorsi della radice** mostrano un grafico degli oggetti effettivi che contengono un riferimento all'istanza. È possibile passare il puntatore del mouse sul nome dell'oggetto per visualizzarne i valori di dati in un suggerimento relativo ai dati.  
  
#### <a name="referenced-types--referenced-objects"></a>Tipi a cui si fa riferimento / Oggetti a cui si fa riferimento  
  
- Per un tipo selezionato dalla tabella **tipo di oggetto** , nella scheda **tipi a cui viene fatto riferimento** vengono visualizzate le dimensioni e il numero di tipi a cui si fa riferimento contenuti in tutti gli oggetti del tipo selezionato.  
  
- Per un'istanza selezionata di un tipo, **oggetti a cui si fa riferimento** Mostra gli oggetti contenuti nell'istanza selezionata. È possibile passare il puntatore del mouse sul nome per visualizzarne i valori di dati in un suggerimento relativo ai dati.  
  
  **Riferimenti circolari**  
  
  Un oggetto può fare riferimento a un secondo oggetto che contiene in modo diretto o indiretto un riferimento al primo oggetto. Quando l'analizzatore di memoria incontra questa situazione, interrompe l'espansione del percorso di riferimento e aggiunge un'annotazione **[ciclo rilevato]** all'elenco del primo oggetto e si arresta.  
  
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
  
### <a name="compare-two-memory-snapshots"></a><a name="BKMK_Compare_two_memory_snapshots"></a>Confrontare due snapshot di memoria  
 È possibile confrontare due file di dump di un processo per individuare oggetti che potrebbero essere la causa di perdite di memoria. L'intervallo tra la raccolta del primo file (precedente) e del secondo file (successivo) deve essere sufficientemente ampio da rendere chiaramente evidente l'incremento del numero di oggetti persi. Per confrontare i due file:  
  
1. Aprire il secondo file di dump, quindi scegliere **debug memoria gestita** nella pagina **Riepilogo file minidump** .  
  
2. Nella pagina report analisi memoria aprire l'elenco **Seleziona Baseline** , quindi scegliere **Sfoglia** per specificare il primo file di dump.  
  
   L'analizzatore aggiunge colonne al riquadro superiore del report in cui viene visualizzata la differenza tra il **conteggio**, le **dimensioni**e le **dimensioni inclusivi** dei tipi in questi valori nello snapshot precedente.  
  
   ![Colonne diff nell'elenco dei tipi](../misc/media/mngdmem-diffcolumns.png "MNGDMEM_DiffColumns")  
  
   Viene aggiunta anche una colonna **diff conteggio riferimenti** alla tabella **percorsi della radice** .  
  
   ![Torna al](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [contenuto](#BKMK_Contents) principale  
  
## <a name="see-also"></a>Vedere anche  
 [Blog di Visual Studio ALM TFS: uso di Visual Studio 2013 per diagnosticare i problemi di memoria .NET nell'ambiente di produzione](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/)   
 [Channel 9 &#124; Visual Studio TV &#124; analisi della memoria gestita](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Managed-Memory-Analysis)   
 [Channel 9 &#124; la casella degli strumenti di Visual Studio &#124; l'analisi della memoria gestita in Visual Studio 2013](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Managed-Memory-Analysis-in-Visual-Studio-2013)