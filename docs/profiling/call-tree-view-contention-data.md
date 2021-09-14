---
title: 'Visualizzazione Albero delle chiamate: dati sui conflitti | Microsoft Docs'
description: Esaminare la visualizzazione Albero delle chiamate, che mostra i dati sui contenuti per i percorsi di esecuzione della funzione attraversati nell'applicazione profilata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: 9bd4bde2-2ca3-446c-9ccc-7421522e03ae
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 28cd7b22e64afbfb4c7c4100bd44c28e6dec6bb6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625439"
---
# <a name="call-tree-view---contention-data"></a>Visualizzazione Albero delle chiamate: dati sui conflitti
La visualizzazione Albero delle chiamate consente di visualizzare i percorsi di esecuzione della funzione usati nell'applicazione profilata. La radice dell'albero è il punto di ingresso nell'applicazione o nel componente. Ogni nodo della funzione elenca tutte le funzioni che ha chiamato, il numero di volte per cui la funzione è stata bloccata e il tempo per il quale la funzione è stata bloccata perché in conflitto per una risorsa con altri thread o processi.

 I valori nella visualizzazione Albero delle chiamate sono relativi alle istanze della funzione chiamate dalla funzione padre nell'albero delle chiamate. I valori percentuali vengono calcolati confrontando il valore dell'istanza della funzione e il numero totale di conflitti nell'esecuzione della profilatura.

## <a name="highlight-the-execution-hot-path"></a>Evidenziare il percorso critico di esecuzione
 Nella visualizzazione Albero delle chiamate è possibile espandere ed evidenziare il percorso di esecuzione del processo o della funzione che ha determinato il maggior numero di conflitti.

- Per visualizzare il percorso più attivo, fare clic con il pulsante destro del mouse sul processo o sulla funzione e quindi scegliere **Espandi percorso critico**.

## <a name="set-the-call-tree-root-node"></a>Impostare il nodo radice dell'albero delle chiamate
 Ogni processo nell'esecuzione della profilatura viene visualizzato come nodo radice. Per impostare il nodo di inizio della visualizzazione Albero delle chiamate, fare clic con il pulsante destro del mouse sul nodo che si vuole impostare come nodo iniziale e fare clic su **Imposta radice**.

 Quando si imposta il nodo radice si eliminano dalla visualizzazione tutte le altre voci ad eccezione del sottoalbero del nodo selezionato. Per reimpostare il nodo radice sul nodo originale, fare clic con il pulsante destro del mouse nella visualizzazione Albero delle chiamate e fare clic su **Reimposta radice**.

|Colonna|Descrizione|
|------------|-----------------|
|**Tempo blocco esclusivo**|Tempo per il quale l'esecuzione delle istanze della funzione in questo percorso di esecuzione è stata bloccata nell'esecuzione della profilatura. Il tempo non include il tempo di blocco delle funzioni figlio chiamate dalla funzione.|
|**% tempo blocco esclusivo**|Percentuale del tempo totale di blocco nell'esecuzione della profilatura corrispondente al tempo di blocco esclusivo per questa funzione in questo percorso di esecuzione.|
|**Conflitti esclusivi**|Numero di conflitti che si sono verificati nelle istanze di questa funzione in questo percorso di esecuzione. Il numero non include i conflitti delle funzioni figlio chiamate dalla funzione.|
|**% conflitti esclusivi**|Percentuale di tutti i conflitti nell'esecuzione della profilatura che rappresenta conflitti esclusivi delle istanze della funzione chiamate dalla funzione padre nell'albero delle chiamate.|
|**Indirizzo funzione**|Indirizzo della funzione.|
|**Nome della funzione**|Nome completo della funzione.|
|**Tempo blocco inclusivo**|Tempo totale per il quale l'esecuzione delle istanze della funzione in questo percorso di esecuzione è stata bloccata nell'esecuzione della profilatura. Il tempo include il tempo di blocco delle funzioni figlio chiamate dalla funzione.|
|**% tempo blocco inclusivo**|Percentuale del tempo totale di blocco nell'esecuzione della profilatura corrispondente al tempo di blocco inclusivo per le istanze di questa funzione in questo percorso di esecuzione.|
|**Conflitti inclusivi**|Numero totale di conflitti che hanno bloccato istanze di questa funzione in questo percorso di esecuzione. Il numero include i conflitti delle funzioni figlio chiamate dalla funzione.|
|**% conflitti inclusivi**|Percentuale del totale di conflitti nell'esecuzione della profilatura corrispondente ai conflitti inclusivi delle istanze di questa funzione in questo percorso di esecuzione.|
|**Level**|Livello della funzione nell'albero delle chiamate. Solo nei rapporti della riga di comando di VSReport. Per altre informazioni, vedere [VSPerfReport](../profiling/vsperfreport.md).|
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|
|**Nome modulo**|Nome del modulo che contiene la funzione.|
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|
|**ID processo**|ID di processo (PID) dell'esecuzione della profilatura.|
|**Nome processo**|Nome del processo.|
|**File di origine**|File di origine che contiene la definizione per questa funzione.|

## <a name="see-also"></a>Vedi anche
- [Procedura: Personalizzare le colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)
- [Visualizzazione Albero delle chiamate](../profiling/call-tree-view.md)
- [Visualizzazione Albero delle chiamate: strumentazione](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Visualizzazione Albero delle chiamate: campionamento](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
- [Visualizzazione Albero delle chiamate](../profiling/call-tree-view-instrumentation-data.md)
- [Visualizzazione Albero delle chiamate](../profiling/call-tree-view-sampling-data.md)
