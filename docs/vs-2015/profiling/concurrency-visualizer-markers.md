---
title: Marcatori del visualizzatore di concorrenza.| Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 143cea7a60fd136777943e849713ca0bdfe171fb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60078317"
---
# <a name="concurrency-visualizer-markers"></a>Marcatori del visualizzatore di concorrenza
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I marcatori del visualizzatore di concorrenza sono icone che rappresentano eventi in un'app.  In genere, l'applicazione genera questi eventi per definire fasi o occorrenze di un'applicazione.  Gli eventi possono essere generati dall'app o da librerie e runtime usati dall'app.  
  
## <a name="kinds-of-markers"></a>Tipi di marcatori  
 Il visualizzatore di concorrenza usa tre tipi di marcatori per rappresentare gli eventi dell'applicazione: flag, messaggi e span.  
  
1. Usare un *flag* per indicare un punto di interesse nell'app.  Si potrebbe ad esempio usare un flag per indicare che un valore della variabile ha raggiunto una determinata soglia o che è stata generata un'eccezione.  
  
2. Si può contrassegnare un momento anche con un *messaggio*. È tuttavia possibile usare questo tipo di marcatore per una traccia in stile log.  Ad esempio, quel che è stato copiato in un file di log può essere incluso in una chiamata di messaggio in modo che è sia possibile tenerne traccia e visualizzarlo nel visualizzatore di concorrenza. È anche possibile usare il visualizzatore di concorrenza per esportare questi dati in un file con estensione csv.  
  
3. Uno *span* è un intervallo di tempo nell'app, ad esempio, una delle sue fasi.  
  
## <a name="marker-linkage-to-threads"></a>Collegamento di marcatori a thread  
 Per ogni thread che genera marcatori esiste un canale temporale separato.  L'ID del thread che genera gli eventi del marcatore viene visualizzato accanto alla descrizione del canale del marcatore.  L'ID visualizzato a sinistra del canale del marcatore corrisponde all'ID di un altro thread nel processo corrente.  
  
## <a name="marker-importance"></a>Importanza dei marcatori  
 Per i marcatori esistono quattro livelli di importanza: bassa, normale, alta e critica.  È possibile filtrare le origini dei marcatori in base al livello di importanza.  Ad esempio, se si vogliono vedere solo i marcatori di una determinata origine con importanza normale o critica, è possibile configurare il filtro nella finestra di dialogo [Impostazioni avanzate](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md). L'importanza di un marcatore viene visualizzata nella relativa descrizione comando e nel [rapporto marcatori](../profiling/markers-report.md).  
  
## <a name="marker-category"></a>Categoria dei marcatori  
 La categoria di un marcatore indica un gruppo di eventi marcatore che provengono dalla stessa origine.  Il visualizzatore di concorrenza usa i colori per distinguere le diverse categorie di flag e span. È possibile configurare il visualizzatore di concorrenza in modo che usi le categorie per filtrare gli eventi marcatore di un provider di eventi specifico.  Usare la finestra di dialogo [Impostazioni avanzate](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) per configurare il filtro.  
  
## <a name="known-sources-of-markers"></a>Origini note di marcatori  
 I marcatori possono essere generati da qualsiasi privider ETW purché il provider sia conforme a determinati vincoli. È possibile configurare il visualizzatore di concorrenza in modo che sia in ascolto di origini evento aggiuntive. Per impostazione predefinita, è in ascolto delle origini evento seguenti:  
  
- [SDK del visualizzatore di concorrenza](../profiling/concurrency-visualizer-sdk.md)  
  
- [Task Parallel Library (TPL)](http://msdn.microsoft.com/library/b8f99f43-9104-45fd-9bff-385a20488a23)  
  
- [Flusso di dati](http://msdn.microsoft.com/library/643575d0-d26d-4c35-8de7-a9c403e97dd6)  
  
- [Parallel LINQ (PLINQ)](http://msdn.microsoft.com/library/3d4d0cd3-bde4-490b-99e7-f4e41be96455)  
  
- [Runtime di concorrenza](http://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)  
  
- [Supporto per marcatori di scenario](http://msdn.microsoft.com/e3b55bc2-b451-4214-ae00-0c7f5a5baec8)  
  
- [C++ AMP (C++ Accelerated Massive Parallelism)](http://msdn.microsoft.com/library/e27824cb-3167-409b-8c3f-a0e476d8f349)  
  
  Nella finestra di dialogo [Impostazioni avanzate](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) è possibile usare la scheda Marcatori per controllare se visualizzare nel visualizzatore di concorrenza i marcatori di varie origini e filtrare i marcatori in base a importanza e categoria.  
  
## <a name="markers-from-eventsource"></a>Marcatori di EventSource  
 Il visualizzatore di concorrenza può visualizzare anche eventi EventSource.  Per altre informazioni, vedere [Visualizing EventSource Events as Markers](../profiling/visualizing-eventsource-events-as-markers.md) (Visualizzazione di eventi EventSource come marcatori).  
  
## <a name="see-also"></a>Vedere anche  
 [Flag Markers](../profiling/flag-markers.md)  (Marcatori di flag)  
 [Message Markers](../profiling/message-markers.md)  (Marcatori di messaggio)  
 [Span Markers](../profiling/span-markers.md) (Marcatori di span)  
 [Visualizzazione di eventi EventSource come marcatori](../profiling/visualizing-eventsource-events-as-markers.md)
