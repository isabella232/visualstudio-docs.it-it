---
description: I dati relativi alle prestazioni di sistema raccolti durante la profilatura indicano che una percentuale significativa della memoria per oggetti .NET Framework è stata recuperata nell'operazione di Garbage Collection di generazione 1 rispetto alla raccolta dei dati di generazione 0.
title: DA0021 - Frequenza elevata di Garbage Collection di generazione 1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.21
- vs.performance.DA0021
- vs.performance.rules.DA0021
ms.assetid: ebf5d9b3-a1ac-4688-8f0f-39a85f4dd15f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1ed53e6999c07f712268be9163f8baa1225e2341
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637115"
---
# <a name="da0021-high-rate-of-gen-1-garbage-collections"></a>DA0021: Frequenza elevata di Garbage Collection di generazione 1

|Elemento|valore|
|-|-|
|ID regola|DA0021|
|Category|Uso di .NET Framework|
|Metodi di profilatura|Tutti|
|Message|È stata rilevata una frequenza elevata di Garbage Collection di generazione 1. In genere, ciò avviene se la maggior parte delle strutture dati del programma sono allocate e rese persistenti per molto tempo per progettazione. Tuttavia, se tale comportamento è imprevisto, l'applicazione potrebbe bloccare gli oggetti. Per altri dettagli, è possibile raccogliere dati sull'allocazione di memoria .NET e informazioni sulla durata degli oggetti per comprendere il criterio di allocazione della memoria usata dall'applicazione.|
|Tipo regola|Informazioni|

 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.

## <a name="cause"></a>Causa
 I dati relativi alle prestazioni di sistema raccolti durante la profilatura indicano che una percentuale significativa della memoria per oggetti .NET Framework è stata recuperata nell'operazione di Garbage Collection di generazione 1 rispetto alla raccolta dei dati di generazione 0.

## <a name="rule-description"></a>Descrizione della regola
 Common Language Runtime (CLR) di Microsoft .NET offre un meccanismo di gestione automatica della memoria che usa un Garbage Collector per recuperare memoria da oggetti che non vengono più usati dall'applicazione. Il Garbage Collector è orientato alla generazione, basandosi sull'ipotesi che molte allocazioni sono di breve durata. Le variabili locali, ad esempio, dovrebbero essere di breve durata. Gli oggetti appena creati vengono avviati in generazione 0 (gen 0), quindi avanzano a generazione 1 se vengono conservati dopo l'esecuzione di un'operazione di Garbage Collection e infine passano a generazione 2 se sono ancora usati dall'applicazione.

 Gli oggetti in generazione 0 vengono raccolti frequentemente e in genere in modo molto efficace. Gli oggetti in generazione 1 vengono raccolti meno frequentemente e in modo meno efficace. Infine, gli oggetti di lunga durata in generazione 2 dovrebbero essere raccolti con una frequenza ancora inferiore. La raccolta in generazione 2, che è l'esecuzione di un'operazione di Garbage Collection completa, è anche l'operazione più costosa.

 Questa regola viene attivata quando si sono verificate proporzionalmente troppe operazioni di Garbage Collection di generazione 1. Se troppi oggetti di durata relativamente breve vengono conservati dopo una raccolta di generazione 0, ma possono essere raccolti in una generazione 1, il costo di gestione della memoria può diventare eccessivo. Per altre informazioni, vedere il post [Mid-life crisis](/archive/blogs/ricom/mid-life-crisis) (Crisi di mezza età) in Rico Mariani's Performance Tidbits (Curiosità sulle prestazioni di Rico Mariani) sul sito Web MSDN.

## <a name="how-to-investigate-a-warning"></a>Come esaminare un avviso
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare alla [visualizzazione Contrassegni](../profiling/marks-view.md) dei dati di profilatura. Individuare le colonne **Memoria CLR .NET\\Raccolte di generazione 0** e **Memoria CLR .NET\\Raccolte di generazione 1**. Determinare se sono presenti fasi specifiche di esecuzione del programma in cui l'operazione di Garbage Collection si verifica più frequentemente. Confrontare questi valori con la colonna **% Time in GC** (% tempo in GC) per verificare se il modello di allocazioni della memoria gestita sta provocando un eccessivo sovraccarico della gestione della memoria.

 Per comprendere il modello di utilizzo della memoria gestita dell'applicazione, eseguire di nuovo la profilatura con un profilo di allocazione della memoria .NET e richiedere misurazioni della durata degli oggetti.

 Per informazioni su come migliorare le prestazioni di Garbage Collection, vedere [Garbage Collector Basics and Performance Hints](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) (Nozioni fondamentali su Garbage Collection e suggerimenti sulle prestazioni) sul sito Web Microsoft. Per informazioni sul sovraccarico della procedura di Garbage Collection automatica, vedere [Large Object Heap Uncovered](/archive/msdn-magazine/2008/june/clr-inside-out-large-object-heap-uncovered) (Heap di oggetti grandi).
