---
title: ActivityDesigner Progettazione flussi di lavoro-ForEach &lt; T &gt;
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30d43351211a6ff857630b47f05be77e27bd7951
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593915"
---
# <a name="foreachlttgt-activity-designer"></a>ActivityDesigner ForEach &lt; T &gt;

L'attività <xref:System.Activities.Statements.ForEach%601> esegue l'attività contenuta nel rispettivo oggetto <xref:System.Activities.Statements.ForEach%601.Body%2A> per ogni elemento di una raccolta di <xref:System.Activities.Statements.ForEach%601.Values%2A> specificata.

## <a name="foreacht-properties-in-the-workflow-designer"></a>Proprietà ForEach<T \> nell'progettazione flussi di lavoro

Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.ForEach%601> e ne viene descritto l'uso nella finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.ForEach%601>. Il valore predefinito è ForEach<Int32 \> . Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|Vero|Raccolta di elementi da scorrere. Per impostare <xref:System.Activities.Statements.ForEach%601.Values%2A> , digitare un'espressione Visual Basic nella casella **valori** dell'ActivityDesigner **foreach<\> T** o nella griglia delle proprietà.|
|*TypeArgument*|Vero|Tipo degli elementi nella <xref:System.Activities.Statements.ForEach%601.Values%2A> raccolta specificata dal parametro generico *T*. Per impostazione predefinita, *TypeArgument* è impostato su **Int32**. Per modificare il tipo, modificare il valore della casella combinata *TypeArgument* nella griglia delle proprietà.|

Per impostazione predefinita, l'iteratore del ciclo è denominato **elemento**. È possibile modificare il nome della variabile di iteratore nell'ActivityDesigner <xref:System.Activities.Statements.ForEach%601>. L'iteratore del ciclo può essere usato nelle espressioni contenute in elementi figlio dell'attività <xref:System.Activities.Statements.ForEach%601>.

## <a name="see-also"></a>Vedere anche

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)
