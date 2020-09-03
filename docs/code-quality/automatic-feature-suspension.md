---
title: Sospensione funzionalità automatica
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 236a95cd8d4af8da91199bf79e7c9fe3aa0d49af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85769478"
---
# <a name="automatic-feature-suspension"></a>Sospensione funzionalità automatica

Se la memoria di sistema disponibile è inferiore a 200 MB, Visual Studio visualizzerà il messaggio seguente nell'editor di codice:

![Testo dell'avviso sospensione dell'analisi completa della soluzione](../code-quality/media/fsa_alert.png)

Quando Visual Studio rileva una condizione di memoria insufficiente, sospende automaticamente determinate funzionalità avanzate per consentirne la stabilità. Visual Studio continua a funzionare come prima, ma le prestazioni sono ridotte.

In una condizione di memoria insufficiente, si verificano le azioni seguenti:

- L'analisi del codice in tempo reale per Visual C# e Visual Basic è ridotta all'ambito minimo.

- La modalità di bassa latenza di [Garbage Collection](/dotnet/standard/garbage-collection/index) (GC) per Visual C# e Visual Basic è disabilitata.

- Le cache di Visual Studio vengono scaricate.

## <a name="improve-visual-studio-performance"></a>Migliorare le prestazioni di Visual Studio

Per suggerimenti e consigli su come migliorare le prestazioni di Visual Studio quando si gestiscono soluzioni di grandi dimensioni o condizioni di memoria insufficiente, vedere [considerazioni sulle prestazioni per soluzioni di grandi dimensioni](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="live-code-analysis-is-reduced-to-minimal-scope"></a>L'analisi del codice in tempo reale è ridotta all'ambito minimo

Per impostazione predefinita, l'analisi del codice in tempo reale viene eseguita per i documenti e i progetti aperti. È possibile personalizzare questo ambito di analisi in modo da ridurlo al documento corrente o aumentarlo a un'intera soluzione. Per altre informazioni, vedere [procedura: configurare l'ambito di analisi del codice in tempo reale per il codice gestito](./configure-live-code-analysis-scope-managed-code.md). In una condizione di memoria insufficiente, Visual Studio forza la riduzione dell'ambito dell'analisi in tempo reale al documento corrente. Tuttavia, è possibile riabilitare l'ambito di analisi preferito scegliendo il pulsante **riabilita** nella barra informazioni quando viene visualizzato o riavviando Visual Studio. Nella finestra di dialogo Opzioni vengono sempre visualizzate le impostazioni correnti dell'ambito di analisi del codice Live.

## <a name="gc-low-latency-disabled"></a>GC a bassa latenza disabilitata

Per abilitare nuovamente la modalità a bassa latenza GC, riavviare Visual Studio. Per impostazione predefinita, Visual Studio Abilita la modalità GC a bassa latenza ogni volta che si digita per assicurarsi che la digitazione non blocchi le operazioni GC. Tuttavia, se una condizione di memoria insufficiente fa in modo che Visual Studio visualizzi l'avviso di sospensione automatica, la modalità di bassa latenza GC viene disabilitata per tale sessione. Il riavvio di Visual Studio Abilita nuovamente il comportamento GC predefinito. Per altre informazioni, vedere <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Cache di Visual Studio scaricate

Se si continua la sessione di sviluppo corrente o si riavvia Visual Studio, tutte le cache di Visual Studio vengono immediatamente svuotate, ma iniziano a essere ripopolate. Le cache scaricate includono le cache per le funzionalità seguenti:

- Trova tutti i riferimenti

- Passa a

- Aggiungi utilizzando

Vengono inoltre cancellate le cache utilizzate per le operazioni interne di Visual Studio.

> [!NOTE]
> L'avviso di sospensione della funzionalità automatica viene eseguito una sola volta per ogni singola soluzione, non per ogni singola sessione. Ciò significa che se si passa da Visual Basic a Visual C# (o viceversa) e si esegue un'altra condizione di memoria insufficiente, è possibile che venga visualizzato un altro avviso di sospensione automatica della funzionalità.

## <a name="see-also"></a>Vedere anche

- [Procedura: configurare l'ambito di analisi del codice in tempo reale per il codice gestito](./configure-live-code-analysis-scope-managed-code.md)
- [Nozioni fondamentali di Garbage Collection](/dotnet/standard/garbage-collection/fundamentals)
- [Considerazioni sulle prestazioni per soluzioni di grandi dimensioni](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
