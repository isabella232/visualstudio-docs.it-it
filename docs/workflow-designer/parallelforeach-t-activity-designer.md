---
title: ActivityDesigner ParallelForEach &lt; T &gt;
description: In Progettazione flussi di lavoro informazioni su come l'attività ParallelForEach enumera gli elementi di una raccolta ed esegue un'istruzione incorporata per ogni elemento della <T> raccolta in parallelo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 07158b14beca37272c19f4a5b896d7c70223a667
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122114563"
---
# <a name="parallelforeach-activity-designer"></a>Activity Designer ParallelForEach

L'attività <xref:System.Activities.Statements.ParallelForEach%601> enumera gli elementi di una raccolta ed esegue in parallelo un'istruzione incorporata per ogni elemento della raccolta, ovvero in modo asincrono sullo stesso thread. Usare questa attività di controllo del flusso anziché l'attività <xref:System.Activities.Statements.Sequence> se si prevede che le relative attività figlio diventeranno inattive.

<xref:System.Activities.Statements.ParallelForEach%601>L'attività ha una proprietà che contiene <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> un'espressione Visual Basic specificata dall'utente. L'attività <xref:System.Activities.Statements.ParallelForEach%601> valuta tale proprietà in seguito al completamento di ogni ramo. Se restituisce **true,** l'attività <xref:System.Activities.Statements.ParallelForEach%601> viene completata senza eseguire gli altri rami. Se non restituisce true, l'attività viene completata al termine di tutte le <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> attività  <xref:System.Activities.Statements.ParallelForEach%601> figlio.

## <a name="the-parallelforeacht-activity"></a>Attività ParallelForEach<\> T

<xref:System.Activities.Statements.ParallelForEach%601> enumera i relativi valori e pianifica l'oggetto per ogni valore su <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> cui esegue l'enumerazione. Esegue la pianificazione solo per l'elemento <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. La modalità di esecuzione del corpo varia a seconda che <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> diventi o meno inattivo.

Se <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> non diventa inattivo, viene eseguito in ordine inverso in quanto le attività pianificate vengono gestite come uno stack, con l'ultima attività pianificata eseguita per prima. Ad esempio, se si dispone di una raccolta {1,2,3,4} di in e si usa <xref:System.Activities.Statements.ParallelForEach%601> **writeLine** come corpo per scrivere il valore. Nella console sono stampati 4, 3, 2, 1. Ciò è dovuto al fatto **che WriteLine** non passa inattivo e quindi, dopo la pianificazione di 4 attività **WriteLine,** vengono eseguite usando un comportamento dello stack (prima nell'ultimo timeout).

Il processo cambia se invece le attività incluse in <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> possono diventare inattive, come nel caso delle attività <xref:System.ServiceModel.Activities.Receive> o <xref:System.Activities.Statements.Delay>. Quindi non è necessario attenderne il completamento. <xref:System.Activities.Statements.ParallelForEach%601> passa all'attività corpo pianificata successiva e prova a eseguirla. Se anche questa attività diventa inattiva, <xref:System.Activities.Statements.ParallelForEach%601> passa ancora alla successiva attività Body.

### <a name="using-the-parallelforeacht-activity-designer"></a>Uso dell'ActivityDesigner ParallelForEach \<T>

Accedere **all'ActivityDesigner \<T> ParallelForEach** nella categoria **Controllo Flow** della casella **degli strumenti**.

L'ActivityDesigner **ParallelForEach \<T>** può essere  trascinato dalla casella degli strumenti e rilasciato nell'area Progettazione flussi di lavoro in cui gli ActivityDesigner vengono in genere posizionati, ad esempio all'interno di un ActivityDesigner **Sequence.** Dopo l'eliminazione nel Progettazione flussi di lavoro, crea un'attività che per impostazione predefinita contiene un oggetto <xref:System.Activities.Statements.ParallelForEach%601> <xref:System.Activities.Activity.DisplayName%2A> **ParallelForEach<Int32 \> .**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>ParallelForEach<T \> nel Progettazione flussi di lavoro

Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.ParallelForEach%601> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo visualizzato nell'intestazione dell'ActivityDesigner. Il valore predefinito è **ParallelForEach \<Int32>**. Il valore può essere modificato facoltativamente nella **griglia** Proprietà o direttamente nell'intestazione di ActivityDesigner.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|Falso|Attività da eseguire per ogni elemento della raccolta. Per aggiungere l'attività, rilasciare un'attività dalla casella degli strumenti nella casella Corpo <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> dell'ActivityDesigner **ParallelForEach \<T>** con il testo del suggerimento "Drop Activity  Here".|
|**TypeArgument**|Vero|Tipo degli elementi nella raccolta <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> specificata dal parametro generico *T*. Per impostazione predefinita, **TypeArgument** è impostato su **Int32.** Per modificare il tipo T nell'ActivityDesigner **parallelForEach<\> T,** modificare il valore della casella combinata **TypeArgument** in Griglia delle proprietà.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|Vero|Raccolta di elementi da scorrere. Per impostare , digitare un'espressione Visual Basic nella casella Valori <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> dell'ActivityDesigner **ForEach \><T**   nella casella con il testo del  suggerimento "Immettere un'espressione VB" o nella casella Valori della finestra Proprietà.|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Valutato al termine di ogni iterazione. Se restituisce true, le iterazioni in sospeso pianificate vengono annullate. Se questa proprietà non è impostata, tutte le istruzioni pianificate vengono eseguite fino al completamento.|

Per impostazione predefinita, l'iteratore del ciclo è denominato item. È possibile modificare il nome della variabile iteratore nella **casella ForEach** in **\<T> ActivityDesigner ParallelForEach.** L'iteratore del ciclo può essere usato nelle espressioni contenute in elementi figlio dell'attività <xref:System.Activities.Statements.ParallelForEach%601>.

## <a name="see-also"></a>Vedi anche

- [Sequenza](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)