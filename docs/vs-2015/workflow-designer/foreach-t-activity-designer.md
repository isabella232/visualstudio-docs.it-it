---
title: ForEach&lt;T&gt; ActivityDesigner | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: b118eb62f3055486e26f9d90a4e3abb74fe38660
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528135"
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
 [Attività ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)