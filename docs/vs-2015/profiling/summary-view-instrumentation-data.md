---
title: 'Visualizzazione Riepilogo: dati di strumentazione | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Summary view
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17534c0c7970238d4b6ef3de79c87d637743ff83
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517430"
---
# <a name="summary-view---instrumentation-data"></a>Visualizzazione Riepilogo: dati di strumentazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [visualizzazione Riepilogo: dati di strumentazione](https://docs.microsoft.com/visualstudio/profiling/summary-view-instrumentation-data).  
  
La visualizzazione Riepilogo mostra informazioni sulle funzioni che influiscono maggiormente sulle prestazioni in un'esecuzione della profilatura. Per altre informazioni, inclusa una descrizione degli elenchi dei collegamenti di notifica e dei rapporti, vedere [Visualizzazione Riepilogo](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Grafico della sequenza temporale  
 Il grafico della sequenza temporale nella visualizzazione Riepilogo mostra l'utilizzo del processore (CPU) per l'applicazione profilata nel periodo di profilatura. È possibile usare il grafico della sequenza temporale per filtrare la visualizzazione in base a un intervallo di tempo selezionato. Per altre informazioni, vedere [Procedura: Filtrare le visualizzazioni dei rapporti dalla sequenza temporale di riepilogo](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="hot-path"></a>Percorso critico  
 In **Percorso critico** viene visualizzato il percorso di esecuzione che ha richiesto la quantità di tempo maggiore. È possibile fare clic su una funzione per attivare la visualizzazione Dettagli funzione per la funzione. Per visualizzare altre visualizzazioni per la funzione, fare clic con il pulsante destro del mouse sulla funzione e scegliere una visualizzazione nell'elenco.  
  
 Il **Percorso critico** include i dati seguenti per ogni funzione:  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Name**|Nome della funzione.|  
|**% tempo inclusivo trascorso**|Percentuale del tempo totale nei dati di profilatura dedicato dalla funzione all'esecuzione del codice nel corpo della funzione e nelle funzioni chiamate dalla funzione stessa.|  
|**% tempo esclusivo trascorso**|Percentuale del tempo totale nei dati di profilatura dedicato dalla funzione all'esecuzione del codice nel corpo della funzione. Il tempo dedicato a funzioni chiamate dalla funzione non è incluso.|  
  
## <a name="functions-with-most-individual-work"></a>Funzioni con più lavoro individuale  
 Elenco delle funzioni che hanno richiesto la quantità di tempo maggiore per l'esecuzione del codice nel corpo della funzione e non nelle funzioni da essa chiamate.  
  
 L'opzione **Funzioni con più lavoro individuale** include i dati seguenti per ogni funzione:  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Name**|Nome della funzione.|  
|**% tempo esclusivo**|Percentuale del tempo totale nei dati di profilatura dedicato dalla funzione all'esecuzione del codice nel corpo della funzione. Il tempo dedicato a funzioni chiamate dalla funzione non è incluso.|  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Riepilogo](../profiling/summary-view-sampling-data.md)   
 [Visualizzazione Riepilogo](../profiling/summary-view-dotnet-memory-data.md)



