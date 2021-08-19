---
title: 'Visualizzazione Albero delle chiamate: dati di campionamento | Microsoft Docs'
description: Informazioni su come la visualizzazione Albero delle chiamate visualizza i dati di campionamento per i percorsi di esecuzione della funzione attraversati nell'applicazione profilata in Esplora prestazioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Call Tree view
- Call Tree view
ms.assetid: 5c4e8ec3-d0d3-485a-93bd-9060df4eb739
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 44aaa125b464b90a101693f7dd6357123e6f7afa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084766"
---
# <a name="call-tree-view---sampling-data"></a>Visualizzazione Albero delle chiamate: dati di campionamento
La visualizzazione Albero delle chiamate consente di visualizzare i percorsi di esecuzione della funzione usati nell'applicazione profilata.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 La radice dell'albero è il punto di ingresso nell'applicazione o nel componente. Per ogni nodo della funzione vengono elencate tutte le funzioni chiamate e i dati delle prestazioni delle relative chiamate di funzione.

 I valori nella visualizzazione Albero delle chiamate sono relativi alle istanze della funzione chiamate dalla funzione padre nell'albero delle chiamate. I valori percentuali vengono calcolati confrontando il valore dell'istanza della funzione e il numero totale di esempi nell'esecuzione della profilatura.

## <a name="highlight-the-execution-hot-path"></a>Evidenziare il percorso critico di esecuzione
 Nella visualizzazione Albero delle chiamate è possibile espandere ed evidenziare il percorso di esecuzione del processo o della funzione campionati con maggiore frequenza. Per visualizzare il percorso più attivo, fare clic con il pulsante destro del mouse sul processo o sulla funzione e quindi scegliere **Espandi percorso critico**.

## <a name="set-the-call-tree-root-node"></a>Impostare il nodo radice dell'albero delle chiamate
 Ogni processo nell'esecuzione della profilatura viene visualizzato come nodo radice. Per impostare il nodo di inizio della visualizzazione Albero delle chiamate, fare clic con il pulsante destro del mouse sul nodo che si vuole impostare come nodo iniziale e selezionare **Imposta radice**.

 Quando imposti il nodo radice, elimini dalla visualizzazione tutte le altre voci ad eccezione del sottoalbero del nodo selezionato. Per reimpostare il nodo radice sul nodo originale, fare clic con il pulsante destro del mouse nella finestra della visualizzazione Albero delle chiamate e selezionare **Reimposta radice**.

|Colonna|Descrizione|
|------------|-----------------|
|**ID processo**|ID di processo (PID) dell'esecuzione della profilatura.|
|**Nome processo**|Nome del processo.|
|**Nome modulo**|Nome del modulo che contiene la funzione.|
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|
|**File di origine**|File di origine che contiene la definizione per questa funzione.|
|**Nome della funzione**|Nome completo della funzione.|
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|
|**Indirizzo funzione**|Indirizzo della funzione.|
|**Level**|Profondità di questa funzione nell'albero delle chiamate. Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|
|**Campioni esclusivi**|Numero di esempi raccolti in questa funzione quando la funzione è stata chiamata dalla funzione padre nell'albero delle chiamate. Questo numero non include gli esempi raccolti nelle funzioni chiamate dalla funzione.|
|**% esempi esclusivi**|Percentuale di tutti gli esempi nell'esecuzione della profilatura che erano esempi esclusivi di questa funzione quando è stata chiamata dalla funzione padre nell'albero delle chiamate.|
|**Esempi inclusivi**|Numero di esempi raccolti in questa funzione quando la funzione è stata chiamata dalla funzione padre nell'albero delle chiamate. Il numero include gli esempi raccolti nelle funzioni chiamate dalla funzione.|
|**% campioni inclusivi**|Percentuale di tutti gli esempi nell'esecuzione della profilatura che erano esempi inclusivi di questa funzione quando è stata chiamata dalla funzione padre nell'albero delle chiamate.|

## <a name="see-also"></a>Vedi anche
- [Procedura: Personalizzare le colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)
- [Visualizzazione Albero delle chiamate: dati di campionamento del profiler](../profiling/call-Tree-view-sampling-data.md)
- [Visualizzazione Albero delle chiamate: campionamento](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
- [Visualizzazione Albero delle chiamate: strumentazione](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Visualizzazione Albero delle chiamate](../profiling/call-tree-view-instrumentation-data.md)
