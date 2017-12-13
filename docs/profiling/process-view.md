---
title: Visualizzazione Processo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.view.process
helpviewer_keywords:
- performance tools reports, process view
- Process view
- performance tools, process view
- Profiling Tools,process view
- Profiling Tools,process report
ms.assetid: 6d4e2a5d-9f17-4ece-a6f1-75836e1fc382
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f174223900b6f8deba2291a80425df1c77589ce1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="process-view"></a>Visualizzazione Processo
La visualizzazione Processo visualizza i dati di profilatura per i processi e i thread eseguiti durante l'esecuzione della profilatura.  
  
 I processi sono elencati per nome. I thread sono elencati come nodi figlio del processo che li ha creati. Il nome dei thread viene definito in base alla funzione che ha definito il thread o all'etichetta **[ntdll.dll]** in assenza di simboli disponibili.  
  
 Per aggiungere o rimuovere colonne, fare clic con il pulsante destro del mouse sulla visualizzazione e quindi scegliere **Aggiungi/Rimuovi colonne**. È anche possibile ordinare i dati facendo clic su un nome di colonna. Per altre informazioni, vedere [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md).  
  
 Le colonne della visualizzazione Processo sono le stesse per i dati generati usando i metodi di campionamento e strumentazione e per i dati che includo i dati sulla memoria .NET. Nella tabella seguente sono descritti i valori delle colonne.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**ID univoco**|Identificatore generato dal profiler univoco per il processo o il thread.|  
|**ID**|Identificatore generato dal sistema per il processo o il thread.|  
|**Nome**|Nome del processo o del thread.|  
|**Ora di inizio**|Numero di millisecondi o di cicli del processore dall'inizio della profilatura all'avvio del processo o del thread.|  
|**Ora di fine**|Numero di millisecondi o di cicli del processore dall'inizio della profilatura alla fine del processo o del thread.|  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazioni dei dati del metodo di campionamento](../profiling/profiler-sampling-method-data-views.md)   
 [Visualizzazioni dei dati del metodo di strumentazione](../profiling/instrumentation-method-data-views.md)   
 [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)