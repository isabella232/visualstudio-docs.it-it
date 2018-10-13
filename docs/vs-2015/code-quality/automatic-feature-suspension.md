---
title: Sospensione di funzionalità automatica | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c8aee8f4ef46d3621bf569b260d943180abd7ad5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49178178"
---
# <a name="automatic-feature-suspension"></a>Sospensione funzionalità automatica
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Se la memoria di sistema disponibili è minore o uguale a 200MB, Visual Studio visualizza il messaggio seguente nell'editor del codice.

 ![Testo dell'avviso la sospensione di analisi della soluzione completa](../code-quality/media/fsa-alert.png "FSA_Alert")

 Quando Visual Studio rileva una condizione di memoria insufficiente, sospende automaticamente alcune funzionalità avanzate per agevolare il rimane stabile. Quando questo avanzata viene visualizzato l'avviso di sospensione di funzionalità, Visual Studio continuano a funzionare come prima, ma saranno danneggiata leggermente le prestazioni.

 In una condizione di memoria insufficiente, si verifica quanto segue:

-   Analisi della soluzione completa per Visual c# e Visual Basic sono disabilitata.

-   [Operazione di Garbage Collection](http://msdn.microsoft.com/library/22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9) modalità di bassa latenza (GC) per Visual c# e Visual Basic sono disabilitati.

-   Vengono scaricate le cache di Visual Studio.

## <a name="improve-visual-studio-performance"></a>Migliorare le prestazioni di Visual Studio
 Per suggerimenti e trucchi su come migliorare le prestazioni di Visual Studio quando si lavora con soluzioni di grandi dimensioni o condizioni di memoria insufficiente, vedere [considerazioni sulle prestazioni per soluzioni di grandi dimensioni](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Analisi della soluzione completa sospesa
 Per impostazione predefinita, analisi della soluzione completa sono abilitato per Visual Basic e disabilitato per Visual c#. Tuttavia, in una condizione di memoria insufficiente, analisi della soluzione completa vengano disabilitato automaticamente in Visual Basic e Visual c#, indipendentemente dalle impostazioni nella finestra di dialogo Opzioni. Tuttavia, è possibile riabilitare analisi della soluzione completa, scegliendo la **riabilitare** pulsante nella scheda info barra quando viene visualizzata, selezionando il **Abilita analisi della soluzione completa** casella di controllo nella finestra di dialogo Opzioni o tramite Riavviare Visual Studio. Finestra di dialogo Opzioni Mostra sempre la soluzione completa corrente delle impostazioni di analisi. Per altre informazioni, vedere [procedura: abilitare e disabilitare analisi della soluzione completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>Catalogo globale a bassa latenza disabilitata
 Per abilitare nuovamente la modalità GC a bassa latenza, riavviare Visual Studio.  Per impostazione predefinita, Visual Studio abilita la modalità di bassa latenza di Garbage Collection ogni volta che si digita per garantire che il testo digitato non blocca le operazioni di Garbage Collection. Tuttavia, se una condizione di memoria insufficiente causa Visual Studio visualizzare l'avviso di sospensione automatica, modalità di bassa latenza Garbage Collection è disabilitata per la sessione. Riavviare Visual Studio, il comportamento di Garbage Collection predefinita verrà riattivata. Per altre informazioni, vedere <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Cache di Visual Studio scaricate

Tutte le cache di Visual Studio vengono svuotate immediatamente, ma verranno avviato il ripopolamento se continuare la sessione corrente di sviluppo o riavviare Visual Studio. Le cache scaricate includono le cache per le funzionalità seguenti.

-   Trova tutti i riferimenti

-   Passa a

-   Aggiungi Using

Inoltre, verranno deselezionate anche le cache utilizzate per operazioni interne di Visual Studio.

> [!NOTE]
> L'avviso di sospensione automatica delle caratteristiche si verifica una sola volta a intervalli per soluzione, non su una singola sessione. Ciò significa che, se passa da Visual Basic a Visual c# (o viceversa) ed eseguire in un'altra condizione di memoria insufficiente, è possibile ottenere probabilmente un altro avviso di sospensione automatica delle caratteristiche.

## <a name="see-also"></a>Vedere anche

- [Procedura: Abilitare e disabilitare l'analisi completa della soluzione](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Principi fondamentali di Garbage Collection](http://msdn.microsoft.com/library/67c5a20d-1be1-4ea7-8a9a-92b0b08658d2)
- [Considerazioni sulle prestazioni per soluzioni di grandi dimensioni](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)