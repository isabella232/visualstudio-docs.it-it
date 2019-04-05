---
title: ForEach&lt;T&gt; ActivityDesigner | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 97732b92c5a90334917ad4e74667f88d605b647d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968134"
---
# <a name="foreachlttgt-activity-designer"></a>ForEach&lt;T&gt; ActivityDesigner
L'attività <xref:System.Activities.Statements.ForEach%601> esegue l'attività contenuta nel rispettivo oggetto <xref:System.Activities.Statements.ForEach%601.Body%2A> per ogni elemento di una raccolta di <xref:System.Activities.Statements.ForEach%601.Values%2A> specificata.  
  
## <a name="foreacht-properties-in-the-workflow-designer"></a>ForEach\<T > proprietà nella finestra di progettazione del flusso di lavoro  
 Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.ForEach%601> e ne viene descritto l'uso nella finestra di progettazione.  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.ForEach%601>. Il valore predefinito è ForEach\<Int32 >. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|  
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|Raccolta di elementi da scorrere. Per impostare il <xref:System.Activities.Statements.ForEach%601.Values%2A>, digitare un [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] espressione nel **valori** nella casella il **ForEach\<T >** attività della finestra di progettazione o nella griglia delle proprietà.|  
|*TypeArgument*|True|Il tipo degli elementi di <xref:System.Activities.Statements.ForEach%601.Values%2A> raccolta specificata dal parametro generico *T*. Per impostazione predefinita *TypeArgument* è impostata su **Int32**. Per modificare il tipo, modificare il valore della *TypeArgument* casella combinata nella griglia delle proprietà.|  
  
 Per impostazione predefinita, l'iteratore del ciclo è denominato **elemento**. È possibile modificare il nome della variabile di iteratore nell'ActivityDesigner <xref:System.Activities.Statements.ForEach%601>. L'iteratore del ciclo può essere usato nelle espressioni contenute in elementi figlio dell'attività <xref:System.Activities.Statements.ForEach%601>.  
  
## <a name="see-also"></a>Vedere anche  
 [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)