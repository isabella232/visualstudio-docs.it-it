---
title: Visualizzazione Processo | Microsoft Docs
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: da3097c276557238e6f5b521f6f7d3231434cd10
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74772176"
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
- [Visualizzazioni dei dati del metodo di campionamento](../profiling/profiler-sampling-method-data-views.md)
- [Visualizzazioni dei dati del metodo di strumentazione](../profiling/instrumentation-method-data-views.md)
- [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)
