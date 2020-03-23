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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8480eb57a08905c2a593adbab519ae793638888
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431241"
---
# <a name="automatic-feature-suspension"></a>Sospensione funzionalità automatica

Se la memoria di sistema disponibile scende a 200 MB o meno, Visual Studio visualizza il seguente messaggio nell'editor di codice:

![Testo di avviso che sospende l'analisi completa della soluzione](../code-quality/media/fsa_alert.png)

Quando Visual Studio rileva una condizione di memoria insufficiente, sospende automaticamente alcune funzionalità avanzate per mantenerle stabili. Visual Studio continua a funzionare come prima, ma le prestazioni sono ridotte.

In una condizione di memoria insufficiente, si svolgono le seguenti azioni:

- L'analisi del codice in tempo reale per Visual C è e Visual Basic viene ridotta all'ambito minimo.

- [La](/dotnet/standard/garbage-collection/index) modalità di Garbage Collection (GC) a bassa latenza per Visual C è e Visual Basic è disabilitata.

- Le cache di Visual Studio vengono scaricate.

## <a name="improve-visual-studio-performance"></a>Migliorare le prestazioni di Visual Studio

Per suggerimenti e suggerimenti su come migliorare le prestazioni di Visual Studio quando si gestiscono soluzioni di grandi dimensioni o condizioni di memoria insufficiente, vedere [Considerazioni sulle prestazioni per soluzioni](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)di grandi dimensioni.

## <a name="live-code-analysis-is-reduced-to-minimal-scope"></a>L'analisi del codice in tempo reale viene ridotta all'ambito minimo

Per impostazione predefinita, l'analisi del codice attivo viene eseguita per i progetti e i documenti aperti. È possibile personalizzare questo ambito di analisi in modo che venga ridotto al documento corrente o aumentato all'intera soluzione. Per ulteriori informazioni, vedere [Procedura: configurare l'ambito di analisi del codice in tempo reale per il codice gestito.](./configure-live-code-analysis-scope-managed-code.md) In una condizione di memoria insufficiente, Visual Studio impone l'ambito di analisi in tempo reale da ridurre al documento corrente. Tuttavia, è possibile riattivare l'ambito di analisi preferito scegliendo il pulsante Riattiva nella barra informazioni quando viene visualizzato o riavviando Visual Studio.However, you can re-enable your preferred analysis scope by choosing the **Re-enable** button in the info bar when it appears or by restarting Visual Studio. Nella finestra di dialogo Opzioni vengono sempre visualizzate le impostazioni correnti dell'ambito dell'analisi del codice attivo.

## <a name="gc-low-latency-disabled"></a>GC bassa latenza disabilitata

Per riattivare la modalità a bassa latenza GC, riavviare Visual Studio.To re-enable GC low-latency mode, restart Visual Studio. Per impostazione predefinita, Visual Studio abilita la modalità a bassa latenza GC ogni volta che si digita per garantire che la digitazione non blocchi alcuna operazione GC. Tuttavia, se una condizione di memoria insufficiente causa Visual Studio per visualizzare l'avviso di sospensione automatica, GC modalità a bassa latenza è disabilitata per quella sessione. Il riavvio di Visual Studio riabilita il comportamento GC predefinito. Per altre informazioni, vedere <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Cache di Visual Studio scaricate

Se si continua la sessione di sviluppo corrente o si riavvia Visual Studio, tutte le cache di Visual Studio vengono immediatamente svuotate, ma iniziano a ripopolare. Le cache scaricate includono cache per le seguenti funzionalità:

- Trova tutti i riferimenti

- Passa a

- Aggiungi utilizzando

Vengono inoltre cancellate le cache utilizzate per le operazioni interne di Visual Studio.In addition, caches used for internal Visual Studio operations are also cleared.

> [!NOTE]
> L'avviso di sospensione automatica delle funzionalità viene generato una sola volta in base alla soluzione, non in base alla sessione. Ciò significa che se si passa da Visual Basic a Visual C , o viceversa, ed eseguire in un'altra condizione di memoria insufficiente, è possibile ottenere un altro avviso di sospensione della funzionalità automatica.

## <a name="see-also"></a>Vedere anche

- [Procedura: configurare l'ambito di analisi del codice attivo per il codice gestitoHow to: Configure live code analysis scope for managed code](./configure-live-code-analysis-scope-managed-code.md)
- [Nozioni fondamentali di Garbage Collection](/dotnet/standard/garbage-collection/fundamentals)
- [Considerazioni sulle prestazioni per soluzioni di grandi dimensioniPerformance considerations for large solutions](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
