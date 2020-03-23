---
title: 'Visualizzazione Riepilogo: dati di memoria .NET | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: a67902af99eaee6c75f92f86c2481dfc2afd744e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771556"
---
# <a name="summary-view---net-memory-data"></a>Visualizzazione Riepilogo: dati di memoria .NET
La visualizzazione Riepilogo riporta informazioni sui tipi e sulle funzioni .NET che hanno allocato la quantità di memoria maggiore e sui tipi che sono stati creati più frequentemente in un'esecuzione della profilatura. Per ulteriori informazioni, inclusa una descrizione degli elenchi Collegamenti notifica e Report, vedere [Visualizzazione Riepilogo.](../profiling/summary-view.md)

## <a name="timeline-graph"></a>Grafico della sequenza temporale
 Il grafico della sequenza temporale nella visualizzazione Riepilogo mostra l'utilizzo del processore (CPU) per l'applicazione profilata nel periodo di profilatura. È possibile usare il grafico della sequenza temporale per filtrare la visualizzazione in base a un intervallo di tempo selezionato. Per ulteriori informazioni, vedere [Procedura: Filtrare le visualizzazioni dei report dalla sequenza temporale di riepilogo](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="functions-allocating-most-memory"></a>Funzioni che allocano molta memoria
 Elenca le funzioni che hanno allocato il maggior numero di byte di memoria nell'esecuzione della profilatura.

|Colonna|Descrizione|
|------------|-----------------|
|**Nome**|Nome della funzione.|
|**% byte**|Percentuale di tutti i byte allocati nell'esecuzione della profilatura che sono stati allocati da questa funzione o da una funzione figlio chiamata da questa funzione.|

## <a name="types-with-most-memory-allocated"></a>Tipi con molta memoria allocata
 Elenca i tipi per cui è stato allocato il maggior numero di byte di memoria nell'esecuzione della profilatura.

|Colonna|Descrizione|
|------------|-----------------|
|**Nome**|Nome del tipo.|
|**% byte**|Percentuale di tutti i byte allocati nell'esecuzione della profilatura che sono stati allocati per questo tipo.|

## <a name="types-with-most-instances"></a>Tipi con molte istanze
 Elenca i tipi creati più frequentemente nell'esecuzione della profilatura. stato

|Colonna|Descrizione|
|------------|-----------------|
|**Nome**|Nome del tipo.|
|**% istanze**|Percentuale del numero totale di oggetti .NET creati nell'esecuzione della profilatura corrispondenti a istanze di questo tipo.|

## <a name="see-also"></a>Vedere anche
- [Visualizzazione Riepilogo: dati di campionamento](../profiling/summary-view-sampling-data.md)
- [Visualizzazione Riepilogo - dati di strumentazioneSummary view - instrumentation data](../profiling/summary-view-instrumentation-data.md)
