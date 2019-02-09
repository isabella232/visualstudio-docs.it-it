---
title: Sospensione funzionalità automatica
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fbe86e085e50dc0e72c00b7bbe7a313e689e0ee5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55950981"
---
# <a name="automatic-feature-suspension"></a>Sospensione funzionalità automatica

Se la memoria di sistema disponibili è minore o uguale a 200 MB, Visual Studio visualizza il messaggio seguente nell'editor di codice:

![Testo dell'avviso la sospensione di analisi della soluzione completa](../code-quality/media/fsa_alert.png)

Quando Visual Studio rileva una condizione di memoria insufficiente, sospende automaticamente alcune funzionalità avanzate per agevolare il rimane stabile. Visual Studio continua a funzionare come prima, ma le prestazioni risultano ridotte.

In una condizione di memoria insufficiente, le seguenti azioni si verificano:

- Analisi della soluzione completa per Visual c# e Visual Basic sono disabilitata.

- [Operazione di Garbage Collection](/dotnet/standard/garbage-collection/index) modalità di bassa latenza (GC) per oggetto visivo C# e Visual Basic è disabilitata.

- Vengono scaricate le cache di Visual Studio.

## <a name="improve-visual-studio-performance"></a>Migliorare le prestazioni di Visual Studio

Per suggerimenti e trucchi su come migliorare le prestazioni di Visual Studio quando si lavora con soluzioni di grandi dimensioni o condizioni di memoria insufficiente, vedere [considerazioni sulle prestazioni per soluzioni di grandi dimensioni](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Analisi della soluzione completa sospesa

Per impostazione predefinita, analisi della soluzione completa sono abilitato per Visual Basic e disabilitato per Visual c#. Tuttavia, in una condizione di memoria insufficiente, analisi della soluzione completa vengano disabilitato automaticamente in Visual Basic e Visual c#, indipendentemente dalle impostazioni nella finestra di dialogo Opzioni. Tuttavia, è possibile riabilitare analisi della soluzione completa, scegliendo la **riabilitare** pulsante nella scheda info barra quando viene visualizzata, selezionando il **Abilita analisi della soluzione completa** casella di controllo nella finestra di dialogo Opzioni o tramite Riavviare Visual Studio. Finestra di dialogo Opzioni Mostra sempre la soluzione completa corrente delle impostazioni di analisi. Per altre informazioni, vedere [Procedura: Abilitare e disabilitare l'analisi della soluzione completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>Catalogo globale a bassa latenza disabilitata

Per abilitare nuovamente la modalità GC a bassa latenza, riavviare Visual Studio. Per impostazione predefinita, Visual Studio abilita la modalità di bassa latenza di Garbage Collection ogni volta che si digita per garantire che il testo digitato non blocca le operazioni di Garbage Collection. Tuttavia, se una condizione di memoria insufficiente causa Visual Studio visualizzare l'avviso di sospensione automatica, modalità di bassa latenza Garbage Collection è disabilitata per la sessione. Riavviare Visual Studio abilita nuovamente il comportamento di catalogo globale predefinito. Per altre informazioni, vedere <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Cache di Visual Studio scaricate

Se si continua la sessione corrente di sviluppo o riavviare Visual Studio, tutte le cache di Visual Studio vengono svuotate immediatamente, ma inizia a eseguire la ricompilazione. Le cache scaricate includono le cache per le funzionalità seguenti:

- Trova tutti i riferimenti

- Passa a

- Aggiungi Using

Inoltre, verranno deselezionate anche le cache utilizzate per operazioni interne di Visual Studio.

> [!NOTE]
> L'avviso di sospensione automatica delle caratteristiche si verifica una sola volta a intervalli per soluzione, non su una singola sessione. Ciò significa che, se passa da Visual Basic a Visual c# (o viceversa) ed eseguire in un'altra condizione di memoria insufficiente, è possibile ottenere probabilmente un altro avviso di sospensione automatica delle caratteristiche.

## <a name="see-also"></a>Vedere anche

- [Procedura: Abilitare e disabilitare l'analisi della soluzione completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Principi fondamentali di Garbage Collection](/dotnet/standard/garbage-collection/fundamentals)
- [Considerazioni sulle prestazioni per soluzioni di grandi dimensioni](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)