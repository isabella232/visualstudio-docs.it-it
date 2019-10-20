---
title: Sospensione funzionalità automatica
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd399d78ac43085d89958ba358954f9e6cefe521
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606531"
---
# <a name="automatic-feature-suspension"></a>Sospensione funzionalità automatica

Se la memoria di sistema disponibile è inferiore a 200 MB, Visual Studio visualizzerà il messaggio seguente nell'editor di codice:

![Testo dell'avviso sospensione dell'analisi completa della soluzione](../code-quality/media/fsa_alert.png)

Quando Visual Studio rileva una condizione di memoria insufficiente, sospende automaticamente determinate funzionalità avanzate per consentirne la stabilità. Visual Studio continua a funzionare come prima, ma le prestazioni sono ridotte.

In una condizione di memoria insufficiente, si verificano le azioni seguenti:

- L'analisi completa della soluzione C# per oggetti visivi e Visual Basic è disabilitata.

- La modalità di bassa latenza di [Garbage Collection](/dotnet/standard/garbage-collection/index) (GC C# ) per Visual e Visual Basic è disabilitata.

- Le cache di Visual Studio vengono scaricate.

## <a name="improve-visual-studio-performance"></a>Migliorare le prestazioni di Visual Studio

Per suggerimenti e consigli su come migliorare le prestazioni di Visual Studio quando si gestiscono soluzioni di grandi dimensioni o condizioni di memoria insufficiente, vedere [considerazioni sulle prestazioni per soluzioni di grandi dimensioni](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Analisi completa della soluzione sospesa

Per impostazione predefinita, l'analisi della soluzione completa è abilitata per Visual Basic C#e disabilitata per Visual. Tuttavia, in una condizione di memoria insufficiente, l'analisi della soluzione completa viene disabilitata automaticamente C#sia per Visual Basic sia per l'oggetto visivo, indipendentemente dalle impostazioni nella finestra di dialogo Opzioni. Tuttavia, è possibile riabilitare l'analisi completa della soluzione scegliendo il pulsante **riabilita** nella barra informazioni quando viene visualizzato, selezionando la casella di controllo **Abilita analisi della soluzione completa** nella finestra di dialogo Opzioni o riavviando Visual Studio. Nella finestra di dialogo Opzioni vengono sempre visualizzate le impostazioni di analisi della soluzione completa correnti. Per altre informazioni, vedere [procedura: abilitare e disabilitare l'analisi della soluzione completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>GC a bassa latenza disabilitata

Per abilitare nuovamente la modalità a bassa latenza GC, riavviare Visual Studio. Per impostazione predefinita, Visual Studio Abilita la modalità GC a bassa latenza ogni volta che si digita per assicurarsi che la digitazione non blocchi le operazioni GC. Tuttavia, se una condizione di memoria insufficiente fa in modo che Visual Studio visualizzi l'avviso di sospensione automatica, la modalità di bassa latenza GC viene disabilitata per tale sessione. Il riavvio di Visual Studio Abilita nuovamente il comportamento GC predefinito. Per ulteriori informazioni, vedere <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Cache di Visual Studio scaricate

Se si continua la sessione di sviluppo corrente o si riavvia Visual Studio, tutte le cache di Visual Studio vengono immediatamente svuotate, ma iniziano a essere ripopolate. Le cache scaricate includono le cache per le funzionalità seguenti:

- Trova tutti i riferimenti

- Passa a

- Aggiungi utilizzando

Vengono inoltre cancellate le cache utilizzate per le operazioni interne di Visual Studio.

> [!NOTE]
> L'avviso di sospensione della funzionalità automatica viene eseguito una sola volta per ogni singola soluzione, non per ogni singola sessione. Ciò significa che se si passa da Visual Basic a Visual C# (o viceversa) e si esegue un'altra condizione di memoria insufficiente, è possibile che venga visualizzato un altro avviso di sospensione automatica della funzionalità.

## <a name="see-also"></a>Vedere anche

- [Procedura: Abilitare e disabilitare l'analisi completa della soluzione](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Principi fondamentali di Garbage Collection](/dotnet/standard/garbage-collection/fundamentals)
- [Considerazioni sulle prestazioni per soluzioni di grandi dimensioni](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
