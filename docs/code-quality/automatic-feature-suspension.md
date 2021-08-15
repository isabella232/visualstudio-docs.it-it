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
ms.openlocfilehash: 28210dd5d34137cd656fa16281c87b3d8f8a55af5b56fe83cb30fae11b667887
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121312613"
---
# <a name="automatic-feature-suspension"></a>Sospensione funzionalità automatica

Se la memoria di sistema disponibile non è inferiore a 200 MB, Visual Studio viene visualizzato il messaggio seguente nell'editor del codice:

![Testo dell'avviso che sospende l'analisi completa della soluzione](../code-quality/media/fsa_alert.png)

Quando Visual Studio rileva una condizione di memoria insufficiente, sospende automaticamente alcune funzionalità avanzate per mantenere la stabilità. Visual Studio continua a funzionare come in precedenza, ma le prestazioni risultano ridotte.

In una condizione di memoria insufficiente, vengono eseguite le azioni seguenti:

- L'analisi del codice in tempo reale per Visual C# e Visual Basic è ridotta all'ambito minimo.

- [La modalità a](/dotnet/standard/garbage-collection/index) bassa latenza di Garbage Collection (GC) per Visual C# e Visual Basic è disabilitata.

- Visual Studio cache vengono scaricate.

## <a name="improve-visual-studio-performance"></a>Migliorare le Visual Studio prestazioni

Per suggerimenti e consigli su come migliorare le Visual Studio quando si gestiscono soluzioni di grandi dimensioni o condizioni di memoria insufficiente, vedere Considerazioni sulle prestazioni per soluzioni [di grandi dimensioni.](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md)

## <a name="live-code-analysis-is-reduced-to-minimal-scope"></a>L'analisi del codice in tempo reale è ridotta all'ambito minimo

Per impostazione predefinita, l'analisi del codice in tempo reale viene eseguita per i documenti e i progetti aperti. È possibile personalizzare questo ambito di analisi per ridursi al documento corrente o aumentarlo all'intera soluzione. Per altre informazioni, vedere [Procedura: Configurare l'ambito di analisi del codice in tempo reale per il codice gestito.](./configure-live-code-analysis-scope-managed-code.md) In una condizione di memoria insufficiente, Visual Studio forza la riduzione dell'ambito di analisi dinamica al documento corrente. È tuttavia possibile abilitare nuovamente l'ambito  di analisi preferito scegliendo il pulsante Ri enable (Ri enable) nella barra delle informazioni quando viene visualizzato o riavviando Visual Studio. Nella finestra di dialogo Opzioni vengono sempre visualizzate le impostazioni correnti dell'ambito di analisi del codice in tempo reale.

## <a name="gc-low-latency-disabled"></a>Gc a bassa latenza disabilitata

Per abilitare nuovamente la modalità GC a bassa latenza, riavviare Visual Studio. Per impostazione predefinita, Visual Studio la modalità GC a bassa latenza ogni volta che si digita per garantire che la digitazione non blocchi le operazioni GC. Tuttavia, se una condizione di memoria insufficiente Visual Studio visualizza l'avviso di sospensione automatica, la modalità GC a bassa latenza è disabilitata per tale sessione. Il riavvio Visual Studio abilita nuovamente il comportamento GC predefinito. Per altre informazioni, vedere <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Visual Studio cache scaricate

Se si continua la sessione di sviluppo corrente o si riavvia Visual Studio, tutte le cache Visual Studio vengono svuotate immediatamente, ma iniziano a essere ripopolate. Le cache scaricate includono le cache per le funzionalità seguenti:

- Trova tutti i riferimenti

- Passa a

- Aggiungere using

Inoltre, vengono cancellate anche le cache usate per le Visual Studio interne.

> [!NOTE]
> L'avviso di sospensione automatica delle funzionalità viene visualizzato una sola volta per ogni soluzione, non per sessione. Ciò significa che se si passa da Visual Basic a Visual C# (o viceversa) e si verifica un'altra condizione di memoria insufficiente, è possibile che si otterrà un altro avviso di sospensione automatica delle funzionalità.

## <a name="see-also"></a>Vedi anche

- [Procedura: Configurare l'ambito di analisi del codice in tempo reale per il codice gestito](./configure-live-code-analysis-scope-managed-code.md)
- [Nozioni fondamentali di Garbage Collection](/dotnet/standard/garbage-collection/fundamentals)
- [Considerazioni sulle prestazioni per soluzioni di grandi dimensioni](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md)
