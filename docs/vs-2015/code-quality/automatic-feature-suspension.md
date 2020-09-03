---
title: Sospensione automatica delle funzionalità | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b9c80ba76ba2da978c9cb475299ba0fc9e614120
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655141"
---
# <a name="automatic-feature-suspension"></a>Sospensione funzionalità automatica
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Se la memoria di sistema disponibile è inferiore a 200 MB, Visual Studio visualizzerà il messaggio seguente nell'editor di codice.

 ![Testo dell'avviso sospensione dell'analisi completa della soluzione](../code-quality/media/fsa-alert.png "FSA_Alert")

 Quando Visual Studio rileva una condizione di memoria insufficiente, sospende automaticamente determinate funzionalità avanzate per consentirne la stabilità. Quando viene visualizzato questo avviso di sospensione della funzionalità avanzata, Visual Studio continuerà a funzionare come prima, ma le prestazioni saranno leggermente ridotte.

 In una condizione di memoria insufficiente, si verifica quanto segue:

- L'analisi completa della soluzione per Visual C# e Visual Basic è disabilitata.

- La modalità di bassa latenza di [Garbage Collection](https://msdn.microsoft.com/library/22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9) (GC) per Visual C# e Visual Basic è disabilitata.

- Le cache di Visual Studio vengono scaricate.

## <a name="improve-visual-studio-performance"></a>Migliorare le prestazioni di Visual Studio
 Per suggerimenti e consigli su come migliorare le prestazioni di Visual Studio quando si gestiscono soluzioni di grandi dimensioni o condizioni di memoria insufficiente, vedere [considerazioni sulle prestazioni per soluzioni di grandi dimensioni](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Analisi completa della soluzione sospesa
 Per impostazione predefinita, l'analisi della soluzione completa è abilitata per Visual Basic e disabilitata per Visual C#. Tuttavia, in una condizione di memoria insufficiente, l'analisi della soluzione completa viene disabilitata automaticamente per Visual Basic e Visual C#, indipendentemente dalle impostazioni nella finestra di dialogo Opzioni. Tuttavia, è possibile riabilitare l'analisi completa della soluzione scegliendo il pulsante **riabilita** nella barra informazioni quando viene visualizzato, selezionando la casella di controllo **Abilita analisi della soluzione completa** nella finestra di dialogo Opzioni o riavviando Visual Studio. Nella finestra di dialogo Opzioni vengono sempre visualizzate le impostazioni di analisi della soluzione completa correnti. Per altre informazioni, vedere [procedura: abilitare e disabilitare l'analisi della soluzione completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>GC a bassa latenza disabilitata
 Per abilitare nuovamente la modalità a bassa latenza GC, riavviare Visual Studio.  Per impostazione predefinita, Visual Studio Abilita la modalità GC a bassa latenza ogni volta che si digita per assicurarsi che la digitazione non blocchi le operazioni GC. Tuttavia, se una condizione di memoria insufficiente fa in modo che Visual Studio visualizzi l'avviso di sospensione automatica, la modalità di bassa latenza GC viene disabilitata per tale sessione. Il riavvio di Visual Studio consentirà di riabilitare il comportamento GC predefinito. Per altre informazioni, vedere <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Cache di Visual Studio scaricate

Tutte le cache di Visual Studio vengono immediatamente svuotate, ma inizieranno a essere ripopolate se si continua la sessione di sviluppo corrente o si riavvia Visual Studio. Le cache scaricate includono le cache per le funzionalità seguenti.

- Trova tutti i riferimenti

- Passa a

- Aggiungi utilizzando

Vengono inoltre cancellate le cache utilizzate per le operazioni interne di Visual Studio.

> [!NOTE]
> L'avviso di sospensione della funzionalità automatica viene eseguito una sola volta per ogni singola soluzione, non per ogni singola sessione. Ciò significa che se si passa da Visual Basic a Visual C# (o viceversa) e si esegue un'altra condizione di memoria insufficiente, è possibile che venga visualizzato un altro avviso di sospensione automatica della funzionalità.

## <a name="see-also"></a>Vedere anche

- [Procedura: Abilitare e disabilitare l'analisi completa della soluzione](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Nozioni fondamentali di Garbage Collection](https://msdn.microsoft.com/library/67c5a20d-1be1-4ea7-8a9a-92b0b08658d2)
- [Considerazioni sulle prestazioni per soluzioni di grandi dimensioni](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)