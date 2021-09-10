---
title: Progettazione flussi di lavoro - ActivityDesigner ForEach &lt; T &gt;
description: Informazioni su come l'attività ForEach <T> esegue l'attività contenuta nel relativo corpo per ogni elemento in una raccolta Values specificata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 2f54139ddcaf214bf63292f49b9f847effed3ba5
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963495"
---
# <a name="foreachlttgt-activity-designer"></a>ActivityDesigner ForEach &lt; T &gt;

L'attività <xref:System.Activities.Statements.ForEach%601> esegue l'attività contenuta nel rispettivo oggetto <xref:System.Activities.Statements.ForEach%601.Body%2A> per ogni elemento di una raccolta di <xref:System.Activities.Statements.ForEach%601.Values%2A> specificata.

## <a name="foreacht-properties-in-the-workflow-designer"></a>Proprietà ForEach<T \> nel Progettazione flussi di lavoro

Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.ForEach%601> e ne viene descritto l'uso nella finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.ForEach%601>. Il valore predefinito è ForEach<Int32 \> . Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|Vero|Raccolta di elementi da scorrere. Per impostare , digitare un'Visual Basic nella casella Valori <xref:System.Activities.Statements.ForEach%601.Values%2A> dell'ActivityDesigner **ForEach<T \>** o nella griglia delle proprietà. |
|*TypeArgument*|Vero|Tipo degli elementi nella raccolta <xref:System.Activities.Statements.ForEach%601.Values%2A> specificata dal parametro generico *T*. Per impostazione predefinita, *TypeArgument* è impostato su **Int32.** Per modificare il tipo, modificare il valore della casella combinata *TypeArgument* nella griglia delle proprietà.|

Per impostazione predefinita, l'iteratore del ciclo è denominato **item**. È possibile modificare il nome della variabile di iteratore nell'ActivityDesigner <xref:System.Activities.Statements.ForEach%601>. L'iteratore del ciclo può essere usato nelle espressioni contenute in elementi figlio dell'attività <xref:System.Activities.Statements.ForEach%601>.

## <a name="see-also"></a>Vedi anche

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)
