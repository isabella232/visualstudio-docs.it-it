---
title: DA0023 - Tempo CPU GC elevato | Microsoft Docs
description: I dati sulle prestazioni del sistema raccolti durante la profilatura indicano che il tempo impiegato in Garbage Collection è elevato rispetto al tempo di elaborazione totale dell'applicazione.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0023
- vs.performance.23
- vs.performance.rules.DA0023
ms.assetid: aba875fe-9cbc-418d-a2c4-6eb47519a5bb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 859c0cb12e76b5e6a12235a51e01efdc8449e207
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131768"
---
# <a name="da0023-high-gc-cpu-time"></a>DA0023: Tempo di CPU GC elevato

|Elemento|valore|
|-|-|
|ID regola|DA0023|
|Category|Uso di .NET Framework|
|Metodo di profilatura|Tutti|
|Message|% tempo in GC elevata. Indica un sovraccarico di Garbage Collection che potrebbe incidere sulla velocità di risposta dell'applicazione. Per altri dettagli, è possibile raccogliere dati sull'allocazione di memoria .NET e informazioni sulla durata degli oggetti per comprendere il criterio di allocazione della memoria usata dall'applicazione.|
|Tipo regola|Informativo|

 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.

## <a name="cause"></a>Causa
 I dati sulle prestazioni del sistema raccolti durante la profilatura indicano che il tempo impiegato in Garbage Collection è elevato rispetto al tempo di elaborazione totale dell'applicazione.

## <a name="rule-description"></a>Descrizione della regola
 Common Language Runtime (CLR) di Microsoft .NET offre un meccanismo di gestione automatica della memoria che usa un Garbage Collector per recuperare memoria da oggetti che non vengono più usati dall'applicazione. Il Garbage Collector è orientato alla generazione, basandosi sull'ipotesi che molte allocazioni sono di breve durata. Le variabili locali, ad esempio, dovrebbero essere di breve durata. Gli oggetti appena creati vengono avviati in generazione 0 (gen 0), quindi avanzano a generazione 1 se vengono conservati dopo l'esecuzione di un'operazione di Garbage Collection e infine passano a generazione 2 se sono ancora usati dall'applicazione.

 Gli oggetti in generazione 0 vengono raccolti frequentemente e in modo efficace. Gli oggetti in generazione 1 vengono raccolti meno frequentemente e in modo meno efficace. Infine, gli oggetti di lunga durata in generazione 2 dovrebbero essere raccolti con una frequenza ancora inferiore. La raccolta in generazione 2, che è l'esecuzione di un'operazione di Garbage Collection completa, è anche l'operazione più costosa.

 Questa regola viene attivata quando la quantità di tempo impiegato per l'operazione di Garbage Collection è significativa rispetto al tempo di elaborazione totale dell'applicazione.

> [!NOTE]
> Quando la percentuale di tempo impiegato per l'operazione di Garbage Collection è eccessivo rispetto al tempo di elaborazione totale dell'applicazione, viene attivato l'avviso [DA0024: Tempo CPU GC eccessivo](../profiling/da0024-excessive-gc-cpu-time.md) anziché la regola.

## <a name="how-to-investigate-a-warning"></a>Come esaminare un avviso
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare alla [visualizzazione Contrassegni](../profiling/marks-view.md) dei dati di profilatura. Individuare la colonna **Memoria CLR .NET\\% Time in GC** (% tempo in GC). Determinare se sono presenti fasi specifiche di esecuzione del programma in cui il sovraccarico di Garbage Collection della memoria gestita è maggiore rispetto ad altre fasi. Confrontare i valori di % Time in GC (% tempo in GC) con la frequenza di Garbage Collection indica nei valori **Raccolte di generazione 0**, **Raccolte di generazione 1**, **Raccolte di generazione 2**.

 Il valore % Time in GC (% tempo in GC) tenta di segnalare la quantità di tempo impiegato da un'applicazione di eseguire operazioni di Garbage Collection proporzionale alla quantità totale di elaborazione. Tenere presente che esistono circostanze in cui il valore % Time in GC (% tempo in GC) può segnalare un valore elevato, ma non a causa di un numero eccessivo di operazioni di Garbage Collection. Per altre informazioni sul modo in cui viene calcolato il valore % Time in GC, vedere la voce [Difference Between Perf Data Reported by Different Tools - 4](https://devblogs.microsoft.com/maoni/archive/difference-between-perf-data-reported-by-different-tools-4.aspx) (Differenza tra i dati delle differenze segnalati da strumenti diversi - 4) del weblog di **Maoni** su MSDN. Se si verificano errori di pagina o l'applicazione viene superata da altre operazioni con priorità superiore sul computer durante l'operazione di Garbage Collection, il valore di % Time in GC (% tempo in GC) rifletterà tali ritardi aggiuntivi.
