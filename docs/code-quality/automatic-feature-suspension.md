---
title: Sospensione funzionalità automatica
ms.date: 11/04/2016
description: Informazioni su Visual Studio l'ambito di analisi, disattiva la modalità a bassa latenza di Garbage Collection e scarica le cache quando la memoria di sistema è limitata.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 0a1791f02264a4e6a32976ef8975375196054b2a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126632988"
---
# <a name="automatic-feature-suspension"></a>Sospensione funzionalità automatica

Se la memoria di sistema disponibile è inferiore a 200 MB, Visual Studio il messaggio seguente nell'editor di codice:

![Testo di avviso che sospende l'analisi completa della soluzione](../code-quality/media/fsa_alert.png)

Quando Visual Studio rileva una condizione di memoria insufficiente, sospende automaticamente alcune funzionalità avanzate per mantenere la stabilità. Visual Studio continua a funzionare come prima, ma le prestazioni sono ridotte.

In una condizione di memoria insufficiente, vengono eseguite le azioni seguenti:

- L'analisi del codice in tempo reale per Visual C# e Visual Basic è ridotta all'ambito minimo.

- [La modalità a](/dotnet/standard/garbage-collection/index) bassa latenza di Garbage Collection (GC) per Visual C# e Visual Basic è disabilitata.

- Visual Studio cache vengono scaricate.

## <a name="improve-visual-studio-performance"></a>Migliorare le Visual Studio prestazioni

Per suggerimenti e consigli su come migliorare le Visual Studio quando si gestiscono soluzioni di grandi dimensioni o condizioni di memoria insufficiente, vedere Considerazioni sulle prestazioni [per soluzioni di grandi dimensioni.](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md)

## <a name="live-code-analysis-is-reduced-to-minimal-scope"></a>L'analisi del codice in tempo reale è ridotta all'ambito minimo

Per impostazione predefinita, l'analisi del codice in tempo reale viene eseguita per i documenti e i progetti aperti. È possibile personalizzare questo ambito di analisi in modo che sia ridotto al documento corrente o aumentato all'intera soluzione. Per altre informazioni, vedere [Procedura: Configurare l'ambito di](./configure-live-code-analysis-scope-managed-code.md)analisi del codice in tempo reale per il codice gestito. In una condizione di memoria insufficiente, Visual Studio l'ambito di analisi dinamica viene ridotto al documento corrente. Tuttavia, è possibile abilitare nuovamente l'ambito  di analisi preferito scegliendo il pulsante Rienzila nella barra delle informazioni quando viene visualizzato o riavviando il Visual Studio. La finestra di dialogo Opzioni visualizza sempre le impostazioni correnti dell'ambito dell'analisi del codice in tempo reale.

## <a name="gc-low-latency-disabled"></a>Gc a bassa latenza disabilitata

Per abilitare nuovamente la modalità gc a bassa latenza, riavviare Visual Studio. Per impostazione predefinita, Visual Studio la modalità gc a bassa latenza ogni volta che si digita per assicurarsi che la digitazione non blocchi le operazioni GC. Tuttavia, se una condizione di memoria insufficiente Visual Studio visualizzare l'avviso di sospensione automatica, la modalità gc a bassa latenza è disabilitata per tale sessione. Il riavvio Visual Studio abilita nuovamente il comportamento GC predefinito. Per altre informazioni, vedere <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Visual Studio cache scaricate

Se si continua la sessione di sviluppo corrente o Visual Studio, tutte le cache Visual Studio vengono svuotate immediatamente, ma iniziano a ripopolarsi. Le cache scaricate includono cache per le funzionalità seguenti:

- Trova tutti i riferimenti

- Passa a

- Aggiungere tramite

Inoltre, vengono cancellate anche le cache usate per Visual Studio operazioni interne.

> [!NOTE]
> L'avviso di sospensione automatica delle funzionalità viene generato una sola volta per ogni soluzione, non per sessione. Ciò significa che se si passa da Visual Basic a Visual C# (o viceversa) e si verifica un'altra condizione di memoria insufficiente, è possibile che si otterrà un altro avviso di sospensione automatica delle funzionalità.

## <a name="see-also"></a>Vedi anche

- [Procedura: Configurare l'ambito di analisi del codice in tempo reale per il codice gestito](./configure-live-code-analysis-scope-managed-code.md)
- [Nozioni fondamentali di Garbage Collection](/dotnet/standard/garbage-collection/fundamentals)
- [Considerazioni sulle prestazioni per soluzioni di grandi dimensioni](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md)
