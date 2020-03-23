---
title: 'DA0005: raccolte GC2 frequenti | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0005
- vs.performance.rules.DAManyGC2Collections
- vs.performance.5
- vs.performance.rules.DA0005
ms.assetid: 8d3f267c-8a74-4cf4-91a5-0b06a76dc2bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a50567a101d77ed6498aaae13a5fe5556d9c1056
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777712"
---
# <a name="da0005-frequent-gc2-collections"></a>DA0005: Collection GC2 frequenti

|||
|-|-|
|ID regola|DA0005|
|Category|Uso di .NET Framework|
|Metodo di profilatura|Memoria .NET|
|Message|Molti degli oggetti vengono raccolti in Garbage Collection di generazione 2.|
|Tipo di messaggio|Avviso|

## <a name="cause"></a>Causa
 Viene recuperato un numero elevato di oggetti di memoria .NET in Garbage Collection di generazione 2.

## <a name="rule-description"></a>Descrizione della regola
 Common Language Runtime (CLR) di Microsoft .NET offre un meccanismo di gestione automatica della memoria che usa il Garbage Collector per recuperare memoria da oggetti che non vengono più usati dall'applicazione. Il Garbage Collector è orientato alla generazione, basandosi sull'ipotesi che molte allocazioni sono di breve durata. Le variabili locali, ad esempio, dovrebbero essere di breve durata. Gli oggetti appena creati vengono avviati in generazione 0 (gen 0), quindi avanzano a generazione 1 se vengono conservati dopo l'esecuzione di un'operazione di Garbage Collection e infine passano a generazione 2 se sono ancora usati dall'applicazione.

 Gli oggetti in generazione 0 vengono raccolti frequentemente e in genere in modo molto efficace. Gli oggetti in generazione 1 vengono raccolti meno frequentemente e in modo meno efficace. Infine, gli oggetti di lunga durata in generazione 2 dovrebbero essere raccolti con una frequenza ancora inferiore. La raccolta in generazione 2, che è l'esecuzione di un'operazione di Garbage Collection completa, è anche l'operazione più costosa.

 Questa regola viene attivata quando si sono verificate proporzionalmente troppe operazioni di Garbage Collection di generazione 2. Se troppi oggetti di durata relativamente breve vengono mantenuti dopo una raccolta di generazione 1, ma possono essere raccolti in una generazione 2 completa, il costo di gestione della memoria può diventare eccessivo. Per altre informazioni, vedere il post [Mid-life crisis](https://blogs.msdn.microsoft.com/ricom/2003/12/04/mid-life-crisis/) (Crisi di mezza età) in Rico Mariani's Performance Tidbits (Curiosità sulle prestazioni di Rico Mariani) sul sito Web MSDN.

## <a name="how-to-investigate-a-warning"></a>Come esaminare un avviso
 Esaminare i report [Visualizzazioni dati di memoria .NET](../profiling/dotnet-memory-data-views.md) per comprendere il modello di allocazione di memoria dell'applicazione. Utilizzare la [visualizzazione Durata](../profiling/object-lifetime-view.md) oggetti per determinare quali oggetti dati del programma sopravvivono alla generazione 2 e quindi vengono recuperati da lì. Usare la [Visualizzazione Allocazioni](../profiling/dotnet-memory-allocations-view.md) per determinare il percorso di esecuzione che ha comportato queste allocazioni.

 Per informazioni su come migliorare le prestazioni di Garbage Collection, vedere [Garbage Collector Basics and Performance Hints](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) (Nozioni fondamentali su Garbage Collection e suggerimenti sulle prestazioni) sul sito Web Microsoft. Per informazioni sul sovraccarico della procedura di Garbage Collection automatica, vedere [Large Object Heap Uncovered](https://msdn.microsoft.com/magazine/cc534993.aspx) (Heap di oggetti grandi).
