---
title: Visualizzazione Processo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.process
helpviewer_keywords:
- performance tools reports, process view
- Process view
- performance tools, process view
- Profiling Tools,process view
- Profiling Tools,process report
ms.assetid: 6d4e2a5d-9f17-4ece-a6f1-75836e1fc382
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0436401c458a7d6771a2785028a8b5fe0ef57546
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180215"
---
# <a name="process-view"></a>Visualizzazione Processo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La visualizzazione Processo visualizza i dati di profilatura per i processi e i thread eseguiti durante l'esecuzione della profilatura.  
  
 I processi sono elencati per nome. I thread sono elencati come nodi figlio del processo che li ha creati. Il nome dei thread viene definito in base alla funzione che ha definito il thread o all'etichetta **[ntdll.dll]** in assenza di simboli disponibili.  
  
 Per aggiungere o rimuovere colonne, fare clic con il pulsante destro del mouse sulla visualizzazione e quindi scegliere **Aggiungi/Rimuovi colonne**. È anche possibile ordinare i dati facendo clic su un nome di colonna. Per altre informazioni, vedere [Procedura: Personalizzare colonne della visualizzazione Report](../profiling/how-to-customize-report-view-columns.md).  
  
 Le colonne della visualizzazione Processo sono le stesse per i dati generati usando i metodi di campionamento e strumentazione e per i dati che includo i dati sulla memoria .NET. Nella tabella seguente sono descritti i valori delle colonne.  
  
|Colonna|DESCRIZIONE|  
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
